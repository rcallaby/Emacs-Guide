# What is Spacemacs?

**Spacemacs** is a community-driven Emacs configuration that combines the power of **Emacs** and the modal editing features of **Vim**, using a concept known as the "**evil mode**." It was created to make Emacs more approachable while still allowing advanced customizations.

* **Website**: [https://www.spacemacs.org](https://www.spacemacs.org)
* **GitHub**: [https://github.com/syl20bnr/spacemacs](https://github.com/syl20bnr/spacemacs)
* **License**: GNU GPL v3

Spacemacs introduces an organized and modular configuration system based on *layers*, each of which bundles configuration for a specific domain or language.

---

## History and Philosophy

* Created by **Sylvain Benner**, also known as `syl20bnr`, around 2015.
* Inspired by the Vim community’s philosophy of mnemonics and composability.
* Seeks to be beginner-friendly without sacrificing power.
* Compared to Doom Emacs, which is minimal and "fast-first", Spacemacs is focused on **community layers** and out-of-the-box functionality.

---

## System Requirements

* Emacs **27.1 or later** (Emacs 29+ recommended).
* Unix-like OS (Linux/macOS) is ideal. Windows is supported, but WSL is preferred.
* Git
* Optional: `ripgrep`, `fd`, and other CLI tools for enhanced search capabilities.

---

## Installation Guide

### Step 1: Install Emacs

**Linux** (Ubuntu/Debian):

```bash
sudo apt install emacs
```

**macOS** (via Homebrew):

```bash
brew install emacs
```

**Windows**:
Download Emacs from [https://www.gnu.org/software/emacs/download.html](https://www.gnu.org/software/emacs/download.html) or use [MSYS2](https://www.msys2.org/) to get a Unix-like shell.

---

### Step 2: Install Spacemacs

```bash
git clone https://github.com/syl20bnr/spacemacs ~/.emacs.d
```

> ⚠️ This will replace any existing Emacs configuration in `~/.emacs.d`.

---

### Step 3: Launch Emacs

```bash
emacs
```

* On first launch, Spacemacs will install all required packages.
* You’ll be prompted to choose:

  * Editing style: **Vim**, **Emacs**, or **Hybrid**
  * Distribution: **Spacemacs** (default) or **Spacemacs-base** (minimal)

---

## Key Features

### Evil Mode (Vim Keybindings)

* Fully embraces **modal editing**.
* `SPC` is the default leader key.
* Example:

  * `SPC f f` → Find file
  * `SPC b b` → Switch buffer
  * `SPC w s` → Split window horizontally

### Layer System

Spacemacs uses layers for modular configuration:

* Example: `html`, `python`, `typescript`, `auto-completion`, `git`, etc.

Enable layers by editing `~/.spacemacs` and adding them to:

```elisp
dotspacemacs-configuration-layers
```

Example:

```elisp
dotspacemacs-configuration-layers
'(
  auto-completion
  emacs-lisp
  git
  markdown
  org
  (python :variables
          python-backend 'lsp
          python-lsp-server 'pyright)
)
```

---

## File Structure Overview

```plaintext
~/.emacs.d/         # Spacemacs itself (cloned repo)
~/.spacemacs        # Your main config file
~/.emacs.d/layers/  # Built-in and custom layers
```

---

## Common Tasks and Usage

### File Navigation

* `SPC f f` → Find file
* `SPC p f` → Find file in project
* `SPC /`   → Search (uses `ripgrep` or `ag`)

### Buffer/Window Management

* `SPC b b` → Switch buffer
* `SPC w s` → Split horizontally
* `SPC w v` → Split vertically
* `SPC w d` → Delete window

### Project Management (via Projectile)

* `SPC p p` → Switch projects
* `SPC p f` → Find file in project

### LSP (Language Server Protocol)

Add language support via LSP in a layer:

```elisp
(python :variables python-backend 'lsp)
```

* `SPC m g g` → Go to definition
* `SPC m r r` → Rename symbol
* `SPC m =` → Format buffer

---

## Updating Spacemacs

```bash
cd ~/.emacs.d
git pull origin develop
```

If you're using the **`develop`** branch (recommended for latest features), keep your config in sync with release notes.

To update packages:

```elisp
SPC f e U
```

---

## Spacemacs vs Doom Emacs

| Feature              | Spacemacs                            | Doom Emacs                       |
| -------------------- | ------------------------------------ | -------------------------------- |
| Philosophy           | Community-driven, batteries-included | Minimalist, fast, manual control |
| Configuration System | Layer-based                          | Module-based                     |
| Startup Time         | Slower                               | Faster                           |
| Default Keybindings  | Vim + Leader (SPC)                   | Vim + Leader (SPC)               |
| Ideal User           | Beginners to Intermediate            | Intermediate to Advanced         |

---

## Advanced Tips

* Use `SPC h d k` to describe keybindings.
* Customize themes with `SPC T s` or in the config.
* Add custom functions in `dotspacemacs/user-config`.
* Use `SPC q r` to reload config.
* Install `use-package` packages manually if needed.

---

## Troubleshooting

* **Missing Packages**: Try `SPC f e R` to reset Spacemacs environment.
* **LSP Not Working**: Ensure the language server is installed in your system.
* **Slow Performance**: Use `Spacemacs-base` distribution or disable heavy layers.

---

## Community and Resources

* **GitHub**: [https://github.com/syl20bnr/spacemacs](https://github.com/syl20bnr/spacemacs)
* **Gitter**: [https://gitter.im/syl20bnr/spacemacs](https://gitter.im/syl20bnr/spacemacs)
* **Reddit**: [/r/spacemacs](https://www.reddit.com/r/spacemacs/)
* **Docs**: [https://develop.spacemacs.org/doc/DOCUMENTATION.html](https://develop.spacemacs.org/doc/DOCUMENTATION.html)

---

## Final Thoughts

Spacemacs is ideal if you:

* Like Vim keybindings.
* Want an organized, modular Emacs configuration.
* Prefer an active community with battle-tested layer configurations.
* Are okay with a larger setup and a slight performance tradeoff in exchange for a polished experience.

# Spacemacs Layers: Full Tutorial

### What is a Layer?

A **layer** in Spacemacs is a self-contained module that organizes configuration, packages, and keybindings for a specific purpose (language, tool, feature).

Each layer typically contains:

* A `packages.el` file for package declarations
* An `extensions.el` (older) or additional logic in `config.el` and `funcs.el`
* Optional files: `keybindings.el`, `config.el`, `funcs.el`, `README.org`

---

## 1. Set Up a Custom Layer Directory

Spacemacs recommends keeping custom layers inside your own `.emacs.d/private` directory (already in `load-path`).

```bash
mkdir -p ~/.emacs.d/private/my-layer-name
cd ~/.emacs.d/private/my-layer-name
```

We'll name this example layer `my-utils`.

---

## 2. Create the Required Files

### Mandatory:

```bash
touch packages.el
```

### Optional (but typical):

```bash
touch config.el
touch funcs.el
touch keybindings.el
touch README.org
```

Your structure now looks like:

```plaintext
~/.emacs.d/private/my-utils/
├── packages.el
├── config.el
├── funcs.el
├── keybindings.el
└── README.org
```

---

## 3. Define Packages in `packages.el`

This is the core file of your layer.

```elisp
(defconst my-utils-packages
  '(
    helpful
    (my-custom-pkg :location local)
  ))

(defun my-utils/init-helpful ()
  (use-package helpful
    :defer t
    :commands (helpful-callable helpful-variable helpful-key)))

(defun my-utils/init-my-custom-pkg ()
  (load "my-custom-pkg.el"))
```

* You list packages in `my-utils-packages`.
* Then define an `init-` function for each.
* `use-package` handles loading and configuration.

---

## 4. Add Custom Configuration in `config.el`

```elisp
;; Custom settings loaded after packages
(setq ring-bell-function 'ignore)
(setq-default fill-column 80)
```

Spacemacs will auto-load this if you add the layer to your config file.

---

## 5. Add Custom Functions in `funcs.el`

```elisp
(defun my-utils/open-init-file ()
  "Quick access to Spacemacs init file."
  (interactive)
  (find-file dotspacemacs-filepath))
```

These can then be bound in keybindings.

---

## 6. Define Keybindings in `keybindings.el`

```elisp
(spacemacs/set-leader-keys
  "ou" 'my-utils/open-init-file)
```

This binds `SPC o u` to your custom function.

---

## 7. Document in `README.org` (optional)

Spacemacs will auto-detect this and display it in the layers list.

Example:

```org
#+TITLE: my-utils layer

This layer provides a few custom Emacs utility functions and tweaks.
```

---

## 8. Enable Your Layer in `~/.spacemacs`

Add `my-utils` to your `dotspacemacs-configuration-layers` list:

```elisp
dotspacemacs-configuration-layers
'(
  auto-completion
  git
  my-utils  ;; 👈 Your custom layer
)
```

Then restart Emacs or `SPC f e R` to reload.

---

## 9. Debugging Tips

* Use `SPC h d v` or `SPC h d f` to inspect variables and functions.
* Check `*Messages*` buffer (`SPC b m`) for errors.
* `SPC f e R` is your friend when updating layers.

---

## Advanced Layer Techniques

* Use `post-init-<pkg>` functions to customize packages from **other layers**.
* Split big layers into submodules or multiple layers.
* Dynamically load parts of config with `:defer`, `:commands`, or `:hook`.

Example: hook `flycheck` in a custom layer

```elisp
(defun my-utils/post-init-flycheck ()
  (add-hook 'prog-mode-hook #'flycheck-mode))
```

---

## Summary

| File             | Purpose                             |
| ---------------- | ----------------------------------- |
| `packages.el`    | Declares and configures packages    |
| `config.el`      | Stores general settings             |
| `funcs.el`       | Stores custom helper functions      |
| `keybindings.el` | Leader key mappings                 |
| `README.org`     | Optional, but helpful documentation |

---

## References

* [Spacemacs Layer Guide](https://develop.spacemacs.org/doc/LAYERS.html)
* [Spacemacs GitHub](https://github.com/syl20bnr/spacemacs)
* [Official Docs](https://develop.spacemacs.org/doc/DOCUMENTATION.html)
* [use-package GitHub](https://github.com/jwiegley/use-package)


