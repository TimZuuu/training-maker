# ## ETAP 3 — Typy danych, błędy i filtrowanie

## Finalny Stan Etapu (z BP v2)

## ETAP 3 — Typy danych, błędy i filtrowanie

### TEXT — Dlaczego typy danych są krytyczne

Typ danych to wymóg, nie opcja.
Program musi wiedzieć, czy ma do czynienia z liczbą, datą, tekstem, walutą.
Zaniedbanie typów danych kończy się błędami obliczeń, merge i sortowania.

### TASK — Konflikt kroków: zmiana nazwy kolumny a `Zmieniono typ`

Otwórz zapytanie `SprzedażPL`.
Kliknij krok `Źródło`.
Zmień nazwę jednej kolumny (np. dodaj `1` na końcu).

Kliknij kolejne kroki po prawej i sprawdź, co się dzieje.

### OBSERVATION (oczekiwane)
- Pojawia się nowy krok zmiany nazwy.
- Krok `Zmieniono typ` (lub podobny) może się wysypać, bo odwołuje się do starej nazwy.

### TASK — Ręczna poprawka kodu kroku `Zmieniono typ`

Kliknij krok `Zmieniono typ`.
Rozwiń pasek formuły i popraw starą nazwę kolumny na nową.

Opisz, co się zmieniło.

### OBSERVATION (oczekiwane)
- Błąd znika i kolejne kroki znów działają.

### TASK — `Cena`: pierwsza próba zmiany typu (`Dodaj nowy krok`)

W kolumnie `Cena` ustaw typ `Waluta`.
Gdy pojawi się pytanie, wybierz `Dodaj nowy krok`.

Opisz efekt w panelu kroków.

### OBSERVATION (oczekiwane)
- Powstaje dodatkowy krok zmiany typu.
- Kolumna jest przekształcana drugi raz.

### TASK — `Cena`: właściwa wersja (`Zamień bieżący`)

Usuń nowy krok.
Powtórz zmianę typu `Cena -> Waluta`, ale wybierz `Zamień bieżący`.

### OBSERVATION (oczekiwane)
- Nie powstaje nowy krok.
- Istniejący krok zostaje podmieniony.

### TASK — `Ilość`: wymuszenie typu i diagnoza błędu

Ustaw typ kolumny `Ilość` na `Liczba całkowita`.
Kliknij komórkę z błędem i przeczytaj raport w dolnym panelu.

### OBSERVATION (oczekiwane)
- Pojawiają się błędy tam, gdzie był tekst.
- Raport mówi o braku możliwości konwersji tekstu na liczbę.

### FILL
Jeśli przypadkiem klikniesz bezpośrednio link `Error` i utworzy się krok prowadzący do błędu, po prostu usuń ten krok i wróć.

### TASK — Zamień błędy na 0

PPM na nagłówku `Ilość` -> `Zamień błędy` -> wpisz `0`.

### OBSERVATION (oczekiwane)
- Błędy zostają zamienione na zera.
- Powstaje krok zamiany błędów.

### TASK — Filtr: usuń 0 i `null`

W filtrze kolumny `Ilość` odznacz `0` i `(null)`.
Zatwierdź filtr.

### OBSERVATION (oczekiwane)
- Wiersze z `0` i `null` znikają.
- Powstaje krok filtrowania.

### FILL
Power Query zapisuje Twoje kliknięcia jako kod M.
Dlatego zawsze warto sprawdzić, jaki dokładnie warunek wygenerował się w kroku filtra.

### CHECKPOINT 2
Skopiuj cały kod M z `SprzedażPL` po typach, błędach i filtrach.


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

### BLOK E3.TEXT — Waga typów
- Typ: `TEXT`
- Decyzje:
  - To ma być mocny wykład: typy to wymóg, nie opcja.
- Źródła: `3505`, `2102`.

### BLOK E3.TASK/OBS — Rename vs Changed Type
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Użytkownik ma kliknąć kroki i sam zauważyć błąd zależności.
- Źródła: `1519`, `3505`.

### BLOK E3.TASK — Add new step vs Replace current
- Typ: `TASK`
- Decyzje:
  - Najpierw pokazać zły wariant, potem poprawny.
  - Dodać uzasadnienie: niepotrzebnie przekształcone drugi raz.
- Źródła: `3505`.

### BLOK E3.TASK/OBS/FILL — Error, Replace Errors, filtr
- Typ: `TASK` + `OBSERVATION` + `FILL`
- Decyzje:
  - Nie robić ćwiczenia z tworzeniem dodatkowego kroku drill-to-error.
  - Instrukcje mają być klikalne i precyzyjne (PPM na etykiecie kolumny).
  - W `FILL` zachować uwagę o tym, że kliknięcia są kodem i filtr może się różnie wygenerować.
- Źródła: `1544`, `3505`.
