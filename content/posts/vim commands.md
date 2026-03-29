---
title: "vim commands"
draft: false
---

## Captalize words in vim i

gUU -> whole line
gU3w -> first 3 words
gUG -> from cursor to whole line


## Some random important command

gf -> jump to the filename
^ -> move back to original file
gv -> jump back to previously selected word
J -> join words downwards. 

## Basic Vim Commands

ZQ -> quite vim without saving any changes
ZZ -> exit vim with saving changes
A  -> go directly in last of the  santance  in insert mode.
I  -> go back to very beginning of the line in insert mode.

## Random Vim Commands

:'<,'>sort -> sort the selected line in alphabetically order.

## Comment out in Vim

:s/^/# -> where # is type of symbol you want to use as Comment
:1,5s/^/# -> This will comment out first 5 lines, for ex in python
:'<,'>s/^/# -> comment out the selected lines.
Ctrl+j to select multiple line

## Deletion in vim 

dw -> delete a word,put the cursor beginning of the word that you want you delete.
d$ -> delete to the end of the line.
D -> do the same as d$ but in shortcut

## Comment and Uncomment in vim

norm I// -> replace '//' with the comment according to add comment to programming language. 
s^//^ -> replace '//' with the comment type to remove the comment.

## Searching the word under the cursor

* -> Place your cursor on the word you want to search then press `*` or `g*`
# -> Same thing as `*` but in backward.

## Find and replace
:%s/foo/bar/gci -> replace `foo` with the text you want to find and `bar` to the text you want to change.









