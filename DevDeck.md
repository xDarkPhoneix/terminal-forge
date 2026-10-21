<div align="center">

# 🖥️ DEV DECK

### Code · Build · Deploy · Repeat — The iTerm2 Developer Workspace

*A neon-blue, cyberpunk developer cockpit built on macOS, iTerm2, tmux, Zsh, Powerlevel10k, and JetBrains Mono Nerd Font.*

<br />

[![Platform](https://img.shields.io/badge/Platform-macOS%2014+-000000?style=for-the-badge&logo=apple&logoColor=white)](#requirements)
[![Terminal](https://img.shields.io/badge/Terminal-iTerm2%203.5+-3d9bff?style=for-the-badge&logo=iterm2&logoColor=white)](#step-2-configure-iterm2)
[![Multiplexer](https://img.shields.io/badge/Multiplexer-tmux%203.4+-1bb91f?style=for-the-badge&logo=tmux&logoColor=white)](#step-6-configure-tmux)
[![Shell](https://img.shields.io/badge/Shell-Zsh%205.9+-f1502f?style=for-the-badge&logo=gnu-bash&logoColor=white)](#step-3-install-oh-my-zsh)
[![Prompt Theme](https://img.shields.io/badge/Theme-Powerlevel10k-38bdf8?style=for-the-badge&logo=powershell&logoColor=white)](#step-4-install-powerlevel10k)
[![Font](https://img.shields.io/badge/Font-JetBrains%20Mono%20Nerd-000000?style=for-the-badge&logo=jetbrains&logoColor=white)](#step-1-install-the-toolchain)
[![License](https://img.shields.io/badge/License-MIT-amber?style=for-the-badge)](#license)

<br />

[⚡ Quick Start](#quick-start) • [🏗️ Architecture](#system-architecture) • [🎨 Palette](#dev-deck-palette) • [📖 Step-by-Step Guide](#step-by-step-installation) • [🧩 Layout](#step-11-launch-the-deck) • [🔍 Verification](#verification-checklist) • [🛠️ Troubleshooting](#troubleshooting)

<br />

![DevDeck Cyberpunk Developer Workspace](./DevDeck%20Cyberpunk%20Developer%20Workspace.png)

<br />

> *"Better tools. Better workflow. Better you."*

</div>

---

<a id="system-architecture"></a>
## 🏗️ System Architecture

Dev Deck turns a single iTerm2 window into a ten-pane cockpit: a header banner, a workspace sidebar, and eight numbered panes for git, the dev server, Docker, system stats, the project tree, a command cheat sheet, branches, and live processes. A bottom status bar tracks your path, branch, and stack versions.

| Component | Layer | Purpose & Highlights |
| :--- | :--- | :--- |
| **[iTerm2](https://iterm2.com)** | Terminal Emulator | Dynamic profiles, a native top status bar (battery, date, clock), and truecolor. |
| **[tmux](https://github.com/tmux/tmux)** | Multiplexer | The ten-pane layout, tab-style pane titles, and the bottom status bar. |
| **[Zsh](https://www.zsh.org)** | Shell Engine | Default macOS shell and the base for the whole stack. |
| **[Oh My Zsh](https://ohmyz.sh)** | Framework | Plugin & theme manager for Zsh. |
| **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)** | Prompt Engine | `~/workspace/projects/backend  main` prompt with a `❯` input line. |
| **[JetBrains Mono Nerd Font](https://www.nerdfonts.com)** | Typography | Monospace font with the folder, git, Docker, and language icons. |
| **[eza](https://eza.rocks)** | File Explorer | The icon-rich workspace sidebar and project tree. |
| **[Docker](https://www.docker.com/products/docker-desktop/)** | Containers | `dev-postgres`, `dev-redis`, `backend`, and `frontend` containers. |
| **[Node.js 22](https://nodejs.org) · [Python 3.12](https://www.python.org)** | Runtimes | Next.js dev server and the FastAPI backend. |
| **DevDeck Scripts** | Productivity | `devdeck`, `devdeck-banner`, `devdeck-sys`, `devdeck-cheats`, `devdeck-branches`, `devdeck-procs`. |

---

<a id="requirements"></a>
## 📋 Requirements

- 🍎 **Operating System**: macOS 14 Sonoma or later (shown on macOS Sequoia 15.6)
- 🍺 **Package Manager**: [Homebrew](https://brew.sh)
- 🐳 **Containers**: Docker Desktop (or OrbStack) running
- 🌐 **Network**: Stable internet connection for packages, fonts, and Git repositories

> [!NOTE]
> Run each step in order and check the verification output before moving on. Paths below assume Apple Silicon (`/opt/homebrew`). On Intel Macs, replace `/opt/homebrew` with `/usr/local`.

---

<a id="quick-start"></a>
## ⚡ Quick Start

For experienced developers, here is the whole deck in one pass:

```bash
# 1. Homebrew packages (see the Brewfile in Step 1)
brew bundle --file=~/Brewfile

# 2. Oh My Zsh, Powerlevel10k, and plugins
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)" "" --unattended
ZSH_CUSTOM="${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}"
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git "$ZSH_CUSTOM/themes/powerlevel10k"
git clone https://github.com/zsh-users/zsh-autosuggestions "$ZSH_CUSTOM/plugins/zsh-autosuggestions"
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git "$ZSH_CUSTOM/plugins/zsh-syntax-highlighting"

# 3. Scaffold the workspace
mkdir -p ~/workspace/{projects/{frontend,backend/api,ai/ml-project,mobile/app,experiments/sandbox},labs/{linux,docker,databases,networking},scripts/{bash,python,automation},configs/{zsh,git,terminal},docs/{notes,cheatsheets},archive/old-projects}
mkdir -p ~/.local/bin ~/.config/devdeck
```

Then add the [iTerm2 profile](#step-2-configure-iterm2), the [`.zshrc`](#step-5-write-the-zshrc), the [`.tmux.conf`](#step-6-configure-tmux), the [DevDeck scripts](#step-7-install-the-devdeck-scripts), seed the [demo projects](#step-8-seed-the-backend-repository), and run `devdeck`.

---

<a id="dev-deck-palette"></a>
## 🎨 Dev Deck Palette

Colours sampled from the workspace — deep navy, electric blue, and neon accents:

| Swatch | Role | Hex |
| :---: | :--- | :--- |
| ⬛ | Background · Deep Navy | `#070c16` |
| ⬜ | Foreground · Console Mist | `#c8d3e6` |
| 🟥 | Red · Modified | `#ff5c7a` |
| 🟩 | Green · Up & Running | `#3fd68f` |
| 🟨 | Yellow · Warning | `#f7c35f` |
| 🟦 | Blue · Electric Path | `#3d9bff` |
| 🟪 | Magenta · Branch | `#b57cff` |
| 🩵 | Cyan · Neon Accent | `#34d3ee` |
| 🔲 | Borders · Grid Line | `#1e2a3d` |
| 🌫️ | Selection · Night Glass | `#1b2a44` |

---

<a id="step-by-step-installation"></a>
## 📖 Step-by-Step Installation

<a id="step-1-install-the-toolchain"></a>
### Step 1 · Install the Toolchain

> Official Documentation: [Homebrew](https://brew.sh) · [Homebrew Bundle](https://github.com/Homebrew/homebrew-bundle) · [Nerd Fonts](https://www.nerdfonts.com)

Install Homebrew if you do not have it yet:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Create `~/Brewfile`:

```ruby
# ── Dev Deck Brewfile ───────────────────────────────────────
brew "git"
brew "tmux"
brew "eza"
brew "tree"
brew "node@22"
brew "python@3.12"
brew "libpq"          # psql client
brew "redis"          # redis-cli (the server runs in Docker)

cask "iterm2"
cask "visual-studio-code"
cask "docker-desktop"
cask "font-jetbrains-mono-nerd-font"
```

Install everything:

```bash
brew bundle --file=~/Brewfile
```

> [!TIP]
> Prefer [OrbStack](https://orbstack.dev)? Replace `cask "docker-desktop"` with `cask "orbstack"` — every `docker` command in this guide works the same.

#### Verify

```bash
tmux -V && eza --version | head -n 1 && /opt/homebrew/opt/node@22/bin/node -v
```

```text
tmux 3.5a
eza - A modern, maintained replacement for ls
v22.x.x
```

---

<a id="step-2-configure-iterm2"></a>
### Step 2 · Configure iTerm2

> Official Documentation: [iTerm2 Docs](https://iterm2.com/documentation.html) · [Dynamic Profiles](https://iterm2.com/documentation-dynamic-profiles.html) · [Status Bar](https://iterm2.com/documentation-status-bar.html)

#### 1. Install the DevDeck Dynamic Profile

iTerm2 loads any JSON file in its `DynamicProfiles` folder automatically — no import needed:

```bash
mkdir -p ~/Library/Application\ Support/iTerm2/DynamicProfiles
nano ~/Library/Application\ Support/iTerm2/DynamicProfiles/devdeck.json
```

Paste the complete profile (font, colours, window size, and the `devdeck` launch command):

```json
{
  "Profiles": [
    {
      "Name": "DevDeck",
      "Guid": "devdeck-cyberpunk-workspace-0001",
      "Tags": [
        "devdeck"
      ],
      "Normal Font": "JetBrainsMonoNFM-Regular 13",
      "Use Non-ASCII Font": false,
      "ASCII Ligatures": true,
      "Use Bold Font": true,
      "Draw Powerline Glyphs": true,
      "Vertical Spacing": 1.05,
      "Columns": 220,
      "Rows": 62,
      "Transparency": 0.03,
      "Blur": true,
      "Blur Radius": 8,
      "Unlimited Scrollback": true,
      "Terminal Type": "xterm-256color",
      "Option Key Sends": 2,
      "Custom Directory": "Yes",
      "Working Directory": "~/workspace",
      "Custom Command": "Yes",
      "Command": "/bin/zsh -lic devdeck",
      "Use Separate Colors for Light and Dark Mode": false,
      "Background Color": {
        "Red Component": 0.0275,
        "Green Component": 0.0471,
        "Blue Component": 0.0863,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Foreground Color": {
        "Red Component": 0.7843,
        "Green Component": 0.8275,
        "Blue Component": 0.902,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Bold Color": {
        "Red Component": 0.9333,
        "Green Component": 0.9529,
        "Blue Component": 0.9843,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Cursor Color": {
        "Red Component": 0.9333,
        "Green Component": 0.9529,
        "Blue Component": 0.9843,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Cursor Text Color": {
        "Red Component": 0.0275,
        "Green Component": 0.0471,
        "Blue Component": 0.0863,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Selection Color": {
        "Red Component": 0.1059,
        "Green Component": 0.1647,
        "Blue Component": 0.2667,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Selected Text Color": {
        "Red Component": 0.9333,
        "Green Component": 0.9529,
        "Blue Component": 0.9843,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Link Color": {
        "Red Component": 0.2392,
        "Green Component": 0.6078,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Badge Color": {
        "Red Component": 0.2392,
        "Green Component": 0.6078,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 0 Color": {
        "Red Component": 0.0431,
        "Green Component": 0.0706,
        "Blue Component": 0.1255,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 1 Color": {
        "Red Component": 1.0,
        "Green Component": 0.3608,
        "Blue Component": 0.4784,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 2 Color": {
        "Red Component": 0.2471,
        "Green Component": 0.8392,
        "Blue Component": 0.5608,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 3 Color": {
        "Red Component": 0.9686,
        "Green Component": 0.7647,
        "Blue Component": 0.3725,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 4 Color": {
        "Red Component": 0.2392,
        "Green Component": 0.6078,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 5 Color": {
        "Red Component": 0.7098,
        "Green Component": 0.4863,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 6 Color": {
        "Red Component": 0.2039,
        "Green Component": 0.8275,
        "Blue Component": 0.9333,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 7 Color": {
        "Red Component": 0.7843,
        "Green Component": 0.8275,
        "Blue Component": 0.902,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 8 Color": {
        "Red Component": 0.2314,
        "Green Component": 0.2902,
        "Blue Component": 0.3882,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 9 Color": {
        "Red Component": 1.0,
        "Green Component": 0.4824,
        "Blue Component": 0.5765,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 10 Color": {
        "Red Component": 0.4314,
        "Green Component": 0.9059,
        "Blue Component": 0.6588,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 11 Color": {
        "Red Component": 0.9882,
        "Green Component": 0.8471,
        "Blue Component": 0.5176,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 12 Color": {
        "Red Component": 0.4235,
        "Green Component": 0.7137,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 13 Color": {
        "Red Component": 0.8118,
        "Green Component": 0.6392,
        "Blue Component": 1.0,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 14 Color": {
        "Red Component": 0.4039,
        "Green Component": 0.9098,
        "Blue Component": 0.9765,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      },
      "Ansi 15 Color": {
        "Red Component": 0.9333,
        "Green Component": 0.9529,
        "Blue Component": 0.9843,
        "Alpha Component": 1,
        "Color Space": "sRGB"
      }
    }
  ]
}
```

#### 2. Window Chrome & Top Status Bar

Open **iTerm2 → Settings** (`⌘ ,`) and set:

| Where | Setting | Value |
| :--- | :--- | :--- |
| Appearance → General | Theme | **Minimal** |
| Appearance → General | Status bar location | **Top** |
| Appearance → Panes | Show per-pane title bar with split panes | **Off** *(tmux draws the titles)* |
| Profiles → DevDeck → Session | Status bar enabled | **On** |
| Profiles → DevDeck → Text | Font | **JetBrainsMono Nerd Font Mono · 13** |

Click **Configure Status Bar** and drag in these components, left to right:

1. **Spring** — pushes the rest to the right
2. **git State** — branch icon
3. **CPU Utilization** & **Memory Utilization**
4. **Battery Level** — e.g. `83%`
5. **Clock** — set *Format* to `MMM d, yyyy    h:mm a` → `Oct 21, 2026    10:42 AM`

Under **Advanced**, set *Background Color* to `#070c16`, *Default Text Color* to `#c8d3e6`, and turn **Auto-Rainbow** off.

> [!NOTE]
> The profile opens straight into the deck. Launch it from **Profiles → DevDeck** (`⌘ O`), or select it and choose **Other Actions… → Set as Default** to start every window in the deck. The centered **DevDeck** title comes from tmux (`set-titles-string`) in [Step 6](#step-6-configure-tmux).

---

<a id="step-3-install-oh-my-zsh"></a>
### Step 3 · Install Oh My Zsh

> Official Documentation: [ohmyz.sh](https://ohmyz.sh) · [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh)

macOS already ships Zsh 5.9 as the default shell. Back up your config and install Oh My Zsh:

```bash
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null || true
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### Verify

```bash
echo $SHELL && zsh --version && ls ~/.oh-my-zsh
```

```text
/bin/zsh
zsh 5.9 (arm64-apple-darwin24.0)
```

---

<a id="step-4-install-powerlevel10k"></a>
### Step 4 · Install Powerlevel10k & Plugins

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

Run the wizard once and choose **Lean**, **Unicode**, **256 colors**, **No** time, **Two lines**, **Disconnected**, **No frame**, **Sparse**, **Few icons**, **Concise**, **Instant prompt: Verbose**:

```bash
p10k configure
```

Recolour the git segment to the Dev Deck magenta and use `↑ ↓` arrows for ahead/behind:

```bash
sed -i '' "s/clean='%76F'/clean='%141F'/; s/⇡/↑/g; s/⇣/↓/g" ~/.p10k.zsh
```

---

<a id="step-5-write-the-zshrc"></a>
### Step 5 · Write the `.zshrc`

Replace `~/.zshrc` with the Dev Deck config. Keep the Powerlevel10k instant-prompt block at the very top.

```bash
# ── Powerlevel10k instant prompt (keep at top) ───────────────
if [[ -r "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh" ]]; then
  source "${XDG_CACHE_HOME:-$HOME/.cache}/p10k-instant-prompt-${(%):-%n}.zsh"
fi

# Dev Deck Terminal Config
# Powerlevel10k + iTerm2 + tmux + Zsh

# ── PATH: Homebrew, keg-only runtimes, DevDeck scripts ───────
eval "$(/opt/homebrew/bin/brew shellenv)"
export PATH="$HOME/.local/bin:/opt/homebrew/opt/node@22/bin:/opt/homebrew/opt/python@3.12/libexec/bin:/opt/homebrew/opt/libpq/bin:$PATH"

export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"
DISABLE_AUTO_TITLE="true"      # keep tmux pane titles like "1: main"
plugins=(git docker npm python zsh-autosuggestions zsh-syntax-highlighting)

source "$ZSH/oh-my-zsh.sh"
[[ -f ~/.p10k.zsh ]] && source ~/.p10k.zsh

# ── Dev Deck prompt: ~/workspace/projects/backend  main ↑2 ──
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(dir vcs newline prompt_char)
typeset -g POWERLEVEL9K_DIR_PREFIX=$'%F{45} '
typeset -g POWERLEVEL9K_DIR_FOREGROUND=75
typeset -g POWERLEVEL9K_DIR_SHORTENED_FOREGROUND=75
typeset -g POWERLEVEL9K_DIR_ANCHOR_FOREGROUND=75
typeset -g POWERLEVEL9K_SHORTEN_STRATEGY=none
typeset -g POWERLEVEL9K_VCS_BRANCH_ICON=$' '
typeset -g POWERLEVEL9K_PROMPT_CHAR_OK_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=78
typeset -g POWERLEVEL9K_PROMPT_CHAR_ERROR_{VIINS,VICMD,VIVIS,VIOWR}_FOREGROUND=204

# ── Autosuggestion colour: grid line ─────────────────────────
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=#3b4a63'

# ── Local dev database (matches compose.yaml) ────────────────
export PGHOST=localhost PGUSER=dev PGPASSWORD=devdeck PGDATABASE=devdb

# ── Aliases ──────────────────────────────────────────────────
alias ll='ls -alF'
alias gs='git status'
alias gl='git log --oneline --graph --decorate -n 20'
alias tree='eza --tree --icons=always --group-directories-first'
alias code.='code .'
alias reload='source ~/.zshrc'

# ── Workspace navigation ─────────────────────────────────────
export WS="$HOME/workspace"
ws()   { cd "$WS"                              && tree -L 1; }
fe()   { cd "$WS/projects/frontend/web-app"; }
be()   { cd "$WS/projects/backend"             && gs; }
labs() { cd "$WS/labs"                         && tree -L 1; }
up()   { docker compose -f "$WS/labs/docker/compose.yaml" up -d && docker ps; }
down() { docker compose -f "$WS/labs/docker/compose.yaml" down; }
```

Apply it:

```bash
exec zsh
```

---

<a id="step-6-configure-tmux"></a>
### Step 6 · Configure tmux

> Official Documentation: [tmux Wiki](https://github.com/tmux/tmux/wiki) · [Formats](https://github.com/tmux/tmux/wiki/Formats) · [Manual](https://man.openbsd.org/tmux)

tmux draws the tab-style pane titles (`○ 3: docker ×`) and the bottom status bar.

```bash
nano ~/.tmux.conf
```

```bash
# ╔══════════════════════════════════════════════════════════╗
# ║              🖥️  DEV DECK — tmux Config                  ║
# ║           Code  /  Build  /  Deploy  /  Repeat            ║
# ╚══════════════════════════════════════════════════════════╝

# ── General ──────────────────────────────────────────────────
set -g default-terminal "tmux-256color"
set -as terminal-features ",xterm-256color:RGB"
set -g mouse on
set -g base-index 1
setw -g pane-base-index 1
set -g escape-time 10
set -g history-limit 50000
set -g focus-events on

# ── Window title shown by iTerm2 ─────────────────────────────
set -g set-titles on
set -g set-titles-string "DevDeck"
set -g allow-rename off
set -g allow-set-title off          # keep "1: main" etc. (tmux 3.4+)

# ── Pane borders: tab-style titles ───────────────────────────
set -g pane-border-status top
set -g pane-border-lines single
set -g pane-border-style "fg=#1e2a3d"
set -g pane-active-border-style "fg=#3d9bff"
set -g pane-border-format "#{?#{==:#{pane_title},header},, #[fg=#{?pane_active,#3d9bff,#34d3ee}]#{?pane_active,●,○} #[fg=#eef3fb#,bold]#{pane_title} #[fg=#3b4a63#,nobold]× }"

# ── Status bar: path · branch · stack · clock ────────────────
set -g status on
set -g status-position bottom
set -g status-interval 5
set -g status-style "bg=#0b1220,fg=#c8d3e6"
set -g status-left-length 90
set -g status-right-length 160
set -g window-status-format ""
set -g window-status-current-format ""

set -g status-left "#[fg=#f7c35f]   #[fg=#3d9bff]#(echo '#{pane_current_path}' | sed \"s|^$HOME|~|\")   #[fg=#b57cff] #[fg=#eef3fb]#(git -C '#{pane_current_path}' branch --show-current 2>/dev/null) "

set -g status-right "#[fg=#3fd68f] #[fg=#3d9bff]node #(node -v 2>/dev/null | cut -d. -f1 | tr -d v)    #[fg=#f7c35f] #[fg=#3d9bff]python #(python3 -V 2>/dev/null | cut -d' ' -f2 | cut -d. -f1-2)    #[fg=#3d9bff] docker    #[fg=#34d3ee] #[fg=#3d9bff]postgres    #[fg=#ff5c7a] #[fg=#3d9bff]redis      #[fg=#c8d3e6] %I:%M %p "

# ── Keybinds ─────────────────────────────────────────────────
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"
bind -n M-Left  select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up    select-pane -U
bind -n M-Down  select-pane -D
bind T command-prompt -p "pane title:" "select-pane -T '%%'"
bind r source-file ~/.tmux.conf \; display "Dev Deck reloaded"
```

> [!NOTE]
> The status-bar icons are Nerd Font glyphs. If you copy this file from a browser and they turn into boxes, check that iTerm2 is using **JetBrainsMono Nerd Font** ([Step 2](#step-2-configure-iterm2)).

---

<a id="step-7-install-the-devdeck-scripts"></a>
### Step 7 · Install the DevDeck Scripts

Each pane runs a small Zsh script. They share one palette file.

```bash
mkdir -p ~/.local/bin ~/.config/devdeck
```

#### 1. Shared Library — `~/.config/devdeck/lib.zsh`

```zsh
# Dev Deck palette as truecolor escapes, plus layout helpers
setopt extendedglob

fg() { local h=${1#\#}; print -n $'\e[38;2;'$((16#${h[1,2]}))';'$((16#${h[3,4]}))';'$((16#${h[5,6]}))'m'; }

BLUE=$(fg 3d9bff)   CYAN=$(fg 34d3ee)   GREEN=$(fg 3fd68f)  RED=$(fg ff5c7a)
YELLOW=$(fg f7c35f) PURPLE=$(fg b57cff) TEXT=$(fg c8d3e6)   WHITE=$(fg eef3fb)
MUTED=$(fg 7d8ca5)  DIM=$(fg 3b4a63)
BOLD=$'\e[1m'       RESET=$'\e[0m'

# visible length of a string, ignoring colour codes
vislen() { local s=${(S)1//$'\e'\[[0-9;]#m/}; print ${#s}; }

# print $1 padded with spaces to $2 visible columns
pad() { print -rn -- "$1"; printf '%*s' $(( $2 - $(vislen "$1") )) ''; }

# keep a static pane on screen with no prompt; any key returns to the shell
hold() { tput civis; read -rs -k1; tput cnorm; clear; }

# "1.2 KB/s" from a byte count over an interval
rate() { printf '%.1f KB/s' $(( $1 / 1024.0 / $2 )); }
```

#### 2. Header Banner — `~/.local/bin/devdeck-banner`

```zsh
#!/usr/bin/env zsh
# Dev Deck header: logo, motto, stack info, and the "Keep Building" sparkline
source ~/.config/devdeck/lib.zsh

info() { print -rn -- "${CYAN}$1 ${TEXT}$(printf '%-9s' $2)${WHITE}$3${RESET}"; }

row() {
  print -r -- "  $(pad "$1" 10)   $(pad "$2" 30)  $(pad "$3" 18) ${DIM}│${RESET}  $(pad "$4" 32) ${DIM}│${RESET}  $5"
}

clear
print -r -- "$(printf '%52s' '')${DIM}C O D E   /   B U I L D   /   D E P L O Y   /   R E P E A T${RESET}"
print
row "${BLUE}╭────────╮" "" "${MUTED}\"Better tools." \
    "$(info $'' OS "macOS $(sw_vers -productVersion)")" "${BLUE}▁▂▄▃▆▂▅▇▆${RESET}"
row "${BLUE}│ ${CYAN}>_${BLUE}     │" "${BOLD}${WHITE}Dev ${BLUE}Deck${RESET}" "${MUTED}Better workflow." \
    "$(info $'' Shell "zsh $ZSH_VERSION")" "${MUTED}Keep${RESET}"
row "${BLUE}│        │" "${MUTED}iTerm2 • Developer Workspace" "${MUTED}Better you.\"" \
    "$(info $'' Editor "VS Code")" "${MUTED}Building${RESET}"
row "${BLUE}╰────────╯" "" "${DIM}--" \
    "$(info $'' Terminal "iTerm2")" "${MUTED}...${RESET}"
hold
```

#### 3. Workspace Sidebar — `~/.local/bin/devdeck-sidebar`

```zsh
#!/usr/bin/env zsh
# Directory map of ~/workspace with a file count footer
source ~/.config/devdeck/lib.zsh

clear
eza --tree --level=3 --only-dirs --icons=always --color=always \
    --group-directories-first ~/workspace | tail -n +2
print -r -- $'\n'"${MUTED}$(command tree -L 3 ~/workspace | tail -n 1)${RESET}"
hold
```

#### 4. System Monitor — `~/.local/bin/devdeck-sys`

```zsh
#!/usr/bin/env zsh
# CPU, memory, load average, disk, network, and battery — refreshes every 2s
source ~/.config/devdeck/lib.zsh

bar() { # percent, colour
  local w=14 n=$(( $1 * 14 / 100 )) s=""
  repeat $n s+="█"; print -rn -- "$2$s${DIM}"
  s=""; repeat $(( w - n )) s+="░"; print -rn -- "$s${RESET}"
}

ncpu=$(sysctl -n hw.ncpu)
iface=$(route -n get default 2>/dev/null | awk '/interface:/{print $2}')
iface=${iface:-en0}
bytes() { netstat -ibn -I $iface | awk 'NR==2{print $7, $10}'; }
read rx0 tx0 <<< "$(bytes)"

tput civis
trap 'tput cnorm; exit' INT TERM
while true; do
  sleep 2
  read rx1 tx1 <<< "$(bytes)"
  cpu=$(ps -A -o %cpu= | awk -v n=$ncpu '{s+=$1} END {printf "%d", s/n}')
  mem=$(( 100 - $(memory_pressure | awk -F': ' '/free percentage/{gsub("%","",$2); print $2}') ))
  load=(${(s: :)$(sysctl -n vm.loadavg | tr -d '{}')})
  disk=$(df -h /System/Volumes/Data | awk 'NR==2{print $5}')
  batt=$(pmset -g batt | grep -Eo '[0-9]+%' | head -n 1)

  clear
  print
  printf "  ${TEXT}CPU     ${WHITE}${BOLD}%3d%%${RESET}  %s\n" $cpu "$(bar $cpu $CYAN)"
  printf "  ${TEXT}MEMORY  ${WHITE}${BOLD}%3d%%${RESET}  %s\n" $mem "$(bar $mem $BLUE)"
  print
  print -r -- "  ${BLUE}Load Avg  ${CYAN}${load[1]}   ${load[2]}   ${load[3]}${RESET}"
  print -r -- "  ${DIM}──────────────────────────${RESET}"
  printf "  ${CYAN}%s${TEXT} Disk      ${WHITE}%s${RESET}\n"    $'' $disk
  printf "  ${CYAN}%s${TEXT} Network   ${MUTED}↑ %s  ↓ %s${RESET}\n" $'' "$(rate $((tx1 - tx0)) 2)" "$(rate $((rx1 - rx0)) 2)"
  printf "  ${CYAN}%s${TEXT} Battery   ${WHITE}%s${RESET}\n"    $'' ${batt:-AC}
  rx0=$rx1 tx0=$tx1
done
```

#### 5. Quick Commands — `~/.local/bin/devdeck-cheats`

```zsh
#!/usr/bin/env zsh
# Cheat sheet of everyday commands
source ~/.config/devdeck/lib.zsh

rows=(
  $'' $RED    "git status"            "Check current git status"
  $'' $RED    "git log --oneline"     "View commit history"
  $'' $RED    "npm run dev"           "Start development server"
  $'' $BLUE   "docker ps"             "List running containers"
  $'' $CYAN   "psql"                  "Connect to PostgreSQL"
  $'' $RED    "redis-cli"             "Open Redis CLI"
  $'' $YELLOW "python -m venv .venv"  "Create virtual environment"
  $'' $TEXT   "ls -la"                "Detailed list"
  $'' $TEXT   "tree"                  "Show directory tree"
)

clear
print
for icon colour cmd desc in $rows; do
  print -r -- "  ${colour}${icon}${RESET}  ${WHITE}$(printf '%-22s' $cmd)${BLUE}${desc}${RESET}"
done
hold
```

#### 6. Git Branches — `~/.local/bin/devdeck-branches`

```zsh
#!/usr/bin/env zsh
# Current branch + upstream first, then other branches by last commit — refreshes every 30s
source ~/.config/devdeck/lib.zsh

short() { print -r -- ${${${${1/ minutes# ago/m ago}/ hours# ago/h ago}/ days# ago/d ago}/ weeks# ago/w ago}; }

tput civis
trap 'tput cnorm; exit' INT TERM
while true; do
  clear
  print
  current=$(git branch --show-current)
  upstream=$(git rev-parse --abbrev-ref '@{u}' 2>/dev/null)
  print -r -- "  ${GREEN}✓ $(pad "$current" 22)${MUTED}${upstream:-—}${RESET}"
  git for-each-ref --sort=-committerdate refs/heads \
      --format='%(refname:short)|%(committerdate:relative)' |
  while IFS='|' read -r name when; do
    [[ $name == $current ]] && continue
    print -r -- "  ${PURPLE}"$''"${RESET} ${WHITE}$(pad "$name" 22)${MUTED}$(short "$when")${RESET}"
  done
  sleep 30
done
```

#### 7. Active Processes — `~/.local/bin/devdeck-procs`

```zsh
#!/usr/bin/env zsh
# Top processes by CPU — refreshes every 3s
source ~/.config/devdeck/lib.zsh

tput civis
trap 'tput cnorm; exit' INT TERM
while true; do
  clear
  printf "\n  ${CYAN}%-8s%-18s%8s%8s${RESET}\n" PID COMMAND 'CPU%' 'MEM%'
  ps -Ao pid=,pcpu=,pmem=,comm= -r | head -n ${1:-6} |
    awk '{pid=$1; cpu=$2; mem=$3; $1=$2=$3=""; sub(/^ +/, ""); n=split($0, p, "/");
          printf "  %-8s%-18.17s%8.1f%8.1f\n", pid, p[n], cpu, mem}'
  sleep 3
done
```

#### 8. Make Them Executable

```bash
chmod +x ~/.local/bin/devdeck-*
```

---

<a id="step-8-seed-the-backend-repository"></a>
### Step 8 · Scaffold the Workspace & Seed the Backend Repository

Create the `~/workspace` map shown in the sidebar:

```bash
mkdir -p ~/workspace/{projects/{frontend,backend/api,ai/ml-project,mobile/app,experiments/sandbox},labs/{linux,docker,databases,networking},scripts/{bash,python,automation},configs/{zsh,git,terminal},docs/{notes,cheatsheets},archive/old-projects}
```

Seed the backend repo with a local `origin`, the four branches from the **git-branches** pane, and the two modified files from the **main** pane:

```zsh
BE=~/workspace/projects/backend
cd $BE && git init -b main
mkdir -p src/{controllers,routes}

cat > src/controllers/userController.js <<'EOF'
export const getUsers = (req, res) => res.json([]);
EOF

cat > src/routes/userRoutes.js <<'EOF'
import { Router } from 'express';
import { getUsers } from '../controllers/userController.js';

export const router = Router().get('/users', getUsers);
EOF

cat > api/main.py <<'EOF'
from fastapi import FastAPI

app = FastAPI()


@app.get("/health")
def health():
    return {"status": "ok"}
EOF

cat > api/Dockerfile <<'EOF'
FROM python:3.12-slim
WORKDIR /app
RUN pip install --no-cache-dir fastapi "uvicorn[standard]"
COPY main.py .
CMD ["uvicorn", "main:app", "--reload", "--host", "0.0.0.0", "--port", "8000"]
EOF

git add -A && git commit -m "feat: users endpoint and health API"

# local "origin" so git status can report "up to date with 'origin/main'"
git init --bare ~/.devdeck/remotes/backend.git
git remote add origin ~/.devdeck/remotes/backend.git
git push -u origin main

# feature branches with staggered ages: 2h, 4h, 1d
ago() { print "$(( $(date +%s) - $1 )) +0000"; }
for branch secs in feature/auth 7200 feature/api 14400 bugfix/ui 86400; do
  git switch -q -c $branch
  GIT_AUTHOR_DATE="$(ago $secs)" GIT_COMMITTER_DATE="$(ago $secs)" \
    git commit -q --allow-empty -m "wip: $branch"
  git switch -q main
done

# unstaged changes for the main pane
echo "export const getUser = (req, res) => res.json({ id: req.params.id });" >> src/controllers/userController.js
echo "// TODO: GET /users/:id" >> src/routes/userRoutes.js
```

#### Verify

```bash
git status --short && git branch
```

```text
 M src/controllers/userController.js
 M src/routes/userRoutes.js
  bugfix/ui
  feature/api
  feature/auth
* main
```

---

<a id="step-9-create-the-nextjs-dev-server"></a>
### Step 9 · Create the Next.js Dev Server

> Official Documentation: [Next.js Installation](https://nextjs.org/docs/app/getting-started/installation)

```bash
cd ~/workspace/projects/frontend
npx create-next-app@15 web-app --ts --app --eslint --tailwind --use-npm --yes
cd web-app && echo "NEXT_PUBLIC_API_URL=http://localhost:8000" > .env.local
printf "node_modules\n.next\n" > .dockerignore

cat > Dockerfile <<'EOF'
FROM node:22-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
CMD ["npm", "run", "dev"]
EOF
```

#### Verify

```bash
npm run dev
```

```text
   ▲ Next.js 15.x
   - Local:        http://localhost:3000
   - Network:      http://192.168.1.10:3000
   - Environments: .env.local

 ✓ Starting...
 ✓ Ready in 2.3s
```

Stop it with `Ctrl + C` — the deck starts it in pane 2.

---

<a id="step-10-start-the-containers"></a>
### Step 10 · Start the Containers

> Official Documentation: [Docker Compose](https://docs.docker.com/compose/) · [postgres image](https://hub.docker.com/_/postgres) · [redis image](https://hub.docker.com/_/redis)

```bash
nano ~/workspace/labs/docker/compose.yaml
```

```yaml
# Dev Deck services — the four containers in the docker pane
name: devdeck

services:
  postgres:
    image: postgres:15
    container_name: dev-postgres
    environment:
      POSTGRES_USER: dev
      POSTGRES_PASSWORD: devdeck
      POSTGRES_DB: devdb
    ports: ["5432:5432"]
    volumes: [pgdata:/var/lib/postgresql/data]

  redis:
    image: redis:7
    container_name: dev-redis
    ports: ["6379:6379"]

  backend:
    build: ../../projects/backend/api
    image: backend-api
    container_name: backend
    ports: ["8000:8000"]
    depends_on: [postgres, redis]

  frontend:
    build: ../../projects/frontend/web-app
    image: frontend-web
    container_name: frontend
    ports: ["3001:3000"]    # host 3000 is used by the dev-server pane
    depends_on: [backend]

volumes:
  pgdata:
```

Start Docker Desktop, then:

```bash
up      # docker compose up -d && docker ps
```

> [!NOTE]
> The screenshot shows `frontend` on `3000->3000`. That clashes with the local `npm run dev` in pane 2, so the container maps to host port **3001**. Change it back to `"3000:3000"` if you don't run the dev server locally.

#### Verify

```bash
docker ps --format "table {{.Names}}\t{{.Image}}\t{{.Status}}\t{{.Ports}}"
```

```text
NAMES          IMAGE          STATUS         PORTS
frontend       frontend-web   Up 2 minutes   0.0.0.0:3001->3000/tcp
backend        backend-api    Up 2 minutes   0.0.0.0:8000->8000/tcp
dev-redis      redis:7        Up 2 minutes   0.0.0.0:6379->6379/tcp
dev-postgres   postgres:15    Up 2 minutes   0.0.0.0:5432->5432/tcp
```

---

<a id="step-11-launch-the-deck"></a>
### Step 11 · Launch the Deck

#### 1. The Layout

```text
┌──────────────────────────────────────────────────────────────────────────┐
│ header · devdeck-banner                                                  │
├────────────┬────────────────────────────────────┬────────────────────────┤
│ ~/workspace│ 1: main          git status        │ 2: dev-server          │
│            │                                    │    npm run dev         │
│ devdeck-   ├────────────────────────────────────┴──────┬─────────────────┤
│ sidebar    │ 3: docker        docker ps                │ 4: system       │
│            │                                           │    devdeck-sys  │
│            ├───────────────┬──────────────────┬────────┴─────────────────┤
│            │ 5: project-   │ 6: quick-        │ 7: git-branches          │
│            │    tree       │    commands      ├──────────────────────────┤
│            │    tree -L 2  │                  │ 8: active-processes      │
└────────────┴───────────────┴──────────────────┴──────────────────────────┘
   path ·  branch                    node · python · docker · postgres · redis · clock
```

#### 2. The Launcher — `~/.local/bin/devdeck`

```zsh
#!/usr/bin/env zsh
# Dev Deck — build the ten-pane tmux workspace and attach (re-attaches if it exists)
S=devdeck
WS=$HOME/workspace
BE=$WS/projects/backend
FE=$WS/projects/frontend/web-app

tmux has-session -t $S 2>/dev/null && exec tmux attach -t $S

split() { tmux split-window "$@" -P -F '#{pane_id}'; }
title() { tmux select-pane -t $1 -T "$2"; }
run()   { tmux send-keys -t $1 "$2" Enter; }

tmux new-session -d -s $S -n deck -c $WS -x $(tput cols) -y $(tput lines)
hdr=$(tmux display -p -t $S '#{pane_id}')

# header on top, sidebar + grid below
side=$(split -v -t $hdr -c $WS)
tmux resize-pane -t $hdr -y 8

# three rows on the right
main=$(split -h -t $side -l 80% -c $BE)
docker=$(split -v -t $main -l 66% -c $WS)
ptree=$(split -v -t $docker -l 55% -c $WS)

# columns inside each row
dev=$(split -h -t $main -l 40% -c $FE)
sys=$(split -h -t $docker -l 25% -c $WS)
cheats=$(split -h -t $ptree -l 72% -c $WS)
branches=$(split -h -t $cheats -l 52% -c $BE)
procs=$(split -v -t $branches -l 55% -c $WS)

title $hdr      header;                run $hdr      devdeck-banner
title $side     '~/workspace';         run $side     devdeck-sidebar
title $main     '1: main';             run $main     'git status'
title $dev      '2: dev-server';       run $dev      'npm run dev'
title $docker   '3: docker';           run $docker   'docker ps'
title $sys      '4: system';           run $sys      devdeck-sys
title $ptree    '5: project-tree';     run $ptree    'tree -L 2'
title $cheats   '6: quick-commands';   run $cheats   devdeck-cheats
title $branches '7: git-branches';     run $branches devdeck-branches
title $procs    '8: active-processes'; run $procs    devdeck-procs

tmux select-pane -t $main
exec tmux attach -t $S
```

```bash
chmod +x ~/.local/bin/devdeck
```

#### 3. Launch

Open a new iTerm2 window with the **DevDeck** profile (`⌘ O` → DevDeck), or run it from any shell:

```bash
devdeck
```

| Keys | Action |
| :--- | :--- |
| `⌥ ← → ↑ ↓` | Move between panes |
| Mouse click / scroll | Focus a pane / scroll its history |
| `Ctrl + B` then `z` | Zoom the current pane full-screen (again to restore) |
| `Ctrl + B` then `T` | Rename the current pane's title |
| `Ctrl + B` then `d` | Detach — `devdeck` re-attaches later |
| `Ctrl + B` then `r` | Reload `~/.tmux.conf` |
| `tmux kill-session -t devdeck` | Tear the deck down and rebuild it from scratch |

> [!TIP]
> Panes 4, 7, and 8 refresh on their own; press `Ctrl + C` to get a prompt. The header, sidebar, and quick-commands panes return to a prompt on any key.

---

<a id="step-12-back-up-the-config"></a>
### Step 12 · Keep Your Config in the Workspace

Copy the deck's config into `~/workspace/configs` so it travels with your dotfiles:

```bash
cp ~/.zshrc                       ~/workspace/configs/zsh/zshrc
cp ~/.p10k.zsh                    ~/workspace/configs/zsh/p10k.zsh
cp ~/.tmux.conf                   ~/workspace/configs/terminal/tmux.conf
cp ~/.config/devdeck/lib.zsh      ~/workspace/configs/terminal/
cp ~/.local/bin/devdeck*          ~/workspace/configs/terminal/
cp ~/Library/Application\ Support/iTerm2/DynamicProfiles/devdeck.json ~/workspace/configs/terminal/
```

---

<a id="verification-checklist"></a>
## 🔍 Verification Checklist

- [ ] **iTerm2 Profile Loaded**
  ```bash
  ls ~/Library/Application\ Support/iTerm2/DynamicProfiles/
  ```
  *Expected: `devdeck.json`, and **DevDeck** listed under iTerm2 → Profiles.*

- [ ] **tmux 3.4+**
  ```bash
  tmux -V
  ```
  *Expected: `tmux 3.4` or later*

- [ ] **Powerlevel10k Prompt**
  ```bash
  echo $ZSH_THEME
  ```
  *Expected: `powerlevel10k/powerlevel10k`*

- [ ] **Runtimes on PATH**
  ```bash
  node -v && python3 -V && psql --version && redis-cli --version
  ```
  *Expected: `v22.x`, `Python 3.12.x`, `psql (PostgreSQL) 1x.x`, `redis-cli 7.x`*

- [ ] **Nerd Font Glyphs**
  ```bash
  echo -e "     "
  ```
  *Expected: branch, Node, Python, Docker, Postgres, and Redis icons — no empty boxes.*

- [ ] **Containers Running**
  ```bash
  docker ps --format '{{.Names}}'
  ```
  *Expected: `dev-postgres`, `dev-redis`, `backend`, `frontend`*

- [ ] **Deck Builds**
  ```bash
  devdeck
  ```
  *Expected: the header, sidebar, and eight numbered panes from the screenshot.*

---

<a id="troubleshooting"></a>
## 🛠️ Troubleshooting

<details>
<summary><b>🔲 Icons render as boxes or question marks</b></summary>

<br />

1. Confirm the font is installed: `brew list --cask font-jetbrains-mono-nerd-font`.
2. In **Settings → Profiles → DevDeck → Text**, pick **JetBrainsMono Nerd Font Mono** by hand if the dynamic profile's font name did not match.
3. Turn off **Use a different font for non-ASCII text** in the same tab.

</details>

<details>
<summary><b>🏷️ Pane titles change to the hostname or command</b></summary>

<br />

1. Check `tmux -V` is **3.4+** — older versions don't have `allow-set-title`.
2. Make sure `DISABLE_AUTO_TITLE="true"` is set in `~/.zshrc` *before* `source $ZSH/oh-my-zsh.sh`.
3. Rename a pane by hand with `Ctrl + B` then `T`.

</details>

<details>
<summary><b>🎨 Colours look washed out inside tmux</b></summary>

<br />

Truecolor must reach tmux. Check:

```bash
tmux info | grep -E 'RGB|Tc'
```

If nothing shows `true`, confirm iTerm2's **Profiles → Terminal → Report terminal type** is `xterm-256color`, then run `tmux kill-server` and start the deck again.

</details>

<details>
<summary><b>🐳 Docker pane says "Cannot connect to the Docker daemon"</b></summary>

<br />

Start Docker Desktop (or OrbStack), wait for it to finish booting, then in the docker pane run:

```bash
up
```

</details>

<details>
<summary><b>🌐 <code>npm run dev</code> says port 3000 is in use</b></summary>

<br />

Something else owns port 3000 — usually the `frontend` container mapped to `3000:3000`. Find it:

```bash
lsof -i :3000
```

Keep the container on `3001:3000` as in [Step 10](#step-10-start-the-containers), or stop it with `docker stop frontend`.

</details>

<details>
<summary><b>📐 Panes are squashed or the layout looks off</b></summary>

<br />

The layout is sized from the window when the session is created. Maximise the iTerm2 window first, then rebuild:

```bash
tmux kill-session -t devdeck && devdeck
```

</details>

<details>
<summary><b>🚨 Broken <code>~/.zshrc</code></b></summary>

<br />

```bash
cp ~/.zshrc.backup ~/.zshrc && exec zsh
```

Or restore the Dev Deck copy kept in the workspace:

```bash
cp ~/workspace/configs/zsh/zshrc ~/.zshrc && exec zsh
```

</details>

---

<a id="official-documentation"></a>
## 📚 Official Documentation & References

| Technology | Project Links | Documentation & Guides |
| :--- | :--- | :--- |
| **iTerm2** | [iterm2.com](https://iterm2.com) | [Documentation](https://iterm2.com/documentation.html) · [Dynamic Profiles](https://iterm2.com/documentation-dynamic-profiles.html) · [Status Bar](https://iterm2.com/documentation-status-bar.html) |
| **tmux** | [tmux/tmux](https://github.com/tmux/tmux) | [Wiki](https://github.com/tmux/tmux/wiki) · [Formats](https://github.com/tmux/tmux/wiki/Formats) · [Manual](https://man.openbsd.org/tmux) |
| **Oh My Zsh** | [ohmyz.sh](https://ohmyz.sh) | [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh) · [Plugins Directory](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins) |
| **Powerlevel10k** | [romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k) | [Configuration](https://github.com/romkatv/powerlevel10k#configuration) · [Fonts](https://github.com/romkatv/powerlevel10k#fonts) |
| **Nerd Fonts** | [nerdfonts.com](https://www.nerdfonts.com) | [Font Downloads](https://www.nerdfonts.com/font-downloads) · [Glyph Cheat Sheet](https://www.nerdfonts.com/cheat-sheet) |
| **eza** | [eza.rocks](https://eza.rocks) | [GitHub Repository](https://github.com/eza-community/eza) |
| **Docker** | [docker.com](https://www.docker.com) | [Docker Desktop for Mac](https://docs.docker.com/desktop/setup/install/mac-install/) · [Compose](https://docs.docker.com/compose/) |
| **Next.js** | [nextjs.org](https://nextjs.org) | [Installation](https://nextjs.org/docs/app/getting-started/installation) |
| **FastAPI** | [fastapi.tiangolo.com](https://fastapi.tiangolo.com) | [Tutorial](https://fastapi.tiangolo.com/tutorial/) |

---

<a id="license"></a>
## 📄 License

This guide is open-source and released under the [MIT License](LICENSE).

<div align="center">

<br />

```text
D E V   D E C K
I T E R M 2   W O R K S P A C E
```

**💻 code · 🔨 build · 🚀 deploy · 🔁 repeat**

*Keep building...* If the deck served you well, leave a ⭐ on GitHub!

</div>
