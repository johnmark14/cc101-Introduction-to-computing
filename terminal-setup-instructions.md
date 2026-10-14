# Terminal Setup Instructions

Set up my macOS terminal with Oh My Zsh, Powerlevel10k theme, and plugins. Follow these steps exactly.

## 1. Install Homebrew (if not installed)

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, follow the on-screen instructions to add Homebrew to PATH.

## 2. Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 3. Install Powerlevel10k Theme

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

## 4. Install Custom Plugins

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

## 5. Install the MesloLGS NF Font

Download and install all four font files:

- MesloLGS NF Regular.ttf
- MesloLGS NF Bold.ttf
- MesloLGS NF Italic.ttf
- MesloLGS NF Bold Italic.ttf

Download from: https://github.com/romkatv/powerlevel10k#fonts

After installing, set your terminal emulator's font to **MesloLGS NF**.

## 6. Configure .zshrc

Open `~/.zshrc` and make these changes:

- Set the theme:
  ```
  ZSH_THEME="powerlevel10k/powerlevel10k"
  ```

- Set the plugins:
  ```
  plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
  ```

- Add the Powerlevel10k instant prompt block at the **very top** of the file:
  ```bash
  if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
    source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
  fi
  ```

- Add this line at the **very bottom** of the file:
  ```bash
  [[ ! -f ~/.p10k.zsh ]] || source ~/.p10k.zsh
  ```

## 7. Copy the Powerlevel10k Theme Config

Copy the file `~/.p10k.zsh` from my other machine to `~/.p10k.zsh` on this machine. This contains my exact prompt style configuration:

- Style: **Rainbow** with powerline
- Icons: Nerd Font v3, small icons
- Separators: Angled, slanted heads and tails
- Layout: 2 lines, dotted connector, full frame, light ornaments, sparse
- Time format: 24h
- Left prompt: OS icon, current directory, git status
- Right prompt: exit code, command execution time, and context info

If you don't have the `.p10k.zsh` file, you can reconfigure interactively by running:
```bash
p10k configure
```
And selecting: nerdfont-v3 + powerline > small icons > rainbow > unicode > 24h time > angled separators > slanted heads > slanted tails > 2 lines > dotted > full frame > light-ornaments > sparse > many icons > fluent > instant_prompt=verbose.

## 8. Apply Changes

```bash
source ~/.zshrc
```

## Notes

- NVM is also used on the original machine. Install it with `brew install nvm` if needed.
- Python is aliased: `alias python=python3` and `alias pip=pip3`.
