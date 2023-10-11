# Table of Contents
- [Introduction](#introduction)
- [Essential Editing Commands in Emacs](#essential-editing-commands-in-emacs)
- [Inserting, Deleting, and Moving Text](#inserting-deleting-and-moving-text)
   - [1. Inserting Text](#1-inserting-text)
   - [2. Deleting Text](#2-deleting-text)
   - [3. Moving Text](#3-moving-text)
   - [4. Copying, Cutting, and Pasting](#4-copying-cutting-and-pasting)
- [Session 4: Searching and Replacing](#session-4-searching-and-replacing)
   - [Exploring Search and Replace in Emacs](#exploring-search-and-replace-in-emacs)
   - [Incremental Search](#incremental-search)
   - [Regular Expressions in Search and Replace](#regular-expressions-in-search-and-replace)

 
# Introduction
## Essential Editing Commands in Emacs

Emacs, a powerful text editor known for its extensibility and versatility, offers a wide array of essential editing commands. In Session 3, we delve into the fundamental operations for manipulating text.

### Inserting, Deleting, and Moving Text

#### 1. **Inserting Text**

   - `i` - Insert text before the cursor.
   - `a` - Append text after the cursor.
   - `o` - Open a new line below the current line and enter insert mode.
   - `O` - Open a new line above the current line and enter insert mode.

#### 2. **Deleting Text**

   - `x` - Delete the character at the cursor.
   - `dd` - Delete the entire line.
   - `D` - Delete from the cursor to the end of the line.
   - `dw` - Delete a word.
   - `d$` - Delete from the cursor to the end of the line.

#### 3. **Moving Text**

   - `h` - Move left (one character).
   - `j` - Move down (one line).
   - `k` - Move up (one line).
   - `l` - Move right (one character).
   - `w` - Move forward by a word.
   - `b` - Move backward by a word.
   - `0` - Move to the beginning of the line.
   - `$` - Move to the end of the line.
   - `gg` - Move to the beginning of the file.
   - `G` - Move to the end of the file.

#### 4. **Copying, Cutting, and Pasting**

   - `yy` - Copy the entire line.
   - `yw` - Copy a word.
   - `dd` - Cut (delete) the entire line.
   - `dw` - Cut (delete) a word.
   - `p` - Paste the copied or cut text after the cursor.
   - `P` - Paste the copied or cut text before the cursor.

# Session 4: Searching and Replacing

## Exploring Search and Replace in Emacs

In Session 4, we delve into the powerful search and replace capabilities of Emacs, providing you with efficient ways to navigate and modify your text.

### Incremental Search

Emacs' incremental search allows you to find text interactively as you type. Simply press `C-s` and start typing your search query. As you type, Emacs narrows down the search results in real-time.

### Regular Expressions in Search and Replace

Emacs supports regular expressions for advanced search and replace operations. This enables you to perform complex pattern matching, making it a valuable tool for manipulating text efficiently.

Remember, mastering these essential editing commands in Emacs will significantly enhance your productivity and efficiency in text editing. Practice and experimentation are key to becoming proficient with these commands. Happy editing!
