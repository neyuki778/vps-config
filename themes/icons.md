# Prompt and terminal icons

## Captured from the source configuration

| Use | Glyph | Source |
| --- | --- | --- |
| Ubuntu OS segment | `` | `dotfiles/starship.toml` |
| Documents path substitution | `󰈙` | `dotfiles/starship.toml` |
| Directory and file listing icons | eza's built-in Nerd Font icon set | `dotfiles/zshrc` aliases `ls`, `ll`, `la`, and `lt` with `--icons` |

The Starship git and language modules currently have empty symbols. The source
configuration therefore shows their values without module icons.

## Font requirement

These glyphs are from Nerd Fonts. No Nerd Font was installed on the source VPS;
the shell package list only records the fonts detected there. Install a Nerd
Font on the computer that renders the terminal (the SSH client), then select
that same family in the terminal emulator. Installing a font only on a remote
VPS does not make it available to the local terminal window.

The repository does not bundle font binaries. A target agent should use the
user's already selected Nerd Font where available, or ask which font family to
install if none is configured.
