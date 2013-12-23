# Source for spin-one.org

This repository contains the source/backup for spin-one.org, my personal
webpage. I wanted something transparent and minimalist, taking text files and
metadata and generating a static webpage with little amortized overhead or
fuss.

Some details: 
* The content is written with [Markdown] (http://daringfireball.net/projects/markdown/) 
  with Emacs on OS X.
* Static pages are generated with [Jekyll] (http://jekyllrb.com/).
* Self-hosted on Linode (Ubuntu/Arch Linux) via git and nginx. A post-receive
  hook on the remote server generates the HTML.

The layout (HTML and CSS) is taken entirely from <https://github.com/mojombo/mojombo.github.com>.

As a personal note, you _could_ learn to use [Hakyll] (http://jaspervdj.be/hakyll/),
but it's probably a waste of your time.

