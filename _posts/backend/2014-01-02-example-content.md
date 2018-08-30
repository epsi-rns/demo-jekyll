---
layout : post
title  : "A Simple Blog Post Example"
date   : 2014-01-02 12:46:15 +0700
categories: backend
tags   : [reversing, forensic, assembler, cryptography, terminal]
author : epsi

excerpt:
  Using terminal only. 
  What to do on first run and.... 
  Terminal customization is 
  different with desktop customization.

related_link_ids: 
  - 14010735  # My SSG Post
  - 14020635  # My Frontend Post
  - 14020435  # My Backend Post

---

### Preface

> Goal: Share common configuration for terminal customization.

Terminal ricing is different in with desktop ricing.
While in desktop ricing we deal with: window manager, panel, notification
and the most ingredient called wallpaper.
Terminal ricing deal with: shell, prompt, pixel-art,
<kbd>keyboard binding</kbd> and multiplexer.
Terminal ricing along with CLI application, are part of desktop ricing.

	This guidance applied for most distribution.

#### Screenshot

![Terminal for Dummies][image-ss-terminal-customization]{: .img-responsive }


#### Table of Content

There are few parts in terminal ricing:

* Terminal: <code>urxvt</code>, <code>xfce4-terminal</code>, <code>termite</code>

* Shell: <code>bash</code>, <code>zsh</code>, <code>fish</code>

* Shell Prompt: <code>powerline</code>, <code>oh-my-bash</code>, <code>oh-my-zsh</code>, <code>oh-my-fish</code>

* Multiplexer: <code>tmux</code>, <code>gnu screen</code>

* Multiplexer Wrapper: <code>teamocil</code>, <code>byobu</code>

* Compositor Decoration: <code>compton</code>

* Padding Decoration: <code>gtk.css</code>

* Background Decoration: Wallpaper

* Example CLI application: <code>neofetch</code>

* Special CLI application: <code>ViM</code> Text Editor

* Pixel Art

-- -- --

#### Dofiles Source

The dotfiles are available at:

*	[gitlab.com/epsi-rns/dotfiles/tree/master/terminal](https://gitlab.com/epsi-rns/dotfiles/tree/master/terminal)

#### Path

Where to put the config, for each part ?

| Category| Part | Path |
| :--- | :--- | :--- |
| terminal | urxvt  | ~/.Xresources, <br/> ~/.Xdefaults |
| terminal | termite  | ~/.config/termite/config |
| shell | oh-my-bash  | ~/.bashrc |
| shell | oh-my-zsh  | ~/.zshrc |
| shell | powerline  | ~/.config/powerline/*, <br/> ~/.bashrc, <br/> ~/.config/fish/config.fish |
| tiling | tmux | ~/.tmux.conf |
| tiling | teamocil | ~/.teamocil/jekyll.yml |
| decoration | compton | ~/.config/compton.conf |
| decoration | gtk-3.0 | ~/.config/gtk-3.0/gtk.css |
| application | vim | ~/.vim/*, <br/> ~/.vimrc |
| application | neofetch | ~/.config/neofetch/config.conf |

-- -- --

#### teamocil configuration

Teamocil is a simple tool used to automatically
create windows and panes in tmux with YAML files.

I'm using Jekyll for daily basis blogging.
Instead of typing the same command over and over again,
using teamocil can be helpful.

{% highlight yaml %}
windows:
  - name: sample-four-panes
    root: /media/Works/githublab/epsi-rns.github.io
    layout: tiled
    panes:
      - vim -M ./_config.yml
      - jekyll-blog
      - git status
      - exa --long
{% endhighlight %}

| Config | Path |
| :--- | :--- |
| teamocil | ~/.teamocil/jekyll.yml |

This is the configuration:

*	[gitlab.com/.../dotfiles/.../teamocil][dotfiles-teamocil]

-- -- --

### Compositor

> compositor for transparency

You need compositor to enable transparency, shadow and such effects.
There are two known compositor for ricing:

*	[xcompmgr](http://cgit.freedesktop.org/xorg/app/xcompmgr/)

*	[compton](https://github.com/chjj/compton): successor of xcompmgr

Simply run compton to enable it.

{% highlight bash %}
$ compton &
{% endhighlight %}

#### compton configuration

{% highlight conf %}
# Opacity
menu-opacity = 0.9;
#inactive-opacity = 0.7;
frame-opacity = 0.7;
inactive-opacity-override = false;
alpha-step = 0.06;
{% endhighlight %}

| Config | Path |
| :--- | :--- |
| compton | ~/.config/compton.conf |

Source

*	[gitlab.com/.../dotfiles/.../compton][dotfiles-compton]

-- -- --

### gtk.css

Terminal can have padding using [gtk.css](https://developer.gnome.org/gtk3/stable/chap-css-overview.html)
Setting this padding would make your terminal way cooler.
The padding config is as simply as:

{% highlight css %}
VteTerminal, vte-terminal {
	padding: 5px 24px 24px 24px;
}
{% endhighlight %}

| Config | Path |
| :--- | :--- |
| gtk.css | ~/.config/gtk-3.0/gtk.css |

Source

*	[gitlab.com/.../dotfiles/.../gtk.css][dotfiles-gtk-css]

A more complete config can be seen here:

*	[M. Yuga Nugraha](https://github.com/myugan/dotfiles/blob/master/home/.config/gtk-3.0/gtk.css)

-- -- --

### Conclusion

That is all.

Thank you for reading and visiting.


[//]: <> ( -- -- -- links below -- -- -- )
{% assign asset_path = site.baseurl | append: '/assets/posts/backend/2014/01' %}
{% assign dotfiles = 'https://gitlab.com/epsi-rns/dotfiles/tree/master/terminal' %}

[image-ss-terminal-customization]: {{ asset_path }}/tmux-vim-gcc-c-asm.png

[dotfiles-teamocil]:      {{ dotfiles }}/teamocil/jekyll.yml
[dotfiles-compton]:       {{ dotfiles }}/compton/compton.default.conf
[dotfiles-gtk-css]:       {{ dotfiles }}/gtk-3.0/gtk.css

