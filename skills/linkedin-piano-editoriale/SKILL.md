---
name: "linkedin-piano-editoriale"
description: "Piano editoriale LinkedIn per una pagina aziendale (o un cliente): 1 post al giorno + 1 articolo a settimana, immagini con ChatGPT o Nano Banana, pubblicazione via Chrome con conferma. Riutilizzabile."
---

# LinkedIn – Piano editoriale (post quotidiano + articolo settimanale, con immagini e pubblicazione)

Serve a costruire e far girare il piano editoriale di una pagina aziendale LinkedIn: calendario, bozze dei post, articolo settimanale, immagini, pubblicazione, revisione delle metriche. Funziona per la pagina dell'utente e per quelle dei suoi clienti: tutto ciò che è specifico del brand viene raccolto all'inizio e non è mai dato per scontato.

Skill collegate: `linkedin-pagina-aziendale` (creazione/ottimizzazione della pagina), `linkedin-articoli-da-sito` (scrittura dell'articolo, con ToV preso dal sito). Questa skill le orchestra, non le sostituisce.

## 1. Raccogli il brief (solo ciò che manca)

Prima di scrivere, verifica cosa è già noto (conversazione, documento di lavoro, sito). Chiedi in un'unica volta solo i buchi:

- **Brand e sito di riferimento** (URL). Leggilo per ToV, offerta, pubblico. Se il sito non è raggiungibile (redirect, blocchi), dillo e chiedi screenshot o testi.
- **Obiettivo** (seguaci, lead, iscritti a un test/assessment, vendite libri/corsi) e **CTA unica** con URL.
- **Pubblico** (ruoli, settori) e **tono** (es. competente, curioso, umano; cosa NON fare: catastrofismo, gergo, hype).
- **Pilastri editoriali**: proponine 3–4 tratti dall'offerta e dal sito, fai confermare.
- **Cadenza**: default 1 post/giorno nei giorni lavorativi + 1 articolo/settimana. Stima onestamente la sostenibilità (tempo di rilettura, immagini) e ridimensiona se serve.
- **Materiali e brand kit**: logo, palette, font, immagini, personaggi/mascotte, libri, casi, dati, social proof. **Chiedi sempre all'utente di caricare logo e immagini che vuole usare**: non rigenerare né alterare mai un logo o un personaggio esistente. Non inventare mai casi, numeri, clienti, citazioni: se manca, segna `[DA COMPLETARE: …]`.
- **Dati vincolanti**: date di eventi/corsi/uscite, norme citate (verificale con una ricerca prima di scriverle).
- **Permessi di pubblicazione**: chiedi se la pubblicazione via Chrome deve avvenire post per post con conferma (default) o se l'utente approva un lotto (es. "pubblica i post di questa settimana alle 9:00").

Assunzioni fatte senza risposta vanno dichiarate in cima al piano.

## 2. Struttura del piano

**Pilastri** (esempio, da adattare): Verifica (smontare un'affermazione dell'AI con fonti), Pratica (un passo da fare oggi), Settore/pubblico (es. scuola, PMI), Norme e contenuti (regolamenti, libri, strumenti).

**Ritmo settimanale** (default, modificabile): lunedì apertura/verifica; martedì pratica; mercoledì settore; giovedì norme/libri; venerdì domanda al pubblico o sintesi; **un giorno fisso per l'articolo** (es. mercoledì) con post-teaser lo stesso giorno.

**Calendario 30 giorni**: tabella con data, giorno, pilastro, tema, formato (testo / immagine / carosello / articolo), immagine abbinata, CTA, stato. Nessun giorno senza tema. Alterna le CTA: non più di 2 post su 5 con link all'offerta.

**Regola dei link**: ogni link a un sito proprio porta parametri UTM coerenti: `utm_source=linkedin&utm_medium=post|article|company_page&utm_campaign=<nome-campagna>`.

## 3. Bozze dei post

Per ogni post: gancio nella prima riga (visibile prima del "altro"), corpo breve a paragrafi corti, un solo concetto, una domanda finale che invita a rispondere, 3–5 hashtag in fondo, CTA al massimo una. Lunghezza indicativa 600–1.300 caratteri. Indica l'immagine abbinata. Niente promesse non verificabili, niente elenchi di emoji decorative.

Controlla ogni bozza contro il ToV del brief e contro i divieti (gergo, catastrofismo, hype). Fatti, norme e numeri: verificali con ricerca e cita la fonte nel documento di lavoro.

## 4. Articolo settimanale

Un articolo a settimana, 600–900 parole, che approfondisce il tema del post più forte della settimana o un tema dell'anno. Usa `linkedin-articoli-da-sito` per la stesura. Ogni articolo: titolo promettente senza clickbait, sottotitolo, 3–4 sezioni, una frase di sintesi, CTA finale con UTM `utm_medium=article`, immagine di copertina. Pubblica sempre anche un post-teaser di 3–4 righe con link, perché l'articolo da solo ha poca distribuzione. Se il cliente vuole notifiche agli iscritti, valuta la newsletter LinkedIn.

## 5. Immagini (ChatGPT o Nano Banana)

Ogni contenuto con immagine ha un brief visivo: soggetto, stile coerente con il brand kit (colori esadecimali, font, mood), formato (post 1200×627 o 1080×1080; copertina articolo 1280×720 circa; cover pagina 1128×191), testo nell'immagine (poco, leggibile da mobile) e cosa NON deve comparire.

Scegli il percorso in quest'ordine:
1. **Connettore o strumento di generazione disponibile** nella sessione (es. un MCP per immagini): usalo.
2. **Chrome con l'account dell'utente già collegato** a ChatGPT (chatgpt.com) o a Gemini/Nano Banana (gemini.google.com): apri un nuovo tab, incolla il prompt, genera, mostra il risultato all'utente. Il download di file richiede il permesso esplicito dell'utente (indica nome file, fonte, dimensione).
3. **Altrimenti**: consegna prompt pronti da incollare, uno per immagine, con formato e istruzioni di stile. Specifica sempre: "usa il logo/immagine caricati come riferimento, non ridisegnarli".

Regole: mai rigenerare o alterare logo, mascotte o personaggi esistenti; se servono, vanno forniti come immagini di riferimento. Se il testo generato nell'immagine ha errori (accenti, refusi), correggi con un secondo prompt o componi il testo a parte. Controlla leggibilità a dimensione ridotta prima di approvare. Niente persone reali riconoscibili, niente loghi di terzi.

## 6. Consegna del piano

Il piano e le bozze vanno in un **documento** (Docs) condivisibile con il cliente: brief e assunzioni, pilastri, calendario, bozze, articoli, brief/prompt delle immagini, checklist di pubblicazione, metriche, elenco `[DA COMPLETARE]`. Chiudi la risposta con una sintesi di due righe e il link, non con il documento incollato.

## 7. Pubblicazione via Chrome (Claude in Chrome)

Lavora in un nuovo tab, con l'account dell'utente già collegato a LinkedIn. Verifica che la pagina corretta sia selezionata come autore ("Pubblica come <pagina>").

**Conferma prima di pubblicare.** Pubblicare è un'azione irreversibile e pubblica: mostra all'utente testo finale, immagine, link con UTM e orario e attendi un sì esplicito nella chat. L'approvazione vale solo per i contenuti elencati; un lotto approvato (es. i post della settimana) va pubblicato esattamente come approvato, senza modifiche. Se il testo cambia dopo l'approvazione, richiedi conferma.

Flusso per un post: Crea → Crea un post → clicca sul testo segnaposto "Di cosa vorresti parlare?" → digita il testo con la tastiera → allega l'immagine → controlla anteprima del link → (programma, se richiesto, con l'icona orologio) → Pubblica. Per un articolo: Crea → Pubblica un articolo (o "Scrivi un articolo"), poi post-teaser.

