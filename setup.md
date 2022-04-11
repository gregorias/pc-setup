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

### Install & configure [Fish](#fish)

### Configure Neovim

## macOS step-by-step instructions

This is an aspirational section on setting up my macOS workspace from scratch.

### Adjust settings

1. Change mouse scroll direction (scrolling up should go up).
   1. Open Finder (Option + ⌘ + Space).
   1. Find Mouse and open its preferences.
   1. Change scroll direction.
1. Switch (CTRL/FN) and (option/⌘) keys on the built-in keyboard. I like it
   when the CTRL is the left-most button and the alt-equivalent is the one left
   of space.
   1. [Guide](https://howchoo.com/mac/mac-remap-fn-to-ctrl#open-keyboard-settings-in-system-preferences).
1. Install [Rectangle](https://rectangleapp.com/) ([StackOverflow source](https://rectangleapp.com/)) and setup your window management shortcuts.

### Install Homebrew

Follow [brew.sh](https://brew.sh/) for instructions.

Homebrew is essential for installing most packages. macOS doesn't support an
apt equivalent.

### Install my nerd font

[Source](https://github.com/ryanoasis/nerd-fonts#option-4-homebrew-fonts)

```fish
brew tap homebrew/cask-fonts
brew install --cask font-dejavu-sans-mono-nerd-font
```

### Install some binaries with brew

```fish
brew install fasd fzf git htop neovim ranger
```

### Install a [GitHub SSH key](#github-ssh-key)

### Install [Chezmoi](#chezmoi)

### Install & configure [Kitty](#kitty)

### Install & configure [Fish](#fish)

### Configure [Neovim](#neovim)

1. Use Chezmoi to fetch Neovim configuration.

   ```shell
   chezmoi apply .config/nvim
   ```

### Install [direnv](http://formulae.brew.sh/formula/direnv#default)

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
2. [Add the key to your GitHub profile](https://github.com/settings/keys).

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
