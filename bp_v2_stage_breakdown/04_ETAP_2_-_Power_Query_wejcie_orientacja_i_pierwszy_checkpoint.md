# ## ETAP 2 — Power Query: wejście, orientacja i pierwszy checkpoint

## Finalny Stan Etapu (z BP v2)

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

### BLOK E2.TEXT.01 — Wejście do PQ
- Typ: `TEXT`
- Decyzje:
  - To ma być "nowa warstwa Excela" i opis mapy UI.
- Źródła: `150`, `1795`, `2332`.

### BLOK E2.TASK/OBS — Klikanie kroków i panel dolny
- Typ: `TASK` + `OBSERVATION`
- Decyzje:
  - User ma klikać kroki i opisać obserwacje.
  - Utrzymać szczegóły o panelu błędu/wartości.
- Źródła: `1795`, `3505`, `1684`.

### BLOK E2.CHECKPOINT.01 — Kod M
- Typ: `CHECKPOINT`
- Decyzje:
  - Wklejanie M jako dowód wykonania ma zostać.
- Źródła: `150`, `206`.
