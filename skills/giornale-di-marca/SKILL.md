---
name: giornale-di-marca
description: Crea un giornale PDF personale con l'identità di UN marchio (logo, palette, font, voce) a partire da un questionario. Wrapper generico su leaderai-giornale, riutilizzabile per clienti diversi.
---

# Giornale di marca (generico, da personalizzare con un questionario)

Produce un giornale PDF A4 a pagina singola con la veste e la voce di un marchio qualsiasi: stessa ricerca, stessi controlli della skill `leaderai-giornale` (4-6 notizie, 450-750 parole, fonti cliccabili, nessun taglio silenzioso), ma testata, colori, font, tagline e voce editoriale vengono da un file `brand.json` compilato con le risposte della persona. Non modifica la skill originale: un wrapper legge il runner installato, applica sostituzioni esatte e lo esegue. Se un aggancio non si trova (runner aggiornato) si ferma con errore invece di produrre un PDF sbagliato.

È la versione generica di `eppure-giornale`: niente dati di un marchio specifico. Usala per il marchio dell'utente o per quello di un cliente; un marchio = una cartella dati = un `brand.json`.

## Prerequisiti

1. `leaderai-giornale` installata (serve il suo `scripts/giornale.py`). Esegui prima `python3 <skill>/scripts/giornale.py doctor`.
2. Una cartella dati privata per questo marchio, FUORI da qualunque repository pubblico (conterrà configurazione, edizioni, logo). Esegui `bootstrap` del runner originale per creare la `.venv` (ReportLab, Pillow) e usa quel Python.
3. Il **logo** del marchio come file immagine (PNG su fondo uniforme, meglio se SVG/PDF convertito). **Chiedi sempre di allegarlo o di indicare il percorso.** Non ridisegnarlo, non inventarlo, non deformarlo. Senza logo il wrapper usa il nome in testo.

## Questionario di personalizzazione

Prima di creare qualsiasi file, verifica cosa è già noto (conversazione, brand kit, sito, documenti indicati dalla persona: non cercare nella home, nelle email o in cartelle private). Chiedi solo ciò che manca, a blocchi (con AskUserQuestion dove disponibile, altrimenti in un unico messaggio numerato). Proponi default sensati e fai confermare: non inventare mai interessi, fonti, slogan o dati di un marchio.

**A. Identità**
1. Nome del marchio (come compare in testata e nei metadati).
2. Tagline (max 60 caratteri) e, se esiste, sottotitolo/motto in 3 tempi (max 60 caratteri).
3. Scritta in alto a destra (es. «Il giornale di <Marchio>»).
4. Frase a piè di pagina (es. «<Marchio>: fonti cliccabili; verifica alla fonte prima di decidere.»).

