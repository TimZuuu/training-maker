# Decyzje zamrożone (source of truth)

1. Projekt ma 3 główne produkty: Master Prompt, Prompt szkoleniowy PQ, Blueprint PQ.
2. Blueprint PQ ma trzymać format z warstwą merytoryczno-techniczną (`TEXT`, `TASK`, `OBSERVATION`, `FILL`).
3. Szkolenie PQ ma pytać użytkownika "co zaobserwował" i uzupełniać brakujące obserwacje.
4. Weryfikacja ma działać checkpointami, ale bez przesady w liczbie (pakietowo, nie po każdym kliknięciu).
5. Tabele: minimum pod PQ obowiązkowe; rozszerzone ćwiczenia z tabel opcjonalne.
6. W scenariuszu PQ musi być ćwiczenie `XLOOKUP` i usunięcie kolumn ćwiczeniowych przed wejściem do PQ.
7. Końcowy case danych to 3 tabele: `SprzedażPL`, `SprzedażCZ`, `Produkty`.
8. W pipeline ma być: merge, reuse kodu M, append, a potem refaktoryzacja append "wcześnie" (jeden pipeline).
9. Na końcu wynik ma trafić do pivota i być zweryfikowany.
10. Tryb ADMIN i ogólna mechanika zachowania trenera to domena promptu szkoleniowego/mastera, nie samego BP.

Uwaga: punkt 10 nie wyklucza wpisywania do BP zachowań specyficznych dla konkretnego etapu, jeśli są częścią metodyki ćwiczenia.
