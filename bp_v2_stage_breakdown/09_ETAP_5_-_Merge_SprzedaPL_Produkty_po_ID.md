# ## ETAP 5 — Merge: `SprzedażPL` + `Produkty` po ID

## Finalny Stan Etapu (z BP v2)

## ETAP 5 — Merge: `SprzedażPL` + `Produkty` po ID

### TEXT — Sens merge w tym ćwiczeniu

W tabeli sprzedaży masz ID produktu, ale potrzebujesz też jego nazwy.
Zrobimy klasyczne połączenie faktu z wymiarem.

### TASK — Scal zapytania jako nowe (Merge)

`Narzędzia główne -> Scal zapytania -> Scal zapytania jako nowe`.

W oknie:
1) Na górze wybierz `SprzedażPL`.
2) Na dole wybierz `Produkty`.
3) Kliknij kolumnę ID produktu w `SprzedażPL`.
4) Kliknij kolumnę ID produktu w `Produkty`.
5) Typ złączenia: `Lewy zewnętrzny`.
6) Sprawdź komunikat, ile rekordów sparowano.
7) Zatwierdź.

Opisz efekt.

### OBSERVATION (oczekiwane)
- Powstaje nowe zapytanie.
- Pojawia się kolumna z wartościami typu `Tabela`.
- Widać krok scalania.
- Jeśli nie sparowało wszystkiego: możliwy problem z ID/typem danych.

### FILL
Na tym etapie tabela jest dołączona, ale nierozwinięta.
Kliknięcie komórki nowej kolumny pokaże w dolnym panelu jej zawartość.
Rozwinięcie = dodanie kolumn z dołączonej tabeli.

### TASK — Rozwinięcie dołączonej tabeli

Kliknij ikonę rozwijania w kolumnie po scaleniu.
Wybierz do rozwinięcia tylko nazwę produktu.
Zdecyduj, czy zostawiasz prefiks nazwy.

### OBSERVATION (oczekiwane)
- Pojawia się kolumna z nazwą produktu.
- Dochodzi krok rozwinięcia.


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

### BLOK E5.TEXT — Sens merge
- Typ: `TEXT`
- Decyzje:
  - Wyjaśnienie: mamy ID produktu, potrzebujemy nazwy.
- Źródła: `4019`, `4514`.

### BLOK E5.TASK — Merge + liczba dopasowań
- Typ: `TASK`
- Decyzje:
  - Obowiązkowo sprawdzić komunikat o liczbie sparowanych rekordów.
- Źródła: `4133`.

### BLOK E5.FILL — Nierozwinięta tabela po merge
- Typ: `FILL`
- Decyzje:
  - Dodać wyjaśnienie: dołączona tabela jest nierozwinięta; rozwinięcie = dodanie kolumn.
- Źródła: `4133`.
