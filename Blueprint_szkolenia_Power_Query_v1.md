# Blueprint szkolenia: Power Query – podstawy pipeline (PL UI) – v1

Zakres: tabele w Excelu (minimum pod PQ + opcjonalne ćwiczenia), Power Query: typy danych, błędy, kolumna z przykładu, merge, reuse kodu M, append + refaktoryzacja, load do tabeli przestawnej, checkpointy kodu.

## ETAP 0 — Cel szkolenia

Na tym szkoleniu nauczysz się pracy z Tabelami oraz Power Query jako alternatywnego trybu pracy z danymi.

To podejście:
- nie polega na klasycznych formułach przeciąganych po arkuszu,
- minimalizuje ryzyko błędów (przesunięte zakresy, brak przeciągnięcia),
- ułatwia kontrolę poprawności,
- szczególnie dobrze sprawdza się w plikach cyklicznych: raz dobrze zbudowany plik staje się aplikacją:
  a) podmieniasz dane wejściowe,
  b) odświeżasz Power Query,
  c) masz gotowy wynik do druku/wysłania/analizy.

To nie będzie tylko szkolenie z funkcjonalności narzędzia. To będzie szkolenie z podejścia do danych i baz.

## ETAP 1 — Tabele w Excelu (minimum pod Power Query)

W pliku masz kilka arkuszy z danymi. Problem w tym, że Excel nie bardzo „wie”, gdzie te dane są.
Operowanie adresami typu A1:H80 jest kruche i wadliwe: dochodzą kolumny i wiersze, ktoś może przesunąć zakres, tabela może się rozjechać. Masa okazji do rozwalenia mechanizmu i błędów.

Dlatego, aby zachować poprawność danych, niezbędne jest pracowanie na zakresach zdefiniowanych jako Tabele.

### TASK — Zamiana zakresu na Tabele (SprzedażPL)

W arkuszu SprzedażPL kliknij gdziekolwiek w dane.
Naciśnij Ctrl + T.
Upewnij się, że zaznaczone jest „Moja tabela ma nagłówki”.
Zatwierdź (Enter).

Opisz, co zaobserwowałeś w arkuszu (jak zmienił się wygląd i zachowanie danych).

### OBSERVATION (oczekiwane)
- Dane zostały objęte obiektem Tabela.
- Pojawia się nowe formatowanie tabelaryczne.
- Kliknięcie w tabelę pokazuje dodatkowe opcje pracy z Tabelą.

### FILL
Excel teraz „widzi” tabelę jako obiekt. To będzie kluczowe dla Power Query i dla bezpiecznych odniesień.

### TASK — Zakładka narzędzi tabeli i nazwa tabeli

Kliknij w tabelę.
Znajdź zakładkę narzędzi tabeli (Projektowanie tabeli / Narzędzia tabeli - nazwa zależy od wersji).
Po lewej znajdź pole „Nazwa tabeli”.

Napisz, jaką nazwę widzisz teraz w polu nazwy tabeli.

### OBSERVATION (oczekiwane)
- Excel nadaje domyślną nazwę (np. Tabela1 / Table1).

Teraz przejdziemy do nazywania tabel.

W bazach danych mamy dwa główne typy tabel:
- Facts: zdarzenia, których przybywa (np. sprzedaż).
- Dimensions: słowniki/opisy, relatywnie stałe (np. produkty, klienci).

To może wydawać się mało istotne teraz, ale przy większych projektach robi ogromną różnicę: jedne tabele rosną i są „ruchem”, a drugie opisują świat i zmieniają się rzadziej.

Dlatego przy nazywaniu tabel warto stosować prefiksy, np. `fct` i `dim`.
Przykład: `dimSklepy` sugeruje stabilny słownik obiektów; `fctSprzedaż` sugeruje strumień zdarzeń.

Dodatkowo warto utrzymać konwencję wizualną: mała litera w prefiksie, wielka litera w nazwie (czytelność rośnie).

