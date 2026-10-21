<div align="center">

# 🐉 DRAGON FORGE

### Build · Learn · Conquer — The Ghostty Terminal Command Centre

*A dark-fantasy, ember-lit developer terminal built on Ubuntu, Ghostty, Zsh, Powerlevel10k, and JetBrains Mono Nerd Font.*

<br />

[![Platform](https://img.shields.io/badge/Platform-Ubuntu%2024.04%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](#requirements)
[![Terminal](https://img.shields.io/badge/Terminal-Ghostty%201.2+-10b981?style=for-the-badge&logo=alacritty&logoColor=white)](#step-2-install-ghostty)
[![Shell](https://img.shields.io/badge/Shell-Zsh%205.9+-f1502f?style=for-the-badge&logo=gnu-bash&logoColor=white)](#step-3-install-zsh)
[![Framework](https://img.shields.io/badge/Framework-Oh%20My%20Zsh-blueviolet?style=for-the-badge&logo=zsh&logoColor=white)](#step-4-install-oh-my-zsh)
[![Prompt Theme](https://img.shields.io/badge/Theme-Powerlevel10k-38bdf8?style=for-the-badge&logo=powershell&logoColor=white)](#step-6-install-powerlevel10k)
[![Font](https://img.shields.io/badge/Font-JetBrains%20Mono%20Nerd-000000?style=for-the-badge&logo=jetbrains&logoColor=white)](#step-5-install-jetbrains-mono-nerd-font)
[![License](https://img.shields.io/badge/License-MIT-amber?style=for-the-badge)](#license)

<br />

[⚡ Quick Start](#quick-start) • [🏗️ Architecture](#system-architecture) • [🎨 Palette](#dragon-forge-palette) • [📖 Step-by-Step Guide](#step-by-step-installation) • [👻 Ghostty Config](#step-7-forge-the-ghostty-config) • [🔍 Verification](#verification-checklist) • [🛠️ Troubleshooting](#troubleshooting)

<br />

![Dragon Forge Terminal Command Centre](./Dragon%20Forge%20Terminal%20Command%20Centre.png)

<br />

> *"Small steps build great legends."*

</div>

---

<a id="system-architecture"></a>
## 🏗️ System Architecture

Dragon Forge turns a single Ghostty window into a five-pane command centre: a map of your realm, a system sigil, git status, a project scout, and your live config.

| Component | Layer | Purpose & Highlights |
| :--- | :--- | :--- |
| **[Ghostty](https://ghostty.org)** | Terminal Emulator | GPU-accelerated, native splits, background images, and a clean text config. |
| **[Zsh](https://www.zsh.org)** | Shell Engine | Powerful completion, globbing, and the base for the whole stack. |
| **[Oh My Zsh](https://ohmyz.sh)** | Framework | Plugin & theme manager for Zsh. |
| **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)** | Prompt Engine | Instant prompt with the dragon glyph, path, and git branch. |
| **[JetBrains Mono Nerd Font](https://www.nerdfonts.com)** | Typography | Ligature-friendly monospace with thousands of developer icons. |
| **[eza](https://eza.rocks)** | File Explorer | The colourful, icon-rich `tree` view of the realm. |
| **[Neofetch](https://github.com/dylanaraps/neofetch)** | System Sigil | The green ASCII dragon and system info panel. |
| **[Papirus-Dark](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)** | Desktop Icons | Dark icon theme reported in the system panel. |
| **Realm Navigation** | Productivity | `castle`, `forge`, `quests`, `dragon`, `scrolls`, `treasures` jump commands. |

---

<a id="requirements"></a>
## 📋 Requirements

- 🐧 **Operating System**: Ubuntu 24.04 LTS (or any recent Debian/Ubuntu derivative)
- 🖥️ **Display**: GNOME on Wayland or X11 with OpenGL 3.3+ support
- 🔑 **Privileges**: A user account with `sudo` permissions
- 🌐 **Network**: Stable internet connection for packages, fonts, and Git repositories

> [!NOTE]
> Run each command in order and check the verification output before moving to the next step. Background images in Ghostty require **Ghostty 1.2.0 or later**.

---

<a id="quick-start"></a>
## ⚡ Quick Start

For seasoned adventurers, here is the whole forge in one pass:

```bash
# 1. Core packages
sudo apt update
sudo apt install -y zsh git curl unzip fontconfig neofetch eza papirus-icon-theme

# 2. Ghostty
sudo snap install ghostty --classic

# 3. Make Zsh the default shell, back up, and install Oh My Zsh
chsh -s "$(which zsh)"
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 4. JetBrains Mono Nerd Font
mkdir -p ~/.local/share/fonts/JetBrainsMonoNerd
curl -fLo /tmp/JetBrainsMono.zip \
  https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip -o /tmp/JetBrainsMono.zip -d ~/.local/share/fonts/JetBrainsMonoNerd
fc-cache -fv

# 5. Powerlevel10k + community plugins
ZSH_CUSTOM="${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "$ZSH_CUSTOM/themes/powerlevel10k"
git clone https://github.com/zsh-users/zsh-autosuggestions "$ZSH_CUSTOM/plugins/zsh-autosuggestions"
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "$ZSH_CUSTOM/plugins/zsh-syntax-highlighting"

# 6. Scaffold the realm
mkdir -p ~/dragon-forge/{dragon/{config,themes,scripts},quests/{beginner,intermediate,boss-fights},forge/{projects,builds,experiments},scrolls/{notes,cheatsheets},treasures/{snippets,archives}}
```

Then drop in the [Ghostty config](#step-7-forge-the-ghostty-config), the [Dragon Forge theme](#step-8-create-the-dragon-forge-theme), and the [`.zshrc`](#step-9-forge-the-zshrc), and log out / back in so the new default shell takes effect.

---

<a id="dragon-forge-palette"></a>
## 🎨 Dragon Forge Palette

Colours sampled from the command centre — midnight steel, jade dragon-fire, and castle embers:

| Swatch | Role | Hex |
| :---: | :--- | :--- |
| ⬛ | Background · Midnight Steel | `#0b1218` |
| ⬜ | Foreground · Moonlit Parchment | `#c9d1d9` |
| 🟥 | Red · Blood Quest | `#d04a4a` |
| 🟩 | Green · Jade Dragon | `#4fb89a` |
| 🟨 | Yellow · Gold Hoard | `#f2c66d` |
| 🟦 | Blue · Frost Path | `#6ea8e0` |
| 🟪 | Magenta · Arcane Scroll | `#8b7cf0` |
| 🩵 | Cyan · Spirit Flame | `#56c2c9` |
| 🟧 | Cursor · Forge Ember | `#e08a3c` |
| 🌫️ | Selection · Mist | `#1f3a44` |

---

<a id="step-by-step-installation"></a>
## 📖 Step-by-Step Installation

<a id="step-1-install-core-packages"></a>
### Step 1 · Install Core Packages

> Official Documentation: [Ubuntu Packages](https://packages.ubuntu.com) · [eza](https://eza.rocks) · [Neofetch](https://github.com/dylanaraps/neofetch)

```bash
sudo apt update
sudo apt install -y zsh git curl unzip fontconfig neofetch eza papirus-icon-theme
```

Apply the **Papirus-Dark** icon theme (shown in the neofetch panel):

```bash
gsettings set org.gnome.desktop.interface icon-theme 'Papirus-Dark'
```

#### Verify

```bash
git --version && eza --version | head -n 1 && neofetch --version
```

---

<a id="step-2-install-ghostty"></a>
### Step 2 · Install Ghostty

> Official Documentation: [ghostty.org](https://ghostty.org) · [Linux Install](https://ghostty.org/docs/install/binary) · [Config Reference](https://ghostty.org/docs/config/reference)

#### Option A: Snap *(Recommended — always current)*

```bash
sudo snap install ghostty --classic
```

#### Option B: Community `.deb` Package

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/mkasberg/ghostty-ubuntu/HEAD/install.sh)"
```

#### Verify

```bash
ghostty +version
```

```text
Ghostty 1.2.x
```

> [!TIP]
> Set Ghostty as your default terminal so `Ctrl + Alt + T` opens the forge:
> ```bash
> sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator "$(which ghostty)" 50
> sudo update-alternatives --config x-terminal-emulator
> ```

---

<a id="step-3-install-zsh"></a>
### Step 3 · Install Zsh as the Default Shell

```bash
chsh -s "$(which zsh)"
```

Log out and back in, then confirm:

```bash
echo $SHELL && zsh --version
```

```text
/usr/bin/zsh
zsh 5.9 (x86_64-ubuntu-linux-gnu)
```

---

<a id="step-4-install-oh-my-zsh"></a>
### Step 4 · Install Oh My Zsh

> Official Documentation: [ohmyz.sh](https://ohmyz.sh) · [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh)

```bash
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null || true
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### Verify

```bash
ls ~/.oh-my-zsh
```

You should see `plugins`, `themes`, and `custom`.

---

<a id="step-5-install-jetbrains-mono-nerd-font"></a>
### Step 5 · Install JetBrains Mono Nerd Font

> Official Documentation: [nerdfonts.com](https://www.nerdfonts.com) · [Font Downloads](https://www.nerdfonts.com/font-downloads)

```bash
mkdir -p ~/.local/share/fonts/JetBrainsMonoNerd
curl -fLo /tmp/JetBrainsMono.zip \
  https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
unzip -o /tmp/JetBrainsMono.zip -d ~/.local/share/fonts/JetBrainsMonoNerd
fc-cache -fv
```

#### Verify

```bash
fc-list | grep -i "JetBrainsMono Nerd Font" | head -n 3
ghostty +list-fonts | grep -i jetbrains
```

---

<a id="step-6-install-powerlevel10k"></a>
### Step 6 · Install Powerlevel10k & Plugins

> Official Documentation: [romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k) · [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) · [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting)

```bash
ZSH_CUSTOM="${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}"

git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  "$ZSH_CUSTOM/themes/powerlevel10k"

git clone https://github.com/zsh-users/zsh-autosuggestions \
  "$ZSH_CUSTOM/plugins/zsh-autosuggestions"

git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  "$ZSH_CUSTOM/plugins/zsh-syntax-highlighting"
```

Run the wizard once (choose **Lean** style, **Unicode**, **2 lines**, **Sparse**) — Dragon Forge overrides the colours in [Step 9](#step-9-forge-the-zshrc):

```bash
p10k configure
```

---

<a id="step-7-forge-the-ghostty-config"></a>
### Step 7 · 👻 Forge the Ghostty Config

> Official Documentation: [Config Reference](https://ghostty.org/docs/config/reference) · [Keybind Reference](https://ghostty.org/docs/config/keybind/reference)

#### 1. Create the Config Folders & Add the Background Art

```bash
mkdir -p ~/.config/ghostty/{themes,assets}
```

Save your dragon-castle wallpaper as `~/.config/ghostty/assets/dragon-forge.png`. *(Any dark, high-resolution fantasy landscape works — keep it dark so text stays readable.)*

#### 2. Write the Config

Ghostty on Linux reads `~/.config/ghostty/config` *(newer releases also accept `config.ghostty`)*. Open it from Ghostty with `Ctrl + ,` or:

```bash
nano ~/.config/ghostty/config
```

Paste the complete Dragon Forge configuration:

```ini
# ╔══════════════════════════════════════════════════════════╗
# ║            🐉  DRAGON FORGE — Ghostty Config              ║
# ║               Build  /  Learn  /  Conquer                 ║
# ╚══════════════════════════════════════════════════════════╝

# ── Theme ────────────────────────────────────────────────────
theme = dragon-forge

# ── Typography ───────────────────────────────────────────────
font-family = "JetBrainsMono Nerd Font"
font-size = 12
font-thicken = true
adjust-cell-height = 8%
bold-is-bright = false

# ── Window ───────────────────────────────────────────────────
title = "Dragon Forge"
window-padding-x = 16
window-padding-y = 12
window-padding-balance = true
window-decoration = auto
window-theme = ghostty
window-width = 160
window-height = 48

# ── Background: castle & dragon art ──────────────────────────
background-opacity = 0.94
background-image = ~/.config/ghostty/assets/dragon-forge.png
background-image-opacity = 0.18
background-image-fit = cover
background-image-position = center

# ── Splits: the five-pane command centre ─────────────────────
unfocused-split-opacity = 0.82
unfocused-split-fill = #0b1218
split-divider-color = #1e2c36

# ── Cursor: forge ember ──────────────────────────────────────
cursor-style = block
cursor-style-blink = true
cursor-color = #e08a3c

# ── Shell ────────────────────────────────────────────────────
shell-integration = zsh
shell-integration-features = cursor,sudo,title
working-directory = ~/dragon-forge
window-inherit-working-directory = true

# ── Comfort ──────────────────────────────────────────────────
copy-on-select = clipboard
mouse-hide-while-typing = true
confirm-close-surface = false
scrollback-limit = 20000000

# ── Keybinds: forge the splits ───────────────────────────────
keybind = ctrl+shift+d=new_split:right
keybind = ctrl+shift+s=new_split:down
keybind = ctrl+alt+h=goto_split:left
keybind = ctrl+alt+j=goto_split:down
keybind = ctrl+alt+k=goto_split:up
keybind = ctrl+alt+l=goto_split:right
keybind = ctrl+shift+left=resize_split:left,20
keybind = ctrl+shift+right=resize_split:right,20
keybind = ctrl+shift+up=resize_split:up,10
keybind = ctrl+shift+down=resize_split:down,10
keybind = ctrl+shift+equal=equalize_splits
keybind = ctrl+shift+z=toggle_split_zoom
keybind = ctrl+shift+comma=reload_config
```

> [!NOTE]
> If the background art does not appear, replace `~` with your full home path (e.g. `/home/<you>/.config/ghostty/assets/dragon-forge.png`) and confirm `ghostty +version` reports 1.2.0 or later.

---

<a id="step-8-create-the-dragon-forge-theme"></a>
### Step 8 · Create the Dragon Forge Theme

Custom themes live in `~/.config/ghostty/themes/`. The file name **is** the theme name:

```bash
nano ~/.config/ghostty/themes/dragon-forge
```

```ini
# 🐉 Dragon Forge — midnight steel, jade fire, castle embers
background = #0b1218
foreground = #c9d1d9
cursor-color = #e08a3c
cursor-text = #0b1218
selection-background = #1f3a44
selection-foreground = #e8edf2

# Normal
palette = 0=#0b1218
palette = 1=#d04a4a
palette = 2=#4fb89a
palette = 3=#f2c66d
palette = 4=#6ea8e0
palette = 5=#8b7cf0
palette = 6=#56c2c9
palette = 7=#c9d1d9

# Bright
palette = 8=#3a4652
palette = 9=#e5675f
palette = 10=#6fd3b0
palette = 11=#f7d68c
palette = 12=#8fc4f0
palette = 13=#a99cf5
palette = 14=#7fd8de
palette = 15=#e8edf2
```

Reload with `Ctrl + Shift + ,` and confirm Ghostty sees the theme:

```bash
ghostty +list-themes | grep -i dragon
```

---

<a id="step-9-forge-the-zshrc"></a>
### Step 9 · Forge the `.zshrc`

Replace `~/.zshrc` with the Dragon Forge config. Keep the Powerlevel10k instant-prompt block at the very top.

```bash
# ── Powerlevel10k instant prompt (keep at top) ───────────────
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# Dragon Forge Terminal Config
# Powerlevel10k + Ghostty + Zsh

export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

source "$ZSH/oh-my-zsh.sh"
[[ -f ~/.p10k.zsh ]] && source ~/.p10k.zsh

# ── Dragon prompt: 🐉 ~/dragon-forge  main ─────────────────
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(os_icon dir vcs newline prompt_char)
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION='🐉'
typeset -g POWERLEVEL9K_DIR_FOREGROUND=117
typeset -g POWERLEVEL9K_DIR_ANCHOR_FOREGROUND=117
typeset -g POWERLEVEL9K_VCS_CLEAN_FOREGROUND=79
typeset -g POWERLEVEL9K_VCS_MODIFIED_FOREGROUND=221
typeset -g POWERLEVEL9K_VCS_UNTRACKED_FOREGROUND=167
typeset -g POWERLEVEL9K_PROMPT_CHAR_OK_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=252
typeset -g POWERLEVEL9K_PROMPT_CHAR_ERROR_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=167
typeset -g POWERLEVEL9K_PROMPT_CHAR_{OK,ERROR}_VIINS_CONTENT_EXPANSION='❯'

# ── Autosuggestion colour: mist ──────────────────────────────
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=#3a4652'

# ── Aliases ──────────────────────────────────────────────────
alias ll='ls -alF'
alias gs='git status'
alias lt='eza --tree --icons --group-directories-first -a'
alias tree='eza --tree --icons --group-directories-first'
alias sigil='neofetch'
alias reforge='source ~/.zshrc'

# ── Realm navigation (the bottom dock) ───────────────────────
export FORGE="$HOME/dragon-forge"
castle()    { cd "$FORGE"                && tree -L 2; }  # main workspace
forge()     { cd "$FORGE/forge"          && ll; }         # build & develop
quests()    { cd "$FORGE/quests"         && tree -L 1; }  # challenges & labs
dragon()    { cd "$FORGE/dragon"         && tree -L 1; }  # terminal config
scrolls()   { cd "$FORGE/scrolls"        && tree -L 1; }  # docs & notes
treasures() { cd "$FORGE/treasures"      && tree -L 1; }  # projects & snippets

forge-map() {
  print -P "%F{117}  🏰 castle%f     main workspace"
  print -P "%F{215}  🔥 forge%f      build & develop"
  print -P "%F{167}  ⚔️  quests%f     challenges & labs"
  print -P "%F{79}  🐉 dragon%f     terminal config"
  print -P "%F{141}  📜 scrolls%f    docs & notes"
  print -P "%F{80}  💎 treasures%f  projects & snippets"
  print -P "\n%F{240}  \"Small steps build great legends.\"%f"
}
```

Apply it:

```bash
exec zsh
```

---

<a id="step-10-scaffold-the-realm"></a>
### Step 10 · Scaffold the Realm

Create the `~/dragon-forge` directory map shown in the top-left pane:

```bash
mkdir -p ~/dragon-forge/{dragon/{config,themes,scripts},quests/{beginner,intermediate,boss-fights},forge/{projects,builds,experiments},scrolls/{notes,cheatsheets},treasures/{snippets,archives}}

cd ~/dragon-forge && git init -b main
```

Keep your terminal config inside the realm so it travels with your repo:

```bash
cp ~/.config/ghostty/config            ~/dragon-forge/dragon/config/ghostty.config
cp ~/.config/ghostty/themes/dragon-forge ~/dragon-forge/dragon/themes/dragon-forge
cp ~/.zshrc                            ~/dragon-forge/dragon/config/zshrc
```

#### Verify

```bash
castle
```

```text
dragon-forge
├── dragon
│  ├── config
│  ├── scripts
│  └── themes
├── forge
│  ├── builds
│  ├── experiments
│  └── projects
├── quests
│  ├── beginner
│  ├── boss-fights
│  └── intermediate
├── scrolls
│  ├── cheatsheets
│  └── notes
└── treasures
   ├── archives
   └── snippets
```

---

<a id="step-11-summon-the-dragon-sigil"></a>
### Step 11 · Summon the Dragon Sigil (Neofetch)

> Official Documentation: [Neofetch Wiki](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info)

#### 1. Generate the Default Config

```bash
neofetch >/dev/null && mkdir -p ~/.config/neofetch
```

#### 2. Add the ASCII Dragon

```bash
nano ~/.config/neofetch/dragon.txt
```

```text
${c1}                 __.--~~.,-.__
${c1}         `~-._.-(`-.__`-.  (`-.
${c1}          .-~~~`-.__   ~.  )  )
${c1}         (  ${c2}<>${c1}   _.-~` (  (`-.
${c1}          `~-.__.-~  _.-~`  )  )
${c1}             ,__.--~~   _.-~ .'
${c1}           .~       _.-~   .'
${c1}          /  /\  .-~      .'
${c1}         (  (  `~       .'
${c1}          \  \     _.-~~
${c1}       _.-~`  `~-~~
${c1}   _.-~  /\ ${c2}/\  /\ ${c1}
${c1}  ~-.__ /  \/  \/  \__.-~
```

#### 3. Point Neofetch at the Dragon

Edit `~/.config/neofetch/config.conf` and set:

```bash
print_info() {
    info title
    info underline

    info "OS" distro
    info "Host" model
    info "Kernel" kernel
    info "Uptime" uptime
    info "Shell" shell
    info "Terminal" term
    prin "Theme" "Dragon Forge"
    info "Icons" icons
    info "Font" term_font
    info "CPU" cpu
    info "Memory" memory
    info "GPU" gpu

    info cols
}

image_backend="ascii"
image_source="$HOME/.config/neofetch/dragon.txt"
ascii_colors=(2 3)
colors=(6 6 7 6 2 7)
underline_char="-"
block_range=(0 7)
block_width=3
```

#### Verify

```bash
sigil
```

*Expected: a jade ASCII dragon beside your system info and an 8-colour Dragon Forge swatch bar.*

---

<a id="step-12-assemble-the-command-centre"></a>
### Step 12 · Assemble the Command Centre

Recreate the five-pane layout from the screenshot using the split keybinds from Step 7:

```text
┌───────────────────────────┬──────────────────────────────────────┐
│ ① castle                  │ ② sigil                              │
│   tree -L 2               │   neofetch                           │
│                           │                                      │
├──────────────┬────────────┴──────────────┬───────────────────────┤
│ ③ gs         │ ④ forge                   │ ⑤ cat ~/.zshrc |      │
│  git status  │   ls -la                  │    head -n 15         │
└──────────────┴───────────────────────────┴───────────────────────┘
```

| Step | Keys | Command in the new pane |
| :---: | :--- | :--- |
| 1 | *(first pane)* | `castle` |
| 2 | `Ctrl + Shift + D` | `sigil` |
| 3 | `Ctrl + Alt + H`, then `Ctrl + Shift + S` | `gs` |
| 4 | `Ctrl + Shift + D` | `forge && cd projects && ls -la` |
| 5 | `Ctrl + Shift + D` | `cat ~/.zshrc \| head -n 15` |
| 6 | `Ctrl + Shift + =` | *(equalise, then fine-tune with `Ctrl + Shift + ←/→/↑/↓`)* |

> [!TIP]
> Press `Ctrl + Shift + Z` to zoom any pane full-screen during a boss fight, and again to return to the command centre.

---

<a id="verification-checklist"></a>
## 🔍 Verification Checklist

- [ ] **Ghostty 1.2+**
  ```bash
  ghostty +version
  ```
  *Expected: `Ghostty 1.2.x` or later*

- [ ] **Config Parses Cleanly**
  ```bash
  ghostty +validate-config
  ```
  *Expected: no output (no errors)*

- [ ] **Dragon Forge Theme Loaded**
  ```bash
  ghostty +list-themes | grep -i dragon
  ```
  *Expected: `dragon-forge (user)`*

- [ ] **Zsh Default Shell**
  ```bash
  echo $SHELL
  ```
  *Expected: `/usr/bin/zsh`*

- [ ] **Powerlevel10k Prompt**
  ```bash
  echo $ZSH_THEME
  ```
  *Expected: `powerlevel10k/powerlevel10k`*

- [ ] **Nerd Font Glyphs**
  ```bash
  echo -e "  "
  ```
  *Expected: branch, GitHub, and Ubuntu icons — no empty boxes.*

- [ ] **Realm Navigation**
  ```bash
  forge-map
  ```
  *Expected: the six realm commands and the forge motto.*

---

<a id="troubleshooting"></a>
## 🛠️ Troubleshooting

<details>
<summary><b>🖼️ Background image does not show</b></summary>

<br />

1. Confirm `ghostty +version` is **1.2.0+** — older versions ignore `background-image`.
2. Use an absolute path: `background-image = /home/<you>/.config/ghostty/assets/dragon-forge.png`.
3. Raise `background-image-opacity` (e.g. `0.3`) to check it is loading at all.
4. Run `ghostty +validate-config` and fix any reported line.

</details>

<details>
<summary><b>🎨 <code>theme = dragon-forge</code> not found</b></summary>

<br />

The theme file must be at `~/.config/ghostty/themes/dragon-forge` with **no file extension**. Check with:

```bash
ls ~/.config/ghostty/themes/
```

</details>

<details>
<summary><b>🔲 Icons render as boxes or question marks</b></summary>

<br />

1. Re-run `fc-cache -fv` after installing the font.
2. Confirm the exact family name with `ghostty +list-fonts | grep -i jetbrains`.
3. Make sure the config line reads `font-family = "JetBrainsMono Nerd Font"` (no space between *JetBrains* and *Mono*).

</details>

<details>
<summary><b>⌨️ Split keybinds do nothing</b></summary>

<br />

GNOME or another app may already own the shortcut. List what Ghostty has bound:

```bash
ghostty +list-keybinds | grep split
```

Change the conflicting `keybind = ...` lines in `~/.config/ghostty/config` and reload with `Ctrl + Shift + ,`.

</details>

<details>
<summary><b>🐚 Shell is still Bash</b></summary>

<br />

```bash
chsh -s "$(which zsh)"
```

Log out of your desktop session completely and back in — a new terminal tab is not enough.

</details>

<details>
<summary><b>🚨 Broken <code>~/.zshrc</code></b></summary>

<br />

```bash
cp ~/.zshrc.backup ~/.zshrc && exec zsh
```

Or restore the Dragon Forge copy kept inside the realm:

```bash
cp ~/dragon-forge/dragon/config/zshrc ~/.zshrc && exec zsh
```

</details>

---

<a id="official-documentation"></a>
## 📚 Official Documentation & References

| Technology | Project Links | Documentation & Guides |
| :--- | :--- | :--- |
| **Ghostty** | [ghostty.org](https://ghostty.org) | [Install](https://ghostty.org/docs/install/binary) · [Config Reference](https://ghostty.org/docs/config/reference) · [Keybinds](https://ghostty.org/docs/config/keybind/reference) · [Theming](https://ghostty.org/docs/features/theme) |
| **Oh My Zsh** | [ohmyz.sh](https://ohmyz.sh) | [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh) · [Plugins Directory](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins) |
| **Powerlevel10k** | [romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k) | [Configuration](https://github.com/romkatv/powerlevel10k#configuration) · [Fonts](https://github.com/romkatv/powerlevel10k#fonts) |
| **Nerd Fonts** | [nerdfonts.com](https://www.nerdfonts.com) | [Font Downloads](https://www.nerdfonts.com/font-downloads) · [Glyph Cheat Sheet](https://www.nerdfonts.com/cheat-sheet) |
| **eza** | [eza.rocks](https://eza.rocks) | [GitHub Repository](https://github.com/eza-community/eza) |
| **Neofetch** | [dylanaraps/neofetch](https://github.com/dylanaraps/neofetch) | [Customizing Info](https://github.com/dylanaraps/neofetch/wiki/Customizing-Info) · [Custom ASCII](https://github.com/dylanaraps/neofetch/wiki/Custom-Ascii-art-file-format) |
| **Papirus** | [Papirus Icon Theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme) | [Installation](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme#installation) |

---

<a id="license"></a>
## 📄 License

This guide is open-source and released under the [MIT License](LICENSE).

<div align="center">

<br />

```text
D R A G O N   F O R G E
T E R M I N A L   S E T U P
```

**🏰 castle · 🔥 forge · ⚔️ quests · 🐉 dragon · 📜 scrolls · 💎 treasures**

*Small steps build great legends.* If the forge served you well, leave a ⭐ on GitHub!

</div>
