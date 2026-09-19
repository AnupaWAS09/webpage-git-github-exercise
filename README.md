# Progetto Webpage condiviso

**Esercizio didattico su Git e GitHub:** fork, clone, modifica di una pagina HTML, commit, push e Pull Request.

---

# Costanti del progetto

Per evitare confusione, in questo esercizio useremo sempre questi nomi.

| Elemento                  | Valore                        |
| ------------------------- | ----------------------------- |
| Repository del Professore | `https://github.com/ProfNardi/webpage-git-github-exercise` |
| Branch principale         | `main`                        |
| Branch classe 4CI         | `Classe4CI`                   |
| Branch classe 4DI         | `Classe4DI`                   |
| Repository dello studente | il proprio **Fork**           |
| Remote del proprio GitHub | `origin`                      |
| Remote del Professore     | `upstream`                    |
| File da modificare        | `index.html`                  |

### Struttura del repository del Professore

```text
webpage-git-github-exercise
│
├── main
├── Classe4CI
└── Classe4DI
```

Gli studenti della **4CI** lavorano sul branch `Classe4CI`.

Gli studenti della **4DI** lavorano sul branch `Classe4DI`.

> **Importante:** `main`, `Classe4CI` e `Classe4DI` sono **branch**.
> `origin` e `upstream` sono invece nomi di **remote**.

---

# 1. Il modello di lavoro

Abbiamo due repository:

| Mio GitHub              | GitHub del Professore                          |
| ----------------------- | ---------------------------------------------- |
| È il mio Fork personale | È il repository originale                      |
| Qui faccio `push`       | Qui propongo le modifiche tramite `Pull Request` |
| Remote: `origin`        | Remote: `upstream`                             |

Il flusso è:

```text
GitHub del Professore
       │
      Fork
       ▼
Mio GitHub
       │
     clone
       ▼
Mio PC
       │
   modifica
       │
   add → commit → push
       │
       ▼
Mio GitHub
       │
 Pull Request
       ▼
GitHub del Professore
```

---

# 2. Creare il Fork

Apri il repository del Professore su GitHub.

Clicca:

**Fork**

Avrai così una copia del progetto nel tuo account GitHub.

---

# 3. Scegliere il branch della classe

Il Professore ha creato due branch:

```text
Classe4CI
Classe4DI
```

Usa il branch della tua classe.

---

# 4. Clonare il proprio repository

Dal **proprio Fork** su GitHub:

**Code → HTTPS**

Copia l'indirizzo e, nel terminale:

```bash
git clone URL-DEL-TUO-FORK
```

Poi entra nella cartella:

```bash
cd webpage-git-github-exercise
```

---

# 5. Controllare Git

Esegui:

```bash
git status
```

Poi:

```bash
git remote -v
```

Dovresti vedere `origin` collegato al **tuo GitHub**.

```text
origin → il mio GitHub
```

---

# 6. Selezionare il branch della classe

Per la 4CI:

```bash
git switch Classe4CI
```

Per la 4DI:

```bash
git switch Classe4DI
```

Controlla:

```bash
git branch
```

Il branch attivo è quello indicato da `*`.

Esempio:

```text
* Classe4CI
  main
```

---

# 7. Modifica in locale il progetto`

Apri:

```text
index.html
```
Oppure aggiungi nuovi file.

---

# 8. Preparare la modifica

Esegui:

```bash
git add index.html
```
oppure se hai più file:

```bash
git add .
```

Poi:

```bash
git status
```

La modifica dovrebbe risultare pronta per il commit.

---

# 9. Creare il commit (versionamento locale, stai usando Git)

Esegui:

```bash
git commit -m "Modifica index.html - Aggiunta intestazione tabella"
```
ATTENZIONE tutti vedranno la descrizione, deve essere **sintetica e significativa**, ricordati che non è un salvataggio, rappresenta una funzionalità.
Il commit salva la modifica nella cronologia **locale** di Git.

---

