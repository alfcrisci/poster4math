# Poster di matematica

Sito statico con un carousel per sfogliare i poster didattici in PDF (A3, pronti per la stampa).

## Struttura

```
index.html              pagina principale con il carousel
posters/
  *.pdf                 i poster in formato PDF
  previews/*.png         anteprime ad alta risoluzione (usate nel carousel)
  thumbs/*.png            miniature piccole (usate nella barra di navigazione)
```

## Pubblicare su GitHub Pages

1. Crea un repository su GitHub e carica tutto il contenuto di questa cartella
   (`index.html` e la cartella `posters/`) nella radice del repository
   (o dentro `/docs` se preferisci).
2. Vai su **Settings → Pages** del repository.
3. In **Source**, scegli il branch (es. `main`) e la cartella (`/root` o `/docs`).
4. Salva: dopo qualche minuto il sito sarà visibile all'indirizzo
   `https://<tuo-utente>.github.io/<nome-repo>/`.

## Aggiungere un nuovo poster

1. Copia il nuovo file PDF dentro `posters/`.
2. Genera l'anteprima e la miniatura (richiede `pdftoppm`, incluso in poppler-utils):
   ```bash
   pdftoppm -png -r 150 -f 1 -l 1 -singlefile posters/nuovo.pdf posters/previews/nuovo
   pdftoppm -png -r 45  -f 1 -l 1 -singlefile posters/nuovo.pdf posters/thumbs/nuovo
   ```
3. Aggiungi una nuova riga all'array `posters` in `index.html`:
   ```js
   { title: "Titolo del poster", pdf: "posters/nuovo.pdf",
     preview: "posters/previews/nuovo.png", thumb: "posters/thumbs/nuovo.png" }
   ```