### TASK — Ustalenie nazw tabel (fct/dim)

Zastanów się, które tabele w pliku są faktami, a które wymiarami.
Zaproponuj nazwę dla tabeli sprzedaży (np. `fctSprzedażPL`) i dla pozostałych tabel.

Następnie wpisz ustalone nazwy do pola „Nazwa tabeli” dla każdej tabeli.
Na koniec opisz, jakie nazwy ustaliłeś.

### OBSERVATION (oczekiwane)
- Tabela sprzedaży zostaje nazwana jako `fct...`
- Pozostałe tabele jako `dim...`
- Nazwy są jednoznaczne i czytelne.

To jest minimum potrzebne do Power Query.

Jeśli chcesz, możemy zrobić kilka dodatkowych ćwiczeń z Tabel, bo są bardzo wartościowe i użyteczne w codziennej pracy.
Te ćwiczenia zajmą tyle, ile pozwala Ci czas szkolenia (typowo kilka-kilkanaście minut w zależności od tempa).
Jeśli pominiesz — przechodzimy od razu do Power Query.

## ETAP 1A — Ćwiczenia z Tabel (opcjonalne)

### TASK — Odniesienia do tabeli i elementów (`#`)

Wpisuj formuły w kolumnie J, jedno pod drugim.

1) Wpisz: `=[nazwa_tabeli]`
   Zwracaj uwagę, że Excel podpowiada pełną nazwę i pokazuje ikonkę tabeli przy nazwie.

2) Teraz wpisz: `=[nazwa_tabeli][`
   (nawias kwadratowy otwiera listę elementów i kolumn tabeli).

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
Jeśli przy `#Totals` widzisz błąd: spodziewaliśmy się tego, bo tabela nie ma jeszcze wiersza sum. Włącz „Wiersz sum” w narzędziach tabeli i zobacz, że odniesienie zaczyna działać. Odniesienia do tabeli dostosowują się automatycznie do aktualnego stanu tabeli. Możesz to też przetestować, zmieniając wartości w tabeli.

### TASK — Symbol `@` (ten sam wiersz)

Wpisz w komórce obok tabeli (w tym samym wierszu co dane):
`=[@Ilość]` (wybierz kolumnę z listy, nie wpisuj na ślepo)

Opisz, co zaobserwowałeś (jaki wynik zwraca ta formuła).

### OBSERVATION (oczekiwane)
- Zwracana jest pojedyncza wartość z tego samego wiersza, a nie cały zakres/kolumna.

### TASK — Rozszerzanie tabeli + automatyczne kopiowanie formuły

W nagłówku w kolumnie X (na potrzeby ćwiczenia) wpisz słowo: `Wartość`.
Opisz, co zaobserwowałeś.

Następnie w pierwszej komórce tej nowej kolumny wpisz:
`=`
kliknij kolumnę `Ilość` (lub wybierz strzałkami)
wpisz `*`
kliknij kolumnę `Cena`
Zatwierdź.

Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Po wpisaniu nagłówka tabela rozszerza się o nową kolumnę.
- Po wpisaniu formuły formuła automatycznie kopiuje się do wszystkich wierszy tabeli.
- Nie trzeba przeciągać formuły.

Teraz kluczowe: w tabeli sprzedaży mamy ID produktu, ale chcielibyśmy też mieć nazwę produktu.
Zrobimy to funkcją `XLOOKUP`, bo jest wygodniejsza niż `VLOOKUP`, szczególnie przy pracy na tabelach.

### TASK — XLOOKUP — pobranie nazwy produktu do tabeli sprzedaży

Dodaj w tabeli nową kolumnę: `NazwaProduktu`.
W pierwszym wierszu tej kolumny wpisz formułę `XLOOKUP`, tak aby:
- szukała ID produktu z bieżącego wiersza tabeli sprzedaży,
- przeszukiwała kolumnę ID w tabeli `dimProdukty`,
- zwracała nazwę produktu.

