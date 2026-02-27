# Overleaf <-> GitHub automation setup (existing Overleaf project)

This workflow pushes files from `overleaf/` in your GitHub repo into your existing Overleaf project.

## 1) Overleaf screens (exact click path)

1. Open your project:
   - `https://www.overleaf.com/project/6998135d3a689ef9ef3dd6c7`
2. In the project editor, open **Integrations** (left sidebar).
3. Click **Git**.
4. Copy the Git project URL (project id = `6998135d3a689ef9ef3dd6c7`).
5. If prompted for auth setup, click **Generate token**.
6. If no token prompt appears:
   - top-right avatar -> **Account Settings** -> **Git** (or **Git integration/authentication tokens**) -> create/copy token.

Required values:
- `OVERLEAF_PROJECT_ID = 6998135d3a689ef9ef3dd6c7`
- `OVERLEAF_GIT_TOKEN = <token from Overleaf>`

## 2) GitHub screens (exact click path)

1. Open your GitHub repo.
2. Go to **Settings** -> **Secrets and variables** -> **Actions**.
3. Click **New repository secret** and add:
   - Name: `OVERLEAF_PROJECT_ID`
   - Secret: `6998135d3a689ef9ef3dd6c7`
4. Click **New repository secret** again and add:
   - Name: `OVERLEAF_GIT_TOKEN`
   - Secret: your Overleaf git token.

## 3) Repo structure required

Put your report files in this repo folder:

- `overleaf/main.tex`
- `overleaf/Densification block within planner.png`
- `overleaf/Savitzky-Golay smoother implementation.png`
- `overleaf/m=30 p=20, (b) m=20, p=5.png`
- `overleaf/part 1 m=30 p=20, (b) m=20, p=5.png`
- `overleaf/Screenshot 2026-02-27 at 7.56.19 PM.png`

You can include additional `.bib`, `.sty`, figures, etc. in `overleaf/`.

## 4) Install workflow in repo

Copy this file into your repo at:
- `.github/workflows/overleaf-sync.yml`

Workflow behavior:
- Triggers on push to `main` when `overleaf/**` changes.
- Can also be run manually from **Actions** -> **Sync Overleaf** -> **Run workflow**.
- Pushes to Overleaf `master` branch (Overleaf Git bridge convention).

## 5) First test

1. Commit workflow + `overleaf/` files.
2. Push to `main`.
3. GitHub: **Actions** tab -> check `Sync Overleaf` job logs.
4. Overleaf: refresh editor and compile.
