# mdm - Minimal Desktop Manager

A properly minimal desktop manager might look like this:

```
#!/bin/sh
set -e
selection=$(cat /usr/share/xsessions/*.desktop | grep -E '^Exec=' | uniq | sed 's/^Exec=//g' | fzf --reverse --header 'Desktop Manager:' --info=hidden)
exec startx $(which $selection)
```

The one here properly parses the `.desktop` files and gives nicer names, but
it's fundamentally the same.

# Dependencies

`python` (3.9+), `fzf`, optionally the `natsort` Python module but it probably
won't make a difference unless the desktop environment names are really weird.

# Installation and Uninstallation

```
# make install
# make uninstall
```

# Usage

Login, run

```
$ mdm
```

and pick a session. The definitions are parsed from whatever is in
`/usr/share/xsessions`.