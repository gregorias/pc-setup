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

### 3. Install & Configure 1Password

1. [Download](https://1password.com/downloads/mac/), install, and login to 1Password.
2. Install (`brew install --cask 1password-cli`) and
   [configure it](https://developer.1password.com/docs/cli/get-started/#step-2-turn-on-the-1password-desktop-app-integration).

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
