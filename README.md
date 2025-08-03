# HelpfulShellScripts
A collection of most of my personal shell scripts that I find to be very useful. The acronym is pronounced "hiss"... like a snake.

# QuickLinks
 - [githubclone](#githubclone) - I hate typing "https:/<n/>/github.com/"
 - [mkcmd](#mkcmd) - I hate typing "touch ~/bin/command && chmod +x ~/bin/command && nano ~/bin/command"
 - [rmcmd](#rmcmd) - I'm just lazy... and a software dev
 - [countfiles](#countfiles) - A quick way to count files and/or directories either recursively or non-recursively

# Descriptions
## githubclone
```
    Usage: githubclone [-hvy] <username>( |/)<repository> [<destination>]

        -y, --noconfirm  do not ask for any confirmation
        -h, --help       print help document
        -v, --version    print script version

    Examples:
        githubclone -y Electron7-7 HelpfulShellScripts
        githubclone Electron7-7/HelpfulShellScripts ./bin/some_shell_scripts
```
I hate typing "https:/<n/>/github.com/".

Yeah, there's not much more to it than that; I made `githubclone` was because I hate having to type out "https:/<n/>/github.com/" every time I clone a repository. If you want to change the URL (e.g: to Gitlab's URL), I've made it easy to do so by keeping the URL in a variable.

I really recommend aliasing this one to something like `ghc` for pure speed and efficiency.
```
$ git clone https://github.com/Electron7-7/HelpfulShellScripts # Belongs in the trash!

$ githubclone Electron7-7/HelpfulShellScripts # Bold and brash!
$ githubclone Electron7-7 HelpfulShellScripts # Bolder and brasher!
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

## countfiles
```
    Usage: countfiles [-hvrdf] [DIRECTORY]

        -h, --help        print help document
        -v, --version     print script version
        -r, --recursive   include all sub-directories in search
        -d, --directory   count directories (files will not be counted unless "-f" is explicitly specified)
        -f, --files       count files (default behaviour; this flag is only useful in combination with "-d")

    Examples:
        countfiles -r
        countfiles -d ~/Documents

    Notes:
        If no directory is specified, the current working directory is used instead.
```
A quick and easy way to count files and/or directories. You can specify whether you want to count directories, files, or both (files being the default) as well as whether or not to search recursively (searching is non-recursive by default). If no directory is specified, then the current working directory is searched.
