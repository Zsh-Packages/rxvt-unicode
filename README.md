# rxvt-unicode as a Zsh package

##### Homepage link: [rxvt-unicode](http://dist.schmorp.de/rxvt-unicode/Attic)

| **Package source:** | Source Tarball | Binary | Git | Node | Gem |
|:-------------------:|:--------------:|:------:|:---:|:----:|:---:|
| **Status:**         |    + <br> (default) |  -  | + | – |  –  |

[Zinit](https://github.com/zdharma/zinit) can use the NPM package registry
to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
    - there can be multiple lists of ices,
    - the ice lists are stored in *profiles*; there's at least one profile, *default*,
    - the ices can be selectively overriden.

Example invocation that'll install
[rxvt-unicode](http://dist.schmorp.de/rxvt-unicode/Attic) from the newest source
tarball:

```zsh
# Download, build and install the latest Rxvt Unicode source tarball
zinit pack for rxvt-unicode
```

## Default Profile

Provides the Rxvt-Unicode by compiling and installing it to the `$ZPFX`
directory (`~/.zinit/polaris` by default). It uses the
[zinit-zsh/z-a-as-monitor](https://github.com/zinit-zsh/z-a-as-monitor) annex to
download the latest Rxvt-Unicode source tarball.

The Zinit command executed will be equivalent to:

```zsh
zinit ice id-as"rxvt-unicode" as"null|monitor" lucid \
    mv"%ID% → pkg.tbz2" \
    atclone'ziextract --move pkg.tbz2; m {nl}{msg2}Building \
        {obj}Rxvt-Unicode{msg2}...{rst}{nl}; \
        ./configure --prefix='\''$ZPFX'\'' --enable-everything \
            --enable-256-color >/dev/null && make >/dev/null && \
        m {nl}{msg2}Installing {obj}Rxvt-Unicode{msg2} to \
            >$ZPFX...{rst}{nl} && make install >/dev/null && \
        m {nl}{success}Installation of >Rxvt-Unicode succeeded.{rst} || \
        m {nl}{ehi}Installation of Rxvt-Unicode failed.{rst}' \
    atpull"%atclone" nocompile is-snippet \
    dlink'!rxvt-unicode-%VERSION%.tar.bz2' for \
        http://dist.schmorp.de/rxvt-unicode/Attic
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->
