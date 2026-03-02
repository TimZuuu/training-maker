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
- Wyświetlana inna ikona dla Tabel niż dla Formuł

### TEXT — Co zaraz zrobimy
Teraz przechodzimy do elementów tabeli.
Wpisz ręcznie:
`=[nazwa_tabeli][`
Po wpisaniu sprawdź, co pokazuje lista elementów.
- Pojawia się lista elementów tabeli.
- Widzisz elementy specjalne z prefiksem `#` oraz kolumny.

### TASK — ODNIESIENIE 3 (`#All/#Data/#Headers/#Totals`)
Wpisz po kolei, każdą formułę w osobnej komórce:
`=[nazwa_tabeli][#All]`
`=[nazwa_tabeli][#Data]`
`=[nazwa_tabeli][#Headers]`
`=[nazwa_tabeli][#Totals]`
Jeśli po wpisaniu formuły widzisz error SPILL, oznacza to że formuła nie ma gdzie się wyświetlić, coś już jest w komórce w której próbuje wyświetlić dane.
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
Włącz `Total Row / Wiersz sum`. (kliknij checkbox)
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
- Poza tabelą pojawia się błąd, bo ta formuła działa poprawnie tylko dla wierszy należących do tabeli.

### TASK — Auto-expand 1/3 (nagłówek kolumny)
Wpisz nowy nagłówek kolumny: `Wartość`.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Po wpisaniu nagłówka tabela rozszerza się o nową kolumnę.

### TASK — Auto-expand 2/3 (formuła)
W pierwszej komórce tej nowej kolumny wpisz: `=`.
Kliknij kolumnę `Ilość` (lub wybierz strzałkami).
Wpisz `*`.
Kliknij kolumnę `Cena` (lub wybierz strzałkami).
Zatwierdź i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Formuła automatycznie kopiuje się w dół tabeli.

### TASK — Auto-expand 3/3 (nowy wiersz)
Dopisz nowy numer ID pod tabelą i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Tabela i formuły rozszerzają się na nowy wiersz.

### TEXT — Dlaczego XLOOKUP w tym ćwiczeniu
W tabeli sprzedaży mamy ID produktu, ale chcemy mieć też nazwę produktu.
Do tego ćwiczenia użyjemy `XLOOKUP`, bo jest wygodniejszy od `VLOOKUP` przy pracy na tabelach.
Łatwiej nim czytelnie wskazać kolumnę wyszukiwania i kolumnę wyniku.

### TASK — XLOOKUP (nazwa produktu)
Dodaj kolumnę `NazwaProduktu`.
Użyj funkcji `XLOOKUP`, aby po ID produktu pobrać nazwę z tabeli produktów.
Opisz, czy działa poprawnie.

### OBSERVATION (oczekiwane)
- Pojawiają się nazwy produktów.
- Formuła działa dla całej tabeli.
- Gdy odwołujesz się do kolumny w tej samej tabeli, nie musisz podawać nazwy tabeli.
- Gdy odwołujesz się do innej tabeli, podajesz jej nazwę.

### TASK — Sprzątanie przed PQ
Usuń kolumny ćwiczeniowe: `Wartość` i `NazwaProduktu`.

### TEXT — Płynne przejście do PQ
Świetnie! Dobra robota z tabelami.
Masz już mocny fundament, więc teraz przechodzimy do Power Query i budowy pipeline.

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
  - Część z `[` przeniesiona do `TEXT` (bez osobnego taska i observation).
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

### BLOK E1A.AutoExpand
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Auto-expand ma być podzielony na 3 osobne taski z oddzielnymi obserwacjami.
- Poprawki:
  - Rozbicie: nagłówek / formuła / nowy wiersz.
- Źródła: `2308-2321`, bezpośrednia uwaga użytkownika #2.

### BLOK E1A.XLOOKUP
- Typ: `TEXT` + `TASK` + `OBSERVATION`
- Decyzje:
  - Dodać wyjaśnienie, dlaczego tu `XLOOKUP` jest lepszy od `VLOOKUP`.
  - Dodać obserwację o różnicy odwołań: ta sama tabela vs inna tabela.
- Poprawki:
  - Dodano `TEXT` i rozszerzono `OBSERVATION`.
- Źródła: `145-156`, `4133`, bezpośrednia uwaga użytkownika #3.
