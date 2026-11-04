---
name: "linkedin-articoli-da-sito"
description: "Scrive articoli LinkedIn (o newsletter) prendendo da un sito di riferimento il Tone of Voice e l'argomento, e chiedendo i parametri mancanti (obiettivo, target, lunghezza, CTA)."
---

# Skill: Articoli LinkedIn da sito di riferimento

Obiettivo: produrre un articolo LinkedIn pronto da pubblicare, con voce coerente con quella del sito di riferimento e contenuto accurato sull'argomento scelto, completo di immagini quando servono.

Lingua: quella dell'utente (di norma italiano), salvo diversa indicazione.

## 1. Input e parametri

L'utente fornisce uno o più **URL di riferimento** (sito, pagine, articoli, blog). Possono servire a due scopi, anche insieme:
- **ToV**: come scrive il brand/la persona.
- **Argomento**: cosa dice il sito sul tema, da cui trarre contenuti e fatti.
Se non è chiaro quale ruolo abbia ogni URL, chiedilo.

Parametri da raccogliere. Se l'utente li ha già dati, non richiederli. Chiedi in un solo giro (usa AskUserQuestion se disponibile, altrimenti un elenco breve) solo quelli mancanti:
1. **Argomento/angolo** dell'articolo (se non ricavabile dal sito).
2. **Obiettivo**: autorevolezza, lead, iscrizioni newsletter, vendita corso/servizio, discussione.
3. **Target**: ruolo, settore, livello di competenza.
4. **Formato**: articolo LinkedIn lungo (800-1.500 parole), post lungo (circa 1.300-3.000 caratteri), newsletter.
5. **Call to action** e link da inserire.
6. **Persona narrante**: prima persona singolare (profilo personale) o noi (pagina aziendale).
7. **Vincoli**: parole da evitare/usare, argomenti da non toccare, dati riservati, riferimenti da citare.
8. **Numero di varianti** di titolo/apertura (default 3).
9. **Immagini**: servono? (copertina, immagini interne, immagine per il post di lancio). Se sì: generarle con **ChatGPT** o con **Nano Banana** (Gemini)? Esiste un brand kit (colori HEX, stile, logo)? Se l'utente non vuole immagini, salta la sezione 5.

## 2. Analisi del sito

Usa WebFetch sugli URL forniti (e, se serve, 2-4 pagine collegate rilevanti: chi siamo, blog, servizi). Se un URL non è raggiungibile, dillo e chiedi di incollare il testo.

