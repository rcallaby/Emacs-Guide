# Introduction to Emacs Lisp

## Syntax and Data Types

Emacs Lisp is the scripting language used in the Emacs text editor. It is a dialect of the Lisp programming language. In Emacs Lisp, code and data share the same syntax, known as S-expressions (sexps). S-expressions are nested lists, where the first element is usually a function or operator, and subsequent elements are arguments.

### Data Types
1. **Numbers**: Integers and floating-point numbers are supported.
   - Integers: `42`, `-10`
   - Floats: `3.14`, `-0.5`
   
2. **Strings**: Enclosed in double quotes.
   - `"Hello, Emacs!"`
   
3. **Symbols**: Represent variables or function names.
   - `my-variable`, `my-function`
   
4. **Lists**: Basic data structure, used for code and data.
   - `(1 2 3)`, `(add 2 3)`

5. **Booleans**: `t` for true, `nil` for false.

6. **Vectors**: Like lists but accessed differently.
   - `#(1 2 3)`

## Variables, Functions, and Control Structures

### Variables
Variables are used to store and manipulate data. They can be bound using the `setq` function.

```elisp
(setq my-variable 42)
```

### Functions
Functions are blocks of code that perform a specific task. They can take arguments and return values.

```elisp
(defun my-function (arg1 arg2)
  (+ arg1 arg2))
```

### Control Structures
Control structures allow you to control the flow of execution in your code.

- **Conditional Statements**:

```elisp
(if condition
    then-body
  else-body)
```

- **Loops**:

```elisp
(while condition
  body)
```

```elisp
(dolist (element list)
  body)
```

```elisp
(dotimes (var count)
  body)
```

- **Iteration**:

```elisp
(mapcar 'function list)
```

# Writing Emacs Customizations

## Creating Custom Functions and Commands

### Custom Functions
To create a custom function, use the `defun` keyword followed by the function name and its arguments.

```elisp
(defun my-custom-function (arg1 arg2)
  (message "Result: %d" (+ arg1 arg2)))
```

### Custom Commands
Commands are interactive functions that can be called via keybindings.

```elisp
(defun my-custom-command ()
  (interactive)
  (message "This is a custom command!"))
```

To bind a command to a key combination, use the `global-set-key` function:

```elisp
(global-set-key (kbd "C-c m") 'my-custom-command)
```

## Writing Simple Modes and Extensions

Emacs modes are specialized environments tailored for specific tasks (e.g., programming languages). To create a simple mode:

```elisp
(define-derived-mode my-mode prog-mode "My Mode"
  "Major mode for editing My Language files."
  (setq-local comment-start "# ")
  (setq-local comment-end ""))

(add-to-list 'auto-mode-alist '("\\.my\\'" . my-mode))
```

For extensions, you can create separate `.el` files and load them using `load` or `require`:

```elisp
(load "my-extension.el")
```

Remember to replace `"my-extension.el"` with the actual file name.

These are the basics of Emacs Lisp and how to write customizations. With practice, you can build more complex extensions and modes to tailor Emacs to your specific needs.