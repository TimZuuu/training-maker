# ETAP 2A — Load, odświeżanie, sposób ładowania

## Finalny stan etapu

### TASK — Zamknij i załaduj
W PQ kliknij `Zamknij i załaduj`.
Opisz, co powstało w Excelu.

### OBSERVATION (oczekiwane)
- Powstaje wynik tabelaryczny.

### TASK — Test odświeżania
1. Usuń kilka wartości z wyniku, potem `PPM -> Odśwież`.
2. Zmień jedną wartość w źródle i ponownie odśwież wynik.
Opisz, co zaobserwowałeś.

### OBSERVATION (oczekiwane)
- Skasowane wartości wracają po odświeżeniu.
- Zmiany ze źródła pojawiają się po odświeżeniu.

### TASK — Załaduj do pivot, potem tylko połączenie
`Załaduj do... -> Tabela przestawna`.
Następnie `Załaduj do... -> Tylko połączenie`.
Opisz, co zostało w pliku.

### OBSERVATION (oczekiwane)
- Zmienia się sposób ładowania wyniku.
- Zapytanie nadal istnieje przy `Tylko połączenie`.

### TASK — Sprzątanie
Usuń zbędny arkusz po testach ładowania.

## Log decyzji i poprawek (per blok)

### BLOK E2A
- Typ: `TASK/OBSERVATION`
- Decyzje:
  - User ma dotknąć obu trybów ładowania.
- Źródła: `1475`.
