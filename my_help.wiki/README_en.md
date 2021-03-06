# Name

my_help

# Summary

This gem makes and supplies user specific helps, emulating CUI(CLI) help usage.

# Target
A very novice of learning some specific operation, such as CUI, shell, or emacs,
has difficulty in remembering commands and grammers.
If he has a key, he can easily remember all, but no key brings nothing.
Especially a non-English-native has strong difficulty on the key rememebering.
The problems are,

- man(ual) is English
- man is heavily documented
- On web, search the same key word,
- and read the same URI repeatedly
- memo goes away somewhere...

# Specs

This gem aims to supply own help by gem environment.
Specs are,
- user makes his own help
- supplies a template
  - same format, looks, operation, and hierarchy
- easily see, read
- supplies editing and install commands.

Wiki targets the whole engineer, my_help target the specific person.
Half of the wiki aim should be covered by my_help.
Making own manual is one of the best practices for remembering operations.
Memo applications are good, if you remember the key word.
my_help supplies the key for remembering the word.

# Usage
## Install

Different from the gem standard, fork and clone from Github.
```
github.com:daddygongon/my_help.git
```
The following operations are performed under 'bundle'.
The main reason of this disturbance is due the developer not to know the last command of 'rake install:local' from gem environment.  
But the second reason is the on-going project to collect and supply the good helps for novices.
We are planning to achieve it by using 'pull request' of Github.

Supplied commands are

```
bob%  bundle exec exe/my_help
Usage: my_help [options]
    -v, --version                    show program Version.
    -l, --list                       list specific helps
    -e, --edit NAME                  edit NAME help(eg test_help)
    -i, --init NAME                  initialize NAME help(eg test_help).
    -m, --make                       make executables for all helps.
    -c, --clean                      clean up exe dir.
        --install_local              install local after edit helps
        --delete NAME                delete NAME help
```

At first, see the list of supplied helps by the option of -l.

```
bob%  bundle exec exe/my_help -l
"/usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/daddygongon"
["-l"]
Specific help file:
  emacs_help
  test_help
```
emacs_help, e_h, test_help, t_h are ready to use.
Play them by a command such as 'bundle exec exe/e_h'.

emacsのキーバインド

```
特殊キー操作
  c-f, controlキーを押しながら    'f'
  M-f, escキーを押した後一度離して'f'
    操作の中断c-g, 操作の取り消し(Undo) c-x u
     cc by Shigeto R. Nishitani, 2016
Usage: e_h [options]
    -v, --version                    show program Version.
    -c, --cursor                     Cursor移動
    -e, --編集                         Edit操作
    -f, --ファイル                       File操作
    -q, --終了                         終了操作
    -p, --ページ                        Page移動
    -w, --ウィンドウ                      Window操作
    -b, --バッファ                       Buffer操作
    -m, --mode                       モード切り替え
        --edit                       edit help contents
        --to_hiki                    convert to hikidoc format
        --all                        display all helps
        --store [item]               store [item] in back
        --remove [item]              remove [item] in back
        --add [item]                 add new [item]
```

## Make own help
The next step is making own help.  
For this, -i NAME supplies new NAME help.

```
bob%  bundle exec exe/my_help -i new_help
"/usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/daddygongon"
["-i", "new_help"]
"/usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/daddygongon/new_help"
"/usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/my_help/template_help"
cp /usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/my_help/template_help 
  /usr/local/lib/ruby/gems/2.2.0/gems/my_help-0.2.1/lib/daddygongon/new_help
```
it makes get ready the template of new_help in ~/.my_help directory.
Edit it by -e new_help.
Then -m makes new_help and n_h in exe directory.

## Activate own help (which is automatically done by -m)

For the last step, at the my_help directory, put the commands in as follows:

```
 git add -A
 git commit -m 'add new help'
 rake install:local
```

That's it. You can use the new_help or short command of n_h on CUI.
If not, restart the terminal to load the bin path.
