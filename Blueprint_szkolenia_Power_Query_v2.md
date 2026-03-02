# Blueprint szkolenia: Power Query – podstawy pipeline (PL UI) – v2

Zakres: tabele w Excelu (minimum pod PQ + opcjonalne ćwiczenia), Power Query: orientacja, typy danych, błędy, kolumna z przykładu, merge, reuse kodu M, append + refaktoryzacja, load do tabeli przestawnej, checkpointy kodu.

To jest blueprint merytoryczno-techniczny.
Nie opisuje pełnej mechaniki zachowania agenta (ustawienia globalne, tryby, ADMIN) poza tym, co jest konieczne do poprawnego przebiegu ćwiczeń.

## Konwencja segmentów

- `TEXT`: narracja, którą trener ma powiedzieć możliwie dosłownie (wygładzenie językowe dopuszczalne bez zmiany sensu).
- `TASK`: konkretne działanie do wykonania przez użytkownika.
- `OBSERVATION`: czego oczekujemy, że użytkownik zauważy.
- `FILL`: dodatkowy `TEXT` po `OBSERVATION`, gdy trzeba dopowiedzieć mechanikę lub skorygować brakującą obserwację.

## ETAP 0 — Cel szkolenia

### TEXT — Otwarcie szkolenia

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

### TEXT — Dlaczego tabele są niezbędne

W pliku masz kilka arkuszy z danymi. Problem w tym, że Excel nie bardzo „wie”, gdzie te dane są.
Musisz mu to „powiedzieć”, pisząc adres typu A1:H80, ale jest to bardzo wadliwa metoda: dochodzą kolumny i wiersze, ktoś przesunie zakres, tabela się rozjedzie. Masa okazji do rozwalenia mechanizmu i błędów.

Dlatego, aby zachować poprawność danych, niezbędne jest pracowanie na zakresach zdefiniowanych jako Tabele.

### TASK — Zamiana zakresu na Tabelę (SprzedażPL)

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
Excel teraz „widzi” tabelę jako obiekt. To będzie kluczowe dla Power Query i bezpiecznych odniesień.

### TASK — Zakładka narzędzi tabeli i nazwa tabeli

Kliknij w tabelę.
Znajdź zakładkę narzędzi tabeli (Projektowanie tabeli / Narzędzia tabeli — nazwa zależy od wersji).
Po lewej znajdź pole „Nazwa tabeli”.

Napisz, jaką nazwę widzisz teraz w tym polu.

### OBSERVATION (oczekiwane)
- Excel nadaje domyślną nazwę (np. Tabela1 / Table1).

### TEXT — Facts i Dimensions

Teraz przejdziemy do nazywania tabel.

W bazach danych mamy dwa główne typy tabel:
- Facts: zdarzenia, których przybywa (np. sprzedaż).
- Dimensions: słowniki/opisy, relatywnie stałe (np. produkty, klienci, sklepy).

To może wydawać się mało istotne teraz, ale przy większych projektach robi ogromną różnicę: jedne tabele rosną i są „ruchem”, a drugie opisują świat i zmieniają się rzadziej.

Dlatego przy nazywaniu tabel warto stosować prefiksy, np. `fct` i `dim`.
Przykład: `dimSklepy` sugeruje stabilny słownik obiektów, a `fctSprzedażPL` sugeruje strumień zdarzeń.

Dodatkowo warto utrzymać konwencję wizualną: mała litera w prefiksie, wielka litera w nazwie.

### TASK — Ustalenie nazw tabel (fct/dim)

Zastanów się, które tabele w pliku są faktami, a które wymiarami.
Zaproponuj nazwę dla tabeli sprzedaży (np. `fctSprzedażPL`) i dla pozostałych tabel.

Następnie wpisz ustalone nazwy do pola „Nazwa tabeli” dla każdej tabeli.
Na koniec opisz, jakie nazwy ustaliłeś.

### OBSERVATION (oczekiwane)
- Tabela sprzedaży zostaje nazwana jako `fct...`.
- Pozostałe tabele jako `dim...`.
- Nazwy są jednoznaczne i czytelne.

To jest minimum potrzebne do Power Query.

### TEXT — Przejście do bloku opcjonalnego

Po tym minimum możesz wykonać dodatkowe ćwiczenia z Tabel (wartościowe w codziennej pracy), ale są opcjonalne.
Jeśli je pomijasz — przechodzisz od razu do ETAPU 2.

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

## ETAP 2 — Power Query: wejście, orientacja i pierwszy checkpoint

### TEXT — Czym jest Power Query

Power Query to osobna warstwa pracy z danymi — silnik transformacji.
Pozwala wykonywać operacje w sposób powtarzalny i kontrolowany.

### TASK — Dodanie `fctSprzedażPL` do Power Query

Kliknij w tabelę `fctSprzedażPL`.
Przejdź do zakładki Dane.
Kliknij: `Z tabeli/zakresu`.
Zatwierdź.

Opisz, co się otworzyło.

### OBSERVATION (oczekiwane)
- Otwiera się edytor Power Query.

### TEXT — Mapa edytora PQ

Po lewej: lista zapytań.
Po prawej: Applied Steps (kroki transformacji).
Na środku: podgląd danych.
Nad tabelą: pasek formuły (kod aktywnego kroku).
Po kliknięciu komórki: na dole pojawia się panel szczegółów wartości/błędu.

### TASK — Przegląd kroków i panelu szczegółów

Kliknij dowolną komórkę w podglądzie.
Sprawdź, co pojawia się w dolnym panelu.

