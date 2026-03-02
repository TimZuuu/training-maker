# Defragmentacja rozmowy

## Blok A - Inicjacja i cel projektu
- Celem jest nie pojedynczy prompt, tylko system tworzenia agentów szkoleniowych.
- Pojawia się architektura dwupoziomowa: master (producent) i trener wykonawczy.

## Blok B - Model szkolenia i weryfikacji
- Szkolenie ma być proceduralne, z kontrolą wykonania i pętlą feedbacku.
- Wchodzi koncept checkpointów i różnych typów weryfikacji.

## Blok C - Przykład referencyjny Power Query
- Rozpisanie szczegółowego scenariusza szkolenia PQ (tabele, PQ, merge, append, load).
- Duży nacisk na "co user ma zauważyć" i reakcję trenera na brak obserwacji.

## Blok D - Konflikt warstw i regresje
- Mieszały się warstwy: blueprint, prompt wykonawczy, mechanika admin/ustawienia.
- Wystąpiły regresje: skracanie narracji, pomijanie OBSERVATION, gubienie ustaleń.

## Blok E - Ustalenie architektury docelowej
- Utrwalono kierunek: oddzielić warstwy i trzymać jasny podział odpowiedzialności.
- Blueprint ma być sercem technicznym szkolenia.

## Blok F - Finalizacja zakresu PQ
- Ustalenie 3 tabel domenowych (SprzedażPL, SprzedażCZ, Produkty).
- Ustalenie etapów: czyszczenie, merge, reuse M, append, refaktoryzacja, pivot.

## Blok G - Trzy produkty końcowe
- Master prompt (generator promptów szkoleniowych)
- Prompt szkoleniowy PQ (mechanika prowadzenia)
- Blueprint PQ (wzorzec standardu)

## Artefakty po defragmentacji
- Surowy zapis: `project_archive/raw/transcript_discussion_raw.txt`
- Chunki liniowe: `project_archive/chunks/line_chunks/`
- Indeks chunków: `project_archive/indices/line_chunks_index.csv`
- Ekstrakty tematyczne: `project_archive/thematic_extracts/`
