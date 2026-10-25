# iCoro: guida alla pubblicazione

Questa cartella contiene l'app completa. Non dipende da Claude: i dati stanno in un tuo progetto Firebase (gratuito) e l'app è ospitata sul tuo GitHub Pages (gratuito).

**Come funziona per il coro**
- Tutti aprono un link e vedono canti e scalette sempre aggiornati, senza account.
- Solo tu (e chi decidi tu) accedete come editor da Impostazioni e potete aggiungere o modificare.
- Ognuno può comunque trasporre o mettere il capotasto per sé: resta solo sul proprio dispositivo.
- Dopo la prima apertura funziona anche senza internet con gli ultimi dati scaricati.

## 1. Crea il progetto Firebase
1. Vai su https://console.firebase.google.com e accedi con un account Google.
2. "Crea un progetto", dagli un nome (es. icoro). Puoi disattivare Google Analytics.

## 2. Database e accessi
1. Menu "Build" → "Firestore Database" → "Crea database". Scegli una sede in Europa (es. eur3) e la modalità produzione.
2. Menu "Build" → "Authentication" → "Inizia" → abilita "Email/password".
3. Nella scheda "Users" → "Aggiungi utente": inserisci email e password di ogni editor (tu e chi cura il repertorio).

## 3. Regole di sicurezza
1. Firestore Database → scheda "Regole".
2. Cancella tutto, incolla il contenuto di `firestore.rules` e sostituisci `TUA-EMAIL@esempio.it` con le email degli editor creati sopra (una per riga, tra apici, separate da virgole).
3. "Pubblica". Senza questo passaggio chiunque potrebbe modificare i canti.

## 4. Collega l'app al progetto
1. Ingranaggio accanto a "Panoramica del progetto" → "Impostazioni progetto" → in basso "Le tue app" → icona web `</>`.
2. Registra l'app (nome a piacere, niente Hosting).
3. Copia i quattro valori `apiKey`, `authDomain`, `projectId`, `appId` e incollali in `config.js` al posto di INCOLLA-QUI. Questi valori non sono segreti: a proteggere i dati sono le regole del passo 3.

## 5. Pubblica su GitHub Pages
1. Su https://github.com crea un repository pubblico (es. canti).
2. "Add file" → "Upload files": carica tutti i file di questa cartella (anche `config.js` già compilato). Conferma con "Commit".
3. "Settings" → "Pages" → Source: "Deploy from a branch", branch `main`, cartella `/ (root)` → Save.
4. Dopo un minuto l'indirizzo è `https://TUOUTENTE.github.io/canti/`. Questo è il link da mandare al coro.

## 6. Primo avvio
1. Apri il link, Impostazioni → Accesso editor → entra con email e password.
2. Per portare i canti già scritti nella versione su Claude: lì Impostazioni → "Scarica copia"; qui Impostazioni → "Ripristina da file". Gli esempi iniziali non vengono copiati nella versione online.
3. Da qui in poi aggiungi canti con "Nuovo canto" e crei le scalette.

## Installarla come app
- iPad/iPhone (Safari): Condividi → "Aggiungi a Home".
- Android (Chrome): menu ⋮ → "Installa app" o "Aggiungi a schermata Home".

## Note
- Il piano gratuito di Firebase (Spark) è ampiamente sufficiente per un coro.
- La lettura da foto non c'è più, perché richiedeva Claude. I canti si scrivono o incollano; l'editor converte accordi sopra al testo nel formato interno.
- Se aggiorni i file su GitHub e il coro vede ancora la vecchia versione, basta chiudere e riaprire l'app due volte.
- Se l'accesso non funziona dopo la pubblicazione: Authentication → Settings → "Domini autorizzati" → aggiungi `TUOUTENTE.github.io`.
