# Table of Contents
- [Emacs: Markers and Bookmarks](#emacs-markers-and-bookmarks)
- [Emacs: Registers and Rectangles](#emacs-registers-and-rectangles)

# Advanced Editing Techniques
---

## Emacs: Markers and Bookmarks

### Setting and Navigating Markers

In Emacs, markers are a powerful way to remember specific positions in a buffer. They allow you to set a point at a certain location and easily return to it later. To set a marker, you can use `C-x r m` (where `C-x r` is the prefix for registering actions) followed by a letter or a number. For example, `C-x r m a` sets a marker at the current point. To return to this marker, you can use `C-x r b a` (or `C-x r ' a` for a single quote prefix).

[<img width="245" alt="screenshot1apcsp" src="https://github.com/AidenW8512/apcsp/assets/146219112/7341c412-b40f-43b6-92b9-2a402626faf1">](url)

### Managing Bookmarks

Bookmarks in Emacs serve as a way to remember specific positions in files, much like bookmarks in a web browser. You can set a bookmark using `C-x r m` followed by `m`, and then provide a name. For instance, `C-x r m m` will prompt you for a bookmark name. To jump to a bookmark, you can use `C-x r b` followed by the bookmark name.

<img width="239" alt="image" src="https://github.com/rcallaby/Emacs-Guide/assets/146219112/ce9c04ae-5ec7-4f37-ba24-a7302ce08cdb">

![](https://github.com/AidenW8512/apcsp/assets/146219112/db006179-cfaa-4f32-b193-f6e4ccce5f67/github-small.png)

---

## Emacs: Registers and Rectangles

### Utilizing Registers for Quick Access

Registers in Emacs are a versatile tool for storing text, positions, or even macros for later use. They're like variables that can hold a wide range of information. To save something to a register, use `C-x r s` followed by a character (e.g., `a`). This saves the current region. To retrieve the content, you can use `C-x r i` followed by the register character.

![image](https://github.com/rcallaby/Emacs-Guide/assets/146219112/73dfc0c5-274f-4794-9e60-5fb7349b2f54)


### Editing Rectangular Regions

Rectangles in Emacs are a powerful way to operate on columns of text rather than entire lines. You can mark a rectangular region by using `C-x SPC` (`C-x` followed by the spacebar) and then navigating with movement keys. Once selected, you can perform various operations like cut, copy, or paste with `C-x r k` (kill rectangle) or `C-x r y` (yank rectangle).

![image](https://github.com/rcallaby/Emacs-Guide/assets/146219112/7eb4ed5b-878c-4f30-a6b8-5400a88f2e32)


---

These features in Emacs provide a high degree of flexibility and efficiency for manipulating text and navigating within files. Mastery of markers, bookmarks, registers, and rectangles can greatly enhance your productivity in Emacs.
