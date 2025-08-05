# HelpfulShellScripts
A collection of most of my personal shell scripts that I find to be very useful. The acronym is pronounced "hiss"... like a snake.

# QuickLinks
 - [githubclone](#githubclone) - I hate typing "https:/<n/>/github.com/"
 - [mkcmd](#mkcmd) - I hate typing "touch ~/bin/command && chmod +x ~/bin/command && nano ~/bin/command"
 - [rmcmd](#rmcmd) - I'm just lazy... and a software dev
 - [countfiles](#countfiles) - A quick way to count files and/or directories either recursively or non-recursively
 - [please](#please) - "*Please* sudo make me a sandwich"
 - [countfiles](#countfiles) - Counts the files and/or directories at any location you choose, recursively or non-recursively
 - [mkheader](#mkheader) - A quick way to generate empty C/C++ header files with header guards

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

## please
```
    Usage: please [-hv] <program> <arguments>

        -h, --help       print help document
        -v, --version    print script version

    Description:
        Used to run a program that interacts with a file/directory (i.e: 'nano', 'rm', 'mkdir', 'git', etc).
        If you don't have sufficient permissions for the file/directory you're trying to access, 'please' will
        automatically re-run the program with 'sudo'.

    Examples:
        please nano /etc/ssh/sshd_config
        please rm /usr/local/bin/something
```
`please` is for those moments where you try to interact with a file/directory, only to find out that you needed to run 'sudo'. Don't you just hate pressing [kbd]Up[/kbd], [kbd]Ctrl[/kbd][kbd]A[/kbd], and typing `sudo`? Don't you just hate seeing "[ File 'somefile' is unwritable ]"? Well, with `please`, you can put all that behind you!

I recommend aliasing the commands you want to use `please` with; for example, I aliased `nano` to be `please nano`.

## countfiles
```
    Usage: countfiles [-hvrdf] [directory]

        -h, --help        print help document
        -v, --version     print script version
        -r, --recursive   include all sub-directories in search
        -d, --directory   count directories (files will not be counted unless "-f" is explicitly specified)
        -f, --files       count files (default behaviour; this flag is only useful in combination with "-d")

    Examples:
        countfiles -r
        countfiles -d ~/Documents

    Notes:
        If either no directory or an invalid directory are specified, the current working directory is used instead.
```

This script exists solely for my amusement. I genuinely forgot why I wrote it; I remember it *had* a purpose other than simply "because I can", but I've forgotten why I needed to recursively count files/folders. My best guess is I was curious to find out how many files were in certain source code folders in a random project and thanks to ADHD, Autism, and free time/will this little guy popped out.

## mkheader
```
    Usage: mkheader [-hv] [-g|--guard <header_guard>] <filename(s)>

        -h, --help              print help document
        -v, --version           print script version
            --force             process duplicate filenames and warn the user instead of exiting
        -g, --guard GUARD       specify the name for the header guard (cannot be used with multiple files)

    Notes:
        When generating multiple files, 'mkheader' will error out if it encounters duplicate filenames. This can
        be overridden with the '--force' flag, although it's not recommended.

    Examples:
        mkheader header_file.hpp another_header_file.h a_weird_header_file another_weird_header_file.headerfile
        mkheader -g PROJECT_FONTS_H fonts.hpp
```

Making new C/C++ header files can be a bit tedious due to having to write out the header guards every time. This is the main reason why lots of people use `#pragma once`, even though it still isn't supported by every compiler. Well, for those old-heads out there (and stubborn autists like me), this script is here to help!

As an example, here's what a file generated by running `mkheader test_file.hpp` would look like:
```C++
#ifndef TEST_FILE_H
#define TEST_FILE_H

#endif // TEST_FILE_H
```

Yup, it even writes that nice little comment there at the end!

If you want to specify your own header guards, you can do so (but only for one file at a time). Here's what a file generated by running `mkheader -g PROJECT_HPP test_file.h` would look like:
```C++
#ifndef PROJECT_HPP
#define PROJECT_HPP

#endif // PROJECT_HPP
```