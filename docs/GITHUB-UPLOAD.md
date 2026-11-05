# Putting this on GitHub - manual steps

Written for someone who has never pushed code. Two ways: the browser (easiest, no software) and GitHub Desktop (better for later updates).

Before you start, open the release folder and confirm you can see:

```
README.md   LICENSE   SETUP.md   .gitignore   .env.example
config.example.json   server.py   requirements.txt
ai/   docs/   web/
```

You should **not** see `config.json`, a `.env` file, a `.venv` folder, or any `.bak` file. If you do, stop - tell me.

---

## Way 1 - the browser (about five minutes)

### 1. Create the repository

1. Go to **github.com** and sign in.
2. Click the **+** in the top right, then **New repository**.
3. **Repository name:** `remote-bridge`
4. **Description:** `Turn any phone or tablet on your Wi-Fi into a mouse, keyboard, macro pad and screen viewer for a Windows PC. No app, no account, no cloud.`
5. Choose **Public**.
6. Leave **Add a README file** unticked - you already have one.
7. **Licence:** leave it as *None*. Your `LICENSE` file already says MIT; choosing one here as well creates a duplicate.
8. Click **Create repository**.

### 2. Upload the files

1. On the empty repository page, click **uploading an existing file**.
2. Open the release folder in File Explorer.
3. Select everything inside it - `Ctrl+A` - and drag it into the browser drop area.
4. Wait for the list to show every file. Folders (`web`, `ai`, `docs`) upload with their contents.
5. In the box at the bottom write: `Initial release - working prototype, MIT`
6. Click **Commit changes**.

### 3. Tidy the page

1. Click the gear next to **About** on the right.
2. Description: paste the same sentence as above.
3. Topics: `remote-control`, `touchpad`, `windows`, `local-network`, `python`, `pwa`, `gesture-recognition`, `productivity`
4. Save.

### 4. Check the result

Open the repository in a private window - that is what a judge sees. Make sure:
- The README renders with its tables.
- The green **Code** button offers **Download ZIP**.
- `LICENSE` says MIT when GitHub reads it.

---

## Way 2 - GitHub Desktop (better if you will update it)

1. Install **GitHub Desktop** from desktop.github.com and sign in.
2. **File → Add local repository** → choose your release folder.
3. It will say the folder is not a repository - click **create a repository**.
4. Name it `remote-bridge`, keep the path, click **Create repository**.
5. Write the summary `Initial release - working prototype, MIT` and click **Commit to main**.
6. Click **Publish repository**. Untick **Keep this code private**.

Later, when I give you a revised folder, copy the changed files over, and Desktop shows the differences; commit and push.

---

## After it is public

- **Send the link to the form** - the repository URL, plus `docs/SUBMISSION.md`.
- **Keep the video on your own channel or Drive**, and link it from the README's first lines. Judges rarely watch a video that is buried.
- **Do not add your key anywhere.** If you later turn on the model feature, the key goes in a local `.env` file only, which the `.gitignore` already refuses to publish.

---

## If something looks wrong

| What you see | What it means |
|---|---|
| `.env.example` is missing from the repo | GitHub hides files starting with a dot in some folder views. It is there - check the file list. |
| A red banner about secrets | GitHub detected a token. Tell me immediately - we rotate it. |
| README shows raw text | The file needs a `.md` ending. Check the name is exactly `README.md`. |
| The zip download is empty | Folders were dragged instead of their contents. Delete the repo and redo step 2. |
