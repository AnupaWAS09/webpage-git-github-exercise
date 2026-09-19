# Progetto Webpage condiviso

**Esercizio didattico su Git e GitHub:** fork, clone, modifica di una pagina HTML, commit, push e Pull Request.

---

# Costanti del progetto

| Elemento                 | Cos'è                                                            | Nel nostro progetto                                                                |
| ------------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Repository o REPO**    | Il progetto Git completo ospitato su GitHub                      | `webpage-git-github-exercise`                                                      |
| **Repository del professore** | Repository originale                                             | `ProfNardi/webpage-git-github-exercise`                                            |
| **Fork**                 | Copia di una repository GitHub → GitHub                          | Copia della REPO del professore → REPO dello studente                                   |
| **Remote**               | Un nome/alias che Git usa per identificare una repository remota | `origin`, `upstream`                                                               |
| **`origin`**             | Remote che normalmente punta al fork dello studente              | GitHub dello studente                                                              |
| **`upstream`**           | Remote che punta alla repository originale                       | GitHub del professore                                                                   |
| **Branch**               | Un ramo della cronologia Git dentro una repository               | `main`, `Classe4CI`, `Classe4DI`                                                   |
| **`main`**               | Branch principale                                                | Branch principale del progetto                                                     |
| **`Classe4CI`**          | Branch dedicato alla 4CI                                         | Branch della 4CI                                                                   |
| **`Classe4DI`**          | Branch dedicato alla 4DI                                         | Branch della 4DI                                                                   |
| **Clone**                | Download da GitHub → Git                                         | Lo studente clona il proprio fork in Git                                           |
| **Commit**               | Salva una versione nella storia di Git                           | `git commit`                                                                       |
| **Push**                 | Upload da Git → GitHub                                           | Lo studente invia i propri commit al proprio GitHub                                |
| **Pull Request**         | Proposta di modifica da una repository/branch verso un'altra     | Lo studente propone le modifiche dal proprio fork al branch del professore |

---

# Flusso di lavoro

```text
GitHub del Professore
       │
      Fork              GitHub → GitHub
       ▼
   Mio GitHub
       │
     clone              GitHub → Git
       ▼
      Git
       │
    modifica
       │
   add → commit         tutto in Git
       │
      push              Git → GitHub
       ▼
   Mio GitHub
       │
 Pull Request           GitHub → GitHub
       ▼
GitHub del Professore
```

---

# 1. Creare il Fork

Apri il repository del Professore su GitHub.

Clicca:

**Fork**

Avrai così una copia del progetto nel tuo account GitHub.

---

# 2. Scegliere il branch della classe

Il Professore ha creato due branch:

```text
Classe4CI
Classe4DI
```

Usa il branch della tua classe.

---

# 3. Clonare il proprio repository

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

# 4. Controllare Git

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

# 5. Selezionare il branch della classe

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

# 6. Sviluppo software (Developement)

Modifica:

```text
index.html
```
Oppure aggiungi nuovi file.

---

# 7. Preparare la commit

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

# 8. Creare la commit (versioning)

Esegui:

```bash
git commit -m "Modifica index.html - Aggiunta intestazione tabella"
```
ATTENZIONE tutti vedranno la descrizione, deve essere **sintetica e significativa**, ricordati che non è un salvataggio, rappresenta una funzionalità.
Il commit salva la modifica nella cronologia **locale** di Git.

---

# 9. Pubblicare su GitHub

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

### 10. Crea la Pull Request

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

# Se il Professore chiede una semplice modifica

Non creare necessariamente una nuova Pull Request.

Modifica nuovamente il file:

```bash
git add index.html
git commit -m "Corregge index.html"
git push
```

Il nuovo commit verrà aggiunto alla Pull Request già aperta.

---

# I quattro comandi fondamentali

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

# Se qualcosa non funziona

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

# Problemi comuni

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

## Obiettivo dell'esercizio

Impara questo percorso:

```text
Fork → Clone → (Modifica → Add → Commit) → Push → Pull Request
```

e capire la differenza tra:

```text
REMOTE
origin / upstream

BRANCH
main / Classe4CI / Classe4DI
```
