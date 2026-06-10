# hhkb-karabiner-config

My [Karabiner-Elements](https://karabiner-elements.pqrs.org/) configuration for the HHKB keyboard, version-controlled so it syncs across Macs.

The repo **is** `~/.config/karabiner` — Karabiner reads `karabiner.json` from there directly.

## Set up on a new Mac

1. Back up any existing config, then clone into place:
   ```bash
   mv ~/.config/karabiner ~/.config/karabiner.bak 2>/dev/null
   git clone git@github.com:samtade/hhkb-karabiner-config.git ~/.config/karabiner
   ```

2. Quit and reopen **Karabiner-Elements** (menu bar icon → Quit, then relaunch). It reloads `karabiner.json` on launch.

## Sync changes

Karabiner rewrites `karabiner.json` whenever you change settings in the UI.

**Pull the latest** (on any machine, before editing):
```bash
git -C ~/.config/karabiner pull
```

**Push your changes** (after editing in the Karabiner UI):
```bash
git -C ~/.config/karabiner add -A
git -C ~/.config/karabiner commit -m "Update config"
git -C ~/.config/karabiner push
```

Tip: alias it in `~/.zshrc`:
```bash
alias kpush='git -C ~/.config/karabiner add -A && git -C ~/.config/karabiner commit -m "Update config" && git -C ~/.config/karabiner push'
alias kpull='git -C ~/.config/karabiner pull'
```

## Notes

- If both machines edit `karabiner.json`, you may hit a merge conflict — it's plain JSON, resolve by hand then `git push`.
- `automatic_backups/` (Karabiner's timestamped backups) and `.omc/` (tooling state) are git-ignored on purpose.
- This config contains keyboard remappings only — no credentials. Keep the repo private regardless.
