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

  - Linux

    - Dbeaver > Help > Install New Software > Work with input field
    - Enter:
      http://download.eclipse.org/mpc/releases/1.9.0
    - Restart Dbeaver
    - Dbeaver > Help > Eclipse Marketplace > Search > Vim > Install


  > See also:
  > https://github.com/dbeaver/dbeaver/issues/8219


- Install vrapper config
  Symlink the `.vrapperrc` file from this repository into your home directory

  i.e. Given that you cloned this repo to your home directory: 
  ```sh
  ln -s ~/.dbeaver/.vrapperrc ~/.vrapperrc
  ```


### Keymap

  - Import `dbeaver-keymap.epf`
  Dbeaver > File > Import > General > Preferences

  > See also: 
  > https://stackoverflow.com/questions/56561439/dbeaver-how-can-i-export-connection-configuration


### Create keyboard shortcut to open Dbeaver

  - Linux, XFCE 
  Keyboard -> Applicatiion Shortcuts -> CTRL+ALT+D
  `/usr/share/dbeaver-ce/dbeaver`


## License

MIT
