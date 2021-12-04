# .dbeaver

DBeaver configuration files

## NOTE:

Dbeaver saves potentially sensitive information to exported preference files,
including filepaths on your machine (which may contain your name). Be sure to
remove those references or otherwise account for them if you fork this repo and
update them.


## Installation


### Vrapper Plugin

- Clone this repository into your home directory


- Install [vrapper](https://github.com/vrapper/vrapper) https://github.com/vrapper/vrapper

  - Dbeaver > Help > Install New Software > Work with (input field)
  - Enter:
    http://download.eclipse.org/mpc/releases/1.9.0
  - Restart Dbeaver
  - Dbeaver > Help > Eclipse Marketplace > Search > Vim > Install

  > See also:
  > https://github.com/dbeaver/dbeaver/issues/8219


  - Install vrapper config
  Symlink the `.vrapperrc` file from this repository into your home directory

    - Linux
    i.e. Given that you cloned this repo to your home directory: 
    ```sh
    ln -s ~/.dbeaver/.vrapperrc ~/.vrapperrc
    ```


### Ace Jump Eclipse Plugin

- Dbeaver > Help > Install New Software > Work with (input field)
  - Enter:
    http://tobiasmelcher.github.io/acejumpeclipse/
  - Select:
    Acejump for Eclipse
  - Restart Dbeaver
  - Dbeaver > Help > Eclipse Marketplace > Search > Vim > Install


### Keymap
SCHEME: DBEAVER

- Import `dbeaver-keymap.epf`
Dbeaver > File > Import > General > Preferences

> NOTE:
> Some key mappings may not import, for example needed to manually remove
> CTRL+K (findNext) and assign to CTRL+N (see .vrapperrc)

> See also: 
> https://stackoverflow.com/questions/56561439/dbeaver-how-can-i-export-connection-configuration


### Create keyboard shortcut to open Dbeaver

- Linux, XFCE 
Keyboard -> Applicatiion Shortcuts -> CTRL+ALT+D
`/usr/share/dbeaver-ce/dbeaver`


## Uninstall

- Linux
```bash
rm -rf ~/.local/share/DBeaverData
rm -rf ~/*.workspace6 
```

## License

MIT
