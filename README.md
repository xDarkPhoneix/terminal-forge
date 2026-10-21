<div align="center">

# ⚡ TERMINAL FORGE

### The Definitive Modern macOS Developer Terminal Guide

_A curated, high-performance, and visually refined developer environment built on macOS, Zsh, Powerlevel10k, and Ghostty / iTerm2._

<br />

[![Platform](<https://img.shields.io/badge/Platform-macOS%20(Apple%20Silicon%20%26%20Intel)-000000?style=for-the-badge&logo=apple&logoColor=white>)](#requirements)
[![Shell](https://img.shields.io/badge/Shell-Zsh%205.9+-f1502f?style=for-the-badge&logo=gnu-bash&logoColor=white)](#step-3-verify-zsh)
[![Framework](https://img.shields.io/badge/Framework-Oh%20My%20Zsh-blueviolet?style=for-the-badge&logo=zsh&logoColor=white)](#step-4-install-oh-my-zsh)
[![Prompt Theme](https://img.shields.io/badge/Theme-Powerlevel10k-38bdf8?style=for-the-badge&logo=powershell&logoColor=white)](#step-6-install-powerlevel10k)
[![Terminal](https://img.shields.io/badge/Terminal-Ghostty%20%7C%20iTerm2-10b981?style=for-the-badge&logo=alacritty&logoColor=white)](#step-2-install-a-terminal-app)
[![License](https://img.shields.io/badge/License-MIT-amber?style=for-the-badge)](#license)

<br />

[🖼️ Design Gallery](#design-gallery) • [⚡ Quick Start](#quick-start) • [🏗️ Architecture](#system-architecture) • [⚖️ Ghostty vs iTerm2](#terminal-selection-ghostty-vs-iterm2) • [📖 Step-by-Step Guide](#step-by-step-installation) • [🔍 Verification](#verification-checklist) • [🛠️ Troubleshooting](#troubleshooting)

<br />

```text
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│  🔴  🟡  🟢   terminal-forge — zsh — 108×28                                                      │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                  │
│   ╭─  macos in ~/Developer/terminal-forge on  main [⇡1] via  v20.12.0 via  v3.12.2          │
│   ╰─❯ git status                                                                                 │
│   On branch main                                                                                 │
│   Your branch is up to date with 'origin/main'.                                                  │
│                                                                                                  │
│   nothing to commit, working tree clean                                                          │
│                                                                                                  │
│   ╭─  macos in ~/Developer/terminal-forge on  main took 12ms                                   │
│   ╰─❯ brew --version && ghostty +version                                                         │
│   Homebrew 4.4.x                                                                                 │
│   Ghostty 1.2.x (Metal GPU-accelerated)                                                          │
│                                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

</div>

---

<a id="design-gallery"></a>

## 🖼️ Design Gallery

Not sure what your terminal should look like? Browse the sample designs below. Click a preview to see it full-size, and if you like one, follow its setup guide to build it yourself.

<table>
  <tr>
    <th align="center">🐉 Dragon Forge</th>
    <th align="center">💻 DevDeck</th>
  </tr>
  <tr>
    <td align="center" width="50%">
      <a href="./Dragon%20Forge%20Terminal%20Command%20Centre.png">
        <img src="./Dragon%20Forge%20Terminal%20Command%20Centre.png" alt="Dragon Forge Terminal Command Centre" width="100%" />
      </a>
    </td>
    <td align="center" width="50%">
      <a href="./DevDeck%20Cyberpunk%20Developer%20Workspace.png">
        <img src="./DevDeck%20Cyberpunk%20Developer%20Workspace.png" alt="DevDeck Cyberpunk Developer Workspace" width="100%" />
      </a>
    </td>
  </tr>
  <tr>
    <td valign="top">
      <i>Build · Learn · Conquer</i><br /><br />
      A dark-fantasy command centre with a dragon-castle background, a jade ASCII dragon, and five Ghostty split panes.<br /><br />
      <b>Stack:</b> Ubuntu · Ghostty · Zsh · Powerlevel10k · JetBrains Mono Nerd Font · eza · Neofetch<br /><br />
      👉 <a href="./DragonForge.md"><b>Set up Dragon Forge</b></a>
    </td>
    <td valign="top">
      <i>Code · Build · Deploy · Repeat</i><br /><br />
      A neon-blue cyberpunk workspace with panes for git, a dev server, Docker containers, system stats, git branches, and quick commands.<br /><br />
      <b>Stack:</b> macOS · iTerm2 · Zsh · VS Code · Node · Python · Docker · Postgres · Redis<br /><br />
      👉 <a href="./DevDeck.md"><b>Set up DevDeck</b></a> 
    </td>
  </tr>
</table>

> [!TIP]
> New to terminal setup? Start with the **step-by-step guide below** to install the base stack (shell, Oh My Zsh, Powerlevel10k, Nerd Font). Then pick a design from the gallery to style it.

---

<a id="system-architecture"></a>

## 🏗️ System Architecture

Terminal Forge assembles an elite, production-grade terminal stack tailored for modern engineering workflows:

| Component                                                              | Layer             | Purpose & Highlights                                                           |
| :--------------------------------------------------------------------- | :---------------- | :----------------------------------------------------------------------------- |
| **[Homebrew](https://brew.sh)**                                        | Package Core      | The standard macOS package manager for CLI utilities and GUI casks.            |
| **[Ghostty](https://ghostty.org)** _(or [iTerm2](https://iterm2.com))_ | Terminal Emulator | GPU-accelerated, lightning-fast native rendering with pristine typography.     |
| **[Zsh](https://www.zsh.org)**                                         | Shell Engine      | macOS native POSIX-compliant default shell with advanced tab completion.       |
| **[Oh My Zsh](https://ohmyz.sh)**                                      | Framework         | Community configuration manager with hundreds of plugins and themes.           |
| **[Powerlevel10k](https://github.com/romkatv/powerlevel10k)**          | Prompt Engine     | Sub-millisecond instant prompt with dynamic git status and glyph support.      |
| **[MesloLGS Nerd Font](https://www.nerdfonts.com)**                    | Typography        | Patched monospace font delivering crisp icons, devicons, and powerline glyphs. |
| **Curated Plugins**                                                    | Productivity      | Contextual aliases, syntax highlighting, and intelligent tab completion.       |

---

<a id="requirements"></a>

## 📋 Requirements

Before getting started, verify you have:

- 💻 **Mac Hardware**: Apple Silicon (`M1/M2/M3/M4`)
- 🍎 **Operating System**: macOS
- 🔑 **Privileges**: Administrator account with `sudo` permissions
- 🌐 **Network**: Stable internet connection for downloading Homebrew casks and Git repositories

> [!NOTE]
> Run each command sequentially in your terminal and press **Return**. Complete every step in order and execute the verification command before advancing to the next stage.

---

<a id="quick-start"></a>

## ⚡ Quick Start

For experienced developers seeking the fast path, here is the complete setup pipeline using **Ghostty**:

```bash
# 1. Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Apple Silicon users: export Homebrew to PATH
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

# 2. Install Terminal Emulator (Ghostty)
brew install --cask ghostty

# 3. Back up existing configuration and install Oh My Zsh
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# 4. Install MesloLGS Nerd Font
brew install --cask font-meslo-lg-nerd-font

# 5. Install Powerlevel10k Theme
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

Activate the theme and starter plugins in `~/.zshrc`:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git macos)
```

Launch a fresh terminal window or run `p10k configure` to step through the visual setup wizard.

---

<a id="terminal-selection-ghostty-vs-iterm2"></a>

## ⚖️ Terminal Selection: Ghostty vs iTerm2

Choose **one** terminal application. Both deliver an exceptional experience, but cater to different philosophies:

| Feature                | 👻 Ghostty _(Recommended)_                       | 🚀 iTerm2                                                |
| :--------------------- | :----------------------------------------------- | :------------------------------------------------------- |
| **Rendering Engine**   | Native Metal GPU acceleration (blazing fast)     | CPU / Metal rendering                                    |
| **Configuration**      | Clean, declarative text file (`config.ghostty`)  | Comprehensive GUI preferences window                     |
| **Resource Footprint** | Ultra-minimal memory footprint                   | Moderate footprint                                       |
| **UI Philosophy**      | Sleek, distraction-free, modern macOS native     | Feature-dense, extensive toolbars & menus                |
| **Best For**           | Developers who value pure speed & dotfile setups | Developers who want deep GUI settings & legacy workflows |

---

<a id="step-by-step-installation"></a>

## 📖 Step-by-Step Installation

<a id="step-1-install-homebrew"></a>

### Step 1 · Install Homebrew

> Official Documentation: [brew.sh](https://brew.sh) · [Installation Guide](https://docs.brew.sh/Installation)

Homebrew is the premier package manager for macOS. It compiles and installs developer tools without requiring manual drag-and-drop downloads.

#### 1. Execute the Installer

Launch **Terminal** (`Applications → Utilities → Terminal`) and paste:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

- Enter your macOS account password when prompted. _(Note: Terminal does not show visual characters while typing passwords)._
- If prompted, accept the installation of the **Xcode Command Line Tools**.

#### 2. Configure PATH (Apple Silicon M-Series)

On Apple Silicon Macs, Homebrew installs to `/opt/homebrew`. Add it to your shell profile:

```bash
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

#### 3. Verify Installation

```bash
brew --version
```

```text
Homebrew 4.x.x
```

---

<a id="step-2-install-a-terminal-app"></a>

### Step 2 · Install a Terminal App

Choose **Option A (Ghostty)** or **Option B (iTerm2)**.

#### Option A: Ghostty _(Recommended)_

> Official Documentation: [ghostty.org](https://ghostty.org) · [Config Guide](https://ghostty.org/docs/config) · [Theme Directory](https://ghostty.org/docs/features/theme)

##### 1. Install via Homebrew

```bash
brew install --cask ghostty
```

_(Alternative: Download the universal `.dmg` installer directly from [ghostty.org/download](https://ghostty.org/download))._

##### 2. Launch Ghostty

```bash
open -a Ghostty
```

##### 3. Configure Appearance

Ghostty uses a clean text configuration file located at:

```text
~/.config/ghostty/config.ghostty
```

_(Or `~/Library/Application Support/com.mitchellh.ghostty/config.ghostty`)_

> [!NOTE]
> Ghostty versions prior to 1.2.3 use a file named `config` instead of `config.ghostty`.

Open the configuration file from Ghostty with `Cmd + ,` or from your shell:

```bash
mkdir -p ~/.config/ghostty && nano ~/.config/ghostty/config.ghostty
```

Add this polished starting configuration:

```ini
# Terminal Forge - Ghostty Configuration
font-family = "MesloLGS Nerd Font"
font-size = 14
theme = "Catppuccin Mocha"
window-padding-x = 12
window-padding-y = 12
window-decoration = true
macos-titlebar-style = transparent
cursor-style = bar
cursor-style-blink = true
```

Discover built-in themes and available fonts:

```bash
ghostty +list-themes
ghostty +list-fonts
```

Press `Cmd + Shift + ,` inside Ghostty at any time to instantly hot-reload configuration changes.

---

#### Option B: iTerm2

> Official Documentation: [iterm2.com](https://iterm2.com) · [Documentation](https://iterm2.com/documentation.html) · [Shell Integration](https://iterm2.com/documentation-shell-integration.html)

##### 1. Install via Homebrew

```bash
brew install --cask iterm2
```

_(Alternative: Download the stable release archive from [iterm2.com/downloads.html](https://iterm2.com/downloads.html))._

##### 2. Launch iTerm2

```bash
open -a iTerm
```

##### 3. Recommended Settings

Open **iTerm2 → Settings…** (`Cmd + ,`) and adjust the following:

| Setting Category    | Recommended Value                | Navigation Path                            |
| :------------------ | :------------------------------- | :----------------------------------------- |
| **Typography**      | `MesloLGS Nerd Font`, Size 14    | **Profiles → Text → Font**                 |
| **Color Preset**    | `Solarized Dark` or `Pastel`     | **Profiles → Colors → Color Presets…**     |
| **Window Geometry** | 100 columns × 30 rows            | **Profiles → Window → Columns / Rows**     |
| **Default Shell**   | Make iTerm2 the default terminal | **iTerm2 menu → Make iTerm2 Default Term** |

> [!TIP]
> From this point forward, run all remaining steps inside your newly installed terminal emulator (**Ghostty** or **iTerm2**).

---

<a id="step-3-verify-zsh"></a>

### Step 3 · Verify Zsh

macOS ships with Zsh as its native default shell. Confirm your active shell:

```bash
echo $SHELL
```

```text
/bin/zsh
```

Inspect the installed version:

```bash
zsh --version
```

```text
zsh 5.9 (arm64-apple-darwin24.0)
```

If your output is not `/bin/zsh`, consult [Zsh is not the default shell](#zsh-is-not-the-default-shell).

---

<a id="step-4-install-oh-my-zsh"></a>

### Step 4 · Install Oh My Zsh

> Official Documentation: [ohmyz.sh](https://ohmyz.sh) · [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh)

Oh My Zsh is an open-source, community-driven framework for managing your Zsh environment, aliases, and functions.

#### 1. Safeguard Existing Configuration

```bash
cp ~/.zshrc ~/.zshrc.backup 2>/dev/null || true
```

#### 2. Run the Official Installer

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

The installer will:

- Clone Oh My Zsh into `~/.oh-my-zsh`
- Archive any prior `~/.zshrc` to `~/.zshrc.pre-oh-my-zsh`
- Initialize a fresh, well-commented `~/.zshrc`

> [!NOTE]
> If your previous config contained custom environmental variables or exports, transfer them from `~/.zshrc.pre-oh-my-zsh` into the new `~/.zshrc`.

#### 3. Verify Structure

```bash
ls ~/.oh-my-zsh
```

Ensure the directory lists `plugins`, `themes`, and `custom`.

---

<a id="step-5-install-a-nerd-font"></a>

### Step 5 · Install a Nerd Font

> Official Documentation: [nerdfonts.com](https://www.nerdfonts.com) · [Powerlevel10k Font Guide](https://github.com/romkatv/powerlevel10k#fonts)

A **Nerd Font** incorporates thousands of developer icons (Git branches, OS badges, programming language symbols) directly into the font's glyph table.

#### 1. Install MesloLGS Nerd Font

```bash
brew install --cask font-meslo-lg-nerd-font
```

> [!TIP]
> If you are using iTerm2, the Powerlevel10k wizard in Step 6 can automatically download and apply MesloLGS NF for you. Ghostty users should install via Homebrew as shown above.

#### 2. Select Font in Ghostty

Add or update the following line in `~/.config/ghostty/config.ghostty`:

```ini
font-family = "MesloLGS Nerd Font"
```

Reload with `Cmd + Shift + ,`.

#### 3. Select Font in iTerm2

1. Open **Settings** (`Cmd + ,`) → **Profiles** → **Text**.
2. Under **Font**, select **MesloLGS Nerd Font** (or **MesloLGS NF**).

#### 4. Test Glyph Rendering

Test if your terminal can render developer glyphs:

```bash
echo -e "  "
```

| Expected Glyph | Representation      |
| :------------: | :------------------ |
|      ``       | Git Branch symbol   |
|      ``       | GitHub Octocat logo |
|      ``       | Apple logo          |

_If you see rectangles, question marks, or broken glyphs, re-check your terminal font preferences._

---

<a id="step-6-install-powerlevel10k"></a>

### Step 6 · Install Powerlevel10k

> Official Documentation: [github.com/romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k)

Powerlevel10k is renowned for its sub-millisecond execution speed, instant prompt capability, and extensive customization options.

#### 1. Clone the Theme Repository

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  "${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k"
```

#### 2. Enable in `~/.zshrc`

Open `~/.zshrc` using your preferred editor:

```bash
nano ~/.zshrc      # Terminal editor (Ctrl+O to save, Ctrl+X to exit)
# or: code ~/.zshrc
```

Find the `ZSH_THEME` assignment and update it:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

#### 3. Launch the Interactive Wizard

Restart Zsh to trigger the interactive setup assistant:

```bash
exec zsh
```

Follow the on-screen visual prompts to pick your preferred aesthetic:

- **Style**: _Pure_, _Classic_, _Rainbow_, or _Lean_
- **Character Set**: _Unicode_
- **Prompt Details**: Time format, head shape, tail shape, line count

To recalibrate your prompt design at any time in the future, simply run:

```bash
p10k configure
```

---

<a id="step-7-enable-plugins"></a>

### Step 7 · Enable Plugins

> Official Documentation: [Oh My Zsh Plugins Directory](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)

Oh My Zsh bundles hundreds of battle-tested plugins. Enable only the plugins you need to preserve ultra-fast shell launch times.

#### 🚀 Recommended Core Plugins

| Plugin   | Capability                      | Example Shortcuts                                                                               |
| :------- | :------------------------------ | :---------------------------------------------------------------------------------------------- |
| `git`    | Git aliases & branch status     | `gst` → `git status`<br>`gco` → `git checkout`<br>`ga` → `git add`<br>`gcmsg` → `git commit -m` |
| `macos`  | Native macOS integrations       | `ofd` → Open current dir in Finder<br>`pfd` → Print Finder path                                 |
| `docker` | Container completions & aliases | `docker <Tab>` tab-completion                                                                   |
| `npm`    | Node package manager shortcuts  | `npmg` → `npm install --global`                                                                 |
| `python` | Python environment helpers      | `py` → `python3`<br>`pyclean` → Remove `__pycache__`                                            |

#### Enable Plugins in `~/.zshrc`

Edit the `plugins=(...)` line in `~/.zshrc`. Ensure entries are separated by **spaces**:

```bash
plugins=(git macos python)
```

Apply the changes immediately:

```bash
source ~/.zshrc
```

#### Verify Active Aliases

```bash
alias gst
```

```text
gst='git status'
```

<details>
<summary><b>🌟 Pro Tip: Supercharge with Community Plugins</b> (Click to expand)</summary>

<br />

Take your terminal to the next level with autosuggestions and fast syntax highlighting:

```bash
# 1. zsh-autosuggestions (Fish-like auto suggestions as you type)
git clone https://github.com/zsh-users/zsh-autosuggestions \
  "${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions"

# 2. zsh-syntax-highlighting (Fish-like syntax validation)
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  "${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting"
```

Then append them to your `plugins=(...)` list in `~/.zshrc`:

```bash
plugins=(git macos python zsh-autosuggestions zsh-syntax-highlighting)
```

</details>

---

<a id="verification-checklist"></a>

## 🔍 Verification Checklist

Ensure every component of your terminal forge is firing on all cylinders:

- [ ] **Homebrew Package Manager**

  ```bash
  brew --version
  ```

  _Expected: `Homebrew 4.x.x`_

- [ ] **Modern Terminal Emulator**
      _Ghostty or iTerm2 launches cleanly with GPU hardware acceleration._

- [ ] **Native Zsh Shell**

  ```bash
  echo $SHELL
  ```

  _Expected: `/bin/zsh`_

- [ ] **Oh My Zsh Framework**

  ```bash
  test -d ~/.oh-my-zsh && echo "Installed"
  ```

  _Expected: `Installed`_

- [ ] **Nerd Font Glyphs**

  ```bash
  echo -e "  "
  ```

  _Expected: Clean branch, GitHub, and Apple icons without missing glyph boxes._

- [ ] **Powerlevel10k Prompt Engine**

  ```bash
  echo $ZSH_THEME
  ```

  _Expected: `powerlevel10k/powerlevel10k`_

- [ ] **Productivity Aliases**
  ```bash
  alias gst
  ```
  _Expected: `gst='git status'`_

---

<a id="troubleshooting"></a>

## 🛠️ Troubleshooting

<a id="command-not-found-brew"></a>

<details>
<summary><b>🔴 <code>command not found: brew</code></b></summary>

<br />

Homebrew's binary directory is missing from your active `PATH`.

On **Apple Silicon** Macs (`M1/M2/M3/M4`), execute:

```bash
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

On **Intel** Macs:

```bash
echo >> ~/.zprofile
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/usr/local/bin/brew shellenv)"
```

</details>

<a id="prompt-icons-show-as-boxes"></a>

<details>
<summary><b>🔲 Prompt icons render as rectangles or question marks</b></summary>

<br />

Your terminal application is not configured to render a Nerd Font:

1. Confirm **MesloLGS Nerd Font** is installed via `brew install --cask font-meslo-lg-nerd-font`.
2. In **Ghostty**: Ensure `font-family = "MesloLGS Nerd Font"` is in `~/.config/ghostty/config.ghostty`.
3. In **iTerm2**: Go to **Profiles → Text → Font** and select **MesloLGS Nerd Font**.
4. Restart your terminal application and execute `p10k configure`.

</details>

<a id="zshrc-changes-do-not-take-effect"></a>

<details>
<summary><b>🔄 <code>~/.zshrc</code> edits do not take effect</b></summary>

<br />

Zsh does not reload dotfiles automatically. Force a refresh in your active session:

```bash
source ~/.zshrc
```

Or start a clean subshell:

```bash
exec zsh
```

</details>

<a id="zsh-is-not-the-default-shell"></a>

<details>
<summary><b>🐚 Zsh is not the default shell</b></summary>

<br />

Verify your current login shell:

```bash
echo $SHELL
```

If it prints `/bin/bash` or another shell, switch to Zsh:

```bash
chsh -s /bin/zsh
```

Enter your macOS password when prompted, then quit and reopen your terminal emulator.

</details>

<a id="prompt-changed-after-oh-my-zsh"></a>

<details>
<summary><b>⚠️ Prompt appearance reset after installing Oh My Zsh</b></summary>

<br />

This is expected behavior. The Oh My Zsh installer initializes a default `~/.zshrc` configured with the `robbyrussell` theme. Your previous setup is saved as `~/.zshrc.pre-oh-my-zsh`. Simply re-apply:

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

</details>

<a id="broken-zshrc"></a>

<details>
<summary><b>🚨 Broken <code>~/.zshrc</code> configuration</b></summary>

<br />

Revert to your pre-install backup:

```bash
cp ~/.zshrc.backup ~/.zshrc && source ~/.zshrc
```

Or restore the pre-Oh My Zsh snapshot:

```bash
cp ~/.zshrc.pre-oh-my-zsh ~/.zshrc && source ~/.zshrc
```

</details>

---

<a id="official-documentation"></a>

## 📚 Official Documentation & References

| Technology        | Project Links                                                     | Documentation & Guides                                                                                                                                                                        |
| :---------------- | :---------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Homebrew**      | [brew.sh](https://brew.sh)                                        | [Installation Guide](https://docs.brew.sh/Installation) · [Formula Directory](https://formulae.brew.sh)                                                                                       |
| **Ghostty**       | [ghostty.org](https://ghostty.org)                                | [Binary Installation](https://ghostty.org/docs/install/binary) · [Configuration Reference](https://ghostty.org/docs/config/reference) · [Theming](https://ghostty.org/docs/features/theme)    |
| **iTerm2**        | [iterm2.com](https://iterm2.com)                                  | [Documentation](https://iterm2.com/documentation.html) · [Settings Reference](https://iterm2.com/documentation-preferences.html) · [Fonts Guide](https://iterm2.com/documentation-fonts.html) |
| **Oh My Zsh**     | [ohmyz.sh](https://ohmyz.sh)                                      | [GitHub Repository](https://github.com/ohmyzsh/ohmyzsh) · [Complete Plugins Directory](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)                                                       |
| **Powerlevel10k** | [romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k) | [Configuration Manual](https://github.com/romkatv/powerlevel10k#configuration) · [Font Installation](https://github.com/romkatv/powerlevel10k#fonts)                                          |
| **Nerd Fonts**    | [nerdfonts.com](https://www.nerdfonts.com)                        | [Font Downloads](https://www.nerdfonts.com/font-downloads) · [Glyph Cheat Sheet](https://www.nerdfonts.com/cheat-sheet)                                                                       |

---

<a id="license"></a>

## 📄 License

This guide is open-source and released under the [MIT License](LICENSE).

<div align="center">

**[Terminal Forge](https://github.com/xDarkPhoneix/terminal-forge)** • Crafted with care for the developer community.

If this guide helped upgrade your daily workflow, consider giving it a ⭐ on GitHub!

</div>
