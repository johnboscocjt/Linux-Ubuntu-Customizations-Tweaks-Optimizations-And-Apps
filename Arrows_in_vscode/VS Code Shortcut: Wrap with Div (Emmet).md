## ⌨️ VS Code Shortcut: Wrap with Div (Emmet)

To speed up development in this project, it is highly recommended to set a custom keyboard shortcut for **Emmet: Wrap with Abbreviation**. This allows you to quickly wrap HTML or Blade components in `div` tags or Tailwind classes.

### 1. Set Up the Shortcut
1. Open **Keyboard Shortcuts** (`Ctrl+K Ctrl+S`).
2. Search for: `Emmet: Wrap with Abbreviation`.
3. Double-click it and assign a shortcut (e.g., `Alt+W`).

### 2. How to Use
1. **Highlight** the code block you want to wrap.
2. Press your shortcut (**`Alt+W`**).
3. Type your tag or class in the input box at the top:
   * Type `div` to wrap in a simple `<div>`.
   * Type `.flex.items-center` to wrap in `<div class="flex items-center">`.
   * Type `section#hero` to wrap in `<section id="hero">`.
4. Press **`Enter`**.

### 3. Advanced Wrapping
* **Wrap multiple lines individually:** Use `div*` in the input box to wrap every selected line in its own `<div>`.
* **Blade Components:** You can also wrap in custom components like `x-app-layout`.
