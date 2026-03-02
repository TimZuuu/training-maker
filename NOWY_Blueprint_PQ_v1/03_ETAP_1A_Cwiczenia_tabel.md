# ETAP 1A — Ćwiczenia z Tabel (opcjonalne)

## Finalny stan etapu

### TEXT — Zapowiedź ćwiczenia
Skoro tabele są już nazwane, przećwiczymy odniesienia strukturalne.
Wpisuj formuły w kolumnie J, jedno pod drugim.
To trening mechaniki odniesień.

### TASK — ODNIESIENIE 1 (cała tabela)
Wpisz ręcznie:
`=[nazwa_tabeli]`
Zwróć uwagę, czy Excel podpowiada pełną nazwę i jaką ikonkę pokazuje.
Po Enter opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Excel podpowiada nazwę tabeli.
- Po Enter wyświetla się wynik odniesienia do tabeli.

### TEXT — Co zaraz zrobimy
Teraz przechodzimy do elementów tabeli: kolumn i elementów specjalnych z `#`.

### TASK — ODNIESIENIE 2 (nawias kwadratowy)
Wpisz ręcznie:
`=[nazwa_tabeli][`
Po wpisaniu opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Pojawia się lista elementów tabeli.
- Widzisz elementy specjalne z prefiksem `#` oraz kolumny.

### TASK — ODNIESIENIE 3 (`#All/#Data/#Headers/#Totals`)
Wpisz po kolei, każdą formułę w osobnej komórce:
`=[nazwa_tabeli][#All]`
`=[nazwa_tabeli][#Data]`
`=[nazwa_tabeli][#Headers]`
`=[nazwa_tabeli][#Totals]`
Po wpisaniu wszystkich opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- `#All` pokazuje całość.
- `#Data` pokazuje dane.
- `#Headers` pokazuje nagłówki.
- `#Totals` zwraca `#REF`, jeśli wiersz sum nie jest włączony.

### TEXT — Wyjaśnienie `#REF`
Spodziewaliśmy się tego.
Odwołujesz się do `#Totals`, a tabela nie ma jeszcze wiersza sum.

### TASK — Włączenie `Total Row`
Kliknij tabelę.
Przejdź do `Table Design / Projektowanie tabeli`.
Włącz `Total Row / Wiersz sum`.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- `#REF` znika.
- `#Totals` zaczyna działać.
- Odniesienia pokazują aktualny stan tabeli.

### TASK — Symbol `@` poza tabelą
Wpisz w komórce obok tabeli, w tym samym wierszu:
`=[nazwa_tabeli][@Ilość]`
Następnie przeciągnij formułę w dół poza obszar tabeli.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- W obszarze tabeli zwracana jest pojedyncza wartość z bieżącego wiersza.
- Poza tabelą pojawia się błąd, bo nie ma wiersza kontekstu tabeli.

### TASK — Auto-expand (rozbite kroki)
1. Wpisz nowy nagłówek kolumny: `Wartość`.
2. Opisz, co zaobserwowałeś.
3. W pierwszej komórce tej kolumny wpisz: `=`.
4. Kliknij kolumnę `Ilość` (lub wybierz strzałkami).
5. Wpisz `*`.
6. Kliknij kolumnę `Cena` (lub wybierz strzałkami).
7. Zatwierdź i opisz, co zaobserwowałeś.
8. Dopisz nowy numer ID pod tabelą i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Po wpisaniu nagłówka tabela rozszerza się o nową kolumnę.
- Formuła automatycznie kopiuje się w dół tabeli.
- Po dopisaniu nowego wiersza tabela i formuły rozszerzają się.

### TASK — XLOOKUP (nazwa produktu)
Dodaj kolumnę `NazwaProduktu`.
Wpisz `XLOOKUP`, aby po ID produktu pobrać nazwę z tabeli produktów.
Opisz, czy działa poprawnie.

### OBSERVATION (oczekiwane)
- Pojawiają się nazwy produktów.
- Formuła działa dla całej tabeli.

### TASK — Sprzątanie przed PQ
Usuń kolumny ćwiczeniowe: `Wartość` i `NazwaProduktu`.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Tabela wraca do układu wyjściowego pod Power Query.

## Log decyzji i poprawek (per blok)

### BLOK E1A.TEXT.01
- Typ: `TEXT`
- Decyzje:
  - Ma być jawny `TEXT` przed taskami odniesień.
- Poprawki:
  - Dodano pełny wstęp przed `TASK`.
- Źródła: `2342`, `2349`, bezpośrednia uwaga użytkownika #2.

### BLOK E1A.TASK.01-03
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Rozdzielić na: najpierw sama nazwa tabeli, potem `[` i dopiero `#...`.
- Poprawki:
  - Rozbicie na osobne taski.
- Źródła: `2247`, `2260`, `2270`, `2372`.

### BLOK E1A.TASK.TotalRow
- Typ: `TASK` (+ `TEXT` wyjaśniający)
- Decyzje:
  - To nie jest sam `FILL`; użytkownik ma wykonać akcję włączenia Total Row.
- Poprawki:
  - Przeklasyfikowano z `FILL` do `TASK`.
- Źródła: `2391`, `2399`, bezpośrednia uwaga użytkownika #3.

### BLOK E1A.TASK.@
- Typ: `TASK`
- Decyzje:
  - Formuła poza tabelą ma zawierać nazwę tabeli.
  - Ma być krok przeciągania poza tabelę.
- Poprawki:
  - Skorygowano formułę i dodano przeciąganie.
- Źródła: `2295`, `2297`, `2298`, bezpośrednia uwaga użytkownika #4.
