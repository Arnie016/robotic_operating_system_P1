# robotic_operating_system_P1

EE4308 Project 1 report repository with automatic sync to an existing Overleaf project.

## Repository structure

- `overleaf/main.tex` - main LaTeX report file.
- `overleaf/*.png` - figures used by the report (kept with exact original filenames).
- `.github/workflows/overleaf-sync.yml` - GitHub Actions workflow that mirrors `overleaf/` to Overleaf.
- `OVERLEAF_AUTOMATION_SETUP.md` - one-time setup guide for secrets and activation.

## How to edit report

1. Edit `overleaf/main.tex`.
2. Add or replace figures inside `overleaf/`.
3. Commit and push to `main`.

The action runs automatically on pushes that touch `overleaf/**` and syncs to Overleaf.

## Workflow status

Check in GitHub:
- `Actions` tab -> `Sync Overleaf`

If sync fails, inspect the failing step logs in the workflow run.

## Notes

- Overleaf sync uses `OVERLEAF_GIT_TOKEN` repository secret.
- Overleaf project id is fixed in workflow as: `6998135d3a689ef9ef3dd6c7`.
