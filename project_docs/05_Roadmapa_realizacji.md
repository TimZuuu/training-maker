# Roadmapa realizacji (proponowana kolejność)

## Etap 1 - Stabilizacja BP jako artefaktu referencyjnego
1. Dodać metadane i macierz etapów do BP v2.
2. Dodać rejestr checkpointów (jedna tabela).
3. Dodać changelog v1 -> v2.

## Etap 2 - Standard blueprintów
1. Na bazie BP v2 utworzyć `STANDARDY_BLUEPRINT.md`.
2. Zdefiniować minimalny format i reguły jakości.
3. Dodać listę anty-regresji.

## Etap 3 - Prompt szkoleniowy PQ (mechanika)
1. Oddzielić od BP: ustawienia, tryby, politykę weryfikacji, logikę ADMIN.
2. Wpiąć BP jako źródło przebiegu i treści merytorycznej.
3. Dodać format raportu po szkoleniu.

## Etap 4 - Master Prompt
1. Zamodelować flow pytań do autora szkolenia.
2. Wymusić produkcję: najpierw BP, potem prompt szkoleniowy.
3. Dodać bramki jakości i komendę finalnego druku prompta.

## Definicja done (dla tej iteracji porządkowania)
- Jest archiwum rozmowy z indeksem i chunkami.
- Są jawne granice 3 produktów.
- Są zamrożone decyzje i backlog pytań.
- Jest gotowa kolejność dalszej pracy.
