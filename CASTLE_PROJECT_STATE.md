# ✦ THE WITCH'S LAIR — Castle Test Lab | stato al 15 novembre 2026

## Obiettivo del progetto
Costruire **un solo Cursed Castle da incorporare come un solo blocco Notion**, articolato in cinque piani continui, non in cinque embed separati. Le stanze attive mantengono illustrazioni pixel originali, hotspot e animazioni approvate. Tutti i tooltip devono avere identico stile: prima riga **nome dell'oggetto**, seconda riga **nome della pagina Notion**.

## Versioni approvate da preservare (non sovrascrivere)
- Ritual Chamber **V25**: `ritual-chamber-interactive-moonbeam-v25.html`, 6 oggetti; pixel fire/fumo/luci approvati.
- Arcane Library **V16**: `arcane-library-interactive-v16-warm-flames.html`, 9 oggetti; fiamme calde, occhi rossi, clessidra e pixel originali approvati.
- Integrated V1: `castle-test-lab-integrated-v1.html` usa gli originali in due iframe dentro un unico embed; stile tooltip uniformato via accesso al DOM dei frame. Il codice V1 nasconde i controlli delle stanze, incluso il pulsante Motion della Ritual.

## Test corrente — Integrated V2 (non ancora verificato su iPhone/Notion)
**URL:** https://mxrcovic.github.io/witchs-lair/castle-test-lab-integrated-v2-mobile-motion.html

**File:**
- `castle-test-lab-integrated-v2-mobile-motion.html` (pagina unica, cinque piani e pulsante globale ✦ MOTION ON/OFF)
- `ritual-chamber-interactive-v26-castle-motion-test.html` (copia isolata della V25, non modifica i pixel approvati)
- `arcane-library-interactive-v17-castle-motion-test.html` (copia isolata della V16, non modifica i pixel approvati)

I due file di test presentano i tooltip a due righe con lo stesso CSS, anche quando la pagina madre non può leggere i loro DOM; nascondono soltanto header/archivi per l'integrazione. La V2 comunica lo stato motion alle stanze con `postMessage({type:"witchs-lair:motion",enabled:boolean})`. Il comando è visibile anche su mobile e può riaccendere esplicitamente le animazioni se iOS usa `prefers-reduced-motion`. Per ragioni di accessibilità il default rispetta la preferenza del dispositivo (OFF se Riduci movimento è attivo).

**Da verificare in un test reale:** animazioni nella pagina GitHub aperta in Safari, animazioni dentro embed nell'app Notion su iPhone, motion ON/OFF entrambe le stanze, tap e swipe orizzontale sulle illustrazioni, hotspot/tooltip, prestazioni. I risultati NON sono stati verificati nel rendering iOS.

## Limite noto della navigazione
Gli hotspot puntano a pagine Notion con `target="_blank"`. Un embed HTML di GitHub Pages non può richiamare il router interno proprietario di Notion come fanno i blocchi nativi `Link to page`. `target="_self"` aprirebbe Notion nel sotto-iframe e rischierebbe una pagina vuota; `target="_top"` dipende dai permessi sandbox, può essere bloccato o ricaricare l'intera pagina, NON equivale a navigazione nativa. Non dichiarare risolto questo punto senza una prova concreta. Evitare di rompere i 15 link esistenti.

## Criteri di continuità
- Un unico castello, cinque piani, un solo embed.
- Non modificare le illustrazioni approvate, l'allineamento degli hotspot o la geometria delle animazioni.
- Usare versioni nuove per ogni esperimento, non sovrascrivere i file approvati.
- Allineare stile tooltip e azioni tra stanze.
- Distinguere `test di codice` da `verificato nel browser/app`.
