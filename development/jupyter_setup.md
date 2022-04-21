# Jupyter Setup

Yifan Ge

## Install JupyterLab

```bash
conda install "jupyterlab>=3" "ipywidgets>=7.6" 
```

## Install Extensions

```bash
conda install -c conda-forge jupyterlab-lsp python-lsp-server jupyterlab_vim jupyterlab_code_formatter jupyterlab-variableinspector black isort
```

Remember to

1. Check `Auto Close Brackets ` in `Settings`;
2. Set `"continuousHinting": true` in `Code Completion`, `Advanced Settings Editor`, `Settings`.

If `R` is needed:

```bash
conda install -c conda-forge r-languageserver
```

## Attach New Env

### Python

```bash
python -m ipykernel install --user --name ${ENV_NAME}
```

### R

(The following is copied from https://github.com/IRkernel/IRkernel/blob/master/README.md. )

```R
install.packages('IRkernel')
IRkernel::installspec()  # to register the kernel in the current R installation
jupyter labextension install @techrah/text-shortcuts  # for RStudio’s shortcuts
```

Per default `IRkernel::installspec()` will install a kernel with the name “ir” and a display name of “R”. Multiple calls will overwrite the kernel with a kernel spec pointing to the last R interpreter you called that commands from. You can install kernels for multiple versions of R by supplying a `name` and `displayname` argument to the `installspec()` call (You still need to install these packages in all interpreters you want to run as a jupyter kernel!):

```R
# in R 3.3
IRkernel::installspec(name = 'ir33', displayname = 'R 3.3')
# in R 3.2
IRkernel::installspec(name = 'ir32', displayname = 'R 3.2')
```

By default, it installs the kernel per-user.  To install system-wide, use `user = FALSE`.  To install in the `sys.prefix` of the currently detected `jupyter` command line utility, use `sys_prefix = TRUE`.

Now both R versions are available as an R kernel in the notebook.

### Cling

```bash
jupyter kernelspec install ${PREFIX}/share/jupyter/xcpp11 --sys-prefix
jupyter kernelspec install ${PREFIX}/share/jupyter/xcpp14 --sys-prefix
jupyter kernelspec install ${PREFIX}/share/jupyter/xcpp17 --sys-prefix
```



## Cheatsheet

### Jupyter

![](https://blog.ja-ke.tech/assets/jupyterlab-shortcuts/Shortcuts.png)

### Jupyter-Vim

(The following is copied from https://github.com/jwkvam/jupyterlab-vim/blob/master/README.md. )

**Please note that all keys are lowercase unless `Shift` is explicitly indicated.**
For example, `Y, Y` is two lowercase `y`s, `Shift-Y, Y` is one uppercase `Y` followed by a lowercase `y`.

Shortcuts this extension introduces:

### Vim Ex commands

| Command  | Action                     |
| -------- | -------------------------- |
| :w[rite] | Save Notebook              |
| :q[uit]  | Enter Jupyter command mode |

### Vim command bindings

| Chord          | Action                    |
| -------------- | ------------------------- |
| Ctrl-O, U      | Undo Cell Action          |
| -              | Split Cell at Cursor      |
| Ctrl-O, -      | Split Cell at Cursor      |
| Ctrl-O, D      | Cut Cell                  |
| Ctrl-O, Y      | Copy Cell                 |
| Ctrl-O, P      | Paste Cell                |
| Ctrl-Shift-J   | Extend Marked Cells Below |
| Ctrl-Shift-K   | Extend Marked Cells Above |
| Ctrl-O, O      | Insert Cell Below         |
| Ctrl-O, Ctrl-O | Insert Cell Above         |
| Ctrl-J         | Select Cell Below         |
| Ctrl-K         | Select Cell Above         |
| Ctrl-O, G      | Select First Cell         |
| Ctrl-O, Ctrl-G | Select Last Cell          |
| Ctrl-E         | Move Cell Down            |
| Ctrl-Y         | Move Cell Up              |
| Ctrl-O, Z, Z   | Center Cell               |
| Ctrl-G         | Show Tooltip              |
| Command/Ctrl-1 | Code Cell Mode            |
| Command/Ctrl-2 | Markdown Cell Mode        |
| Command/Ctrl-3 | Raw Cell Mode             |
| Shift-Escape   | Leave Vim Mode            |

### Jupyter command bindings

| Chord   | Action            |
| ------- | ----------------- |
| G, G    | Select First Cell |
| Shift-G | Select Last Cell  |
| D, D    | Delete Cell       |
| Y, Y    | Yank (Copy) Cell  |
| P       | Paste Cell        |
| Shift-P | Paste Cell Above  |
| O       | Insert Cell       |
| Shift-O | Insert Cell Above |
| U       | Undo Cell Action  |
| Ctrl-E  | Move Cells Down   |
| Ctrl-Y  | Move Cells Up     |
| Z, Z    | Center Cell       |