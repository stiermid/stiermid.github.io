# VIM

I love using vim as a daily editor. That's why I wanted to reach my feasible vim comfort. With the help of Gemini I succesfully got this cheatsheet-ish output:

### 1. Basic Character Movement

| Motion                            | Description                                                   |
| --------------------------------- | ------------------------------------------------------------- |
| `h`                               | Left (similar to ←)                                           |
| `j`                               | Down (similar to ↓)                                           |
| `k`                               | Up (similar to ↑)                                             |
| `l`                               | Right (similar to →)                                          |
| `[`**count**`]` + `h`/`j`/`k`/`l` | Repeat motion **count** times (e.g., `5j` moves down 5 lines) |

### 2. Word & WORD Movement

Vim distinguishes between **word** (`w`, `b`, `e`) and **WORD** (`W`, `B`, `E`).

- A **word** is a sequence of letters, digits, and underscores.
    
- A **WORD** is a sequence of non-blank characters.
    

| Motion        | Description                                                 |
| ------------- | ----------------------------------------------------------- |
| `w`           | Move to the beginning of the **next word**                  |
| `b`           | Move to the beginning of the **previous word**              |
| `e`           | Move to the **end of the current word**                     |
| `ge`          | Move to the **end of the previous word**                    |
| `W`, `B`, `E` | Same as `w`, `b`, `e`, but for a **WORD** (space-separated) |

### 3. Line Movement

| Motion     | Description                                      |
| ---------- | ------------------------------------------------ |
| `0` (zero) | To the beginning of the line                     |
| `^`        | To the first **non-blank** character of the line |
| `$`        | To the end of the line                           |
| `g_`       | To the last **non-blank** character of the line  |
| `          | `                                                |

### 4. Intra-Line Search

These are very fast for navigating within a single line.

| Motion      | Description                                                                       |
| ----------- | --------------------------------------------------------------------------------- |
| `f`**char** | **F**ind the next occurrence of **char** on the line (lands _on_ **char**)        |
| `t`**char** | **T**ill the next occurrence of **char** on the line (lands _before_ **char**)    |
| `F`**char** | **F**ind the previous occurrence of **char** on the line (lands _on_ **char**)    |
| `T`**char** | **T**ill the previous occurrence of **char** on the line (lands _after_ **char**) |
| `;`         | Repeat the last `f`, `t`, `F`, or `T` motion in the **same direction**            |
| `,`         | Repeat the last `f`, `t`, `F`, or `T` motion in the **opposite direction**        |

### 5. Document & Jump Movement

| Motion                                          | Description                                             |
| ----------------------------------------------- | ------------------------------------------------------- |
| `gg`                                            | Go to the **first** line of the file (start)            |
| `G`                                             | Go to the **last** line of the file (end)               |
| `[`**count**`]` + `G` or `[`**count**`]` + `gg` | Go to line **count** (e.g., `50G` or `:50`)             |
| `(`                                             | Jump to the beginning of the **previous sentence**      |
| `)`                                             | Jump to the beginning of the **next sentence**          |
| `{`                                             | Jump to the beginning of the **previous paragraph**     |
| `}`                                             | Jump to the beginning of the **next paragraph**         |
| `H`                                             | Move to the **top** of the screen (High)                |
| `M`                                             | Move to the **middle** of the screen (Middle)           |
| `L`                                             | Move to the **bottom** of the screen (Low)              |
| `%`                                             | Jump to the **matching parenthesis, brace, or bracket** |
| `*` / `#`                                       | Search forward / backward for the word under the cursor |
| `/`**pattern**                                  | Search **forward** for **pattern**                      |
| `?`**pattern**                                  | Search **backward** for **pattern**                     |
| `n` / `N`                                       | Repeat the last search **forward** / **backward**       |

### 6. Scrolling & Viewport

| Motion       | Description                                          |
| ------------ | ---------------------------------------------------- |
| `Ctrl` + `f` | Scroll **f**orward one full screen (page down)       |
| `Ctrl` + `b` | Scroll **b**ackward one full screen (page up)        |
| `Ctrl` + `d` | Scroll **d**own half a screen                        |
| `Ctrl` + `u` | Scroll **u**p half a screen                          |
| `zz`         | Center the current line in the screen                |
| `zt`         | Put the current line at the **t**op of the screen    |
| `zb`         | Put the current line at the **b**ottom of the screen |

### Text Objects

Text objects are a powerful concept that defines a block of text. They are not motions themselves, but are used _with_ operators (e.g., `d`, `c`, `y`) to act on a logical block of text without needing precise movement. The general syntax is `[operator]` + `[i | a]` + `[text object]`.

- `i` = **i**nner (does **not** include surrounding delimiters/whitespace)
- `a` = **a**round (includes surrounding delimiters/whitespace)

| Text Object | Description      | Example Operator Command                            |
| ----------- | ---------------- | --------------------------------------------------- |
| `w`         | Word             | `diw` (delete inner word), `yaw` (yank around word) |
| `p`         | Paragraph        | `cip` (change inner paragraph)                      |
| `s`         | Sentence         | `yas` (yank around sentence)                        |
| `'`         | Single quotes    | `di'` (delete inner single quotes)                  |
| `"`         | Double quotes    | `ci"` (change inner double quotes)                  |
| `(` or `)`  | Parentheses `()` | `da(` (delete around parentheses)                   |
| `{` or `}`  | Braces `{}`      | `ci{` (change inner braces)                         |
| `[` or `]`  | Brackets `[]`    | `yi]` (yank inner brackets)                         |

### Key Concept: [count][operator][motion]

The true power of Vim motions comes from combining them with a count and an operator.
-   Count (optional): A number to repeat the operation.
-   Operator: The action to perform (d, c, y, >, <, =, gU, gu, etc.).
-   Motion: The key or keys that specify where the action should stop.

Examples:

-   `d$` = Delete to the end of the line.
-   `y2w` = Yank (copy) 2 words forward.
-   `cib` = Change inner block (parentheses, braces, or brackets depending on cursor position).
-   `3dd` = Delete 3 dlines.
-   `>}` = Indent from the current line to the next paragraph.
