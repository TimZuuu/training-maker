# ## ETAP 7 — Append + refaktoryzacja: jeden pipeline zamiast dwóch

## Finalny Stan Etapu (z BP v2)

## ETAP 7 — Append + refaktoryzacja: jeden pipeline zamiast dwóch

### TEXT — Dlaczego nie zostawiamy dwóch osobnych pipeline'ów

Mamy `SprzedażPL` i `SprzedażCZ` przetworzone identycznie.
Da się je połączyć przez Append, ale to wciąż oznacza, że ten sam pipeline wykonał się dwa razy.
Lepiej: najpierw połączyć dane, a potem czyścić je jednym wspólnym pipeline.

### TASK — Append jako nowe (pierwsza wersja)

`Narzędzia główne -> Dołącz zapytania -> Dołącz zapytania jako nowe`.
Wybierz `SprzedażPL` i `SprzedażCZ`.
Nazwij wynik `SprzedażTOTAL`.

Opisz efekt.

### OBSERVATION (oczekiwane)
- Powstaje zapytanie z połączonymi wierszami PL i CZ.

### FILL
To działa, ale czyszczenie było liczone dwa razy (osobno dla PL i CZ).
Lepiej: najpierw dołączyć dane, potem wykonać jeden wspólny pipeline.

### TASK — Refaktoryzacja: Append wcześnie (po `Source`)

Usuń zapytanie `SprzedażTOTAL`.
Wróć do `SprzedażPL`.
Kliknij krok `Źródło` i dodaj Append tak, aby połączyć PL + CZ od razu po pobraniu danych.
Zostaw kolejne kroki czyszczenia, aby działały już na danych połączonych.

### OBSERVATION (oczekiwane)
- Append jest bardzo wcześnie w pipeline.
- Dalsze kroki działają na PL + CZ razem.
- Masz jeden wspólny pipeline.

### CHECKPOINT 3 (końcowy techniczny)
Skopiuj cały kod M końcowego zapytania po refaktoryzacji.


## Log decyzji i poprawek (per blok)

### BLOK 1
- Typ: TEXT/TASK/OBSERVATION/FILL (uzupełnij wg bloku)
- Decyzje:
- Poprawki:
- Źródła (transkrypt linie):

### BLOK 2
- Typ: TEXT/TASK/OBSERVATION/FILL (uzupełnij wg bloku)
- Decyzje:
- Poprawki:
- Źródła (transkrypt linie):


## Log decyzji i poprawek (uzupełniony)

### BLOK E7.TEXT — Narracja przed append
- Typ: `TEXT`
- Decyzje:
  - Ten `TEXT` jest krytyczny i był wprost wskazany jako wzorzec blueprintu.
- Źródła: `4514`, `1620`.

### BLOK E7.TASK.01 — Append as new
- Typ: `TASK`
- Decyzje:
  - Najpierw wykonać prosty append jako nowy.
- Źródła: `1625`, `4514`.

### BLOK E7.FILL + TASK.02 — Refaktoryzacja pipeline
- Typ: `FILL` + `TASK`
- Decyzje:
  - Po obserwacji dopiero wprowadzić argument o nieefektywności 2x pipeline.
  - Następnie append przenieść po `Source`, przed czyszczenie.
- Źródła: `1628`, `4514`.
