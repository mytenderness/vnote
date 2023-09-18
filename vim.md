# vim
`do` - Get changes from other window into the current window.
`dp` - Put the changes from current window into the other window.
`]c` - Jump to the next change.
`[c` - Jump to the previous change.
`zo` - Open folded lines.
`zc` - Close folded lines.
`zr` - Unfold both files completely.
`zm` - Fold both files completely.
`Ctrlww` - change window.
`:only | wq` - quit other windows, write and quit.


# gvimdiff 不区分大小写


在 gvimdiff 中不区分大小写的方法与 Vimdiff 相同。您可以通过以下命令来实现：

```bash
:set diffopt+=icase
:set diffopt+=iwhite
:diffupdate
```

这会忽略空格和大小写，并且仅在单词级别上进行比较。


# vim替换
```bash
:%s/foo/bar/g
```