# Customizing the User Interface

### `Table of contents`

- [Themes and Fonts](#themes-and-fonts)
- [Configuring Window Layout](#configuring-window-layout)
- [Keybindings and Macros](#keybindings-and-macros)
- [Example Customization in `.emacs`](#example-customization-in-emacs)



### Themes and Fonts:

#### Themes:
1. **Installing Themes:**
   - Emacs supports various themes. To install a theme, you can add it to your `.emacs` or `init.el` file.

   ```elisp
   (add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")
   (load-theme 'theme-name t)
   ```

2. **Popular Themes:**
   - Some popular themes include `spacemacs-theme`, `zenburn`, `solarized-theme`, `monokai`, etc.

#### Fonts:
1. **Setting Fonts:**
   - To set a font in Emacs, you can add the following lines to your `.emacs` or `init.el` file:

   ```elisp
   (set-frame-font "font-name")
   ```

   - Replace `"font-name"` with the name of the font you want to use.

2. **Font Customization:**
   - You can customize the font size, weight, and other attributes using `set-face-attribute`:

   ```elisp
   (set-face-attribute 'default nil :height 120)
   ```

### Configuring Window Layout:

#### Splitting Windows:
- `C-x 2`: Split the window horizontally.
- `C-x 3`: Split the window vertically.
- `C-x 0`: Close the current window.

#### Switching Windows:
- `C-x o`: Cycle through windows.
- `C-x 1`: Keep only the current window.

#### Customizing Window Layout:
- You can save and restore window layouts with packages like `winner-mode` and `perspective`.

```elisp
(winner-mode 1)    ; Enable winner mode for window configuration undo/redo.
(perspective-mode) ; Enable perspective mode for saving layouts.
```

### Keybindings and Macros:

#### Customizing Keybindings:

1. **Rebinding Keys:**
   - You can rebind keys using `global-set-key` or `define-key`:

   ```elisp
   (global-set-key (kbd "C-c c") 'some-function)
   ```

   - This example binds `C-c c` to `some-function`.

2. **Keymaps:**
   - Create custom keymaps using `define-key`:

   ```elisp
   (define-key my-keymap (kbd "C-c a") 'another-function)
   ```

   - Load the keymap with `(use-global-map my-keymap)`.

#### Recording and Playing Macros:

1. **Recording Macros:**
   - `F3` to start recording.
   - Perform actions.
   - `F4` to stop recording.

2. **Playing Macros:**
   - `F4` to execute the last defined macro.
   - `C-u <number> F4` to execute a macro `<number>` times.

3. **Saving Macros:**
   - You can save macros in your init file:

   ```elisp
   (fset 'macro-name (kbd "macro-commands"))
   ```

   - Use `M-x insert-kbd-macro` to generate Elisp code for a macro.

### Example Customization in `.emacs`:

```elisp
;; Theme and font
(add-to-list 'custom-theme-load-path "~/.emacs.d/themes/")
(load-theme 'zenburn t)
(set-frame-font "Monospace-12")

;; Window layout
(winner-mode 1)

;; Keybindings
(global-set-key (kbd "C-c c") 'compile)
(define-key my-keymap (kbd "C-c a") 'another-function)
(use-global-map my-keymap)

;; Macros
(fset 'my-macro (kbd "macro-commands"))
```

Remember to replace placeholders like `theme-name`, `font-name`, `macro-commands`, etc., with actual values.

Make sure to back up your configuration files before making changes, and restart Emacs after editing the configuration for the changes to take effect.