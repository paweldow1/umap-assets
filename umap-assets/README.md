# umap-assets — hosting obrazków do map uMap 1 Maja

Statyczne repozytorium na obrazki (logo organizacji + ikony) podpinane jako
`iconUrl` w obiektach uMap. Zero backendu — GitHub serwuje pliki po bezpośrednim URL.

## Struktura

```
umap-assets/
├── index.html          # galeria — generuje gotowe URL-e do skopiowania
├── test/test.png       # obraz testowy (czerwone koło z checkiem)
├── logo/
│   ├── berlin/         # DGB, verdi, IG BAU, ...
│   ├── warszawa/       # OPZZ, PPS, Solidarnosc, ...
│   └── kijow/kpu.png   # gotowa okrągła odznaka KPU
└── ikony/              # ikony tematyczne (puste — wrzuć własne)
```

Konwencja nazw: skrót organizacji małymi literami, bez spacji — `dgb.png`,
`verdi.png`, `opzz.png`. Kwadratowe PNG z przezroczystymi rogami (patrz
`circular_marker.py`), żeby marker nie wychodził poza obiekt.

## Uruchomienie (raz)

1. Załóż repo na GitHubie, np. `umap-assets`, i wypchnij tę zawartość:
   ```
   git init && git add . && git commit -m "assets"
   git branch -M main
   git remote add origin https://github.com/<USER>/umap-assets.git
   git push -u origin main
   ```
2. (Opcjonalnie) włącz GitHub Pages: Settings → Pages → Branch `main` → `/root`.

## Wzorce URL (do wklejenia w polu „symbol obiektu" w uMap)

Podstaw swój `<USER>` i nazwę repo:

- **raw (działa od razu po push, bez Pages):**
  `https://raw.githubusercontent.com/<USER>/umap-assets/main/<ścieżka>`
- **GitHub Pages (po włączeniu Pages):**
  `https://<USER>.github.io/umap-assets/<ścieżka>`

Przykłady:
```
https://raw.githubusercontent.com/<USER>/umap-assets/main/test/test.png
https://raw.githubusercontent.com/<USER>/umap-assets/main/logo/kijow/kpu.png
```

## Test „czy w ogóle działa"

**Bez zakładania repo** — wklej ten publiczny link do symbolu dowolnego obiektu
w uMap; powinna pojawić się czerwona flaga:
```
https://raw.githubusercontent.com/twitter/twemoji/master/assets/72x72/1f6a9.png
```

**Po wypchnięciu tego repo** — wklej swój link do `test/test.png` (wzorzec wyżej).
Jeśli zobaczysz czerwone koło z białym „✓", hosting działa end-to-end.

## Galeria / generator linków

Otwórz `index.html` (lokalnie albo na Pages), wpisz u góry swój `USER` i `REPO`,
a strona wygeneruje gotowe do skopiowania URL-e dla każdego pliku. Nowe pliki
dopisujesz do tablicy `ASSETS` w `index.html`.
