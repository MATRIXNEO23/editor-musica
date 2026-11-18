# Handoff operativo — Una Meta Tan Alta (2026-11-18)

## Scopo
Riprendere in ChatGPT Work + Codex Cloud la produzione del videoclip di **«Una Meta Tan Alta»** senza perdere scelte narrative, riferimento del volto e sincronizzazione approvata dall'utente.

## Stato verificato
- Repository: `MATRIXNEO23/editor-musica` — ramo `main`.
- **Fonte canonica dei sottotitoli:** `data/Una_Meta_Tan_Alta_tempi_sincronizzati.json`; formato `viaje-andino-lyrics-v1`, **47 cue** `{time, end, text}`, secondi relativi all'inizio dell'MP3.
- I tempi sono stati impostati **manualmente dall'utente**, sono autoritativi e **non vanno ritoccati automaticamente**. Il primo cue parte a 2,5 s, l'ultimo è `Para siempre...` 211–213 s. Nel finale strumentale successivo non inventare frasi.
- Traccia di riferimento: `Una Meta Tan Alta.mp3`, durata in precedenti render ~4:12,36. Verificare la durata reale del file allegato prima di esportare.
- Precedente bozza: `Una_Meta_Tan_Alta_TikTok_Ricreato_v2.mp4`, verticale 540 × 960, 12 fps, circa 10,7 MB. **È solo una bozza**, non la versione approvata; contiene problemi di identità nelle ultime due scene e camera ancora 2.5D.
- Il JSON è nella repository; l'MP3 e la fotografia personale sono **fuori dalla repository pubblica**.

## Intento narrativo NON negoziabile
- Storia continua: **dall'oscurità alla luce**, con crescita graduale della speranza e avanzamento verso **lei**, che rappresenta la luce/la meta.
- Ambientazioni ispirate alle Ande (montagne, sentieri, nebbia), **nessuna bandiera del Cile e nessuno scooter**.
- Lei all'inizio è un miraggio delicato, distante e semitrasparente; man mano diventa più nitida e tangibile fino all'**abbraccio conclusivo**.
- **Identità femminile univoca:** preservare in TUTTE le inquadrature e angolazioni i lineamenti visibili nella fotografia fornita dall'utente: forma del viso, occhi, naso/piercing, bocca, sopracciglia, capelli scuri mossi, piccolo neo. Il problema più recente riguarda soprattutto **ultime due inquadrature** che sembrano un'altra persona. Non sostituire con un volto genericamente simile; prevedere controllo frame-by-frame e rigenerare le scene incoerenti.
- Stile **film d'animazione 3D semi-realistico**, chiaramente animato ma vicino al realismo; non foto statiche e non cartoon infantile.

## Regia, effetti e transizioni
- **Video verticale 9:16** per TikTok; attenzione a safe-area in basso per i sottotitoli e alle aree coperte dall'interfaccia social.
- Movimenti cinematografici *percepibili*: carrellate, dolly, panoramiche, avvicinamento/allontanamento e **orbite leggere attorno ai panorami e ai personaggi**. Con un solo still 2D non è una vera orbita 3D: usare più punti di vista/asset coerenti o animazione effettiva; non fingere che lo zoom sia una rotazione 3D.
- Transizioni **pulite, senza due visi o due immagini sovrapposte per diversi secondi**: preferire cut motivati dalla musica, passaggio al nero brevissimo o transizioni con maschera senza morph del volto. Nessuna apparizione di un omino/sagoma stilizzata aggiunta in overlay.
- Luci/bagliori **agganciati ai transienti reali dei bassi/cassa dell'MP3**, con decadimento naturale; evitare flash sul viso di lei, usare cielo, paesaggio e sfondo.
- Effetti naturali: pioggia ridotta, niente pioggia finta o luci kitsch; progressione cromatica freddo/scuro -> dorato/luminoso.
- Le immagini devono illustrare **il testo e l'evoluzione della canzone**; no montaggio casuale o ripetizione di scene senza progressione.

## Sottotitoli
- Leggere **esattamente** `data/Una_Meta_Tan_Alta_tempi_sincronizzati.json`, campo `lyricsData`. Ogni frase appare solo nel proprio intervallo `[time, end)`.
- Preservare testi, accenti e tempi del JSON; niente frasi inventate, nessun offset globale implicito.
- Font leggibile, discreto e non sopra i volti; evitare una scatola enorme al centro del verticale.
- Conservare una possibilità di correzione manuale/export JSON separata dal rendering, ma NON sostituire i dati approvati.

## Soluzione tecnica da definire in Work
- **Tutto in cloud**, niente carico di rendering sul PC dell'utente. Proposta: **Remotion + Codex Cloud + GitHub Actions + FFmpeg** per montaggio e consegna MP4; alternativa equivalente solo se documentata.
- Remotion/Canvas/FFmpeg controllano montage e rendering, **non inventano da soli veri movimenti 3D né garantiscono la stessa identità tra fotogrammi**. Per animazione tridimensionale reale servono clip coerenti, modelli o un motore adatto.
- Costi: preferire soluzioni gratuite/open source; verificare limiti/quota e non attivare servizi a pagamento senza consenso.
- Output: MP4 verticale H.264/AAC direttamente scaricabile; qualità dignitosa ma peso ridotto (obiettivo indicativo ~10–20 MB da valutare), preferire fluidità 24 fps rispetto al vecchio 12 fps se budget lo consente.
- Non effettuare upload di MP3, volto personale o assets privati alla repository **pubblica** senza esplicito consenso e verifica licenze/privacy. Valutare repository privata o artifacts Actions protetti.

## Sequenza operativa per Work
1. Leggere **questo handoff**, `AGENTS.md` e il JSON; verificare il contenuto e la struttura della repository.
2. Recuperare dall'utente/conversazione **MP3 originale, foto reference originale, bozza video** come allegati privati a Work (non inventare URL o affidarsi a `sandbox:` come link persistenti).
3. Definire storyboard per sezioni musicali, pose/angolazioni e criteri di identity consistency, prima di generare/integrare nuovi asset.
4. Allestire repo con codice Remotion/FFmpeg, test su durata/audio, cue JSON, frame di controllo e workflow di cloud rendering; includere README con comandi.
5. Creare **preview breve verticale** di apertura + avvicinamento + esempio transizione + confronto viso (anche finale), chiedere feedback; solo dopo fare full export.
6. Controlli pre-release: nessuna sovrapposizione impropria, viso coerente, ritmo luci, timing JSON invariato, audio sincronizzato, corretto 9:16 e file scaricabile; differenze dalla bozza in changelog.

## Criteri di accettazione
Il video deve seguire davvero la canzone, partire dal buio e arrivare alla luce/abbraccio, mantenere **sempre la stessa lei** della reference anche in profilo e nelle ultime due scene, mostrare movimento di camera cinematografico, transizioni pulite e testo esattamente sincronizzato secondo i 47 tempi approvati. Il rendering si svolge nel cloud, senza operazioni pesanti sul PC.

## Stato dell'handoff
Questa commit conserva **piano e dati**, non certifica che il nuovo rendering/engine siano già stati implementati. Il passo successivo è passare a **ChatGPT Work**, collegare la repo e iniziare dalla lettura di questo file.
