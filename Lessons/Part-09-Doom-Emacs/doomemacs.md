# Doom Emacs: An Introduction

Doom Emacs is a highly extensible and pre-configured Emacs framework that aims to make Emacs more accessible and user-friendly. In this tutorial, I'll guide you through the process of installing, using, and customizing Doom Emacs.

### Step 1: Installing Doom Emacs

1. **Install Emacs**:
   Make sure you have Emacs installed on your system. You can download it from the official Emacs website: [Download Emacs](https://www.gnu.org/software/emacs/).

2. **Clone Doom Emacs**:
   Open your terminal and run the following command to clone the Doom Emacs repository:
   ```bash
   git clone https://github.com/hlissner/doom-emacs ~/.emacs.d
   ```

3. **Install Dependencies**:
   Depending on your system, you may need to install additional dependencies. Refer to the [official Doom Emacs documentation](https://github.com/doomemacs/doomemacs/blob/master/docs/getting_started.org) for detailed instructions.

4. **Run Doom Emacs**:
   Once the clone is complete, start Emacs by running `emacs` from your terminal.

### Step 2: Getting Familiar with Doom Emacs

1. **Initial Startup**:
   When you first start Doom Emacs, it will perform some initial setup. Wait for it to finish.

2. **Understanding the Leader Key**:
   Doom Emacs uses a leader key (which is customizable, but defaults to `SPC`) to access various commands and functions. For example, `SPC f f` opens a file, and `SPC b b` switches buffers.

3. **Basic Navigation**:
   - Use `Ctrl-g` to quit or cancel any ongoing operation.
   - Use `Ctrl-x Ctrl-f` to find/open a file.
   - Use `Ctrl-x b` to switch buffers.

### Step 3: Customizing Doom Emacs

Doom Emacs is designed to be highly customizable. Here's how you can start customizing it to suit your preferences:

1. **Editing Configuration**:
   Doom Emacs uses a configuration file located at `~/.doom.d/init.el`. This file is where you'll make most of your customizations.

2. **Adding Packages**:
   To add additional packages, open `~/.doom.d/init.el` and look for the `package!` lines. Add any package you want to install there, save the file, and restart Emacs.

   For example, to install the `rainbow-delimiters` package, add the following line:
   ```elisp
   (package! rainbow-delimiters)
   ```

3. **Custom Keybindings**:
   You can define your own keybindings in the `~/.doom.d/config.el` file. For example, to bind `Ctrl-x Ctrl-o` to open the recent files menu, you can add:
   ```elisp
   (global-set-key (kbd "C-x C-o") 'recentf-open-files)
   ```

4. **Themes and Appearance**:
   You can change the theme by customizing the `doom-theme` variable in your `config.el` file. For example:
   ```elisp
   (setq doom-theme 'doom-one)
   ```

5. **Other Customizations**:
   The Doom Emacs documentation provides a wide range of options for customizing your environment. Check the [official documentation](https://github.com/doomemacs/doomemacs/blob/master/docs/getting_started.org) for more details.

### Step 4: Updating Doom Emacs

Doom Emacs is a constantly evolving project. To update Doom Emacs and its packages, you can run the following command in Emacs:

```elisp
M-x doom/update
```

### Conclusion

That's it! You've now installed, configured, and customized Doom Emacs. Remember that this is just a starting point. Feel free to explore the extensive documentation and community resources to further enhance your Emacs experience. Happy coding!