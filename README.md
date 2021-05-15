# Tesztelési móddszerek projektmunka

Charlie csapat:
 - Gáspár Tamás
 - Magyar Ákos 
 - Daniel János Róbert
 
Eredeti repo:
https://github.com/ihmcrobotics/euclid


# Tartalomjegyzék
1. [Projekt struktúra](#introduction)
   1. [Unit tesztek](#utests)
2. [Mutációs tesztelés PIT-el (Vanilla)](#pit-v)
   1. [PIT konfigurálása](#pit-config)
      1. [Példa konfiguráció](#pit-config-ex)
3. [Mutációs tesztelés PIT-el (IntelliJ)](#pit-j)
4. [Jelentések](#jelentes)

# Projekt struktúra <a name="introduction"></a>

Ez egy Maven projekt.

## Unit tesztek <a name="utests"></a>

A projekt JUnit5-öt használ. Körülbelül 1700 teszt van a 
*\test* mappában. Ezek így futtathatóak:

 - *mvn clean test*
 
A futtatás körülbelül 1,5 - 2 percet vesz igénybe.

# Mutációs tesztelés PIT-el (Vanilla) <a name="pit-v"></a>

A PIT a teljes kódbázist mutálni tudjuk, így: 

 - *mvn org.pitest:pitest-maven:mutationCoverage*
 
Ezt azonban **nem érdemes futtatni konfiguráció nélkül**, mivel a mutációs tesztelés 
exponenciális idejű. A projekt mérete miatt ez több óráig tart.

## A PIT konfigurálása <a name="pit-config"></a>

A PIT konfigurálását a POM.xml-ben tudjuk elvégezni, a paramétereket 
a PIT *<plugin>* részébe, azon belül pedig a *<configuration>* tag-ek közé kell helyezni. 
A legfontosabb lehetséges konfigurációk:

 - *targetClasses*: Megmondja, hogy melyik osztályok legyenek mutálva.
 - *targetTests*: Megmondja, hogy melyik tesztel legyenek futtatva az osztályok mutálása után.
 - *threads*: Hány szálon fusson a folyamat.
 - *mutators*: Azoknak a mutációknak a listája, amiket használni fog.
 
A konfigurációk teljes listája megtalálható [itt](http://pitest.org/quickstart/maven/).

### Példa konfiguráció<a name="pit-config-ex"></a>

Itt egy lehetséges konfiguráció, ha csak a *tuple2D* csomag tartalmát 
szeretnénk mutálni és tesztelni. Ugyanez a konfiguráció megvan a POM.xml-ben is.

```
<configuration>
	<!-- Legyenek csak a tuple2D csomag osztályai mutálva --> 
	<targetClasses>
		<param>us.ihmc.euclid.tuple2D*</param>
	</targetClasses>
	
	<!-- Legyenek csak a tuple2D csomag teszjei futtava -->
	<targetTests>
		<param>us.ihmc.euclid.tuple2D*</param>
	</targetTests>
	
	<!-- 8 szál használata. -->
	<threads>8</threads>
	
	<!-- Használt mutátorok. -->
	<mutators>
		<!-- Ez 7 darab alap mutátort foglal magába. -->
		<mutator>OLD_DEFAULTS</mutator>
	</mutators>
</configuration>
```

Ha ezzel a konfigurációval futtatjuk újra a PIT-et (a fentebb látott 
*mvn* utasítással, akkor kevesebb mint egy perc alatt végez.

# Mutációs tesztelés PIT-el (IntelliJ) <a name="pit-j"></a>

A PIT a teljes kódbázist mutálni tudjuk IntelliJ-ben is. Érdemes telepíteni a [*PIT mutation testing Idea plugin*](https://plugins.jetbrains.com/plugin/7119-pit-mutation-testing-idea-plugin)-t. Mivel a projekt Jupiter teszteket is tartalmaz (JUnit 5), ezért fontos, hogy ebben a módban futtassuk a PIT-et. Ehhez a következő kapcsoló szükséges: **--testPlugin=junit5**

A plugin telepítése után megjelenik egy új konfigurációs lehetőség, melyet a következőképpen tudjuk használni a mutációs tesztelés futtatásához (Vanilla példája IntelliJ-ben):

- **Target classes**: us.ihmc.euclid.tuple2D*
- **Target tests**: us.ihmc.euclid.tuple2D*
- **Source dir**: <<Projekt mappája>>
- **Report dir**: *<<Projekt mappája>>\target\pit-reports*
- **Other params**: --testPlugin=junit5 --outputFormats XML,HTML, mutators OLD_DEFAULTS

*Megjegyzés: Java 16-al futtatva a mutációs tesztelést Unsupported class file major version 60 IllegalArgumentExceptiont kapunk, ez nem befolyásolja a mutációs tesztelés kimenetelét. Mindenesetre érdemes Java 11-et használni a mutációs teszteléshez.*

Természetesen a pom.xml tartalma maradhat változatlan, az nem befolyásolja a tesztek futását.

# Jelentések <a name="jelentes"></a>

A PIT az eredményeket a *\target\pit-reports* mappába rakja, *HTML* oldalként. 
A konkrét eredményekért lásd a *mutacio_eredmenyek* fájlt.

