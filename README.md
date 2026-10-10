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
> CTRL+T also has to be unbound by hand for the tab mapping in
> [Tab control](#tab-control-vrapper) to work
>
> See also:
> https://stackoverflow.com/questions/56561439/dbeaver-how-can-i-export-connection-configuration

### Tab control (Vrapper)

`.vrapperrc` maps tab open/close in normal and visual mode only, so insert mode
keeps typing `W` and `CTRL+T` behaves as before:

- `<C-t>` - new SQL script tab (`org.jkiss.dbeaver.core.sql.editor.create`)
- `<S-w>` - close the current tab (`org.eclipse.ui.file.close`, prompts to save)
- `<leader>t` - same as `<C-t>`, without the manual step below
- `<leader>W` - the vim `W` motion, which `<S-w>` takes over

- Unbind DBeaver's own `CTRL+T`, otherwise Eclipse resolves the binding before
  Vrapper ever sees the keystroke and the map never fires:

  - DBeaver > Window > Preferences > User Interface > Keys
  - Search: `Toggle results panel`
  - Select the binding with scheme DBEAVER and context *DBeaver SQL Script*
  - Unbind Command
  - Apply

  > The same applies to any `<C-...>` map in `.vrapperrc`: see the `Incremental`
  > and `Find Next` notes above.

- Restart DBeaver. Vrapper reads `.vrapperrc` at startup, not when the file
  changes; if a key does nothing, check Help > Error Log for a parse error.

> Alternative, no Vrapper involved: bind `CTRL+T` to *New SQL script* and
> `SHIFT+W` to *Close* in Preferences > Keys. Not recommended - those fire in
> insert mode too, so uppercase `W` can no longer be typed in the editor.

### Command mode (`:`)

Vrapper has a real Ex-style command line: press `:` in normal or visual mode, type
a command, Enter. History works (`up`/`down`), Tab completes arguments, and the
built-in subset is `:q[uit]` `:w[all]` `:e[dit]` `:noh` `:set` `:map` `:tabnext`
`:tabnew` `:eclipseuiaction`. It is not full vim Ex, and a mapped command cannot
receive arguments.

`:Rename` comes from this line in `.vrapperrc`:

```vim
eclipseuiaction Rename org.jkiss.dbeaver.ui.editors.sql.rename
```

- `:Rename` Enter, or `<leader>R` in normal/visual mode, renames the script behind
  the current tab: it opens DBeaver's Rename dialog, the same command DBeaver puts
  on `CTRL+F2` in the SQL script editor. Nothing to unbind for it - `CTRL+F2`
  still works, the `:` form is just the vim-style entry point.
- Unlike vim's `:Rename newname` it cannot take the new name inline:
  `eclipseuiaction` fires a command by id and passes no parameters, and vrapper's
  `:command` replays a fixed string with no `<args>` substitution. The dialog is
  the input step.

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
