# ## ETAP 1A — Ćwiczenia z Tabel (opcjonalne)

## Finalny Stan Etapu (z BP v2)

## ETAP 1A — Ćwiczenia z Tabel (opcjonalne)

### TASK — Odniesienia do tabeli i elementów (`#`)

Wpisuj formuły obok tabeli, jedno pod drugim.

1) Wpisz: `=[nazwa_tabeli]`
2) Wpisz: `=[nazwa_tabeli][`
3) Napisz cztery formuły:
   `=[nazwa_tabeli][#All]`
   `=[nazwa_tabeli][#Data]`
   `=[nazwa_tabeli][#Headers]`
   `=[nazwa_tabeli][#Totals]`

Po wpisaniu wszystkich czterech opisz, jaki efekt widzisz przy każdej z nich.

### OBSERVATION (oczekiwane)
- `#All` pokazuje całą tabelę.
- `#Data` pokazuje same dane.
- `#Headers` pokazuje nagłówki.
- `#Totals` zwraca błąd, jeśli tabela nie ma włączonego wiersza sum.

### FILL
Jeśli przy `#Totals` widzisz błąd: to spodziewane. Włącz „Wiersz sum” i zobacz, że odniesienie zaczyna działać. Odniesienia tabelaryczne pokazują aktualny stan tabeli.

### TASK — Symbol `@` (ten sam wiersz)

Wpisz obok tabeli formułę z odwołaniem do bieżącego wiersza, np.:
`=[@Ilość]`

Opisz, co zaobserwowałeś (jaki wynik zwraca ta formuła).

### OBSERVATION (oczekiwane)
- Zwracana jest pojedyncza wartość z tego samego wiersza, a nie cały zakres kolumny.

### TASK — Rozszerzanie tabeli + automatyczne kopiowanie formuły

W nagłówku nowej kolumny wpisz: `Wartość`.
Opisz, co zaobserwowałeś.

Następnie w pierwszej komórce tej kolumny wpisz:
`=`
kliknij kolumnę `Ilość`
wpisz `*`
kliknij kolumnę `Cena`
Zatwierdź.

Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Po wpisaniu nagłówka tabela rozszerza się o nową kolumnę.
- Po wpisaniu formuły formuła automatycznie kopiuje się do wszystkich wierszy.
- Nie trzeba przeciągać formuły ręcznie.

### TASK — XLOOKUP: pobranie nazwy produktu do tabeli sprzedaży

Dodaj kolumnę `NazwaProduktu`.
W pierwszym wierszu tej kolumny wpisz `XLOOKUP`, tak aby:
- szukał ID produktu z bieżącego wiersza tabeli sprzedaży,
- przeszukiwał kolumnę ID w tabeli `dimProdukty`,
- zwracał nazwę produktu.

Opisz, czy działa i co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- W kolumnie `NazwaProduktu` pojawiają się nazwy.
- Formuła działa dla całej tabeli bez ręcznego przeciągania.

### TASK — Przygotowanie do PQ

Usuń kolumny ćwiczeniowe: `Wartość` i `NazwaProduktu`.

### OBSERVATION (oczekiwane)
- Tabela wraca do układu wejściowego pod pipeline Power Query.


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

### BLOK E1A.TEXT.01 — Zapowiedź odniesień
- Typ: `TEXT`
- Decyzje:
  - Przed taskami ma być wyjaśnienie, że elementy tabeli to kolumny + elementy specjalne `#...`.
- Poprawki:
  - Wymuszone przywrócenie `TEXT` przed `TASK`.
- Źródła: `2342`, `2349`, `4514`.

### BLOK E1A.TASK.01 — `=[nazwa_tabeli]`
- Typ: `TASK`
- Decyzje:
  - Użytkownik wpisuje ręcznie; nie podawać gotowca do wklejenia.
  - Zwrócić uwagę na podpowiedź nazwy i ikonę tabeli.
- Poprawki:
  - Przywrócić pełniejszą instrukcję (w v2 było okrojone).
- Źródła: `2332`, `2342`.

### BLOK E1A.TASK.02-03 + OBS — `[` i `#All/#Data/#Headers/#Totals`
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - Ma być osobny `TEXT` o elementach `#` przed wpisywaniem 4 formuł.
  - Przy `#Totals` user ma dojść do #REF i opisać obserwację.
- Poprawki:
  - Wskazanie, że ten fragment był skrócony i wymaga rozszerzenia.
- Źródła: `2260`, `2270`, `2275`, `2385`.

### BLOK E1A.TASK/FILL — `#Totals` i Total Row
- Typ: `TASK` + `FILL`
- Decyzje:
  - Włączenie `Wiersz sum` to akcja użytkownika, więc to `TASK`, a nie czysty `FILL`.
- Poprawki:
  - Oznaczone do korekty klasyfikacji (zgodnie z Twoją uwagę #3).
- Źródła: `2278`, `2281`, `2391`, `2399`.

### BLOK E1A.TASK — Symbol `@`
- Typ: `TASK`
- Decyzje:
  - Formuła ma być wpisana poza tabelą i zawierać nazwę tabeli, nie samą kolumnę.
- Poprawki:
  - Oznaczone do korekty (zgodnie z Twoją uwagę #4).
- Źródła: `2295`, `2300`.
