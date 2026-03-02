# ETAP 3 — Typy danych, błędy i filtrowanie

## Finalny stan etapu

### TEXT
Teraz bardzo istotny temat w pracy na danych: typ danych.
Warto nie traktować tego jako opcji, tylko jako wymóg.
Nawyk zwracania uwagi na typ danych pozwala uniknąć wielu błędów.
Program musi wiedzieć, czy pracuje na liczbie, dacie, tekście lub walucie.

### TASK — Zmiana nazwy i konflikt kroku `Zmieniono typ`
Otwórz zapytanie sprzedaży PL.
Kliknij krok `Źródło`.
Zmień nazwę jednej kolumny.
Kliknij po kolei wszystkie kroki po prawej i sprawdź, co zaobserwowałeś w panelu kroków i podglądzie.

### OBSERVATION (oczekiwane)
- Pojawia się nowy krok zmiany nazwy.
- Na kroku `Zmieniono typ` pojawia się błąd zależności od starej nazwy.

### TASK — Ręczna poprawka kroku `Zmieniono typ`
Kliknij krok `Zmieniono typ`.
W pasku formuły popraw starą nazwę kolumny na nową.
Sprawdź kroki ponownie i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Błąd znika.

### TASK — Typ `Cena`: pierwsza próba (`Dodaj nowy krok`)
Znajdź kolumnę `Cena`.
Zmień typ na `Waluta`.
Jeśli pojawi się wybór, kliknij `Dodaj nowy krok`.
Następnie spójrz na panel kroków i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Powstaje dodatkowy krok.
- Kolumna jest niepotrzebnie przekształcona drugi raz.

### TEXT
Żeby przekształcić kolumnę tylko raz, zrobimy to inaczej.

### TASK — Typ `Cena`: właściwa wersja (`Zamień bieżący`)
Usuń nowy krok.
Powtórz zmianę typu `Cena -> Waluta`, wybierając `Zamień bieżący`.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Nie powstaje dodatkowy krok.
- Ustawienie typu jest wykonane raz.

### TASK — `Ilość`: wymuszenie typu i diagnoza błędu
Zmień typ kolumny `Ilość` na `Liczba całkowita`.
Kliknij komórkę z błędem.
W dolnym panelu sprawdź raport błędu i opisz jego treść.

### OBSERVATION (oczekiwane)
- Pojawiają się błędy konwersji tekst -> liczba.

### TASK — Zamiana błędów na 0
Kliknij PPM na etykietę kolumny `Ilość`.
Wybierz `Zamień błędy` i wpisz `0`.
Opisz, co zaobserwowałeś w danych i krokach.

### OBSERVATION (oczekiwane)
- Błędy zamienione na zera.
- Powstaje krok zamiany błędów.

### TASK — Filtr 0 i null
W kolumnie `Ilość` kliknij strzałkę filtra po prawej stronie nagłówka.
Odznacz `0` oraz `(null)`.
Zatwierdź.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Znikają wiersze z `0` i `null`.
- Powstaje krok filtrowania.

### FILL
Uwaga: Twoje klikanie jest interpretowane przez PQ i zamieniane na kod.
W zależności od rozkładu danych ten sam filtr może wygenerować inny warunek.
Dlatego zawsze sprawdzaj kod kroku filtra.

### CHECKPOINT 2
Skopiuj cały kod M po tym etapie (typy, błędy, filtr).

## Log decyzji i poprawek (per blok)

### BLOK E3
- Typ: `TEXT/TASK/OBSERVATION/FILL`
- Decyzje:
  - Typy danych jako wymóg, nie opcja.
  - Obserwacja zawsze na końcu taska.
  - Bez zadania tworzącego dodatkowy krok przez kliknięcie linku Error.
  - Instrukcje klikalne i precyzyjne (PPM na nagłówku).
- Źródła: `3505`, `3519-3651`, `3933-3938`.
