# Bar Museo · Carta dei Distillati

Menu digitale interattivo per la selezione di distillati del Bar Museo. Si apre direttamente nel browser, non richiede installazioni, e funziona su telefono, tablet e computer.

---

## Cos'è questo progetto

È una pagina web che mostra la carta dei distillati del bar in modo elegante e navigabile. I clienti possono:

- Sfogliare le categorie: **Gin**, **Whiskey**, **Rum**, **Amari**, **Grappe**
- Filtrare i prodotti per profilo di gusto (secco, agrumato, morbido, speziato, floreale, erbaceo)
- Leggere la storia e le caratteristiche di ogni bottiglia
- Visualizzare la foto di ogni distillato

Il design è sobrio ed elegante, con caratteri raffinati e colori caldi ispirati all'ambiente del bar.

---

## Come aprirlo

Fare doppio clic sul file `index.html` — si aprirà nel browser come qualsiasi pagina web.  
Non serve internet (le immagini sono già salvate nella cartella `immagini`).

---

## Come personalizzarlo — guida passo per passo

> Questa sezione è scritta per chi non ha esperienza di informatica. Seguire i passi nell'ordine indicato.

### Strumento necessario: un editor di testo semplice

Aprire il file `index.html` con il **Blocco note** (su Windows) oppure con **TextEdit** (su Mac, impostato in modalità testo normale).  
*Non usare Word o altri programmi di scrittura: potrebbero rovinare il file.*

---

### Aggiungere un nuovo distillato a una sezione esistente

Ogni distillato nel file `index.html` ha questa forma:

```html
<article class="item" data-img="immagini/gin/nome-file.jpg" data-category="secco">
  <div class="image"><img alt="Nome del Gin"><div class="placeholder">Immagine</div></div>
  <div class="content">
    <h3>Nome del Gin</h3>
    <div class="origin">Paese · Gradazione%</div>
    <p class="description">Descrizione del distillato.</p>
  </div>
</article>
```

**Per aggiungere una nuova bottiglia:**

1. Aprire `index.html` con il Blocco note
2. Usare la funzione **Cerca** (Ctrl+F) e cercare il nome della sezione, ad esempio `SEZIONE GIN`
3. Scorrere fino alla fine della sezione e trovare l'ultimo `</article>`
4. Subito dopo, incollare il blocco qui sopra modificando:
   - `immagini/gin/nome-file.jpg` → il percorso della foto (vedi sotto come aggiungerla)
   - `secco` → il profilo di gusto (vedi tabella in fondo)
   - `Nome del Gin` → il nome della bottiglia
   - `Paese · Gradazione%` → paese di origine e gradazione alcolica (es. `Scozia · 43%`)
   - La descrizione tra `<p class="description">` e `</p>`
5. Salvare il file con **Ctrl+S**
6. Aprire (o ricaricare) `index.html` nel browser per vedere il risultato

**Come aggiungere la foto:**

1. Copiare l'immagine della bottiglia nella cartella `immagini/gin/` (o nella cartella della categoria giusta)
2. Rinominare il file con un nome semplice, senza spazi e senza lettere accentate (es. `nuovo_gin.jpg`)
3. Scrivere il percorso corretto nel blocco: `immagini/gin/nuovo_gin.jpg`

---

### Aggiungere una nuova categoria (es. Cognac, Tequila...)

Questa operazione richiede di modificare tre punti nel file `index.html`:

**Passo 1 — Aggiungere il link nella barra di navigazione in alto**

Cercare questa parte vicino all'inizio del file:

```html
<ul>
  <li><a href="#gin">Gin</a></li>
  <li><a href="#whiskey">Whiskey</a></li>
  ...
</ul>
```

Aggiungere una riga con il nome della nuova categoria, ad esempio:

```html
<li><a href="#tequila">Tequila</a></li>
```

---

**Passo 2 — Creare la sezione con i prodotti**

Cercare la fine dell'ultima sezione (quella delle Grappe) e, subito dopo il suo `</section>`, aggiungere:

```html
<!-- SEZIONE TEQUILA -->
<section class="category" id="tequila">
  <div class="category-title">
    <div class="ornament"><span>Capitolo VI</span></div>
    <h2>Tequila</h2>
  </div>

  <div class="grid" id="tequila-grid">

    <!-- Qui dentro vanno gli articoli delle bottiglie, come spiegato sopra -->

  </div>
</section>
```

> Cambiare `Capitolo VI` con il numero corretto (se è la sesta sezione).  
> Cambiare `tequila` con il nome scelto (tutto minuscolo, senza spazi).

---

**Passo 3 — Creare la cartella per le immagini**

Nella cartella `immagini`, creare una nuova sotto-cartella con lo stesso nome usato sopra (es. `tequila`) e metterci dentro le foto dei prodotti.

---

### Modificare nome, descrizione o gradazione di una bottiglia già presente

1. Aprire `index.html` con il Blocco note
2. Usare **Cerca** (Ctrl+F) e digitare il nome della bottiglia
3. Trovare il blocco corrispondente e modificare il testo desiderato
4. Salvare con **Ctrl+S**

---

### Modificare il logo o il titolo del bar

- **Logo:** sostituire il file `logo.png` nella cartella principale con uno nuovo, mantenendo lo stesso nome `logo.png`
- **Titolo nel browser:** cercare `<title>Bar Museo · Carta dei Distillati</title>` e modificare il testo
- **Titolo sulla pagina:** cercare `<h1>Carta dei <em>Distillati</em></h1>` e modificarlo

---

## Struttura dei file

```
menu-distillati/
├── index.html          ← la pagina principale (qui si aggiungono i prodotti)
├── logo.png            ← logo del bar
├── css/
│   └── style.css       ← stile grafico (colori, font, layout)
└── immagini/
    ├── gin/            ← foto dei gin
    ├── whiskey/        ← foto dei whiskey
    ├── rum/            ← foto dei rum
    ├── amari/          ← foto degli amari
    └── grappe/         ← foto delle grappe
```

---

## Valori ammessi per il profilo di gusto (`data-category`)

| Valore | Significato |
|---|---|
| `secco` | Secchi e classici |
| `agrumato` | Con note di agrumi |
| `morbido` | Rotondi e vellutati |
| `speziato` | Con spezie in primo piano |
| `floreale` | Con note di fiori |
| `erbaceo` | Con erbe aromatiche |

> Se si vuole aggiungere un nuovo profilo di gusto non presente in questa lista, il pulsante di filtro corrispondente non apparirà automaticamente nella pagina — sarà necessario aggiungerlo manualmente nella sezione dei filtri del file `index.html`.

