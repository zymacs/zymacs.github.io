---
title: 'Modding Alacritty'
thumbnail: "img/alacritty_logo.png"
date:  2026-05-03T20:56:47+03:00
draft: true
tags:
  - ricing
  - configs
categories:
  - linux-setup
---

If something in my surroundings looks too good I can\'t stop thinking
how to make it look better. Maybe its ADHD but that\'s thrown around too much these days its hard to
tell who\'s just making things up. But anyways. I looked into modding my
alacritty terminal just out of curiosity. I have been using it as it was
out of the box for a while. But I felt bored and thought modding it would be
a good pass time.


Here\'s what I learnt.

## Config location

Alacritty configs are placed at one of the following locations
( _organized by order in which alacritty searches for them_ )

``` txt
- $XDG_CONFIG_HOME/alacritty/alacritty.toml
- $XDG_CONFIG_HOME/alacritty.toml
- $HOME/.config/alacritty/alacritty.toml
- $HOME/.alacritty.toml
- /etc/alacritty/alacritty.toml
```

I had none so I had to create one. Turns out installing alacritty does
not auto create a config file.

## The Mods

-   **2 Options for theme configuration**

    1.  Paste your theme-config in a config file at one of the above
        specified locations.
    2.  Installing a package from the AUR.
         -   Install alacritty-theme-git from the aur with `yay -S alacritty-theme-git`.
         -  Add path to your preferred theme to the config section
           general.yaml

           ``` yaml 
             [general]
             import = ["/usr/share/alacritty/themes/your_theme.toml"]
	     
	    ```
            

-   **Fonts** My font looks a bit like its Monospace. `fc-match` says
    its Free Sans. But [alacritty](https://alacritty.org/config-alacritty.html)'s configuration page says its `monospace regular` so I guess thats what it is.
    I like how my font is but it doesn't hurt to know how to
    change it if I ever want to.
    Modifying the following settings should do that job.

    ``` yml
    [font]
    size = 12.0

    [font.bold]
    family = "monospace"
    style = "Bold"

    [font.bold_italic]
    family = "monospace"
    style = "Bold Italic"

    [font.italic]
    family = "monospace"
    style = "Italic"

    [font.normal]
    family = "monospace"
    style = "Regular"
    ```

-   You can find what fonts you have on your system by runnig:

    ``` bash
    $ fc-list : family style
    ```

## Extras

-   I like how my terminal looks and always want to maintain that when I
    ssh into some remote server. I did not know how to make that so. But now I do.
    Here\'s how;

    ``` bash
    infocmp > alacritty.terminfo  # export Alacritty's Terminfo 
    scp alacritty.terminfo user@remote-host:~/  # or any other method to copy to the remote host

    ```

    So in the above bash code, `Infocmp` is a command to get info about your terminal.
    That data is redirected the to the file _alacritty.terminfo_ with the redirection operator `>`.
    `scp`  is then used to copy that file to the server.

    ``` sh
    infocmp | ssh "$user@$host" 'tic -x /dev/stdin'
    ```

## Closing

-   Well, after all that I only changed my default theme to  `Linux.toml`.
    This post will keep getting more mod sections as I add more settings to my config. Meanwhile, you can visit alacritty's config page via the second link provided among the links below.

## Refs and Sources

-   <https://wiki.archlinux.org/title/Alacritty>
-   <https://alacritty.org/config-alacritty.html>