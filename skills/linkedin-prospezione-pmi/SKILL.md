---
name: linkedin-prospezione-pmi
description: Individua su LinkedIn titolari di PMI e decisori a cui proporre i tuoi servizi, valutando pochi profili alla volta con una griglia di punteggio e preparando i messaggi. Lavoro a lotti, sempre con la tua approvazione.
---

# LinkedIn – Prospezione PMI (a basso volume, con conferma)

Aiuta l'utente a trovare e qualificare, su LinkedIn, titolari di PMI e altre figure decisionali a cui proporre i suoi servizi. Lavora tramite Claude in Chrome nella sessione LinkedIn dell'utente.

## Principi non negoziabili

LinkedIn vieta lo scraping e l'automazione. Un account limitato o chiuso è un danno reale per l'utente. Quindi:

1. **Solo lavoro assistito, mai massivo.** Claude legge i profili come farebbe una persona che li apre uno alla volta. Niente script che scorrono centinaia di pagine, niente estensioni di esportazione, niente servizi esterni di scraping.
2. **Lotti piccoli.** Massimo **25 profili al giorno** per sessione di lavoro e **non più di 10 per lotto**, poi pausa. Con account gratuito o Premium base meglio **15**. Il limite si abbassa, mai si alza, se LinkedIn mostra segnali di allarme.
3. **Ritmo umano.** Tra un profilo e l'altro aspetta alcuni secondi, apri solo ciò che serve alla valutazione (intestazione, Informazioni, esperienze, attività recente), non percorrere tutti i collegamenti del profilo.
4. **Nessuna azione senza conferma.** Claude non invia inviti, messaggi, commenti o reazioni da solo. Prepara bozze e l'utente decide. Se l'utente chiede di inviare, si invia **un'azione alla volta**, dopo la sua conferma esplicita su testo e destinatario.
5. **Stop immediato ai segnali di allarme.** Se compaiono verifica d'identità, CAPTCHA, avviso di "attività insolita", limite di ricerca raggiunto o caricamenti anomali, Claude **si ferma**, lo dice e non riprova nella stessa giornata. Non risolve CAPTCHA e non aggira i blocchi.
6. **Dati minimi.** Si registra solo ciò che serve a decidere: nome, ruolo, azienda, link al profilo, punteggio, motivo, stato del contatto. Niente telefoni, email o dati personali non pubblici raccolti altrove, niente profili di persone non rilevanti.
7. **Nessun invio di massa.** Un invito con nota personalizzata ha senso solo se c'è un motivo concreto. Niente modelli identici a tutti.

## Cosa chiedere all'utente (prima di iniziare)

Fai le domande in un unico messaggio. Se l'utente ha già un profilo cliente ideale salvato, riutilizzalo.

1. **Cosa vende**: servizio, a chi serve, risultato concreto, prezzo indicativo o fascia.
2. **Cliente ideale (PMI)**: settori, zona (province o regioni), dimensione (dipendenti), ruoli da cercare (titolare, amministratore, direttore generale, HR, formazione, responsabile operativo).
3. **Segnali di opportunità**: cosa rende un profilo "caldo" (assume, sta crescendo, parla di digitale o AI, ha un problema che il servizio risolve, ha appena cambiato ruolo).
4. **Esclusioni**: settori, aziende, persone da non contattare (clienti attuali, concorrenti, contatti già avuti).
5. **Tipo di account**: gratuito, Premium o Sales Navigator. Con Sales Navigator si usano le ricerche salvate; senza, la ricerca standard con filtri.
6. **Tono**: formale o diretto, come vuole presentarsi (nome, ruolo, sito).
7. **Obiettivo del contatto**: una chiacchierata di 15 minuti, un audit, una demo, un invito a un evento.
8. **Dove salvare il risultato**: foglio nuovo (CSV/Excel) o uno esistente da aggiornare.

## Flusso di lavoro

### 1. Definire la ricerca
- Costruisci insieme all'utente i filtri (ruolo, zona, settore, dimensione azienda). Meglio ricerche strette che producono pochi profili buoni.
- Apri la ricerca in Chrome (nuova scheda) oppure usa quella che l'utente ha già impostato. Non aggirare i limiti di ricerca: se LinkedIn li segnala, fermati.