Opisz, czy działa i co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- W kolumnie `NazwaProduktu` pojawiają się nazwy.
- Formuła działa dla wielu wierszy bez ręcznego przeciągnięcia (tabela robi to za Ciebie).

Zanim przejdziemy do Power Query, usuwamy dwie kolumny dodane w ćwiczeniach (`Wartość` i `NazwaProduktu`). Były potrzebne tylko do treningu mechaniki.

## ETAP 2 — Power Query: wejście i orientacja

### TASK — Usunięcie kolumn ćwiczeniowych przed Power Query

Usuń z tabeli sprzedaży kolumny: `Wartość` oraz `NazwaProduktu`.
(Szybka akcja przed przejściem do Power Query.)

Teraz przechodzimy do Power Query.

Power Query to osobna warstwa pracy z danymi — silnik transformacji.
Pozwala wykonywać operacje na danych w sposób powtarzalny i kontrolowany.
W praktyce: zamiast budować plik na dziesiątkach formuł, budujesz pipeline transformacji, który odświeżasz.

### TASK — Dodanie tabeli SprzedażPL do Power Query

Kliknij w tabelę `fctSprzedażPL`.
Przejdź do zakładki Dane.
Kliknij: `Z tabeli/zakresu`.
Zatwierdź.

Opisz, co zaobserwowałeś (co się otworzyło).

### OBSERVATION (oczekiwane)
- Otworzyło się okno/edytor Power Query.

To jest edytor Power Query.

Po lewej: lista zapytań (`query = zapytanie`).
Po prawej: pojedyncze kroki transformacji danego query (np. filtr, zmiana typu, usunięcie duplikatów).
Na środku: tabela — efekt aktualnie wybranego kroku.
Nad tabelą: pasek kodu pokazujący kod wybranego kroku.

Dodatkowo na dole jest pole z detalami zaznaczonej komórki — pojawia się dopiero po kliknięciu dowolnej komórki w tabeli.

### TASK — Dolne pole + kroki po prawej

Kliknij dowolną komórkę w tabeli podglądu.
Zobacz, co pojawia się w polu na dole.

Następnie kliknij po kolei kilka kroków po prawej stronie i obserwuj, jak zmienia się:
- tabela na środku,
- pasek kodu nad tabelą.

Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Pole na dole pokazuje szczegóły zaznaczonej komórki (wartość albo raport błędu).
- Klikanie kroków zmienia widok tabeli.
- Pasek kodu pokazuje kod aktywnego kroku.

### TASK — Edytor zaawansowany (M) + checkpoint

Przejdź do Narzędzia główne i kliknij Edytor zaawansowany.

Zobaczysz kod w języku M (ten język jest też używany w Power BI).
Widzisz strukturę `let ... in` oraz krok `Source` i kolejne kroki jako instrukcje.

Skopiuj cały kod i wklej do czatu jako checkpoint.

### CHECKPOINT
Wklej cały kod M z Edytora zaawansowanego (pierwszy checkpoint).

## ETAP 2A — Zamknij i załaduj + odświeżanie + Załaduj do

### TASK — Zamknij i załaduj

Wyjdź z edytora, klikając `Zamknij i załaduj`.
Staramy się nie używać klasycznego `X` w prawym górnym rogu, bo `Zamknij i załaduj` daje nam kontrolę nad sposobem załadowania wyniku do Excela.

Opisz, co zaobserwowałeś w Excelu.

### OBSERVATION (oczekiwane)
- Powstała tabela wynikowa w nowym arkuszu (domyślnie).

Ta tabela to wynik działania zapytania.
Nie traktuj jej jak kopii — to efekt pipeline'u.
Sprawdzimy to na dwa sposoby: kasowanie w wyniku i zmiana w źródle.

### TASK — Test odświeżania (2 działania)

