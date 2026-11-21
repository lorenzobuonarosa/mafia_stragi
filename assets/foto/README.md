# Foto delle schede

Metti qui i file delle foto (JPG o WebP, circa 1200 px sul lato lungo, meglio sotto i 300 KB) e descrivili in `data/foto.csv`, una riga per strage:

```
ordine;file;posizione;didascalia;autore;licenza;fonte
1;capaci.jpg;50% 50%;Che cosa si vede, in una frase.;Autore o agenzia;Licenza o "per concessione";https://link-alla-fonte
```

- `ordine`: numero della strage, come nella colonna `ordine` di `stragi.csv` (1-7).
- `file`: nome del file in questa cartella.
- `posizione` (facoltativa): punto dell'immagine da tenere nel ritaglio, per esempio `50% 30%`. La foto è mostrata in un riquadro 3:2.
- `didascalia`, `autore`, `licenza`, `fonte`: compaiono sotto la foto come "Didascalia. Foto: autore, licenza, via Wikimedia Commons" con il link alla fonte.

Le schede senza riga in `foto.csv` restano senza foto.