**B. Grafica**
5. Logo: file allegato o percorso. Esiste un manuale di marca? (Se sì, chiedi di allegarlo: palette e regole d'uso si prendono da lì.)
6. Palette: colore del testo (`ink`), fondo (`paper`), accento per le etichette di sezione (`accent`), testi secondari (`muted`); facoltativi: filetti (`rule`) e «punto» decorativo accanto alla tagline (`dot`). Formato `#RRGGBB`. Controlla il contrasto testo/fondo (almeno 4,5:1).
7. Font: serif per titoli e testi, sans per didascalie. Default: Liberation Serif (metricamente affine a Times) e Helvetica. Font diversi solo se la persona fornisce i file TTF (3 per il serif: regular, bold, italic; 2 per il sans: regular, bold) e se la pagina regge ancora (font larghi come Georgia possono non entrare in una pagina).

**C. Contenuti**
8. Temi/interessi da seguire (3-6) e area geografica/lingua delle fonti.
9. Fonti primarie preferite (istituzioni, produttori, autorità, testate), con URL.
10. Argomenti da escludere (se ce ne sono; sono preferenze del marchio, mai default).
11. Finestra temporale (default 24-48 ore, estendibile fino a un massimo da concordare) e numero di notizie (4-6).

**D. Voce**
12. Tre aggettivi per la voce e cosa NON deve mai fare (es. catastrofismo, gergo, superiorità, hype).
13. Struttura desiderata per gli articoli (es. «una domanda + una prova + un passo pratico»; oppure semplice cronaca con fonte).
14. Vincoli legali o di reputazione: affermazioni da non fare, marchi di terzi da non citare, indirizzi web da non inserire.

**E. Consegna**
15. Motore: Claude o Codex (il doctor lo rileva; chiedi solo se entrambi sono presenti e il contesto non decide).
16. Orario e fuso (default 06:00, Europe/Rome), cartella di destinazione dei PDF sul computer della persona, nome file (`<Prefisso>-AAAA-MM-GG.pdf`).
17. Serve anche una bozza di post LinkedIn per ogni numero? Vanno pubblicate le edizioni sul sito? Se sì dove (la skill non pubblica nulla da sola).

Riepiloga le risposte in una tabella e chiedi conferma prima di procedere.

## Regole editoriali di base (valide per ogni marchio)

- **Se su un tema non ci sono notizie, non si scrive nulla** su quel tema: niente «nessuna notizia su X» in pagina, nella nota o nei post.
- **La nota di edizione** contiene solo l'intervallo di date (es. «Notizie del 26-29 ottobre 2026.»). Mai riferimenti a strumenti, CLI, runner o processo; mai la parola «parziale» scritta a mano (la antepone il runner se `coverage` è `partial`).
- I limiti reali della ricerca (pagine primarie non lette, errori di login, fonti secondarie) vanno nel campo `audit` del JSON. Se un limite è grave (fonte pertinente bloccata con HTTP 403, ricerca che non copre il tema principale) usa `coverage: partial` e dillo alla persona. Mai `complete` se la ricerca è stata bloccata.
- Ogni articolo mostra la sua fonte; distingui sempre ciò che dichiara il produttore da ciò che è verificato.
- Mai inventare marchio, sito, dominio, dati o citazioni del cliente.

## Preparazione (una volta per cartella dati)

1. Crea `<dati>/brand/scripts/brand_giornale.py` con il codice del wrapper in fondo a questa skill (copialo senza modifiche) e un file `<dati>/brand/.install.json` contenente `{}` (serve allo scheduler).
2. Crea `<dati>/brand/brand.json` dalle risposte al questionario (schema e esempio in fondo). Poi `PYTHON_VENV <dati>/brand/scripts/brand_giornale.py check-brand`: valida colori e lunghezze.
3. Se c'è il logo: `PYTHON_VENV <dati>/brand/scripts/brand_giornale.py prep-logo --source "PERCORSO/logo.png"`. Produce `<dati>/brand/masthead.png`, ritagliato e con sfondo trasparente (nessun riquadro). Controlla il risultato prima di procedere.
4. `PYTHON_VENV <dati>/brand/scripts/brand_giornale.py init --data-dir <dati> --engine <claude|codex> --binary <PERCORSO ASSOLUTO CLI> --interest "…" --source "https://…"` (ripeti `--interest` e `--source` per ciascuno), con `--timezone` e `--at` se diversi dal default.
5. In `<dati>/config.json` imposta `"runner_path"` sul percorso assoluto del wrapper, così `schedule --plan` richiama la versione di marca.
6. **Prova di impaginazione**: `render <esempio.json> --output prova.pdf --demo` con l'edizione dimostrativa del runner originale (`examples/edition-demo.json`). Apri il PDF: una pagina, logo senza riquadro e non deformato, tagline e sottotitolo non sovrapposti ai box in alto a destra, corpo ≥ 9 pt, colori coerenti con la palette. Se qualcosa non va, correggi `brand.json` (tagline più corta, logo diverso) e riprova.

Da qui usa **sempre il wrapper** al posto di `giornale.py` (`run`, `render`, `status`, `feedback`, `schedule --plan`, `recover-note`). Il PDF si chiama `<Prefisso>-AAAA-MM-GG.pdf`.

## Ogni numero

`PYTHON_VENV <dati>/brand/scripts/brand_giornale.py run --data-dir <dati>`; poi apri il PDF e controlla: una pagina, logo corretto, corpo ≥ 9 pt, link attivi, nota neutra. Un errore resta in `status`: non ripetere alla cieca.

Se la CLI del motore risponde «Authentication error» (tipico nei sandbox senza login), non aggirarlo: fai la ricerca con i tuoi strumenti web, scrivi `editions/AAAA-MM-GG/edition.json` con i campi dello schema (`date, status, window_hours, note, coverage, audit, articles`), poi `render <json> --output <pdf>` (o `run --resume-render` se esiste una ricevuta fallita). Rispetta 450-750 parole: se «il testo non entra in una pagina», accorcia i corpi (circa 120 parole per articolo con 5 articoli), non il layout.

## Consegna (attività pianificata)

Ogni esecuzione pianificata parte da una sessione nuova e vuota: ricostruisci cartella dati, venv, wrapper, `brand.json` e logo da questa skill e dai file del marchio, genera il numero e copia il PDF nella cartella scelta (collegata come cartella), con il nome concordato. Il computer deve essere acceso con l'app aperta. Nelle esecuzioni non presidiate salva accanto al PDF una bozza di post (`<Prefisso>-AAAA-MM-GG-post.txt`); **non pubblicare mai** senza che la persona abbia confermato il testo in una sessione interattiva.

## Post LinkedIn (solo se richiesto nel questionario)

Struttura da concordare con il marchio; schema di partenza: apertura con una domanda o un fatto, cosa è stato fatto, la prova (data e fonte per ogni notizia; dichiarato dall'azienda vs verificato), un passo pratico, una domanda finale, 3-5 hashtag adatti ai temi. Niente frasi sui temi senza notizie. Pubblica con Claude in Chrome solo dopo conferma del testo; i file non si possono allegare da automazione (pubblica senza allegato o fai allegare alla persona). Rifiuta le proposte di promozione a pagamento. Per il piano editoriale completo vedi `linkedin-piano-editoriale`.

## Aggiornamenti e manutenzione

- Se `leaderai-giornale` viene aggiornata e il wrapper risponde «Aggancio non trovato», non forzare: leggi il nuovo `giornale.py`, aggiorna la sola sostituzione che non combacia in `build_replacements`/`MASTHEAD_OLD` e rigenera una prova.
- Se cambia il brand (palette, tagline, logo) modifica solo `brand.json` (e ripeti `prep-logo`), poi rigenera la prova.
- Limiti del layout: tagline ≤ 60 caratteri, sottotitolo ≤ 60, logo o nome limitati a 150 pt di larghezza; senza logo un nome lungo viene rimpicciolito.
- I dati di un cliente restano nella sua cartella dati: non copiarli in questa skill né in repository pubblici.

## Schema di `brand.json`

Campi obbligatori: `name`, `header_right`, `tagline`, `footer`, `voice`, `colors.{ink,paper,accent,muted}`. Facoltativi: `subline`, `pdf_prefix`, `colors.rule`, `colors.dot`, `name_font_size` (default 48, usato solo senza logo), `fonts.serif_files` (3 TTF) e `fonts.sans_files` (2 TTF). `voice` è testo libero senza parentesi graffe problematiche (vengono comunque neutralizzate).

```json
{
  "name": "Studio Esempio",
  "header_right": "Il giornale di Studio Esempio",
  "tagline": "Capire prima di decidere.",
  "subline": "Un fatto · Una fonte · Un passo",
  "footer": "Studio Esempio: fonti cliccabili; verifica alla fonte prima di decidere.",
  "pdf_prefix": "StudioEsempio",
  "colors": {
    "ink": "#1F2A30",
    "paper": "#FAF8F2",
    "accent": "#1F6F78",
    "muted": "#4A5560",
    "rule": "#B9B2A3",
    "dot": "#C69B4B"
  },
  "fonts": {
    "serif_files": [],
    "sans_files": []
  },
  "voice": "VOCE: competente, curiosa, umana. Serietà nei contenuti, ironia leggera nel modo di raccontarli. Mai catastrofismo, toni di superiorità o gergo. Per ogni notizia: cosa è successo, la prova (dato, fonte, data) e, dove c'è spazio, un passo pratico."
}
```

## Codice del wrapper (`brand/scripts/brand_giornale.py`)

```python
#!/usr/bin/env python3
"""Giornale di marca: wrapper generico sul runner leaderai-giornale.

Legge <dati>/brand/brand.json, poi il giornale.py installato, applica sostituzioni
esatte (palette, font, testata, voce editoriale, nome file) e lo esegue.
Se un punto di aggancio non si trova (runner aggiornato) si ferma con un errore:
mai un PDF a meta'.

Uso: come giornale.py, piu':
  prep-logo --source FILE.png     prepara <dati>/brand/masthead.png (fondo trasparente)
  check-brand                      valida brand.json e stampa il riepilogo
Posizione attesa: <dati>/brand/scripts/brand_giornale.py  e  <dati>/brand/brand.json
"""
import json, os, re, sys
from pathlib import Path

HERE = Path(__file__).resolve().parent
BRAND_DIR = HERE.parent
CONFIG = BRAND_DIR / 'brand.json'
LOGO = BRAND_DIR / 'masthead.png'

REQUIRED = ['name', 'header_right', 'tagline', 'colors', 'footer', 'voice']
COLOR_KEYS = ['ink', 'paper', 'accent', 'muted']
HEX = re.compile(r'^#[0-9A-Fa-f]{6}$')

# Regole editoriali di base, valide per ogni marchio (modificabili qui).
BASE_RULES = (
    "Il campo note contiene SOLO l'intervallo di date delle notizie (es. «Notizie del 26-29 ottobre 2026.»): "
    "mai elenchi di temi senza notizie, mai riferimenti a strumenti, CLI o processo. "
    "Se su un tema non ci sono notizie, non scriverlo: salta quel tema. "
    "Distingui sempre ciò che dichiara il produttore da ciò che è verificato. "
    "Nessun marchio, sito o indirizzo inventato."
)


def load_brand():
    if not CONFIG.is_file():
        sys.exit(f'brand.json non trovato in {CONFIG}. Compila prima il questionario della skill.')
    b = json.loads(CONFIG.read_text(encoding='utf-8'))
    missing = [k for k in REQUIRED if not b.get(k)]
    if missing:
        sys.exit('brand.json incompleto, mancano: ' + ', '.join(missing))
    for k in COLOR_KEYS:
        if not HEX.match(str(b['colors'].get(k, ''))):
            sys.exit(f'Colore non valido o mancante: colors.{k} (formato #RRGGBB)')
    for k in ('rule', 'dot'):
        if b['colors'].get(k) and not HEX.match(b['colors'][k]):
            sys.exit(f'Colore non valido: colors.{k}')
    if len(b['tagline']) > 60:
        sys.exit('tagline troppo lunga (max 60 caratteri): non entra nella testata.')
    if b.get('subline') and len(b['subline']) > 60:
        sys.exit('subline troppo lunga (max 60 caratteri).')
    b.setdefault('pdf_prefix', re.sub(r'[^A-Za-z0-9]+', '-', b['name']).strip('-') or 'Giornale')
    return b


def find_runner():
    env = os.environ.get('GIORNALE_RUNNER')
    cands = [env] if env else []
    cands += [str(Path.home() / d / 'leaderai-giornale/scripts/giornale.py') for d in ('.claude/skills', '.agents/skills')]
    cands += [str(p) for p in Path.home().glob('.claude/skills/synced/*/leaderai-giornale/scripts/giornale.py')]
    for c in cands:
        if c and Path(c).is_file():
            return Path(c).resolve()
    sys.exit('Runner leaderai-giornale non trovato: installa la skill o imposta GIORNALE_RUNNER.')


def prep_logo(source):
    """Ritaglia il logo, rende trasparente lo sfondo (colore dell'angolo) e fonde i bordi sul colore carta."""
    from PIL import Image, ImageChops, ImageFilter
    im = Image.open(source).convert('RGB')
    bg = im.getpixel((4, 4))
    diff = ImageChops.difference(im, Image.new('RGB', im.size, bg))
    bbox = diff.point(lambda v: 255 if v > 24 else 0).convert('L').getbbox()
    if not bbox:
        sys.exit('Logo vuoto o uniforme: controlla il file.')
    pad = int((bbox[2] - bbox[0]) * .04)
    box = (max(0, bbox[0] - pad), max(0, bbox[1] - pad), min(im.width, bbox[2] + pad), min(im.height, bbox[3] + pad))
    im = im.crop(box)
    near = ImageChops.difference(im, Image.new('RGB', im.size, bg)).convert('L').point(lambda v: 255 if v <= 10 else 0)
    out = im.convert('RGBA')
    out.putalpha(ImageChops.invert(near).filter(ImageFilter.GaussianBlur(1)))
    out.save(LOGO)
    print(LOGO)


def fonts_block(b):
    f = b.get('fonts', {})
    serif = f.get('serif_files') or ['/usr/share/fonts/truetype/liberation/LiberationSerif-%s.ttf' % s for s in ('Regular', 'Bold', 'Italic')]
    sans = f.get('sans_files') or []
    return (
        "\ndef _brand_fonts():\n"
        "    from pathlib import Path as _P\n"
        "    names = ['Times-Roman', 'Times-Bold', 'Times-Italic']\n"
        "    sans = ['Helvetica', 'Helvetica-Bold']\n"
        "    try:\n"
        "        from reportlab.pdfbase import pdfmetrics\n"
        "        from reportlab.pdfbase.ttfonts import TTFont\n"
        f"        serif_files = {serif!r}\n"
        f"        sans_files = {sans!r}\n"
        "        if len(serif_files) == 3 and all(_P(p).is_file() for p in serif_files):\n"
        "            names = ['BrandSerif', 'BrandSerif-Bold', 'BrandSerif-Italic']\n"
        "            for n, p in zip(names, serif_files): pdfmetrics.registerFont(TTFont(n, p))\n"
        "        if len(sans_files) == 2 and all(_P(p).is_file() for p in sans_files):\n"
        "            sans = ['BrandSans', 'BrandSans-Bold']\n"
        "            for n, p in zip(sans, sans_files): pdfmetrics.registerFont(TTFont(n, p))\n"
        "    except Exception:\n"
        "        pass\n"
        "    return names + sans\n"
        "F_SERIF, F_SERIF_B, F_SERIF_I, F_SANS, F_SANS_B = _brand_fonts()\n"
    )


MASTHEAD_OLD = """    txt('EDIZIONE DIMOSTRATIVA' if demo else 'IL TUO GIORNALE PERSONALE', 345, 20, 7)
    line(34, .6, ink)
    txt('LeaderAI', margin-2, 45, 56, 'Times-Bold')
    txt('LE NOTIZIE CHE TI INTERESSANO', margin, 107, 7.7, 'Helvetica-Bold')
    txt('www.salchiarenza.ai', margin, 121, 8)
    c.linkURL('https://www.salchiarenza.ai', (margin,H-134,225,H-120), relative=0)
"""


def masthead_new(b):
    """Testata: logo (o nome in testo) a sinistra, tagline e sottotitolo in una colonna che
    finisce prima dei box 'teaser' (x=326). La larghezza del logo/nome e' limitata a 150 pt."""
    dot = b['colors'].get('dot')
    subline = b.get('subline')
    name_size = int(b.get('name_font_size', 48))
    parts = [
        f"    txt('EDIZIONE DIMOSTRATIVA' if demo else {b['header_right'].upper()!r}, 345, 20, 7)\n",
        "    line(34, .6, ink)\n",
        "    _logo = BRAND_LOGO\n",
        "    if _logo and Path(_logo).is_file():\n",
        "        from PIL import Image as _I\n",
        "        with _I.open(_logo) as _im: _lw, _lh = _im.size\n",
        "        _w = min(98 * _lw / _lh, 150); _h = _w * _lh / _lw\n",
        "        c.drawImage(str(_logo), margin - 2, H - 40 - _h, _w, _h, mask='auto')\n",
        "        _tx = margin + _w + 14\n",
        "    else:\n",
        "        from reportlab.pdfbase.pdfmetrics import stringWidth as _sw\n",
        f"        _ns = {name_size}; _nw = _sw({b['name']!r}, F_SERIF_B, _ns)\n",
        "        if _nw > 150: _ns = _ns * 150 / _nw; _nw = 150\n",
        f"        txt({b['name']!r}, margin-2, 45, _ns, F_SERIF_B)\n",
        "        _tx = margin + _nw + 14\n",
        "    _tw = max(70, 318 - (_tx + 10))\n",
    ]
    if dot:
        parts.append(f"    c.setFillColor(HexColor({dot!r})); c.circle(_tx + 2.5, H - 68, 2.5, fill=1, stroke=0)\n")
    parts.append(f"    draw((paragraph({b['tagline']!r}, _tw, 11, F_SERIF_I, 13), _tx + 10, 60, _tw, 11), 'tagline')\n")
    if subline:
        parts.append(f"    draw((paragraph({subline.upper()!r}, _tw, 6, F_SANS_B, 7.4, muted), _tx + 10, 104, _tw, 6), 'tagline')\n")
    return ''.join(parts)


def build_replacements(b):
    c = b['colors']
    rule = c.get('rule') or c['muted']
    voice = (f"Sei il redattore del giornale personale {b['name']}. Oggi locale: {{now.isoformat()}}.\n"
             + b['voice'].replace('{', '{{').replace('}', '}}') + '\n'
             + BASE_RULES.replace('{', '{{').replace('}', '}}') + '\n')
    return [
        (MASTHEAD_OLD, masthead_new(b)),
        ("['#18211F', '#F3EADD', '#B95F43', '#5B5C52', '#A79D8A']",
         repr([c['ink'], c['paper'], c['accent'], c['muted'], rule])),
        ("'Times-Roman'", 'F_SERIF'), ("'Times-Bold'", 'F_SERIF_B'), ("'Times-Italic'", 'F_SERIF_I'),
        ("'Helvetica-Bold'", 'F_SANS_B'), ("'Helvetica'", 'F_SANS'),
        ("c.setTitle('LeaderAI - Giornale personale - '", f"c.setTitle({(b['name'] + ' - ' + b['header_right'] + ' - ')!r}"),
        ("c.setAuthor('LeaderAI')", f"c.setAuthor({b['name']!r})"),
        ("f'LeaderAI-{day}.pdf'", "f'" + b['pdf_prefix'] + "-{day}.pdf'"),
        ("'Preparato con AI. Fonti cliccabili. Audit completo nel JSON. Verifica prima di decidere.'", repr(b['footer'])),
        ("Sei il redattore del giornale personale LeaderAI. Oggi locale: {now.isoformat()}.\n", voice),
    ]


def main():
    args = sys.argv[1:]
    if args and args[0] == 'prep-logo':
        return prep_logo(args[args.index('--source') + 1])
    brand = load_brand()
    if args and args[0] == 'check-brand':
        print(json.dumps({k: brand[k] for k in ('name', 'header_right', 'tagline', 'colors', 'pdf_prefix')}, ensure_ascii=False, indent=2))
        print('Logo:', LOGO if LOGO.is_file() else 'assente (verra\' usato il nome in testo)')
        return
    runner = find_runner()
    src = runner.read_text(encoding='utf-8')
    for old, new in build_replacements(brand):
        if old not in src:
            sys.exit('Aggancio non trovato (il runner e\' cambiato?): ' + old[:70].replace('\n', ' '))
        src = src.replace(old, new)
    marker = 'def render_pdf('
    if marker not in src:
        sys.exit('Aggancio non trovato: render_pdf')
    src = src.replace(marker, fonts_block(brand) + '\n' + marker, 1)
    src = src.replace("    W, H = A4\n    margin, gap = 25, 13\n",
                      "    W, H = A4\n    margin, gap = 25, 13\n    BRAND_LOGO = LOGO if LOGO.is_file() else ''\n", 1)
    ns = {'__name__': '__main__', '__file__': str(runner), 'LOGO': LOGO, 'Path': Path}
    sys.argv[0] = str(runner)
    exec(compile(src, str(runner), 'exec'), ns)


if __name__ == '__main__':
    main()
```