1) W tabeli wynikowej usuń kilka wartości. Potem PPM na tabeli wynikowej -> `Odśwież`.
2) Wróć do tabeli źródłowej, zmień jedną wartość. Wróć do tabeli wynikowej i ponownie -> `Odśwież`.

Na koniec opisz, co zaobserwowałeś w obu przypadkach.

### OBSERVATION (oczekiwane)
- Skasowane dane w tabeli wynikowej wracają po odświeżeniu.
- Zmiana w tabeli źródłowej pojawia się w wyniku po odświeżeniu.

### FILL
Każde odświeżenie to ponowne wykonanie kroków transformacji na źródle.

### TASK — Załaduj do: tabela przestawna, potem tylko połączenie

Kliknij tabelę wynikową.
Przejdź do zakładki Zapytanie.
Kliknij `Załaduj do...`
Wybierz: `Tabela przestawna` i zatwierdź.
Excel poinformuje, że można załadować wynik tylko do jednego miejsca naraz i poprzednia tabela wynikowa zostanie usunięta — kliknij `OK`.

Opisz, co zaobserwowałeś.

Następnie ponownie: `Zapytanie -> Załaduj do... -> Tylko połączenie`.
Opisz, co zaobserwowałeś i co zostało w pliku.

### OBSERVATION (oczekiwane)
- Powstała tabela przestawna oparta o wynik zapytania.
- Po ustawieniu `Tylko połączenie` wynik nie jest wyświetlany jako tabela/pivot, ale zapytanie nadal istnieje.
- Zostaje zbędny arkusz po wynikach, który można usunąć.

### FILL
Teraz nie potrzebujemy wyświetlać tych query. Przechodzimy do budowy i ćwiczenia transformacji. Wynik załadujemy, gdy transformacja będzie gotowa.

### TASK — Sprzątanie po ładowaniu

Usuń zbędny arkusz, który pozostał po wcześniejszych operacjach ładowania wyników (teraz jest pusty/zbędny).

## ETAP 3 — Typy danych, błędy, filtrowanie

Teraz bardzo istotny temat w pracy na danych: typ danych.
Warto nie traktować tego jako opcji, tylko jako wymóg.
Nawyk zwracania uwagi na typ danych pozwala uniknąć wielu błędów.

Program musi wiedzieć:
- czy ma do czynienia z liczbą (żeby liczyć),
- czy z datą (żeby budować chronologię),
- czy z tekstem (żeby nie próbować liczyć),
- czy z walutą / liczbą dziesiętną (żeby nie generować błędów i zaokrągleń).

Zaniedbanie typów danych prowadzi do: błędnych wyników, problemów z merge, złego sortowania, błędów na końcu procesu.

### TASK — Konflikt kroków: zmiana nazwy kolumny i `Zmieniono typ`

Otwórz zapytanie `SprzedażPL` (PPM -> `Edytuj`).
Kliknij krok `Źródło`.
Zmień nazwę jednej kolumny (np. dodaj `1` na końcu) i zatwierdź (Enter).

Kliknij po kolei wszystkie kroki po prawej stronie i sprawdź, jak zmienia się podgląd danych.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Pojawia się nowy krok zmiany nazwy.
- Jeden z kolejnych kroków przestaje działać (typowo `Zmieniono typ`), bo oczekuje starej nazwy.

Kroki w Power Query zależą od siebie. Jeśli zmienisz coś w strukturze danych (np. nazwę kolumny), kolejne kroki mogą przestać działać.

### TASK — Poprawka w pasku kodu dla kroku `Zmieniono typ`

Kliknij krok `Zmieniono typ`.
Rozwiń pasek kodu nad tabelą.
Znajdź starą nazwę kolumny i popraw ją ręcznie na nową.
Zatwierdź.

Kliknij ponownie kilka kolejnych kroków i opisz, co teraz zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Błąd znika i kroki znów działają poprawnie.

### TASK — Zmiana typu `Cena`: Dodaj nowy krok (pierwsza próba)

