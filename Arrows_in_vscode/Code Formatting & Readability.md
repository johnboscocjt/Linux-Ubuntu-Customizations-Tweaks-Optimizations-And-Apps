## 💅 Code Formatting & Readability

To keep the code clean and prevent long lines of Tailwind classes from overflowing the screen, use these settings.

### 1. Toggle Word Wrap (Visual Fix)
If a line is too long, you can wrap it visually so it stays within the editor window without adding actual line breaks.
*   **Shortcut:** `Alt` + `Z` (Windows/Linux) or `Opt` + `Z` (Mac).
*   **Setting:** Search for `Editor: Word Wrap` in Settings and set it to `on`.

### 2. Auto-Format on Save
Ensure the project remains consistent by formatting code every time you save.
1. Open **Settings** (`Ctrl` + `,`).
2. Search for `Format On Save`.
3. Check the box for **Editor: Format On Save**.

### 3. Handle Long HTML/Tailwind Lines
To force the formatter to break long lines (like 20+ Tailwind classes) into multiple lines:
1. Search for `HTML: Format: Wrap Line Length` in Settings.
2. Set it to **80** or **100** (characters).
3. Search for `HTML: Format: Wrap Attributes` and set it to **`force-aligned`** or **`expand-multiline`**. This puts each attribute on a new line for better readability.

### 4. Recommended Extensions for this Project
Since we are using **Laravel & Tailwind**, please install:
*   **Laravel Blade Formatter**: Better formatting for `.blade.php` files.
*   **Tailwind CSS IntelliSense**: Autocomplete and class sorting.
*   **Prettier**: The industry standard for consistent code style.
