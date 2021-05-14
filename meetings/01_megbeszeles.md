# 1. megbeszélés

Jelenlévők: Mindenki

Téma: Projekt felépítése saját környezeten.
Törlésre került két osztály:   

```
test/us/ihmc/euclid/tools/SingularValueDecomposition3DTest.java
test/us/ihmc/euclid/tools/SymmetricEigenDecomposition3DTest.java
```

Törlés oka: a két teszt javafx.utils.Pair objektumokat használkt, amely elavult java 11 óta. A Pair-re nem volt szükség, egyébként a projekt nem javafx-alapú

A csapatban két fő IntelliJ keretrendszert, egy fő Eclipse keretrendszert használ a teszteléshez.

# Kiírt feladat

## A projekt

Választani kell egy tetszőleges open-source projektet, amelyhez már léteznek tesztek, majd a kiválasztott feladatot végre kell hajtani. A projekt (tesztek nélkül) legalább 2000 nemüres, nem-komment sort kell, hogy tartalmazzon.

## Leadandók

Az elvégzett feladatokról és az eredményekről jelentést kell készíteni. A projekt forrását, az eredeti és a módosított teszthalmazt, a mérési környezet "saját" részét, valamint a jelentést összecsomagolva a bemutatás előtt le kell adni.

## Bemutatás
A bemutató órán a csapatok a többiek előtt röviden prezentálják a munkájukat és az eredményeiket.

## Feladat

Minden csapat választ magának egy témát az alábbiak közül:

- Tesztesetek bővítése branch szintű lefedettség alapján.
  - Branch szintű lefedettség-mérés megvalósítása.
  - Branch lefedettség növelése.
  - Teszt redundancia csökkentése.
- Tesztesetek bővítése függvény szintű lefedettség alapján.
  - Eljárás szintű lefedettség-mérés megvalósítása.
  - Eljárás lefedettség növelése.
  - Teszt redundancia csökkentése.
- Tesztesetek bővítése mutációs teszt segítségével.
  - Mutációk definíciója.
  - Tesztek bővítése.
  - Felesleges tesztesetek elhagyása.

# Kiválasztott projekt

```
- Tesztesetek bővítése mutációs teszt segítségével.
  - Mutációk definíciója.
  - Tesztek bővítése.
  - Felesleges tesztesetek elhagyása.
```