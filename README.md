# SegFolt Toornament 🏓

Web app per le classifiche di ping pong: inserimento delle gare da WhatsApp, classifica generale e settimanale, SEG counter, ordine al tavolo, andamento della season e albo d'oro.

- **Pagina:** `index.html`, servita da GitHub Pages
- **Dati:** `data.json`. Ogni gara inserita dall'app è un commit, quindi lo storico completo è in *Commits*

## Messa online (una volta sola)

1. **Crea il repository.** Su GitHub fai *New repository*, per esempio `pingpong`, **Public**. Carica i file di questa cartella (`index.html`, `data.json`, `README.md`, `.nojekyll`) con *Add file → Upload files* e poi *Commit changes*.
2. **Attiva GitHub Pages.** Vai in *Settings → Pages*. In *Source* scegli *Deploy from a branch*, poi *Branch* `main` e cartella `/ (root)`, e premi *Save*. Dopo un minuto circa la pagina è su `https://TUO-UTENTE.github.io/pingpong/`.
3. **Crea il codice di accesso** per chi inserisce le gare:
   - Avatar → *Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token*
   - *Token name*: `pingpong`. *Expiration*: la durata che preferisci, anche *No expiration*.
   - *Repository access*: **Only select repositories**, poi scegli `pingpong`.
   - *Permissions → Repository permissions → Contents*: **Read and write**.
   - *Generate token* e copia il codice (`github_pat_…`).
4. **Distribuisci il codice.** Chi deve inserire apre la pagina, va nella scheda **Accesso** e incolla il codice. In alternativa puoi mandare nel gruppo un link già pronto, che salva il codice da solo:
   `https://TUO-UTENTE.github.io/pingpong/#token=github_pat_…`

Chi non ha il codice può comunque consultare tutto.

> Il codice permette di modificare **solo** i file di questo repository. Non scriverlo mai dentro i file del repository: GitHub lo disattiverebbe. Se finisce nelle mani sbagliate, revocalo dalla stessa pagina dei token e creane uno nuovo. Ogni modifica resta comunque nello storico e si può annullare.

## Uso quotidiano

- **Inserisci gara:** scegli giorno e gara (1–3), incolla l'elenco da WhatsApp (di default dall'ultimo al primo) e salva.
- **Ordine:** il primo giorno di gioco della settimana l'ordine segue la generale (a pari punti decide il SEG counter), dal secondo giorno la settimanale (a pari punti decide la generale).
- **Season:** a fine season vince chi ha più punti in generale + SEG counter. "Chiudi season" salva il vincitore nell'albo d'oro e azzera tutto.

Dopo ogni salvataggio, chi ha il codice vede subito i dati aggiornati. Chi consulta senza codice li vede circa un minuto dopo, il tempo che GitHub Pages ripubblichi il sito. La pagina si aggiorna da sola ogni 30 secondi.

## Correggere o annullare

- Una gara sbagliata si elimina dalla scheda *Storico gare*.
- Per tornare a una situazione precedente: su GitHub apri `data.json` → *History*, scegli il commit e fai *Revert*, oppure modifica il file a mano.

## Aggiornare l'app

Si sostituisce `index.html` con la nuova versione (*Add file → Upload files*). `data.json` non va toccato: i dati restano.

## Dominio personalizzato

Se la pagina non sta su `*.github.io`, compila `owner` e `repo` in cima allo script di `index.html`:

```js
const CONFIG = { owner: 'tuo-utente', repo: 'pingpong', branch: 'main', dataPath: 'data.json' };
```
