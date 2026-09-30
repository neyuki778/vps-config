# Instructions for agents using this repository

This repository is a source of terminal setup to synchronize across VPS hosts.
When asked to install it on a target VPS:

1. Read this file, `README.md`, and both files under `manifest/` first.
2. Identify the target OS, architecture, login user, and existing shell setup.
   This snapshot was taken on Ubuntu 24.04; adapt package names for other
   systems rather than running Ubuntu commands blindly.
3. Install the CLI and font packages from the manifest where available. Install
   Starship using the official instructions for the target OS and architecture.
4. Install Oh My Zsh and its plugins from the upstream URLs and exact commits in
   `manifest/components.txt`. Keep existing plugin repositories if they are
   already at those commits.
5. Before replacing `~/.zshrc` or `~/.config/starship.toml`, make timestamped
   backups of existing files. Then install `dotfiles/zshrc` and
   `dotfiles/starship.toml` for the target login user, preserving ownership and
   permissions.
6. Do not replace the target `.bashrc` or `.profile` by default. The tracked
   copies are Ubuntu source-machine defaults and are included for reference.
7. Do not look for or copy shell history, credentials, SSH keys, or unrelated
   application configuration. They are outside this repository's scope.
8. Do not invent terminal emulator settings: none were available on the source
   SSH host. The theme files in `themes/` define portable target settings based
   on the colors actually present in the source Starship prompt. Apply the
   matching adapter only if the target machine runs that terminal emulator;
   the terminal app's colors, window appearance, and selected font on the
   original client cannot be recovered from this VPS.
9. Report what was installed, what was backed up, and any target-specific
   differences. Only change the login shell to zsh when that is part of the
   user's requested setup and the target account can be identified safely.

The zsh configuration uses `$HOME` and is not tied to the source username.
Optional Bun completion is loaded only when `$BUN_INSTALL/_bun` exists.
The prompt and eza icon glyphs require a Nerd Font in the terminal emulator on
the client side. No Nerd Font was installed on the source VPS.