# 10. Pubblicare su GitHub

Esegui:

```bash
git push
```

Il percorso è:

```text
Mio PC
  │
  │ git push
  ▼
Mio GitHub
```

---

Certo. Per il punto 12 possiamo mettere **entrambe le modalità**, tenendole separate e semplici.

### 11. Crea la Pull Request

Dopo aver fatto `push`, puoi creare la Pull Request in due modi.

#### A. Da GitHub (GUI)

1. Vai sul tuo **Fork** in GitHub.
2. Apri **Pull requests**.
3. Clicca **New pull request**.
4. Imposta:

   * **base repository:** `webpage-git-github-exercise`
   * **base branch:** `Classe4CI` oppure `Classe4DI`
   * **compare branch:** la tua branch con le modifiche.
5. Clicca **Create pull request**.

#### B. Da Terminale (CLI)

Se hai installato GitHub CLI (`gh`):

```bash
gh pr create --base Classe4CI --head NOME-DELLA-TUA-BRANCH --title "Modifica pagina web" --body "Esercizio Git e GitHub"
```

Per la classe 4DI:

```bash
gh pr create --base Classe4DI --head NOME-DELLA-TUA-BRANCH --title "Modifica pagina web" --body "Esercizio Git e GitHub"
```

> **Nota:** il comando `gh pr create` crea la Pull Request su GitHub.
> Con il solo comando `git` non esiste un comando `git pull-request`.

---

# 12. Se il Professore chiede una semplice modifica

Non creare necessariamente una nuova Pull Request.

Modifica nuovamente il file:

```bash
git add index.html
git commit -m "Corregge index.html"
git push
```

Il nuovo commit verrà aggiunto alla Pull Request già aperta.

---

# 13. I quattro comandi fondamentali

Durante il lavoro utilizzerai soprattutto:

```bash
git status
```

Controlla la situazione.

```bash
git add .
```

Prepara le modifiche.

```bash
git commit -m "Descrizione"
```

Salva una versione nella storia Git (locale).

```bash
git push
```

Invia il commit al tuo GitHub (remoto).

La sequenza fondamentale è:

```text
MODIFICA
   ↓
git status
   ↓
git add .
   ↓
git commit
   ↓
git push
   ↓
Pull Request
```

---

# 14. Se qualcosa non funziona

Prima di eseguire altri comandi, controlla sempre:

### Su quale branch sono?

```bash
git branch
```

### Cosa è cambiato?

```bash
git status
```

### A quale GitHub sono collegato?

```bash
git remote -v
```

Questi sono i **quattro controlli fondamentali**.

---

# 16. Problemi comuni

### `git push` dice `Everything up-to-date`

Controlla:

```bash
git status
```

Potresti avere già pubblicato il commit oppure potresti essere sul branch sbagliato.

---

### Ho modificato qualcosa per errore

Prima controlla:

```bash
git diff
```

Se la modifica non è stata ancora committata e vuoi eliminarla:

```bash
git restore index.html
```

> ⚠️ Questo elimina le modifiche locali non ancora committate.

---

# 17. La cosa più importante da ricordare

```text
origin   = il mio GitHub
upstream = GitHub del Professore
```

e:

```text
main       = branch principale
Classe4CI  = branch della 4CI
Classe4DI  = branch della 4DI
```

Quindi:

```text
                GITHUB DEL PROFE
                       │
              ┌────────┴────────┐
              │                 │
          Classe4CI          Classe4DI
              │                 │
             Fork              Fork
              │                 │
              ▼                 ▼
         MIO GITHUB        MIO GITHUB
           origin            origin
              │                 │
            clone             clone
              │                 │
            MIO PC            MIO PC
```

## Obiettivo dell'esercizio

Imparare questo percorso:

```text
Fork → Clone → Modifica → Add → Commit → Push → Pull Request
```

e capire la differenza tra:

```text
REMOTE
origin / upstream

BRANCH
main / Classe4CI / Classe4DI
```
