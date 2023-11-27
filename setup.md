# Workspace Setup

This page documents how to set up my workspace.

## Linux step-by-step instructions

This is an aspirational section on how to set up my Manjaro workspace from
scratch.

### Install some basic binaries

```fish
sudo pamac install fasd fzf git htop neovim ranger
```

### Install a [GitHub SSH key](#github-ssh-key)

### Install [Chezmoi](#chezmoi)

### Install & configure [Kitty](#kitty)

### Configure Neovim

## macOS step-by-step instructions

This is an aspirational section on setting up my macOS workspace from scratch.

### 1. Adjust system settings

1. Switch ⌃, fn, ⌥, ⌘ keys on the built-in keyboard.
   1. [Guide](https://howchoo.com/mac/mac-remap-fn-to-ctrl#open-keyboard-settings-in-system-preferences).
   On MacBook Pro M1 I have the following setup: ⌃, ⌘, fn, ⌥. I like Ctrl to be
   the leftmost button and the Alt-equivalent key to be the rightmost button.
   fn is at the most awkward spot, as is tradition. Set Capslock to function as
   an escape key.
1. Adjust other keyboard settings.
   1. Change 🌐 to show emojis and symbols. It's a useful keyboard extension.
   2. Select "use F keys as standard keys".
1. Adjust keyboard shortcuts in `Settings > Keyboard`.
   1. In `Mission Control > Mission Control`, use `⌃⌘H` and `⌃⌘L` for moving
      spaces.
   1. In `Input Sources > Select the previous input source`, use `⌃⌘I`.
1. [Show macOS app switcher across all monitors.](https://gist.github.com/jthodge/c4ba15a78fb29671dfa072fe279355f0)

   ```shell
   defaults write com.apple.Dock appswitcher-all-displays -bool true
   killall Dock
   ```

1. [Remove the Spotlight icon from the menu
   bar.](https://discussions.apple.com/thread/250065431) You may do it in
   `Settings > Control Center`.
   Its shortcut is well-known to me (⌘ + SPACE). I don't need this crutch.
1. In `System Preferences > Control Center`,
   1. Set "Sound" to "Always". I like to have the icon available, so that I can easily change sinks.
   2. Set "Now Playing" to "Show when active".
1. Delete Quick Notes from turning on when I hover in the bottom right corner
   of a screen (I don't use the app):
   `System Settings > Desktop & Dock > Hot Corners...`.
1. Set "Automatically hide and show the Dock" in `System Settings > Desktop & Dock`.
1. Give Full Disk Access to terminals. This will be necessary for them to enact
   changes.

### 2. Install Homebrew

Follow [brew.sh](https://brew.sh/) for instructions.

Homebrew is essential for installing most packages. macOS doesn't support an
apt equivalent.

### 3. Install & Configure 1Password

1. [Download](https://1password.com/downloads/mac/), install, and login to 1Password.
2. Install (`brew install --cask 1password-cli`) and
   [configure it](https://developer.1password.com/docs/cli/get-started/#step-2-turn-on-the-1password-desktop-app-integration).

### 4. Install & Configure Firefox

1. Install [Firefox](https://www.mozilla.org/de/firefox/download/thanks/).
2. Login to Firefox.
3. Login to Firefox extensions.

### 5. (macOS) Install a [GitHub SSH key](#github-ssh-key)

### 6. (macOS) Install [Chezmoi](#chezmoi)

1. Install Fish (`brew install fish`) as they are needed by
   scripts.

### 7. Install XCode

Follow instructions from
[freecodecamp.org](https://www.freecodecamp.org/news/how-to-download-and-install-xcode/).
Install from [App
Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12).

### 8. [Install and setup Google Drive for Desktop](https://www.google.com/drive/download/)

### 9. [Install Bartender 5](https://www.macbartender.com/)

### 10. Install [iTerm2](https://iterm2.com)

1. [Configure](obsidian://open?vault=STEM&file=Zettelkasten%2FiTerm2)

## Miscellaneous setup instructions

This section lists out installation sub-steps that are shared by all systems.

### GitHub SSH key

If the key has been restored and is present in `.ssh`, you don't need this step.

1. [Generate a key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

   ```bash
   ssh-keygen -t ed25519 -C "grzegorzmilka@gmail.com"
   ```

1. [Add the key to your GitHub profile](https://github.com/settings/keys).

### Chezmoi

This step requires [a GitHub SSH Key](#github-ssh-key).

1. Follow [install instructions](https://www.chezmoi.io/install/).
1. Initialize the repo with

    ```shell
    chezmoi init git@github.com:gregorias/dotfiles.git
    ```

1. Fork my chezmoi config, `.config/chezmoi/chezmoi.toml` from the initialized
   repo.

### Kitty

1. Install [kitty](https://sw.kovidgoyal.net/kitty/).
1. Install the selection plugin:

    ```fish
    cd $HOME/.config/kitty
    git clone https://github.com/yurikhan/kitty_grab.git
    ```

### Ranger

My Ranger uses devicons, so install
[alexanderjeurissen/ranger_devicons](https://github.com/alexanderjeurissen/ranger_devicons).

### Sendmail

It's useful to be able to use `sendmail` or `mail` to send mail from the
command line.

On macOS, [configure
Postfix](https://gist.github.com/kany/c44c077881047ead8faa).

### Anki

Install the following Anki add-ons:

1. 112228974 # Highlight Code
2. 1140138750 # Hyphenate Words
3. 1312865748 # Scale Images

### (macOS) Cron

#### Authorization

macOS has additional authorization system. You need to give cron full disk
access to use it.

1. Open System Preferences from the  Apple menu, then choose “Security & Privacy”.
2. Go to the “Privacy” tab, then select “Full Disk Access” from the side menu options
3. Add `/usr/sbin/cron` to the list of allowed apps.

[Source](https://osxdaily.com/2020/04/27/fix-cron-permissions-macos-full-disk-access/).

### Utilities

* For `pdftotext`, `brew install poppler`
  ([Source](https://superuser.com/questions/56272/is-the-pdftotext-command-line-tool-for-mac/613342#613342)).
* For `flock`, see [github/flock](https://github.com/discoteq/flock).
