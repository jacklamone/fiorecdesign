# Handoff: Sito Studio Dott. Stefano Fiore

## Obiettivo per Claude Code
Pubblicare e mantenere il sito dello Studio Dott. Stefano Fiore (finanza agevolata e microcredito, Sassari) su GitHub Pages.

- Repository: **jacklamone/fiorecdesign** — ramo `main`, cartella root
- URL pubblico: https://jacklamone.github.io/fiorecdesign/
- Pubblicazione: GitHub Pages "Deploy from a branch" (main / root). File `.nojekyll` presente.

### Primo compito
1. Clonare `jacklamone/fiorecdesign`.
2. Sostituire il contenuto della root con i file di `sito-pronto/` (index.html, favicon.png, apple-touch-icon.png, og-image.jpg, .nojekyll, LEGGIMI.txt).
3. Verificare che non restino duplicati tipo `index 2.html` o sottocartelle con copie vecchie; eliminarli.
4. Commit ("Aggiornamento sito: dati reali, storie, filigrane, form") e push su `main`.
5. Attendere la spunta verde del workflow "pages build and deployment" e controllare l'URL pubblico.

## Com'è fatto il sito
- `sito-pronto/index.html` è un file **unico e autocontenuto** (~6,9 MB): immagini, font e script sono incorporati. È una single-page con 10 viste (Home, Chi siamo, Finanza agevolata, Microcredito, Come lavoriamo, Storie di successo, Contatti, Privacy, Cookie, Note legali) navigate via hash (`#chi-siamo`, `#contatti`, …).
- **Non modificare a mano `index.html`**: è generato. Il sorgente è `sorgente/Studio Fiore v2.dc.html` (Design Component: template HTML con stili inline + una classe logica JS). Le modifiche si fanno di norma nel progetto di design e si riesporta `index.html`.
- Se si decide di passare a un sorgente mantenibile nel repo (es. Astro/Eleventy/HTML statico multipagina), usare `sorgente/` come riferimento hi-fi: ricreare pixel-perfect, stesse copy, colori e comportamenti descritti sotto.

## Fedeltà
Hi-fi: colori, tipografia, spaziature, testi e interazioni sono definitivi e approvati dal cliente.

## Design tokens
Font: **Hanken Grotesk** (Google Fonts) per titoli e testo; pesi 400–800.

| Token | Hex | Uso |
|---|---|---|
| --c-ink | #0e1f3a | blu notte: testate, footer, titoli |
| --c-bg | #f8f6f1 | sfondo pagina |
| --c-surf | #ece8df | superfici chiare |
| --c-tint | #f1e6cf | tinta calda |
| --c-acc | #a8823d | accento oro |
| --c-accd | #7d5f27 | oro scuro: link, etichette |
| --c-accb | #d9b56a | oro chiaro su fondo scuro |
| --c-text | #1a2233 | testo |
| --c-text2 | #36405a | testo secondario |
| --c-mute / --c-mute2 | #56607a / #5e677d | testo attenuato |
| --c-ondark / --c-ondarkm | #d8dde8 / #a3adc2 | testo su blu |
| --c-deco1 / --c-deco2 | #c9b891 / #2c4a7a | decorazioni |

Motivi: trama esagonale sottile (repeating-linear-gradient a 30°) sulle testate blu; logo in filigrana (`mix-blend-mode: screen; filter: grayscale(1) invert(1); opacity: .12`, ruotato ±8°) su testate di Chi siamo, Come lavoriamo, Storie di successo; filigrana `multiply` opacity .08 su sezioni chiare.
Radius card 22px. Animazioni: solo fade-in/scorrimento leggero all'ingresso (`data-reveal`), niente effetti vistosi (richiesta del cliente).

## Interazioni
- Menu a scomparsa su mobile; pulsante "torna su".
- **Form Contatti** → FormSubmit AJAX: `POST https://formsubmit.co/ajax/fiorestefano@hotmail.com` (JSON). Campi + `interesse`, `_subject`, `_replyto`, `_template=table`; honeypot `_honey`. Stato errore con messaggio e mailto. **Al primo invio dal sito online arriva un'email "Activate Form" da confermare.**
- Link WhatsApp `https://wa.me/393469546917`, tel `+393469546917`.

## Dati dello Studio (definitivi)
- Studio Dott. Stefano Fiore – Consulenze aziendali finanza agevolata
- Via Pietro Mastino 1, 07100 Sassari (SS)
- Lun–ven 9:30–13:00 · 15:30–18:30
- Tel/WhatsApp +39 346 954 6917 · fiorestefano@hotmail.com · PEC fiorestefano@arubapec.it
- P.IVA 02519650903 · C.F. FRISFN72P28I452H
- LinkedIn https://www.linkedin.com/in/stefano-fiore-a02bb4a3/ · Facebook https://www.facebook.com/stefano.fiore.735 (niente Instagram)

## Vincoli del cliente
- Storie di successo: **nessun nome di azienda, nessun logo, nessuna foto** — solo tipo di finanziamento, settore, descrizione.
- Footer: a sinistra copyright + Privacy/Cookie/Note legali; a destra "Sito realizzato da" + logo Intellecta Solutions in oro.

## Ancora aperto
- Foto del Dott. Fiore per "Chi siamo".
- Dominio personalizzato (non ancora scelto). Quando c'è: file `CNAME` nella root + DNS.
- Revisione legale di Privacy, Cookie, Note legali.
- Attivazione FormSubmit (click sul link di conferma).

## File
- `sito-pronto/` — da pubblicare così com'è nella root del repo.
- `sorgente/Studio Fiore v2.dc.html` — sorgente di design (richiede `support.js` e `image-slot.js` nella stessa cartella per l'anteprima).
- `sorgente/assets/` — logo-fiore.png, logo-fiore-t.png, logo-intellecta.png, hero-vetro.jpg.
