# ## ETAP 6 — Reuse pipeline: `SprzedażPL` -> `SprzedażCZ` (kopiowanie kodu M)

## Finalny Stan Etapu (z BP v2)

## ETAP 6 — Reuse pipeline: `SprzedażPL` -> `SprzedażCZ` (kopiowanie kodu M)

### TEXT — Po co kopiować pipeline

Masz analogiczne dane sprzedażowe dla Czech.
Zamiast klikać wszystko drugi raz, kopiujesz pipeline M.

### TASK — Kopiowanie kodu M z PL do CZ

W `SprzedażPL` otwórz Edytor zaawansowany i skopiuj cały kod.
W `SprzedażCZ` wklej kod i zmień w kroku `Source` nazwę tabeli wejściowej z `SprzedażPL` na `SprzedażCZ`.
Zatwierdź.

### OBSERVATION (oczekiwane)
- `SprzedażCZ` przechodzi przez analogiczne kroki.
- Ewentualne problemy zwykle wynikają z nazw źródła/kolumn.


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

### BLOK E6.TASK — Reuse M PL -> CZ
- Typ: `TASK`
- Decyzje:
  - Kopiujemy cały kod i zmieniamy tylko źródło w `Source`.
- Źródła: `4514`, `422`.
