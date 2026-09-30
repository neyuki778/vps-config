# VPS terminal configuration

This repository records the terminal-related setup found on the source machine
(Ubuntu 24.04, captured 2026-09-30). It is intended as a portable reference for
another machine; it does not contain shell history, credentials, SSH files, or
application data.

Agents performing a target-host migration should follow `AGENTS.md` before
making changes.

## Included

- `dotfiles/zshrc`: zsh setup, Oh My Zsh plugin selection, prompt initialization,
  and CLI aliases.
- `dotfiles/starship.toml`: Starship prompt colors, segments, and symbols.
- `dotfiles/bashrc` and `dotfiles/profile`: source machine's Bash defaults.
- `manifest/ubuntu-24.04-packages.txt`: installed terminal and font packages.
- `manifest/components.txt`: tool versions and pinned Oh My Zsh repositories.

## Source machine notes

- Login shell: zsh.
- Oh My Zsh theme: Starship (`ZSH_THEME` is empty).
- Oh My Zsh plugins: `git`, `zsh-autosuggestions`, `fzf-tab`, and
  `zsh-syntax-highlighting`.
- `tmux` and `screen` are installed, but there was no `~/.tmux.conf` or
  `~/.screenrc` to migrate.
- No terminal emulator configuration was present on this SSH host. Window
  appearance, emulator colors, and the font selected in the terminal app are
  normally configured on the computer running that app. The installed system
  fonts are listed in the package manifest.
- Nerd Font was not detected among the installed fonts. Some prompt glyphs may
  therefore render differently on another machine unless its terminal font has
  the required symbols.

## Ubuntu migration outline

Install the packages listed in `manifest/ubuntu-24.04-packages.txt` with apt
(review availability first if the target Ubuntu release differs). Install
Starship using its official installation instructions. Clone Oh My Zsh and the
three plugin repositories at the commits recorded in
`manifest/components.txt`, then copy `dotfiles/zshrc` to `~/.zshrc` and
`dotfiles/starship.toml` to `~/.config/starship.toml`. Back up any existing
files before replacing them. The zsh configuration is portable and uses
`$HOME` paths.

The Bash files are source-machine defaults. Keep the target system's own
`.bashrc` and `.profile` unless you specifically want to replace them.