Znajdź w tabeli kolumnę `Cena`.
Kliknij ikonkę typu danych przy jej nazwie i ustaw typ `Waluta`.
Jeśli pojawi się pytanie: `Dodaj nowy krok / Zamień bieżący` — wybierz `Dodaj nowy krok`.

Następnie spójrz na panel kroków po prawej i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Powstaje dodatkowy krok zmiany typu.
- Kolumna jest niepotrzebnie przekształcana drugi raz.
- Lista kroków wydłuża się bez potrzeby.

Nie chcemy przekształcać tej samej kolumny dwa razy. To komplikuje logikę zapytania. Ustawimy typ tylko raz.

### TASK — Zmiana typu `Cena`: `Zamień bieżący` (właściwa wersja)

Usuń nowo powstały krok (`X` przy kroku).
Powtórz zmianę typu kolumny `Cena` na `Waluta`, ale tym razem wybierz `Zamień bieżący`.

Opisz, co zaobserwowałeś w panelu kroków.

### OBSERVATION (oczekiwane)
- Nie powstaje dodatkowy krok.
- Istniejący krok zostaje zmodyfikowany.
- Typ jest ustawiony tylko raz.

Spójrz teraz na kolumnę `Ilość`.
Jeśli w kolumnie są różne typy danych, Power Query może nadać typ `Dowolny` (`Any`).
`Any` oznacza: system nie jest pewien typu — może tu być wszystko.

### TASK — `Ilość`: wymuszenie typu liczbowego i diagnoza błędu

Kliknij ikonkę typu przy kolumnie `Ilość` i ustaw typ `Liczba całkowita`.

Opisz, co zaobserwowałeś w danych.

Kliknij komórkę z błędem. W polu na dole sprawdź raport błędu i opisz, co on mówi.

### OBSERVATION (oczekiwane)
- Pojawiają się błędy w wierszach, gdzie były wartości tekstowe.
- Raport błędu wskazuje brak możliwości konwersji tekstu na liczbę.

### TASK — Zamień błędy na 0

Kliknij PPM na nagłówku kolumny `Ilość`.
Wybierz: `Zamień błędy`.
Wpisz `0` i zatwierdź.

Opisz, co zaobserwowałeś w danych i w panelu kroków.

### OBSERVATION (oczekiwane)
- Błędy zostały zastąpione zerami.
- Powstał nowy krok.
- Kolumna nie pokazuje już błędów.

### TASK — Filtr: usuń 0 i `null`

W kolumnie `Ilość` kliknij strzałkę filtra po prawej stronie nagłówka.
Odznacz: `0` oraz `(null)`.
Zatwierdź filtr.

Opisz, co zaobserwowałeś w danych i w panelu kroków.

### OBSERVATION (oczekiwane)
- Zniknęły wiersze z `0` i `null`.
- Powstał krok filtrowania.

### FILL
Uwaga: Twoje klikanie jest interpretowane przez Power Query i zamieniane na kod.
Kod filtrowania zależy od rozkładu danych.
Jeśli w kolumnie są różne liczby, `0` i `null` — zwykle powstaje filtr typu: `<> 0` oraz `<> null`.
Jeśli jednak w kolumnie byłyby tylko `1`, `0` i `null` — ta sama akcja może wygenerować filtr: wartość `= 1`.
Dlatego warto patrzeć, jaki kod powstał w kroku filtrowania.

### CHECKPOINT
Skopiuj cały kod z Edytora zaawansowanego (stan po typach, błędach i filtrach) i wklej do czatu.

## ETAP 4 — Kolumna z przykładu: Wartość (`Cena * Ilość`)

Teraz zrobimy bardzo praktyczną rzecz: policzymy wartość sprzedaży.
W Excelu zrobiłbyś to formułą. W Power Query zrobimy to jako krok transformacji — powtarzalny i bezpieczny.

### TASK — Kolumna z przykładu (z wybranych kolumn)

