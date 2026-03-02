# ETAP 5 — Merge: sprzedaż + produkty po ID

## Finalny stan etapu

### TEXT
W danych sprzedaży mamy ID produktu, ale potrzebujemy nazwy produktu.
Scalimy tabelę sprzedaży z tabelą produktów.

### TASK — Scalanie
`Narzędzia główne -> Scal zapytania -> Scal zapytania jako nowe`.
Wybierz zapytanie sprzedaży PL i zapytanie produktów.
Wskaż kolumny ID produktu po obu stronach.
Typ złączenia: `Lewy zewnętrzny`.
Sprawdź komunikat, ile rekordów sparowano (jeśli nie wszystkie, możliwy problem z ID/typem).
Zatwierdź i opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Powstaje nowe zapytanie.
- Pojawia się kolumna typu `Tabela`.
- Powstaje krok scalania.

### TEXT
Póki co tabela jest dołączona, ale nierozwinięta.
Kliknięcie komórki tej kolumny pokaże w dolnym panelu jej zawartość.
Rozwinięcie = dodanie kolumn.

### TASK — Rozwinięcie
Kliknij ikonę rozwijania kolumny po merge.
Wybierz tylko nazwę produktu.
Zdecyduj o prefiksie.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Dochodzi kolumna z nazwą produktu.
- Powstaje krok rozwinięcia.

## Log decyzji i poprawek (per blok)

### BLOK E5
- Typ: `TEXT/TASK/OBSERVATION`
- Decyzje:
  - Dodać jawny warunek o liczbie sparowanych rekordów.
  - Dodać wyjaśnienie „nierozwinięta tabela -> rozwinięcie = kolumny”.
- Źródła: `4019-4048`, `4133`.
