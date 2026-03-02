# ETAP 2 — Power Query: wejście, orientacja, checkpoint

## Finalny stan etapu

### TEXT
Teraz przechodzimy do Power Query.
To nowa warstwa Excela do pracy z danymi.
Możesz tam zrobić prawie wszystko, co robisz w klasycznym Excelu, ale w sposób bezpieczniejszy, bardziej powtarzalny i zwykle szybszy przy większych danych.

### TASK — Wejście do PQ z tabeli sprzedaży
Kliknij tabelę `fctSprzedażPL`.
Przejdź do `Dane -> Z tabeli/zakresu`.
(Alternatywnie: PPM na tabeli i skrót do pobrania danych z tabeli/zakresu, jeśli jest dostępny w Twojej wersji.)
Zatwierdź.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Otwiera się edytor Power Query.

### TEXT — Mapa edytora
Po lewej widzisz listę zapytań (`query` = `zapytanie`).
Po prawej widzisz pojedyncze kroki transformacji danych (Applied Steps).
Na środku widzisz podgląd efektu aktualnie wybranego kroku.
Nad tabelą widzisz pasek formuły (kod aktywnego kroku).
Na dole masz panel szczegółów komórki, ale pojawia się dopiero po kliknięciu komórki w podglądzie.

### TASK — Przegląd kroków i dolnego panelu
Kliknij dowolną komórkę w podglądzie, żeby aktywować dolny panel.
Następnie klikaj po kolei kroki po prawej stronie.
Za każdym kliknięciem obserwuj:
- jak zmienia się widok tabeli na środku,
- jak zmienia się kod aktywnego kroku w pasku nad tabelą.
Na koniec opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Zmienia się podgląd zależnie od aktywnego kroku.
- Pasek formuły pokazuje kod aktywnego kroku.
- Dolny panel pokazuje szczegóły zaznaczonej komórki (wartość albo informację o błędzie).

### TEXT — Advanced Editor: po co i kiedy
W Power Query możesz edytować kod na dwa sposoby:
- w pasku formuły nad tabelą: wygodne do drobnych poprawek pojedynczego kroku,
- w `Advanced Editor`: wygodne do większych zmian, przeklejania fragmentów i modyfikacji struktury zapytania.
To właśnie stąd będziesz kopiować kod do chatu.
Taki kod jest idealnym wejściem dla chatu, bo od razu widać nazwę tabeli źródłowej i nazwy kolumn.

### TASK — Edytor zaawansowany
Przejdź do `Narzędzia główne -> Advanced Editor / Edytor zaawansowany`.
Otwórz kod i zobacz, jak wygląda pełna struktura zapytania.

## Log decyzji i poprawek (per blok)

### BLOK E2.TEXT.01
- Typ: `TEXT`
- Decyzje:
  - W ETAPIE 2 ma być obszerniejsze intro do PQ jako "nowej warstwy Excela".
- Źródła: `2677`, `2720`.

### BLOK E2.TASK.01
- Typ: `TASK`
- Decyzje:
  - Wejście ma wskazywać konkretnie tabelę `fctSprzedażPL`.
- Źródła: bezpośrednia uwaga użytkownika #2.

### BLOK E2.TEXT.02
- Typ: `TEXT`
- Decyzje:
  - Mapa edytora ma być mniej sucha i bardziej opisowa.
  - Termin `query` ma być od razu wyjaśniony jako `zapytanie`.
- Źródła: `1995`, `2788`, `2955`.

### BLOK E2.TASK.02
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Ten task ma akcentować, że klikając kroki, widzimy zmianę widoku tabeli i kodu kroku.
- Źródła: `2685`, `2804`, `2966`.

### BLOK E2.TEXT.03
- Typ: `TEXT`
- Decyzje:
  - Dolny panel opisywać funkcjonalnie i wskazać, że pojawia się po kliknięciu komórki.
- Źródła: `1840`, `2514`, `2720`.

### BLOK E2.TEXT.04 + TASK.03
- Typ: `TEXT` + `TASK`
- Decyzje:
  - Dodać osobny tekst do Advanced Editor (co robić w pasku, co w Advanced Editor).
- Źródła: `2812`, `2824`, `2918`.
