# ## ETAP 2A — Load, odświeżanie i sposób ładowania wyników

## Finalny Stan Etapu (z BP v2)

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

### BLOK E2A.TASK — Zamknij i załaduj / odświeżanie
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - User ma zobaczyć, że wynik to efekt query, nie ręczna tabela.
- Źródła: `1475`, `150`.

### BLOK E2A.TASK — Load to Pivot -> Only Connection
- Typ: `TASK`
- Decyzje:
  - Przełączenie sposobu ładowania jest elementem obowiązkowej orientacji.
- Źródła: `150`, `4133`.
