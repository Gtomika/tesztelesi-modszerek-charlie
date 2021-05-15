# Mutációs tesztelés eredmények

Ez a fájl tartalmazza, hogy mely csomagokon milyen 
lefedettséget és teszt erőt mutatott ki a mutációs tesztelés.

A teljes kódbázisra minden mutátorral nem lehet futtatni, mivel ez 
nagyon hosszú ideig fut, ezért csomagonként végeztük a méréseket.

# OLD_DEFAULTS mutátorok

Ezek a mutátorok a PIT egy alapértelmezett mutátor csoportját alkotják. 
A következők tartoznak ide:

 - Conditional Boundary: az *<, <=, >, >=* operátorokat cserélgeti.
 - Increments: A *++* és *--* operátorokat cserélgeti.
 - Invert Negatives: Az egészek -1-el szorzását cseréli 1-el szorzásra.
 - Math: A *+, -, szorzás, osztás* és egyéb aritmetikai műveleteket cserélgeti.
 - Negate Conditionals: A *==* és *!=* operátorokat cserélgeti.
 - Return Value: Primitív visszatérési értékeket módosít, például *true*-t *false*-ra, 1-et 0-ra.
 - Void Method Calls: A visszatérési érték nélküli metódusok hívását egyszerűen kitörli.
 
Két jellemzőt vizsgáltunk:

 - Mutációs lefedettség: Megmondja, hogy a teszt utasítások hány százalékát érintjük a a mutált kód tesztelése során. 
 - Teszt erő: megmondja, hogy a tesztek hány százalékát "ölték meg" a mutánsoknak. Egy mutáns akkor 
 hal meg, ha van legalább egy teszt, ami elbukik amiatt.
 
Ezeket a jellemzőket a PIT beleírja az elkészült jelentésbe, ami a *\target\pit-reports* alatt fog létrejönni.
 
Az *OLD_DEFAULTS* mutátorokkal futtava a PIT-et a projekt különböző csomagjain a 
következő eredményeket kaptuk:
 
 | Csomag\*    | Mutációs lefedettség   | Teszt erő | Futásidő
 | ---         | :-:                    | :-:       | ---
 | geometry    | 75%                    | 90%       | 7p 29mp
 | matrix      | 86%                    | 93%       | 1p 26mp
 | orientation | 7%                     | 80%       | 2mp
 | shape       | -                      | -         | Időtúllépés (40+ p)
 | transform   | 91%                    | 98%       | 26mp
 | tuple2D     | 86%                    | 93%       | 34mp
 | tuple3D     | 80%                    | 93%       | 21mp
   
\* A csomagnevek elejére mindig oda kell érteni az *us.ihmc.euclid*-et. A kevésbé 
lényeges, csomagokat nem vizsgáltuk (pl: *exceptions*)