# 4. megbeszélés

Jelenlévők: Mindenki

Téma: Helyzetjelentés.

# Jelenlegi állás:

OLD_DEFAULTS futtatása package-enként, shape TIME_OUT-ként jelenik meg a jelentésben
STRONGER futtatása más környezeti változókkal is MEMORY_ERROR. Megoldás:
STRONGER futtatása történjen mutációnként az összes package-re, shape legyen excluded a tesztelés során.