# HelpfulShellScripts
A collection of most of my personal shell scripts that I find to be very useful. The acronym is pronounced "hiss"... like a snake.

# QuickLinks
[fastgit](#fastgit)

# Descriptions
## fastgit
```
    Usage: fastgit [-hvy] <command> <username>( |/)<repository> [<destination>]

        -y, --noconfirm  do not ask for any confirmation
        -h, --help       print help document
        -v, --version    print script version

    Examples:
        fastgit -y clone Electron7-7 HelpfulShellScripts
        fastgit clone Electron7-7/HelpfulShellScripts ./bin/some_shell_scripts
```
I hate typing "https://github.com/".

Okay, there's more to it than that, but tbh the main reason I made `fastgit` was because I hate having to type out "https://github.com/" every time I clone a repository. Compare the difference between `git` and `fastgit` and you'll see why I made it:

```
$ git clone https://github.com/Electron7-7/HelpfulShellScripts # Belongs in the trash!

$ fastgit clone Electron7-7/HelpfulShellScripts # Bold and brash!
$ fastgit clone Electron7-7 HelpfulShellScripts # Bolder and brasher!
```
