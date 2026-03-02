# ETAP 1 — Tabele w Excelu (minimum pod Power Query)

## Finalny stan etapu

### TEXT
Otwórz plik.
Znajdziesz w nim arkusze z danymi.
Problem z tym, że Excel nie bardzo „wie”, gdzie te dane są.
Możesz mu to „powiedzieć”, pisząc adres typu A1:H80, ale to bardzo wadliwa metoda.
Dochodzą nowe kolumny, dochodzą nowe wiersze, ktoś przesunie zakres i mechanizm się rozsypie.
Dlatego, żeby zachować poprawność i kontrolę, niezbędne jest pracowanie na zakresach zdefiniowanych jako Tabele.

### TASK — Zamiana zakresu na tabelę (arkusz SprzedażPL)
Wejdź w arkusz SprzedażPL.
Kliknij gdziekolwiek w danych.
Wciśnij `Ctrl + T`.
Upewnij się, że zaznaczony jest checkbox „Moja tabela ma nagłówki”.
Zatwierdź.
Następnie opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Pojawiła się tabela jako obiekt Excela.
- Widać styl tabelaryczny.
- Po kliknięciu tabeli pojawia się zakładka narzędzi tabeli.

### TEXT
Excel właśnie „zobaczył” tabelę. Teraz możemy ją kontrolować.

### TEXT — Facts / Dimensions
Teraz przejdziemy do kwestii nazywania tabel.
W bazach danych mamy dwa główne typy tabel: facts i dimensions.
Facts to zdarzenia, których przybywa.
Dimensions to słowniki/opisy, bardziej stabilne obiekty.
To może wydawać się mało istotne teraz, ale przy większych projektach robi ogromną różnicę.

### TEXT — Prefiksy i czytelność
Dlatego przy nazywaniu tabel warto stosować prefiksy typu `fct` i `dim`.
Przykład stabilnego wymiaru: `dimSklepy`.
Dodatkowo warto utrzymać konwencję: mała litera w prefiksie, wielka litera w nazwie.
To zwiększa czytelność wizualną.

### TASK — Klasyfikacja i nazwy
Zdecyduj, które tabele są facts, a które dimensions.
Dla tabeli sprzedaży sam zaproponuj nazwę (bez podpowiedzi gotowej odpowiedzi).
Następnie nazwij pozostałe tabele zgodnie z tą samą konwencją.
Na końcu opisz, jakie nazwy ustaliłeś.

### OBSERVATION (oczekiwane)
- Nazwy są spójne i czytelne.
- Użytkownik rozumie różnicę fact/dimension.

### TEXT
To jest minimum potrzebne pod Power Query.
Dodatkowe ćwiczenia tabelaryczne są opcjonalne, ale rekomendowane.

## Log decyzji i poprawek (per blok)

### BLOK E1.TEXT.01
- Typ: `TEXT`
- Decyzje:
  - Utrzymać frazę „musisz mu to powiedzieć adresem A1:H80”, ale wskazać wady.
- Poprawki:
  - Doprecyzowanie: dochodzą też wiersze.
- Źródła: `2102`, `2334`.

### BLOK E1.TEXT.02
- Typ: `TEXT`
- Decyzje:
  - Rozszerzyć facts/dim, nie okrajać.
  - Utrzymać przykład `dimSklepy`.
- Poprawki:
  - Usunięto przykład sugerujący gotową nazwę faktu sprzedaży.
- Źródła: `2102`, `2334`.

### BLOK E1.TASK.02
- Typ: `TASK`
- Decyzje:
  - User ma sam wywnioskować nazwę tabeli sprzedaży.
- Poprawki:
  - Brak podpowiedzi „a fctSprzedażPL sugeruje...”.
- Źródła: bezpośrednia uwaga użytkownika (bieżąca wiadomość #1).
