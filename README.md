# VIM 插件安装命令



```

curl -O https://raw.githubusercontent.com/vince67/v7_config/master/vim.sh

zsh vim.sh

```



# VIM 快捷键解析



GitHub 的教程有详细的教程，但是此处我就写点最常用的。

以下命令都是在命令模式下执行，不是转移模式

,e 默认打开文件 打开之后可以输入文件名进行模糊匹配

,g 在当前文件中进行查找模糊符号 （类，方法，变量，函数)，如果输入 “user” 就会查询User类的介绍，此处与 ,f 不同， “,f” 用来查找模糊文本，更具与普遍性。

,f 在所有文本上进行模糊的文本查找。

,m 为最近使用过的文件模糊查找器。

F4 查看当前文件的类，函数，方法等，并在按下ENTER时进行跳转。

更好的文件浏览器，切换F3，或使用您选择的当前文件打开它,t
使用当前文件保存为sudo:w!!

“shift v “ + “ shift g “ + “ =” 自动格式化代码(自动缩进)

\e 查看当前不满足PEP8的警告或者错误

Ctrl + W + H(光标左移)，J(光标下移)，K(光标上移), L(光标右移)，可以从文件浏览器，代码块，代码结构快各个窗口之间来回跳转。

:s /old/new 当前行中找到的第一个old 替换为new
:s /old/new/g 当前行中查找到的所有old 替换为new
:#,# s/old/new/g 行号“#,#”范围内替换所有的old为new
:% s/old/new/g 整个文件范围内替换所有的old为new
:s /old/new/c c命令:将对每个替换动作提示用户进行确认

当写完函数但是不知道函数的参数时:



```

   # coding=utf-8

   

   import os

   os.popen() # 打完括号会自动弹出函数参数提示

   

```

```

 # coding=utf-8

   

   import os

           (cmd, mode="r", buffering=-1)   # 此处为提示

   os.popen()

   import sys                

```

此处使用的vim插件管理器命令是 :PlugeInstall 而不是使用 :BundleInstall



若编写完程序，需要运行时，在 ~/.vimrc 添加如下内容:



```

map <F5> :call CompileRunGcc()<CR>
    func! CompileRunGcc()
        exec "w" 
if &filetype == 'c' 
            exec "!g++ % -o %<"
            exec "!time ./%<"
elseif &filetype == 'cpp'
            exec "!g++ % -o %<"
            exec "!time ./%<"
elseif &filetype == 'java'
            exec "!javac %"
            exec "!time java %<"
elseif &filetype == 'sh'
            :!time bash %
elseif &filetype == 'python'
            exec "!time python %"
elseif &filetype == 'html'
            exec "!firefox % &"
elseif &filetype == 'go'
    "        exec "!go build %<"
            exec "!time go run %"
elseif &filetype == 'mkd'
            exec "!~/.vim/markdown.pl % > %.html &"
            exec "!firefox %.html &"
endif
    endfunc

```



可以看出无论是java, sh, go 等都可以的使用F5运行。



插件默认带的有行号，取消命令:

```

:set nonumber

```



# 设置 Ctrl + S 保存文件



Vim 默认 Ctrl + s是挂起终端， Ctrl + q 是恢复，但是一般情况下功能我们是没有用的。所以我们把它替换掉。



所有在 ~/.zshrc 或者 ~/.bashrc 中添加一行



```

 stty -ixon

```



在 ~/.vimrc 添加如下内容:



```

nmap <C-S> :update<CR>
437 vmap <C-S> <C-C>:update<CR>
438 imap <C-S> <C-O>:update<CR>

```



接下来就可以使用Ctrl + S 保存文件了



# VIM 多行注释



## 添加多行注释



首页输入 CTRL + V 或者 CTRL + Q 选择 几列作为注释符号添加到位置



然后输入 大写的 i 即 Shift + i 然后输入 注释符号 # 或者 /

然后按下 ESC　即可创建多行注释



## 取消多行注释



CTRL + V 或者 CTRL + Q　选择注释符号所在的列

输入　x 或者　d　即可删除。



# 成品图



![](https://cherrymonth.top:8888/admin/fileadmin/download/ls/vim.png)



# VIM 教程



[VIM教程](http://blog.51cto.com/hashlinux/1761788)
``````````````
