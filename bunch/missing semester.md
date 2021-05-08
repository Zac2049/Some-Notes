# missing semester

## Shell

1. `date`

2. `echo` word or $PATH

   * absolute path
   * relative path

   `which echo`

3. `pwd`(print working directory)

4. `cd`(change directory)

   `cd ~`(home directory)

   `cd -`(cd to the directory you previously in)

5. dot. (current directory)

   dot dot.. (parent directory)

   ​	e.g. `cd ./home` relative path

6. `--help`

   man(manual pages) word

7. ls(list) -l(long)

   <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200724084740511.png" alt="image-20200724084740511" style="zoom: 67%;" />

   在Linux中第一个字符代表这个文件是目录、文件或链接文件等等。

   - 当为[ **d** ]则是目录
   - 当为[ **-** ]则是文件；
   - 若是[ **l** ]则表示为链接文档(link file)；
   - 若是[ **b** ]则表示为装置文件里面的可供储存的接口设备(可随机存取装置)；
   - 若是[ **c** ]则表示为装置文件里面的串行端口设备，例如键盘、鼠标(一次性读取装置)。

   接下来的字符中，以三个为一组，且均为『rwx』 的三个参数的组合。其中，[ r ]代表可读(read)、[ w ]代表可写(write)、[ x ]代表可执行(execute)。 要注意的是，这三个权限的位置不会改变，如果没有权限，就会出现减号[ - ]而已。

   从左至右用0-9这些数字来表示。

   chown 更改文件属主，也可更改属组

   ```
   chown [–R] 属主名 文件名
   chown [-R] 属主名：属组名 文件名
   ```

   ```
    chmod [-R] xyz 文件或目录
   ```

   各权限的分数对照表如下：

   - r:4
   - w:2
   - x:1

   ![image-20200724090257671](C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200724090257671.png)

8. `mv`(move) [from] [to]

   `cp`(copy) [from] [to]

   `rm`(single file) -r(recursively)

   `rmdir `(remove single directory)

   `mkdir` (make a directory) +"my photos" or my\photos

9. streams

   default input: keyboard

   ​			output: terminal

   `< file `: input

   `> file`: output

   ​		`e.g. echo hello > hello.txt`

10. `cat`(concatenate,print the content of a file)

    `cat < hello.txt > hello2.txt `works like `cp`

    `cat < hello.txt >> hello2.txt`in which >> is to append

11. `|`(pipe, take the output of left, make it the input of right)

    `e.g. ls -l / | tail -n1 > ls.txt`

    it can also manipulate binary image through this

12. `ctrl +L == clear`

13. `sudo`(do as super user)

    root user on Linux, like the administrator user on Windows

14. `echo 1 | sudo tee brightness`

    <img src="C:\Users\zacbi\AppData\Roaming\Typora\typora-user-images\image-20200724094648478.png" alt="image-20200724094648478" style="zoom:50%;" />

## **Shell Tools and Scripting**

1. To assign variables in bash, use the syntax `foo=bar` and access the value of the variable with `$foo`. Note that `foo = bar` will not work since it is interpreted as calling the `foo` program with arguments `=` and `bar`. In general, in shell scripts the space character will perform argument splitting. This behavior can be confusing to use at first, so always check for that.

   Strings in bash can be defined with `'` and `"` delimiters, but they are not equivalent. Strings delimited with `'` are literal strings and will not substitute variable values whereas `"` delimited strings will.

   ```bash
   foo=bar
   echo "$foo"
   # prints bar
   echo '$foo'
   # prints $foo
   ```

2. As with most programming languages, bash supports control flow techniques including `if`, `case`, `while` and `for`. Similarly, `bash` has functions that take arguments and can operate with them. Here is an example of a function that creates a directory and `cd`s into it.

   ```bash
   mcd () {
       mkdir -p "$1"
       cd "$1"
   }
   ```

## Vim

### Inserting text

From Normal mode, press `i` to enter Insert mode. Now, Vim behaves like any other text editor, until you press `<ESC>` to return to Normal mode. This, along with the basics explained above, are all you need to start editing files using Vim (though not particularly efficiently, if you’re spending all your time editing from Insert mode).

### Buffers, tabs, and windows

Vim maintains a set of open files, called “buffers”. A Vim session has a number of tabs, each of which has a number of windows (split panes). Each window shows a single buffer. Unlike other programs you are familiar with, like web browsers, there is not a 1-to-1 correspondence between buffers and windows; windows are merely views. A given buffer may be open in *multiple* windows, even within the same tab. This can be quite handy, for example, to view two different parts of a file at the same time.

By default, Vim opens with a single tab, which contains a single window.

### Command-line

Command mode can be entered by typing `:` in Normal mode. Your cursor will jump to the command line at the bottom of the screen upon pressing `:`. This mode has many functionalities, including opening, saving, and closing files, and [quitting Vim](https://twitter.com/iamdevloper/status/435555976687923200).

- `:q` quit (close window)

- `:w` save (“write”)

- `:wq` save and quit

- `:e {name of file}` open file for editing

- `:ls` show open buffers

- ```plaintext
  :help {topic}
  ```

   

  open help

  - `:help :w` opens help for the `:w` command
  - `:help w` opens help for the `w` movement

### Vim’s interface is a programming language

The most important idea in Vim is that Vim’s interface itself is a programming language. Keystrokes (with mnemonic names) are commands, and these commands *compose*. This enables efficient movement and edits, especially once the commands become muscle memory.

### Movement

You should spend most of your time in Normal mode, using movement commands to navigate the buffer. Movements in Vim are also called “nouns”, because they refer to chunks of text.

- Basic movement: `hjkl` (left, down, up, right)

- Words: `w` (next word), `b` (beginning of word), `e` (end of word)

- Lines: `0` (beginning of line), `^` (first non-blank character), `$` (end of line)

- Screen: `H` (top of screen), `M` (middle of screen), `L` (bottom of screen)

- Scroll: `Ctrl-u` (up), `Ctrl-d` (down)

- File: `gg` (beginning of file), `G` (end of file)

- Line numbers: `:{number}<CR>` or `{number}G` (line {number})

- Misc: `%` (corresponding item)

- Find:

   

  ```plaintext
  f{character}
  ```

  ,

   

  ```plaintext
  t{character}
  ```

  ,

   

  ```plaintext
  F{character}
  ```

  ,

   

  ```plaintext
  T{character}
  ```

  - find/to forward/backward {character} on the current line
  - `,` / `;` for navigating matches

- Search: `/{regex}`, `n` / `N` for navigating matches