Następnie kliknij po kolei kilka kroków po prawej i obserwuj, jak zmienia się podgląd danych oraz kod kroku.

Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Dolny panel pokazuje szczegóły zaznaczonej komórki (wartość albo raport błędu).
- Klikanie kroków zmienia efekt widoczny na środku.
- Pasek formuły pokazuje kod aktywnego kroku.

### TASK — Edytor zaawansowany (M) + checkpoint 1

Przejdź do Narzędzia główne i kliknij Edytor zaawansowany.
Skopiuj cały kod M i wklej jako checkpoint.

### CHECKPOINT 1
Wklej cały kod M z Edytora zaawansowanego (stan początkowy zapytania `SprzedażPL`).

## ETAP 2A — Load, odświeżanie i sposób ładowania wyników

### TASK — Zamknij i załaduj

Wyjdź z edytora przez `Zamknij i załaduj`.

Opisz, co powstało w Excelu.

### OBSERVATION (oczekiwane)
- Powstaje tabela wynikowa (domyślnie w nowym arkuszu).

### TASK — Test odświeżania (2 działania)

1) W tabeli wynikowej usuń kilka wartości, potem PPM -> `Odśwież`.
2) W tabeli źródłowej zmień jedną wartość, wróć do wyniku i ponownie `Odśwież`.

Opisz oba efekty.

### OBSERVATION (oczekiwane)
- Skasowane wartości wracają po odświeżeniu.
- Zmiana w źródle pojawia się po odświeżeniu.

### FILL
Odświeżenie = ponowne wykonanie kroków transformacji na źródle.

### TASK — `Załaduj do`: pivot, potem `Tylko połączenie`

Kliknij tabelę wynikową.
Przejdź do zakładki Zapytanie -> `Załaduj do...`.
Wybierz `Tabela przestawna` i zatwierdź (potwierdź komunikat Excela o jednym miejscu ładowania).

Następnie ponownie `Załaduj do...` i ustaw `Tylko połączenie`.

Opisz, co zostało w pliku.

### OBSERVATION (oczekiwane)
- Da się przełączyć miejsce/sposób ładowania.
- Przy `Tylko połączenie` wynik nie jest renderowany jako tabela/pivot, ale zapytanie nadal istnieje.

### TASK — Sprzątanie po ładowaniu

Usuń zbędny arkusz, który pozostał po wcześniejszym ładowaniu.

## ETAP 2B — Dodanie pozostałych tabel do PQ (Only Connection)

### TEXT — Przygotowanie zapytań pomocniczych

Do dalszych zadań potrzebujesz w PQ też tabele `Produkty` i `SprzedażCZ`.

### TASK — Dodaj `Produkty` i `SprzedażCZ` do PQ

Dla każdej z tych tabel:
- kliknij tabelę,
- `Dane -> Z tabeli/zakresu`,
- `Zamknij i załaduj do... -> Tylko połączenie`.

Na koniec otwórz panel `Zapytania i połączenia` i upewnij się, że masz 3 zapytania:
- `SprzedażPL`
- `SprzedażCZ`
- `Produkty`

### OBSERVATION (oczekiwane)
- Wszystkie trzy zapytania są dostępne i gotowe do ćwiczeń (minimum: połączenia).

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

## ETAP 4 — Kolumna z przykładu: `Wartość = Cena * Ilość`

### TASK — Kolumna z przykładu (z wybranych kolumn)

Przejdź do `Dodaj kolumnę`.
Z Ctrl zaznacz `Cena` oraz `Ilość`.
Kliknij `Kolumna z przykładu -> Z wybranych kolumn`.

Wpisz przykłady dla 2-3 wierszy tak, aby odpowiadały `Cena * Ilość`.
Zatwierdź i nazwij kolumnę `Wartość`.

### OBSERVATION (oczekiwane)
- PQ dopasowuje regułę na podstawie przykładów.
- Powstaje nowa kolumna i nowy krok.

### FILL
To szybki sposób na transformacje bez pisania M od zera.

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

## ETAP 7 — Append + refaktoryzacja: jeden pipeline zamiast dwóch

### TEXT — Dlaczego nie zostawiamy dwóch osobnych pipeline'ów

Mamy `SprzedażPL` i `SprzedażCZ` przetworzone identycznie.
Da się je połączyć przez Append, ale to wciąż oznacza, że ten sam pipeline wykonał się dwa razy.
Lepiej: najpierw połączyć dane, a potem czyścić je jednym wspólnym pipeline.

### TASK — Append jako nowe (pierwsza wersja)

`Narzędzia główne -> Dołącz zapytania -> Dołącz zapytania jako nowe`.
Wybierz `SprzedażPL` i `SprzedażCZ`.
Nazwij wynik `SprzedażTOTAL`.

Opisz efekt.

### OBSERVATION (oczekiwane)
- Powstaje zapytanie z połączonymi wierszami PL i CZ.

### FILL
To działa, ale czyszczenie było liczone dwa razy (osobno dla PL i CZ).
Lepiej: najpierw dołączyć dane, potem wykonać jeden wspólny pipeline.

### TASK — Refaktoryzacja: Append wcześnie (po `Source`)

Usuń zapytanie `SprzedażTOTAL`.
Wróć do `SprzedażPL`.
Kliknij krok `Źródło` i dodaj Append tak, aby połączyć PL + CZ od razu po pobraniu danych.
Zostaw kolejne kroki czyszczenia, aby działały już na danych połączonych.

### OBSERVATION (oczekiwane)
- Append jest bardzo wcześnie w pipeline.
- Dalsze kroki działają na PL + CZ razem.
- Masz jeden wspólny pipeline.

### CHECKPOINT 3 (końcowy techniczny)
Skopiuj cały kod M końcowego zapytania po refaktoryzacji.

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