Przejdź do zakładki `Dodaj kolumnę`.
Przytrzymaj `Ctrl` i zaznacz dwie kolumny: `Cena` oraz `Ilość`.
Kliknij strzałkę pod `Kolumna z przykładu` i wybierz: `Z wybranych kolumn`.

Pojawi się nowa kolumna do wpisywania przykładów.
Wpisz kilka przykładów (dla 2-3 wierszy) tak, aby odpowiadały mnożeniu `Cena * Ilość`.
Po wpisaniu wartości zatwierdź (Enter).
Zmień nazwę nowej kolumny na `Wartość`.

Opisz, co zaobserwowałeś: co zrobił Power Query i jaki krok pojawił się po prawej.

### OBSERVATION (oczekiwane)
- Power Query dopasował regułę na podstawie przykładów i utworzył nową kolumnę.
- Powstał nowy krok w panelu.
- Kolumna została nazwana `Wartość`.

### FILL
To jest przydatna funkcja: nie musisz znać składni M, żeby budować część transformacji.
Ostatecznie najwygodniej jest zmieniać kod z Chatem, ale dobrze wiedzieć, jak czasem samemu dodać kolumnę.

## ETAP 5 — Merge: SprzedażPL + Produkty po ID

W tabeli sprzedaży masz ID produktu, ale chcesz mieć też jego nazwę.
Zrobimy to jak w bazach danych: łącząc fakty z wymiarem (`fact + dimension`).

### TASK — Scal zapytania jako nowe (Merge)

W `Narzędzia główne` kliknij: `Scal zapytania -> Scal zapytania jako nowe`.

W oknie scalania:
1) Na górze wybierz `SprzedażPL`.
2) Na dole wybierz `Produkty`.
3) Kliknij kolumnę ID produktu w `SprzedażPL`.
4) Kliknij kolumnę ID produktu w `Produkty`.
5) Upewnij się, że typ złączenia to `Lewy zewnętrzny` (zachowaj wszystkie ze `SprzedażPL`).
   Powinno wyświetlić się, ile rekordów zostało sparowanych. Jeśli nie wszystkie — możliwy problem z ID.
6) Zatwierdź.

Opisz, co zaobserwowałeś (co powstało w tabeli i w panelu kroków).

### OBSERVATION (oczekiwane)
- Powstaje nowe zapytanie.
- W tabeli pojawia się nowa kolumna z wartościami typu `Tabela`.
- W panelu kroków dochodzi krok scalania.

Póki co dołączyliśmy tabelę, ale jest ona nierozwinięta.
Jeśli klikniesz komórkę w nowej kolumnie, w polu na dole zobaczysz, co ta komórka zawiera.

Rozwinięcie = dodanie kolumn z dołączonej tabeli.

### TASK — Rozwinięcie dołączonej tabeli (dodanie kolumn)

W kolumnie po scaleniu kliknij ikonkę rozwijania (dwie strzałki).
Wybierz do rozwinięcia tylko nazwę produktu.
Jeśli jest opcja prefiksu — zdecyduj, czy zostawiasz prefiks.
Zatwierdź.

Opisz, co zaobserwowałeś (jakie kolumny pojawiły się i jaki krok doszedł).

### OBSERVATION (oczekiwane)
- Pojawia się kolumna z nazwą produktu.
- Dochodzi krok rozwinięcia.
- Nazwa może mieć prefiks zależnie od ustawień.

## ETAP 6 — Reuse pipeline: SprzedażPL -> SprzedażCZ (kopiowanie kodu M)

Teraz okazuje się, że masz jeszcze dane sprzedażowe z Czech.
Chcemy wykonać identyczne czyszczenie i transformacje.
Zamiast robić to od nowa — kopiujemy cały pipeline (kod M).

### TASK — Kopiowanie kodu M z PL i wklejenie do CZ

