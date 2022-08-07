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

### Install & Configure Firefox

1. Install [Firefox](https://www.mozilla.org/de/firefox/download/thanks/).
2. Login to Firefox.
3. Login to Firefox extensions.

### Adjust settings

1. Switch ⌃, fn, ⌥, ⌘ keys on the built-in keyboard.
   1. [Guide](https://howchoo.com/mac/mac-remap-fn-to-ctrl#open-keyboard-settings-in-system-preferences).
   2. On MacBook Pro M1 I have the following setup: ⌃, ⌘, fn, ⌥. Ctrl is the
      leftmost button. Alt-equivalent is the rightmost. fn is at the most
      awkward spot. Capslock is set to escape.
1. Adjust Keyboard settings.
   1. Open Keyboard settings.
   2. Change 🌐 to do show emojis and symbols.
   3. Select use F keys as standard keys.
1. [Show macOS app switcher across all monitors](https://gist.github.com/jthodge/c4ba15a78fb29671dfa072fe279355f0).

   ```shell
   defaults write com.apple.Dock appswitcher-all-displays -bool true
   killall Dock
   ```

### Install Homebrew

Follow [brew.sh](https://brew.sh/) for instructions.

Homebrew is essential for installing most packages. macOS doesn't support an
apt equivalent.

### Configure mouse scroll direction

Change mouse scroll direction on the mouse. Scrolling up should go up.

1. Install [Unnatural](https://github.com/ther0n/UnnaturalScrollWheels).

   ```shell
   brew install --cask unnaturalscrollwheels
   ```

2. [Set the app to run at
   login](https://github.com/ther0n/UnnaturalScrollWheels/blob/master/RunAtLogin.md).

### Install my nerd font

[Source](https://github.com/ryanoasis/nerd-fonts#option-4-homebrew-fonts)

```fish
brew tap homebrew/cask-fonts
brew install --cask font-dejavu-sans-mono-nerd-font
```

### Install some binaries with brew

```fish
brew install \
  bat \
  fasd \
  fd \
  fzf \
  git \
  htop \
  neovim \
  node \
  pyenv \
  ranger \
  rg
```

#### Install [Universal Ctags](https://github.com/universal-ctags/ctags#the-latest-build-and-package)

This package is useful for my Neovim Tagbar plugin.

```shell
brew install --HEAD universal-ctags/universal-ctags/universal-ctags
```

### (macOS) Install a [GitHub SSH key](#github-ssh-key)

### (macOS) Install [Chezmoi](#chezmoi)

### (macOS) Install & configure [Fish](#fish)

### (macOS) Install & configure [Kitty](#kitty)

### Install Python Dev Tools

```shell
pip3 install \
  pipenv
  pipx
  pls
  virtualenv
```

### Configure [Neovim](#neovim)

1. Install neovim python package.

   ```shell
   pip3 install neovim
   ```

1. Use Chezmoi to fetch Neovim configuration.

   ```shell
   chezmoi apply .config/nvim
   ```

1. Run neovim once for Packer to bootstrap itself.

### Install [direnv](http://formulae.brew.sh/formula/direnv#default)

### Install & Configure Rectangle Pro

1. Install [Rectangle][rectangle] for convenient window management.
   1. Download and install the app.
   2. Provide my pro license key (the pro version can sync my config in iCloud).
1. Fetch the most recent config.

   ```shell
   chezmoi apply $HOME/.config/RectangleProConfig.json
   ```

1. Import `$HOME/.config/RectangleProConfig.json` into RectanglePro

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

[rectangle]: https://rectangleapp.com/

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
* For `XCode`, see [freecodecamp.org](https://www.freecodecamp.org/news/how-to-download-and-install-xcode/).
