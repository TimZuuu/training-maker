# ## ETAP 1 — Tabele w Excelu (minimum pod Power Query)

## Finalny Stan Etapu (z BP v2)

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
- Facts: zdarzenia, których przybywa (np. zatrudnienie).
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

### BLOK E1.TEXT.01 — Dlaczego tabele
- Typ: `TEXT`
- Decyzje:
  - Zachować frazę o "mówieniu Excelowi, gdzie są dane" i wadliwości adresów A1:H80.
  - Podkreślić, że dochodzą także wiersze, nie tylko kolumny.
- Poprawki:
  - Wzmocniona semantyka wyjaśniająca kruchość zakresów.
- Źródła: `2102`, `2332`.

### BLOK E1.TEXT.02 — Facts/Dimensions i prefiksy
- Typ: `TEXT`
- Decyzje:
  - Nie okrajać tego bloku; ma budować intuicję "ruch vs słownik/stabilność".
  - Dodać przykład `dimSklepy` dla poczucia stałości.
  - Nie podawać gotowego przykładu nazwy sprzedaży jako oczywistego rozwiązania dla usera.
- Poprawki:
  - Usunięto/oznaczono do usunięcia przykład sugerujący gotową nazwę faktu.
- Źródła: `2102`, `2332`, `4514`.

### BLOK E1.TASK.01-03 — Konwersja i nazewnictwo
- Typ: `TASK`
- Decyzje:
  - User najpierw wykonuje minimum pod PQ, potem opcjonalnie ćwiczenia.
  - Nazwy mają być wywnioskowane przez usera, a nie podane z góry.
- Poprawki:
  - Zachowany podział minimum vs opcjonalne.
- Źródła: `1684`, `2102`.
