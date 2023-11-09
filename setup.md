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

### Install & configure [Fish](#fish)

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
1. [Show macOS app switcher across all monitors.](https://gist.github.com/jthodge/c4ba15a78fb29671dfa072fe279355f0)

   ```shell
   defaults write com.apple.Dock appswitcher-all-displays -bool true
   killall Dock
   ```

1. [Remove the Spotlight icon from the menu
   bar.](https://discussions.apple.com/thread/250065431) You may do it in
   `Settings > Control Center`.
   Its shortcut is well-known to me (⌘ + SPACE). I don't need this crutch.
1. Delete Quick Notes from turning on when I hover in the bottom right corner
   of a screen (I don't use the app):
   `System Settings > Desktop & Dock > Hot Corners...`.

### 2. Install & Configure 1Password

1. [Download](https://1password.com/downloads/mac/), install, and login to 1Password.

### 3. Install & Configure Firefox

1. Install [Firefox](https://www.mozilla.org/de/firefox/download/thanks/).
2. Login to Firefox.
3. Login to Firefox extensions.

### 4. Install Homebrew

Follow [brew.sh](https://brew.sh/) for instructions.

Homebrew is essential for installing most packages. macOS doesn't support an
apt equivalent.

### 5. (macOS) Install a [GitHub SSH key](#github-ssh-key)

### 6. (macOS) Install [Chezmoi](#chezmoi)

1. Install Fish and 1Password (`brew install fish op`) as they are needed by
   scripts.

### 7. Configure mouse scroll direction

Change mouse scroll direction on the mouse. Scrolling up should go up.

1. Install [Unnatural](https://github.com/ther0n/UnnaturalScrollWheels).

   ```shell
   brew install --cask unnaturalscrollwheels
   ```

1. Set the app to run at login. Open the app and enable the option.

### 7. Install some binaries with brew

```fish
brew install \
  direnv \
  exa \
  fasd \
  fzf \
  git-delta \
  go \
  htop \
  node \
  pyenv \
  ranger \
  terminal-notifier \
  \
  catimg \
  timg \
  \
  watch \
  fswatch
```

### 8. (macOS) Install & configure [Fish](#fish)

### 9. Install Python Dev Tools

```shell
pip3 install \
  pipenv
  pipx
  virtualenv
```

### 10. Configure [Neovim](#neovim)

1. Install the Neovim Python package.

   ```shell
   pip3 install neovim
   ```

1. Use Chezmoi to fetch Neovim configuration.

   ```shell
   chezmoi apply .config/nvim
   ```

1. Run Neovim once for Packer to bootstrap itself.

### 11. Install & configure [Fish](#fish)

### 12. Install & configure Amethyst

1. Install [Amethyst][amethyst] for convenient window management.

### 13. Install & configure [Key Combiner][keycombiner]

1. [Install Key Combiner for desktop](https://keycombiner.com/desktop/).
2. Set up ^+⌘+c as the shortcut.

### 14. Install XCode

Follow instructions from
[freecodecamp.org](https://www.freecodecamp.org/news/how-to-download-and-install-xcode/).
Install from [App
Store](https://apps.apple.com/us/app/xcode/id497799835?mt=12).

### 15. [Install and setup Google Drive for Desktop](https://www.google.com/drive/download/)

### 16. Set up [Homebrew  auto-updates](https://github.com/Homebrew/homebrew-autoupdate)

1. Install the auto-updating software:

    ```shell
    brew tap homebrew/autoupdate
    ```

2. Start the job:

    ```shell
    brew autoupdate start 604800 --upgrade
    ```

3. Enable terminal-notifier and brew-autoupdate notifications in system
   settings.

### 17. Install [Switch Theme](https://github.com/gregorias/switch-theme.command)

## Miscellaneous setup instructions

This section lists out installation sub-steps that are shared by all systems.

### Fish

1. Install [fish](https://fishshell.com/)
1. Install [fisher](https://github.com/jorgebucaran/fisher#installation)
1. Install [fishmarks](https://github.com/techwizrd/fishmarks)
1. Use Chezmoi to fetch fish configuration.

   ```fish
   chezmoi apply .config/fish
   ```

1. Run

   ```fish
   fisher update
   ```

1. (macOS) To fix `grep -P` not being available, apply [this PR](https://github.com/fishgretel/fasd/pull/23).

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

1. Use Chezmoi to fetch Kitty configuration.

   ```shell
   chezmoi apply .config/kitty
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

### macOS Sound

I like to have the sound menu in the menu bar. It enables me to quickly change
the sink if needed.

1. Open System Preferences > Sound
2. Select "Show Sound in menu bar (always)."

### Utilities

* For `pdftotext`, `brew install poppler`
  ([Source](https://superuser.com/questions/56272/is-the-pdftotext-command-line-tool-for-mac/613342#613342)).
* For `flock`, see [github/flock](https://github.com/discoteq/flock).

[amethyst]: https://ianyh.com/amethyst/
[keycombiner]: https://keycombiner.com/
