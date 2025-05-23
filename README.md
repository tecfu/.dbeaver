# .dbeaver

DBeaver configuration files

## NOTE

DBeaver saves potentially sensitive information to exported preference files,
including filepaths on your machine (which may contain your name). Be sure to
remove those references or otherwise account for them if you fork this repo and
update them.

## Installation

### dbeaver.ini

- Force DBeaver to use UTC as default timezone (i.e. Postgres)

Append the following to dbeaver.ini:

```
-Duser.timezone=UTC
```

Linux: /usr/share/dbeaver-ce/dbeaver.ini
MacOS: /Applications/DBeaver.app/Contents/Eclipse/dbeaver.ini
Windows: C:\Program Files\DBeaver\dbeaver.ini

### Vrapper Plugin

- Clone this repository into your home directory

- Install [vrapper](https://github.com/vrapper/vrapper) https://github.com/vrapper/vrapper

  - DBeaver > Help > Install New Software > Work with (input field)
  - Enter:
    http://vrapper.sourceforge.net/update-site/stable
  - Trust the signers
  - Wait for the installation to finish

  > See also:
  > https://github.com/dbeaver/dbeaver/issues/8219

- Install the vrapper config from this repository:

  i.e. Given that you cloned this repo to your home directory:

  ```sh
  ln -s ~/.dbeaver/.vrapperrc ~/.vrapperrc
  ```

### Ace Jump Eclipse Plugin

- DBeaver > Help > Install New Software > Work with (input field)
  - Enter:
    http://tobiasmelcher.github.io/acejumpeclipse/
  - Select:
    Acejump for Eclipse
  - Trust the signers
  - Wait for the installation to finish

### Keymap

SCHEME: DBEAVER

- Import `dbeaver-keymap.epf`
DBeaver > File > Import > General > Preferences

> NOTE:
> Some key mappings may not import, for example needed to manually remove
> CTRL+K (findNext) and assign to CTRL+N (see .vrapperrc)
>
> See also:
> https://stackoverflow.com/questions/56561439/dbeaver-how-can-i-export-connection-configuration

### Create keyboard shortcut to open DBeaver

- Linux, XFCE
Keyboard -> Applicatiion Shortcuts -> CTRL+ALT+D
`/usr/share/dbeaver-ce/dbeaver`

## Uninstall

- Linux

```bash
rm -rf ~/.local/share/DBeaverData
rm -rf ~/*workspace6 
rm -rf ~/.eclipse
```

## License

MIT
