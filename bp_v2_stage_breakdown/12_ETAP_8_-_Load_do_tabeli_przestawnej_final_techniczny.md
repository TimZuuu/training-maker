# ## ETAP 8 — Load do tabeli przestawnej + final techniczny

## Finalny Stan Etapu (z BP v2)

## ETAP 8 — Load do tabeli przestawnej + final techniczny

### TASK — Załaduj wynik do pivot table

Wybierz zapytanie końcowe.
Kliknij: `Załaduj do... -> Tabela przestawna`.
Ustaw dowolny prosty pivot pokazujący sprzedaż (np. suma `Wartość` po produkcie).

Opcjonalnie: wklej screen do czatu.

### OBSERVATION (oczekiwane)
- Pivot działa i pokazuje sensowne agregacje.
- `Wartość` jest poprawnie liczona, a suma nie wygląda na przypadkową.

## Koniec przebiegu technicznego

Po wykonaniu szkolenia można przejść do domknięcia (pytania końcowe, refleksja, co wdrożysz).
Ta część należy do prompta szkoleniowego, nie do blueprintu technicznego.

## Rejestr checkpointów (v2)

- CHECKPOINT 1: pierwszy kod M po wejściu do PQ (`SprzedażPL`, stan początkowy).
- CHECKPOINT 2: kod M po typach, błędach i filtrach (`SprzedażPL`).
- CHECKPOINT 3: kod M końcowego pipeline po append + refaktoryzacji.

## Anty-regresja (co nie może zniknąć w kolejnych wersjach)

- Każdy ważny task percepcyjny ma sekcję `OBSERVATION`.
- W ETAPIE 1 jest minimum tabel pod PQ + opcjonalny blok ćwiczeń.
- W ETAPIE 1A jest ćwiczenie `XLOOKUP` oraz usunięcie kolumn ćwiczeniowych.
- W ETAPIE 2 jest orientacja w edytorze PQ, w tym dolny panel szczegółów.
- W ETAPIE 3 jest konflikt nazw kolumny z krokiem `Zmieniono typ` i ręczna korekta.
- Jest scenariusz `Add new step` vs `Replace current` dla typów danych.
- Jest merge + rozwinięcie + komentarz o problemach dopasowania ID.
- Jest reuse kodu M PL -> CZ.
- Jest append "jako nowe" i potem refaktoryzacja append wcześnie.
- Jest finalny load do pivot table.

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

### BLOK E8.TASK — Pivot + walidacja
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Finalny wynik ma być w pivocie.
  - Screen opcjonalny, bardziej jako element interakcji niż twarda walidacja.
- Źródła: `4133`, `1684`.
