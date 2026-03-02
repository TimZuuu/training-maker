# ETAP 7 — Append + refaktoryzacja (jeden pipeline)

## Finalny stan etapu

### TEXT
Mamy PL i CZ przetworzone podobnie.
Można je połączyć przez Append, ale to nadal oznacza podwójne czyszczenie.
Lepiej: połączyć dane wcześniej i czyścić jednym pipeline.

### TASK — Append jako nowe (wersja 1)
`Dołącz zapytania -> Dołącz zapytania jako nowe`.
Wybierz PL i CZ.
Nazwij wynik `SprzedażTOTAL`.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Powstaje nowe zapytanie z rekordami PL i CZ.
- Powstaje krok dołączania.

### TEXT
To działa, ale czyszczenie wykonaliśmy dwa razy.
Teraz przechodzimy do lepszej architektury.

### TASK — Refaktoryzacja append po `Source`
Usuń `SprzedażTOTAL`.
Wróć do zapytania sprzedaży PL.
Na kroku `Source` dodaj append PL+CZ, a dopiero potem zostaw kroki czyszczenia.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Append jest wcześnie w pipeline.
- Dalsze kroki działają na połączonych danych.
- Jest jeden wspólny pipeline.

### CHECKPOINT 3
Skopiuj cały kod M po refaktoryzacji.

## Log decyzji i poprawek (per blok)

### BLOK E7
- Typ: `TEXT/TASK/OBSERVATION`
- Decyzje:
  - Najpierw zwykły append, dopiero potem komentarz o nieefektywności.
  - Refaktoryzacja po `Source` jest obowiązkowa.
- Źródła: `4081-4114`, `4514`, `4133`.
