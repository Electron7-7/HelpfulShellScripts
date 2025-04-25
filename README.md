# HelpfulShellScripts
A collection of most of my personal shell scripts that I find to be very useful. The acronym is pronounced "hiss"... like a snake.

# QuickLinks
[fastgit](#fastgit)

[mkcmd](#mkcmd)

[rmcmd](#rmcmd)

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

## mkcmd
```
    Usage: mkcmd [-hvn] [-b|--bin <directory>] <command>

        -h, --help        print help document
        -v, --version     print script version
        -n, --no-edit     do not edit file
        -b, --bin=OUTDIR  set the output directory to OUTDIR

    Config:
        mkcmd can be configured with a pre-determined output directory via the
        variable "default_bin_directory". The config file can be either
        $HOME/.mkcmd.conf or $XDG_CONFIG_HOME/mkcmd.conf. As an example, to set
        the default output directory to $HOME/bin, you would write this in the
        config file: default_bin_directory=$HOME/bin

    Examples:
        mkcmd new_command
        mkcmd -n --bin .local/bin new_command_2
```
I hate typing `touch ~/bin/command && chmod +x ~/bin/command && nano ~/bin/command`.

This little guy lets you create shell scripts with ease! By default, `mkcmd` searches for `$HOME/bin` and `$HOME/.local/bin` and if both exist, asks you to select the one you want to use. You can pass the `--bin` flag with an output directory to skip this check, or create a config file at either `$HOME/.mkcmd.conf` or `$HOME/.config/mkcmd.conf` and set `default_bin_directory` to whatever you want! For example, here's my `.mkcmd.conf` file, which sets the default output directory to my `$HOME/bin` folder:
```
default_bin_directory=$HOME/bin
```

## rmcmd
```
    Usage: rmcmd [-hvn] [-b|--bin <directory>] <command>

        -h, --help        print help document
        -v, --version     print script version
        -n, --no-warn     do not prompt before delete
        -b, --bin=OUTDIR  set the search directory to OUTDIR

    Config:
        rmcmd can be configured with a pre-determined search directory via the
        variable "default_bin_directory". The config file is the same as mkcmd,
        either $HOME/.mkcmd.conf or $XDG_CONFIG_HOME/mkcmd.conf. As an example,
        to set the default output directory to $HOME/bin, you would write this
        in the config file: default_bin_directory=$HOME/bin

    Examples:
        rmcmd new_command
        rmcmd -n --bin .local/bin new_command_2
```
The companion to [`mkcmd`](#mkcmd), `rmcmd` simply removes the specified command. It does the same directory check and query that [`mkcmd`](#mkcmd) does, and you can override it with the same flag or config file. There's a confirmation before deleting the file, for safety, that you can skip with the `--no-warn` flag (although, I wouldn't reccomend it)
