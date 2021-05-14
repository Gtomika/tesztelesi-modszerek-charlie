# Tesztelési móddszerek projektmunka

Charlie csapat:
 - Gáspár Tamás
 - Magyar Ákos 
 - Daniel János Róbert
 
Eredeti repo:
https://github.com/ihmcrobotics/euclid

# Projekt struktúra

Ez egy Maven projekt.

# Unit tesztek

A projekt JUnit5-öt használ. Körülbelül 1700 teszt van a 
*\test* mappában. Ezek így futtathatóak:

 - *mvn clean test*
 
A futtatás körülbelül 1,5 - 2 percet vesz igénybe.

# Mutációs tesztelés PIT-el

A PIT a teljes kódbázist mutálni tudjuk, így: 

 - *mvn org.pitest:pitest-maven:mutationCoverage*
 
Ezt azonban **nem érdemes futtatni konfiguráció nélkül**, mivel a mutációs tesztelés 
exponenciális idejű. A projekt mérete miatt ez több óráig tart.

# A PIT konfigurálása

A PIT konfigurálását a POM.xml-ben tudjuk elvégezni, a paramétereket 
a PIT *<plugin>* részébe, azon belül pedig a *<configuration>* tag-ek közé kell helyezni. 
A legfontosabb lehetséges konfigurációk:

 - *targetClasses*: Megmondja, hogy melyik osztályok legyenek mutálva.
 - *targetTests*: Megmondja, hogy melyik tesztel legyenek futtatva az osztályok mutálása után.
 - *threads*: Hány szálon fusson a folyamat.
 - *mutators*: Azoknak a mutációknak a listája, amiket használni fog.
 
A konfigurációk teljes listája megtalálható [itt](http://pitest.org/quickstart/maven/).

# Példa konfiguráció

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

# Jelentések

A PIT az eredményeket a *\target\pit-reports* mappába rakja, *HTML* oldalként.