Wejdź do zapytania `SprzedażPL` -> `Edytor zaawansowany` -> skopiuj cały kod.
Wejdź do zapytania `SprzedażCZ` -> `Edytor zaawansowany` -> wklej cały kod.
W kodzie znajdź wskazanie źródła (`Source`) i zmień nazwę tabeli wejściowej z `SprzedażPL` na `SprzedażCZ`.
Zatwierdź.

Opisz, co zaobserwowałeś: czy `SprzedażCZ` ma teraz podobne kroki i czy działa.

### OBSERVATION (oczekiwane)
- `SprzedażCZ` przechodzi przez te same (lub bardzo podobne) kroki.
- Dane są przetworzone analogicznie.
- Ewentualne problemy zwykle wynikają z nazwy źródła lub nazw kolumn.

## ETAP 7 — Append + refaktoryzacja: jeden pipeline zamiast 2x

Mamy `SprzedażPL` i `SprzedażCZ` przetworzone identycznie.
Da się je połączyć przez `Append`.
Zrobimy to najpierw w najprostszej wersji, a potem poprawimy architekturę.

### TASK — Append jako nowe (pierwsza wersja)

W `Narzędzia główne` kliknij: `Dołącz zapytania -> Dołącz zapytania jako nowe`.
Wybierz `SprzedażPL` i `SprzedażCZ`.
Zatwierdź.
Zmień nazwę nowego zapytania na `SprzedażTOTAL`.

Opisz, co zaobserwowałeś: co powstało w tabeli i jakie kroki widzisz po prawej.

### OBSERVATION (oczekiwane)
- Powstaje nowe zapytanie z połączonymi wierszami.
- Dochodzi krok dołączania.
- Dane zawierają rekordy PL i CZ.

To działa.
Ale teraz czyszczenie wykonało się osobno na PL i osobno na CZ.
W kolejnym kroku zrobimy to lepiej: najpierw dołączymy dane, a potem wykonamy czyszczenie raz — wspólnym pipeline.

### TASK — Refaktoryzacja: Append po `Source`, przed czyszczeniem

Usuń zapytanie `SprzedażTOTAL`.

Wróć do zapytania `SprzedażPL`.
Kliknij krok `Źródło`.
Na tym etapie dodaj `Append`, tak aby połączyć `SprzedażPL` i `SprzedażCZ` zaraz po pobraniu danych.
Następnie pozostaw dalsze kroki czyszczenia, aby działały na połączonych danych.

Opisz, co zaobserwowałeś w panelu kroków (gdzie jest `Append` i na czym działają kolejne kroki).

### OBSERVATION (oczekiwane)
- `Append` znajduje się bardzo wcześnie (zaraz po `Source`).
- Kolejne kroki czyszczenia działają na danych PL i CZ razem.
- Jest jeden wspólny pipeline.

### CHECKPOINT
Skopiuj cały kod M końcowego zapytania (po refaktoryzacji) i wklej do czatu.

## ETAP 8 — Load do tabeli przestawnej + final

Teraz, gdy mamy gotową transformację, wracamy do Excela i robimy wynik.

### TASK — Załaduj do: Tabela przestawna + weryfikacja

Wybierz zapytanie końcowe.
Kliknij: `Załaduj do... -> Tabela przestawna`.
Ustaw dowolny prosty pivot — jakikolwiek zechcesz — który pokazuje sprzedaż (np. suma `Wartość` po produkcie).
Zrób screen i wklej go do czatu — ocenię, jak Ci poszło.

Opisz, co zaobserwowałeś: czy pivot działa i czy dane wyglądają sensownie.

### OBSERVATION (oczekiwane)
- Pivot działa i pokazuje oczekiwane agregacje.
- Dane wyglądają spójnie (`Wartość` nie jest pusta, suma ma sens).

## Koniec przebiegu technicznego

Po wykonaniu szkolenia przechodzimy do zakończenia (ankieta, refleksja, co wdrożysz) — to będzie część prompta szkoleniowego, nie blueprint techniczny.