### 2. Lotto di valutazione (max 10 profili)
Per ogni profilo raccogli, dalla pagina pubblica visibile all'utente:
- nome, ruolo attuale, azienda, zona, anzianità nel ruolo;
- dimensione e settore dell'azienda (dalla pagina aziendale, con cautela: sono dati dichiarati);
- sezione Informazioni e ultimi post o attività, per capire temi e momento;
- se c'è già un collegamento in comune o una relazione precedente.

### 3. Punteggio (0-100)
| Criterio | Peso |
|---|---|
| Ruolo decisionale (titolare/amministratore/DG = massimo) | 30 |
| Azienda nel target (dimensione, settore, zona) | 25 |
| Segnale di opportunità recente (post, assunzioni, crescita, tema affine) | 20 |
| Legame o terreno comune (collegamenti, contesto, interessi) | 15 |
| Raggiungibilità (profilo attivo, risponde, messaggi aperti) | 10 |

Fasce: **70+ = priorità**, 50-69 = da valutare, sotto 50 = scartare. Per ogni profilo scrivi in una riga **perché** quel punteggio. Se un dato manca, scrivi "non verificabile" e non indovinare.

### 4. Strategia di contatto (solo per i profili 70+)
Proponi la sequenza più leggera possibile:
1. interazione genuina su un loro contenuto (commento utile, non un "bel post");
2. richiesta di collegamento con nota breve, solo se c'è un motivo concreto;
3. messaggio dopo l'accettazione, senza vendere subito, con una domanda o un'osservazione utile;
4. un solo follow-up dopo 5-7 giorni, poi basta.

Per ogni profilo prepara:
- la nota di collegamento (massimo 300 caratteri);
- il primo messaggio (60-90 parole);
- il follow-up (30-50 parole).

I testi citano un elemento reale del profilo, parlano del problema del destinatario e non del servizio. Niente frasi da catena di montaggio, niente promesse non dimostrabili, niente lusinghe.

### 5. Consegna del lotto
Salva o aggiorna la tabella con queste colonne:
`data | nome | ruolo | azienda | zona | settore | dimensione | link profilo | punteggio | motivo | segnale | azione proposta | stato | prossimo passo`

Stati ammessi: `da valutare`, `scartato`, `da contattare`, `contattato`, `risposto`, `in corso`, `non interessato`, `non contattare`.

Poi mostra all'utente: i profili in priorità con motivo e bozze, quelli da valutare, il numero di profili guardati oggi rispetto al limite.

### 6. Pausa e ripresa
Dopo ogni lotto chiedi se continuare, fino al limite giornaliero. Alla ripresa, aggiorna prima la tabella con gli esiti reali (chi ha accettato, chi ha risposto).

## Conformità (Italia/UE)

- La prospezione B2B su dati professionali pubblici può reggersi sul **legittimo interesse**, ma richiede: motivo professionale pertinente, **informativa** al primo contatto (chi sei, perché scrivi, dove vengono i dati), **facilità di opposizione** ("se preferisci non ricevere altri messaggi, dimmelo e non scrivo più") e **conservazione limitata**.
- Chi dice di non voler essere contattato va marcato `non contattare` subito e non riproposto.
- Non conservare profili non contattati oltre il necessario: suggerisci all'utente di ripulire la tabella ogni 90 giorni.
- Per email e telefono valgono regole diverse (consenso o registro delle opposizioni): questa skill **non** raccoglie contatti fuori da LinkedIn.
- Claude non è un consulente legale: per un uso sistematico suggerisci di far verificare informativa e procedura.

## Alternative meno rischiose per trovare le aziende

Se serve volume, trova le **aziende** fuori da LinkedIn (registro imprese, siti aziendali, Google Maps, elenchi di associazioni di categoria) e usa LinkedIn solo per individuare il titolare di quelle aziende, una per volta. Riduce le ricerche su LinkedIn e migliora la qualità del target.

## Cose da non fare

- Non fingere di essere l'utente in conversazioni lunghe: ogni messaggio inviato passa dalla sua conferma.
- Non inventare dati su persone o aziende; se un dato non è visibile, scrivilo.
- Non cercare, dedurre o registrare dati sensibili (salute, opinioni politiche, religione, orientamento) né usarli per il punteggio.
- Non riprovare dopo un blocco nello stesso giorno, non cambiare scheda o browser per aggirarlo.
- Non superare i limiti di lotto e di giornata, nemmeno se l'utente ha fretta: spiega il rischio e proponi di continuare domani.
