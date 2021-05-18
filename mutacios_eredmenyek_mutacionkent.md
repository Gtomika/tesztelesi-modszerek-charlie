# Tartalomjegyzék
1. [Mutációs tesztelés eredmények](#eredmeny)
   1. [Tesztelés futtatása](#utests)
   2. [Mutatátorok](#mutator)
2. [Jellemzővizsgálat](#jellemzovizsgalat)
   - [Changed conditional boundary](#1)
   - [Increments](#2)
   - [Invert Negatives](#3)
   - [Math](#4)
   - [Negate Conditionals](#5)
   - [Void Method Calls](#6)
   - [Empty returns](#7)
   - [False returns](#8)
   - [True returns](#9)
   - [Null returns](#10)
   - [Primitive returns](#11)
   - [Remove Conditionals (else)](#12)
   - [Experimental Switch](#13)


# Mutációs tesztelés eredmények <a name="eredmeny"></a>

Ebben a fájlban gyűjtöttük össze, hogy egyes mutációkra a tesztesetek milyen lefedettséget adnak osztályonként. 

Ezt a lépést azért hajtottuk végre, mert túlságosan sok tesztet tartalmaz a projekt, hogy a Stronger group-ot futtassuk a tesztekre (még akkor is, ha a shape package-et figyelmen kívül hagyjuk). Emiatt a package-eket jobban szétszedtük, így minden egyes package-re külön lettek a mutációk futtatva.

## Tesztelés futtatása <a name="futtatas"></a>

- **Target classes**: us.ihmc.euclid.*
- **Target tests**: us.ihmc.euclid.*
- **Source dir**: <<Projekt mappája>>
- **Report dir**: *<<Projekt mappája>>\target\pit-reports*
- **Other params**: --testPlugin=junit5 --outputFormats XML,HTML, --mutators=**<<AKTUALIS_MUTATOR>>** --timeoutConst=400000 --excludedTestClasses=us.ihmc.euclid.shape.*

## Ahol az aktuális mutatátorok a *STRONGER* group elemei: <a name="mutator"></a>

Az *OLD_DEFAULTS* group-hoz hasonlóan:
 - Conditional Boundary: az *<, <=, >, >=* operátorokat cserélgeti.
 - Increments: A *++* és *--* operátorokat cserélgeti.
 - Invert Negatives: Az egészek -1-el szorzását cseréli 1-el szorzásra.
 - Math: A *+, -, szorzás, osztás* és egyéb aritmetikai műveleteket cserélgeti.
 - Negate Conditionals: A *==* és *!=* operátorokat cserélgeti.
 - Void Method Calls: A visszatérési érték nélküli metódusok hívását egyszerűen kitörli.

Továbbá:
 - Empty returns: Lecseréli az egyes visszatérési értékeket azok üres megfelelőjével.
 - False returns: A primitív és a beágyazott boolean értékeket azok hamis megfelelőjére cseréli
 - True returns: A primitív és a beágyazott boolean értékeket azok igazmegfelelőjére cseréli
 - Null returns: Lecseréli a visszatérési értékeket null-ra, amennyiben azok nem tartalmaznak @NotNull annotációt
 - Primitive returns: Lecseréli a primitív számok értékét 0-ra
 - Remove Conditionals (else): Eltünteti az összes feltételes állítást, hogy mindenképpen az else ág fusson le
 - Experimental Switch: A Switch default ága lesz az első case, amelyet a mutátor megtalál, minden más ág a default ág kifejezéseit kapja.

# Jellemzővizsgálat <a name="jellemzovizsgalat"></a>

Megfigyelt jellemzők:

 - Mutációs lefedettség: Megmondja, hogy a teszt utasítások hány százalékát érintjük a a mutált kód tesztelése során. 
 - Teszt erő: megmondja, hogy a tesztek hány százalékát "ölték meg" a mutánsoknak. Egy mutáns akkor hal meg, ha van legalább egy teszt, ami elbukik amiatt.


<br/>

## Changed conditional boundary - 8:51 <a name="1"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle.interfaces    | 0%                   | 0%        |
| geometry                | 63%                  | 67%       |
| geometry.interfaces     | 68%                  | 74%       |
| geometry.tools          | 26%                  | 27%       |
| matrix.interfaces       | 100%                 | 100%      |
| orientation.interfaces  | 0%                   | 0%        |
| rotationConversion      | 0%                   | 0%        |
| tools                   | 28%                  | 31%       |
| transform               | 100%                 | 100%      |
| tuple2D.interfaces      | 25%                  | 25%       |
| tuple3D.interfaces      | 8%                   | 8%        |
| tuple4D.interfaces      | 10%                  | 10%       |
| yawPitchRoll.interfaces | 0%                   | 0%        |

<br/><br/>


## Increments mutator - 9:13 <a name="2"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry.interfaces     | 91%                  | 96%       |
| geometry.tools          | 76%                  | 96%       |
| matrix.interfaces       | 100%                 | 100%      |
| tools                   | 92%                  | 97%       |
| transform               | 100%                 | 100%      |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D.interfaces      | 100%                 | 100%      |
| yawPitchRoll.interfaces | 100%                 | 100%     |

<br/><br/>

## Invert negatives - 14:16 <a name="3"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry                | 100%                 | 100%      |
| geometry.interfaces     | 100%                 | 100%      |
| geometry.tools          | 91%                  | 96%       |
| matrix.interfaces       | 100%                 | 100%      |
| tools                   | 96%                  | 96%       |
| transform               | 100%                 | 100%      |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D.interfaces      | 100%                 | 100%      |
| yawPitchRoll.interfaces | 0%                   | 0%        |

<br/><br/>

## Math mutator - 32:12 <a name="4"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry                | 79%                  | 88%       |
| geometry.interfaces     | 73%                  | 84%       |
| geometry.tools          | 94%                  | 97%       |
| matrix.interfaces       | 95%                  | 95%       |
| orientation.interfaces  | 0%                   | 0%        |
| rotationConversion      | 91%                  | 91%       |
| tools                   | 92%                  | 97%       |
| transform               | 60%                  | 60%       |
| tuple2D.interfaces      | 93%                  | 93%       |
| tuple3D.interfaces      | 95%                  | 95%       |
| tuple4D.interfaces      | 95%                  | 95%       |
| yawPitchRoll.interfaces | 0%                   | 0%        |

<br/><br/>

## Negate conditionals - 30:55 <a name="5"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry                | 79%                  | 88%       |
| geometry.interfaces     | 73%                  | 84%       |
| geometry.tools          | 94%                  | 97%       |
| matrix.interfaces       | 95%                  | 95%       |
| orientation.interfaces  | 0%                   | 0%        |
| rotationConversion      | 91%                  | 91%       |
| tools                   | 92%                  | 97%       |
| transform               | 60%                  | 60%       |
| tuple2D.interfaces      | 93%                  | 93%       |
| tuple3D.interfaces      | 95%                  | 95%       |
| tuple4D.interfaces      | 95%                  | 95%       |
| yawPitchRoll.interfaces | 0%                   | 0%        |

<br/><br/>

## Void method calls - 51:20 <a name="6"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő |
| ---                     | :-:                  | :-:       |
| axisAngle               | 76%                  | 87%       |
| axisAngle.interfaces    | 87%                  | 99%       |
| geometry                | 69%                  | 84%       |
| geometry.interfaces     | 45%                  | 80%       |
| geometry.tools          | 72%                  | 86%       |
| matrix                  | 76%                  | 81%       |
| matrix.interfaces       | 92%                  | 98%       |
| orientation             | 27%                  | 75%       |
| orientation.interfaces  | 69%                  | 98%       |
| tools                   | 72%                  | 85%       |
| transform               | 92%                  | 95%       |
| transform.interfaces    | 90%                  | 98%       |
| tuple2D                 | 71%                  | 79%       |
| tuple2D.interfaces      | 90%                  | 96%       |
| tuple3D                 | 64%                  | 82%       |
| tuple3D.interfaces      | 92%                  | 96%       |
| tuple4D                 | 81%                  | 93%       |
| tuple4D.interfaces      | 95%                  | 96%       |
| yawPitchRoll            | 83%                  | 83%       |
| yawPitchRoll.interfaces | 81%                  | 95%       |

<br/><br/>


## Empty returns - 4:23 <a name="7"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| axisAngle               | 0%                   | 0%        |
| geometry                | 23%                  | 75%       |
| geometry.interfaces     | 20%                  | 100%      |
| geometry.tools          | 18%                  | 28%       |
| matrix                  | 50%                  | 67%       |
| orientation             | 0%                   | 0%        |
| orientation.interfaces  | 0%                   | 0%        |
| tools                   | 41%                  | 57%       |
| transform               | 100%                 | 100%      |
| tuple2D                 | 60%                  | 100%      |
| tuple3D                 | 50%                  | 100%      |
| tuple4D                 | 25%                  | 50%       |
| yawPitchRoll            | 0%                   | 0%        |

<br/><br/>

## False returns - 9:40 <a name="8"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| axisAngle               | 67%                  | 100%      |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry                | 52%                  | 100%      |
| geometry.interfaces     | 56%                  | 97%       |
| geometry.tools          | 84%                  | 98%       |
| matrix                  | 63%                  | 83%       |
| matrix.interfaces       | 85%                  | 100%      |
| orientation             | 33%                  | 100%      |
| orientation.interfaces  | 33%                  | 67%       |
| tools                   | 73%                  | 96%       |
| transform               | 71%                  | 100%      |
| transform.interfaces    | 50%                  | 100%      |
| tuple2D                 | 44%                  | 54%       |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D                 | 40%                  | 67%       |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D                 | 33%                  | 67%       |
| tuple4D.interfaces      | 75%                  | 86%       |
| yawPitchRoll            | 67%                  | 100%      |
| yawPitchRoll.interfaces | 100%                 | 100%      |

<br/><br/>

## True returns - 16:23 <a name="9"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| .                       | 0%                   | 0%        |
| axisAngle               | 75%                  | 100%      |
| axisAngle.interfaces    | 92%                  | 92%       |
| geometry                | 50%                  | 92%       |
| geometry.interfaces     | 61%                  | 98%       |
| geometry.tools          | 80%                  | 90%       |
| matrix                  | 55%                  | 79%       |
| matrix.interfaces       | 90%                  | 100%      |
| orientation             | 25%                  | 100%      |
| orientation.interfaces  | 50%                  | 100%      |
| tools                   | 48%                  | 73%       |
| transform               | 81%                  | 81%       |
| transform.interfaces    | 100%                 | 100%      |
| tuple2D                 | 62%                  | 72%       |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D                 | 50%                  | 76%       |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D                 | 50%                  | 80%       |
| tuple4D.interfaces      | 100%                 | 100%      |
| yawPitchRoll            | 75%                  | 100%      |
| yawPitchRoll.interfaces | 100%                 | 100%      |

<br/><br/>

## Null returns - 8:49 <a name="10"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| .                       | 63%                  | 100%      |
| axisAngle               | 100%                 | 100%      |
| geometry                | 88%                  | 100%      |
| geometry.interfaces     | 79%                  | 98%       |
| geometry.tools          | 76%                  | 100%      |
| matrix                  | 100%                 | 100%      |
| tools                   | 77%                  | 100%      |
| transform               | 100%                 | 100%      |

<br/><br/>

## Primitive returns - 23:08 <a name="11"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| .                       | 71%                  | 88%       |
| axisAngle               | 100%                 | 100%      |
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry                | 52%                  | 100%      |
| geometry.interfaces     | 68%                  | 99%       |
| geometry.tools          | 89%                  | 99%       |
| matrix                  | 97%                  | 100%      |
| matrix.interfaces       | 100%                 | 100%      |
| orientation             | 50%                  | 100%      |
| orientation.interfaces  | 50%                  | 100%      |
| rotationConversion      | 100%                 | 100%      |
| tools                   | 81%                  | 97%       |
| transform               | 97%                  | 100%      |
| transform.interfaces    | 100%                 | 100%      |
| tuple2D                 | 100%                 | 100%      |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D                 | 100%                 | 100%      |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D                 | 100%                 | 100%      |
| tuple4D.interfaces      | 100%                 | 100%      |
| yawPitchRoll            | 100%                 | 100%      |
| yawPitchRoll.interfaces | 100%                 | 100%      |

<br/><br/>

## Remove Conditionals (else) - 25:13 <a name="12"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| axisAngle               | 100%                 | 100%      |
| axisAngle.interfaces    | 82%                  | 82%       |
| geometry                | 55%                  | 78%       |
| geometry.exceptions     | 100%                 | 100%      |
| geometry.interfaces     | 50%                  | 80%       |
| geometry.tools          | 73%                  | 82%       |
| matrix                  | 36%                  | 40%       |
| matrix.interfaces       | 44%                  | 44%       |
| orientation             | 0%                   | 0%        |
| orientation.interfaces  | 50%                  | 100%      |
| rotationConversion      | 23%                  | 23%       |
| tools                   | 64%                  | 71%       |
| transform               | 89%                  | 89%       |
| transform.interfaces    | 97%                  | 97%       |
| tuple2D                 | 100%                 | 100%      |
| tuple2D.interfaces      | 58%                  | 58%       |
| tuple3D                 | 81%                  | 87%       |
| tuple3D.interfaces      | 62%                  | 62%       |
| tuple4D                 | 50%                  | 50%       |
| tuple4D.interfaces      | 55%                  | 60%       |
| yawPitchRoll            | 100%                 | 100%      |
| yawPitchRoll.interfaces | 88%                  | 88%       |

<br/><br/>

## Experimental Switch - 2:45 <a name="13"></a>

| Csomag\*                | Mutációs lefedettség | Teszt erő | 
| ---                     | :-:                  | :-:       | 
| axisAngle.interfaces    | 100%                 | 100%      |
| geometry.tools          | 100%                 | 100%      |
| matrix.interfaces       | 100%                 | 100%      |
| tools                   | 33%                  | 33%       |
| tuple2D.interfaces      | 100%                 | 100%      |
| tuple3D.interfaces      | 100%                 | 100%      |
| tuple4D.interfaces      | 100%                 | 100%      |
| yawPitchRoll.interfaces | 100%                 | 100%      |
