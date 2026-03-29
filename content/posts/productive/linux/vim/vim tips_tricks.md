---
title: "vim tips_tricks"
draft: false
---

# Vim Tips and Tricks

Tags: #vim #motion

- Press `x` to delete word under the cursor.
- Press `gu` to lowercase words, press `gU` to uppercase words
- Press `vit` to select the text in the tag, in this case "Practical Vim" will be selected after running `vit`.

  `<a href="http://pragprog.com/dnvim/">Practical Vim</a>`

- `>G` command increase the indent. 
- `I` start editing on fist char of the line.
- `A` start editing on last char of the line.
- `s` deletes character under cursor then put into insert mode.
- `S` deletes whole line then put into insert mode.
- `;` this command will repeat the last search that the `f{char}` command performed.
- `,` this command will reverse the `f{char}` performed.
- `daw` Deletes the whole word and the white space where cursor is.
- `cw` Deletes a word then insert mode.
- `gcap` Comments the paragraph.
- `gcc` Comments the current line.

`Operator+Motion=Action`

- The `d{motion}` command can operate on a single character `dl`, a complete world `daw`, or an entire paragraph `dap` 
- same goes for `c{motion}` , `y{motion}`. for more info look `:help operator`

### Dictionary

- `[s`  Search for previous incorrect words in paragraph or whole file.
- `]s`  Search for next incorrect words in paragraph or whole file.
- `z=`  List the options for incorrect words and choose the correct one by number.
- `zg`  Add the words in the dictionary, if you think your word is correct.

#### The Dot Command

- for more info read `:h .` docs in vim.
- `.` means "repeat last change"
- The dot command is micro Macro

```js
var foo=1
var bar='0'

var foobar=foo+bar
```

Consider this JavaScript file example, if want semicolon at end of each line then you have to manually do it ,but using `.` operator you can easily do it.
- First on first line, type `A` then `;` and then `<ESC>` combine them its `A;<ESC>`.
  - After using this combination `.` will register it in buffer, then after pressing `.` you can replicate it by pressing `j.`.
  - It's a pretty neat solution for all that manual work.

> The ideal: One keystroke to move, One Keystroke to execute. 

### Insert Mode.

Most's vim commands are provoked in `normal mode` but some commands can be run in `insert mode`. Let's learn about them.
