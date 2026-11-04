# Skill LinkedIn per Claude

Quattro skill in italiano per lavorare su LinkedIn con Claude, più una skill generica per il giornale PDF di marca. Ognuna è una cartella in `skills/` con un `SKILL.md`.

| Skill | A cosa serve |
|---|---|
| [`linkedin-profilo-efficace`](skills/linkedin-profilo-efficace/SKILL.md) | Audit e riscrittura del profilo personale (headline, Informazioni, esperienze, in evidenza, competenze, banner) verso un obiettivo e un target. |
| [`linkedin-pagina-aziendale`](skills/linkedin-pagina-aziendale/SKILL.md) | Creazione o ottimizzazione di una pagina aziendale: testi, impostazioni, immagini, post di lancio e primo piano editoriale. |
| [`linkedin-articoli-da-sito`](skills/linkedin-articoli-da-sito/SKILL.md) | Articoli o newsletter LinkedIn con Tone of Voice e argomento presi da un sito di riferimento. |
| [`linkedin-piano-editoriale`](skills/linkedin-piano-editoriale/SKILL.md) | Piano editoriale (1 post al giorno + 1 articolo a settimana), bozze, immagini con ChatGPT o Nano Banana, pubblicazione via Chrome con conferma. |
| [`giornale-di-marca`](skills/giornale-di-marca/SKILL.md) | Giornale PDF personale con l'identità di un marchio (logo, palette, font, voce), personalizzato con un questionario. Si appoggia alla skill `leaderai-giornale`, che deve essere installata a parte. |

Tutte chiedono all'utente di caricare logo e immagini da usare e non rigenerano né alterano mai un logo esistente. Nessuna contiene dati di un cliente specifico.

## Installazione

**Claude Code**: copia le cartelle di `skills/` in `~/.claude/skills/` (per tutti i progetti) oppure in `.claude/skills/` del progetto.

**claude.ai / app**: comprimi in zip la cartella di una singola skill (la cartella deve contenere `SKILL.md`) e caricala dalla sezione skill delle impostazioni. I nomi dei menu possono cambiare tra versioni.

## Note d'uso

- La pubblicazione via Chrome richiede Claude in Chrome collegato al tuo account LinkedIn e **non avviene mai senza una tua conferma esplicita**.
- Il caricamento di file (logo, cover, immagini dei post) da parte dell'automazione può essere bloccato: in quel caso la skill chiede di allegarli a mano.
- Le dimensioni delle immagini indicate (logo 300×300, cover 1128×191, post 1200×627) sono indicative: LinkedIn può cambiarle.
