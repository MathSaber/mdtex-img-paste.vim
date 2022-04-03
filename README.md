# mdtex-img-paste.vim
Referring to the small modification made by "ferrine/md-img-paste.vim" file, the latex image paste was added to the file.

## 在 plugin/mdip.vim 中添加了如下指令
```vim
" let g:PasteImageFunction = 'g:MarkdownPasteImage'
autocmd FileType markdown let g:PasteImageFunction = 'g:MarkdownPasteImage'
autocmd FileType tex let g:PasteImageFunction = 'g:LatexPasteImage'

function! g:LatexPasteImage(relpath)
    execute "normal! i\\begin{figure}[!htbp]\r\\centering\r\\includegraphics[width=0.6\\textwidth]{" . a:relpath . "}\r\\caption{I"
    let ipos = getcurpos()
    execute "normal! a" . "mage   \\label{fig:" . g:mdip_tmpname[0:] . "} }\r\\end{figure}"
    call setpos('.', ipos)
    execute "normal! ve\<C-g>"
endfunction

```