Regole pratiche emerse sul campo:
- **Caricamento file**: l'automazione può non essere autorizzata a caricare file (logo, cover, immagini). Se rifiuta, non ritentare: dillo e chiedi all'utente di allegare l'immagine (icona immagine nel compositore), indicando nome file e formato. Poi puoi completare e, con la conferma, pubblicare.
- **Campi di testo**: l'impostazione diretta del valore (form_input) può non aggiornare lo stato del modulo e il salvataggio risulta vuoto. Clicca nel campo e digita con la tastiera, poi verifica.
- **Compositore post**: clicca sul testo segnaposto, non sull'area vuota sotto, altrimenti il testo non entra.
- **Autocompletamento indirizzi**: scegli il suggerimento e controlla che i campi non si siano sovrascritti.
- Il campo "Panoramica" in modifica può apparire vuoto anche se salvato: verificalo con "Visualizza come utente" e non risalvare il campo vuoto.
- **Fissare un post**: tre puntini sul post nella gestione della pagina → "Gestisci elementi in primo piano" (non esiste "Fissa in alto"). Visibile solo da amministratore e solo dopo la pubblicazione.
- Popup "condividi le modifiche in un post" dopo un salvataggio: "No grazie", salvo diversa richiesta.
- **Programmazione**: se l'utente chiede orari, usa la programmazione di LinkedIn (icona orologio nel compositore) invece di tenere aperta la sessione.
- Se dopo 2–3 tentativi un'azione non funziona, fermati e spiega cosa vedi. Dopo la pubblicazione verifica che il post compaia nella pagina e riporta lo stato; chiudi i tab che hai aperto.

## 8. Metriche e revisione (dopo 2–4 settimane)

Guarda: impressioni, follower nuovi, tasso di interazione per pilastro, clic sulla CTA (UTM), visualizzazioni dell'articolo. Se i dati non sono sufficienti (pagina nuova, pochi numeri), dillo: non interpretare dati insufficienti. Proponi 2–3 correzioni concrete (pilastro, formato, orario, CTA) e aggiorna il calendario.

## Regole di qualità

- Mai inventare: casi, clienti, statistiche, citazioni, date. Se non verificato, `[DA VERIFICARE]` o `[DA COMPLETARE]`.
- Un solo messaggio e una sola CTA per contenuto.
- Adatta ogni piano al cliente: non riusare tono, slogan, pilastri o immagini di un altro brand.
- Dichiara i limiti (tempo, risorse, permessi, assenza di dati) prima, non dopo.