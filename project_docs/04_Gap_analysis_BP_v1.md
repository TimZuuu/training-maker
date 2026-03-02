# Gap analysis - Blueprint v1

Plik analizowany: `Blueprint_szkolenia_Power_Query_v1.md`

## Co jest mocne
- Spójna ścieżka od tabel do końcowego pivota.
- Dobre pokrycie techniczne PQ: typy, błędy, merge, append, reuse M.
- Jest struktura `TASK` + `OBSERVATION` + checkpointy M.

## Luki / ryzyka
1. Brak jawnego mapowania BP do pozostałych 2 produktów (co idzie do promptu szkoleniowego i mastera).
2. Brak sekcji "z czego ten BP wynika" (czyli źródło decyzji z rozmowy).
3. Brak tabeli priorytetów etapów (co jest krytyczne, co opcjonalne, co można skrócić przy braku czasu).
4. Checkpointy są, ale brak jednego miejsca z ich pełnym wykazem i celem walidacji.
5. Brak formalnego changelogu uzasadniającego odstępstwa od pierwotnej narracji rozmowy.
6. Brak listy "anty-regresji" (co absolutnie nie może znów zostać pominięte przy kolejnych przeróbkach).

## Co dopisać w v2
- Metadane BP: `Zakres`, `Poziom`, `Cel`, `Krytyczne elementy`.
- Macierz etapów: `Obowiązkowe / Opcjonalne / Do skrótu`.
- Rejestr checkpointów: `ID`, `moment`, `co weryfikuje`, `dowód`.
- Sekcja "Powiązanie z promptem szkoleniowym" (interfejs BP -> prompt).
- Sekcja "Powiązanie ze standardem blueprintów" (BP -> standardy mastera).