Produci internamente (e mostra in breve all'utente prima dello scritto) una **scheda ToV**:
- Registro (formale/colloquiale), persona grammaticale, lunghezza media delle frasi.
- Lessico ricorrente e parole da evitare; presenza di metafore, ironia, domande retoriche.
- Struttura tipica dei contenuti (apertura, ritmo, chiusura).
- Valori e promessa di posizionamento.
- Termini tecnici e come vengono spiegati.
- 5-8 regole operative (es. "frasi brevi, niente anglicismi inutili, un esempio concreto per paragrafo").
- Se il sito ha un'identità visiva: palette, stile delle immagini, tono grafico (serve per la sezione 5).

E una **scheda contenuti**:
- Tesi e fatti del sito sull'argomento (con pagina di provenienza).
- Esempi, casi, dati usabili.
- Lacune da colmare con ricerca esterna.

Mostra la scheda in 10-15 righe e prosegui senza attendere, salvo che emergano ambiguità vere.

## 3. Ricerca di supporto

Se l'articolo afferma fatti attuali o numeri (normative, statistiche, date, prodotti), verificali con WebSearch su fonti primarie prima di scrivere. Non inventare dati, citazioni o casi. Se un dato non è verificabile, evitalo o marcalo [DA VERIFICARE]. Non riprodurre testo dei siti: rielabora con parole proprie e cita la fonte quando serve.

## 4. Scrittura

Struttura di default (adattala al formato):
1. **Titolo** (3 varianti, max circa 70 caratteri, promessa chiara, niente clickbait vuoto).
2. **Apertura** (prime 2-3 righe decisive): scena, domanda o affermazione controcorrente legata al target.
3. **Tesi** in una frase.
4. **Sviluppo** in 3-5 sezioni con sottotitoli brevi, ciascuna con un esempio concreto o un dato verificato.
5. **Cosa fare adesso**: passi pratici o criterio decisionale.
6. **Chiusura** con una sola CTA coerente con l'obiettivo.
7. **Opzionale**: 3-5 hashtag pertinenti e una riga di descrizione per la condivisione.

Regole di stile:
- Rispetta la scheda ToV; in caso di conflitto con le regole generali, vince il ToV.
- Paragrafi brevi (1-3 frasi), molto bianco, elenchi solo quando servono.
- Specificità su genericità: nomi, numeri, situazioni reali, mai aggettivi vuoti.
- Niente frasi "da AI" ripetitive (es. "nel panorama attuale", "in un mondo in cui"), niente elenchi di tre aggettivi di default, niente chiusure retoriche scontate.
- Onestà: nessun risultato, cliente o esperienza inventati. Esperienze personali solo se fornite dall'utente.

## 5. Immagini (ChatGPT o Nano Banana, solo se servono)

Usa questa sezione solo se l'utente vuole immagini o l'articolo ne trae un vantaggio chiaro (una copertina, uno schema, un'immagine per il post di lancio). Non riempire l'articolo di immagini decorative.

1. **Cosa serve**, in ordine di priorità: copertina dell'articolo (rapporto indicativo 16:9, es. 1920×1080 o 1280×720; verifica le specifiche attuali), immagine per il post di lancio (indicativamente 1200×627 o 1080×1080), 1-3 immagini interne solo se spiegano qualcosa (schemi, metafore visive).
2. **Scelta dello strumento.** Usa quello indicato dall'utente. Se non ha preferenze, proponi: ChatGPT per illustrazioni pulite e composizioni con poco testo; Nano Banana per fotorealismo, modifiche su immagini esistenti e coerenza tra più varianti. Sono indicazioni di massima, non regole fisse.
3. **Come eseguire.**
   - Se in sessione è disponibile un connettore o uno strumento che genera immagini con il servizio scelto, usalo.
   - Altrimenti non fingere di generare: consegna per ogni immagine un **prompt pronto da incollare** nello strumento scelto, con rapporto d'aspetto e posizione nell'articolo ("copertina", "dopo la sezione 2"), e di' chiaramente che l'immagine va generata lì. Puoi indicare strumenti di design disponibili (es. Canva, Figma) come alternativa.
4. **Struttura del prompt** (in inglese per maggiore resa, salvo testo da inserire nella lingua del target):
   - Soggetto e scena legati al contenuto dell'articolo; stile coerente con la scheda ToV/visiva del sito; palette in HEX; composizione con spazio libero per titolo o testo; rapporto d'aspetto; cosa evitare.
   - Preferisci immagini **senza testo** e aggiungi il testo in un editor: il testo generato dall'AI può contenere errori, specie in italiano. Se deve essere generato, mettilo tra virgolette e verifica ogni lettera.
5. **Varianti**: 2-3 prompt per la copertina (più concreta, più metaforica, più sobria) con consiglio motivato.
6. **Vincoli.** Niente persone reali riconoscibili, loghi o marchi altrui, personaggi protetti. Niente immagini ingannevoli (finti screenshot, grafici con dati inventati, finti risultati). Per grafici con dati reali, usa dati verificati e costruiscili con uno strumento di data-viz anziché farli generare a un modello.
7. **Testo alternativo**: scrivi una breve alt text per ogni immagine.
8. **Dopo la generazione**, se l'utente incolla o allega il risultato, controllalo (coerenza col testo, leggibilità su mobile, errori, artefatti) e proponi un prompt di correzione.

## 6. Output

Consegna:
1. Scheda ToV + scheda contenuti (breve).
2. Titoli alternativi.
3. Articolo completo, pronto da copiare, con conteggio di parole/caratteri e segnaposto di posizione per le immagini.
4. Immagini: prompt (o immagini generate, se disponibile uno strumento) con strumento, formato, posizione e alt text.
5. Elenco di fatti/dati usati con fonte (Sources) e punti [DA VERIFICARE].
6. Una proposta di variante breve come post di lancio (circa 1.000-1.300 caratteri) con gancio e link.

Se l'articolo è lungo e l'utente lo conserverà o modificherà, creane un doc; per testi brevi resta in chat.

## 7. Controlli finali

- La voce somiglia al sito di riferimento (verifica contro le regole operative).
- Le prime due righe reggono da sole nel feed.
- Una sola idea centrale e una sola CTA.
- Ogni dato ha una fonte; nessun testo copiato dal sito (parafrasi, citazioni brevissime).
- Formato e lunghezza rispettano i parametri.
- Le immagini servono al contenuto, rispettano formato e palette e non contengono testo non verificato.
- Rilettura per eliminare ripetizioni e frasi generiche.

## 8. Iterazione

Dopo la consegna, se l'utente corregge il tono ("troppo formale", "più diretto"), aggiorna la scheda ToV e riscrivi applicando la regola a tutto il testo, non solo al punto segnalato. Lo stesso vale per lo stile delle immagini: aggiorna la scheda visiva e rigenera i prompt.