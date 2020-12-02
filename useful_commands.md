# Useful commands

## Create Brewfile

```console brew bundle dump -f
```

## Install from Brewfile

```console
brew bundle -f=path/to/brewfile
```

## Errors about writing grammar tables when using the black formatter in Jupyterlab

```console
python -c "import black; black.CACHE_DIR.mkdir(parents=True, exist_ok=True)"
```

## Clear outputs of all notebooks recursively

```console
jupyter nbconvert --clear-output **/*.ipynb
```

## Duplicate folder structure without files

```console
rsync -a /path/from/ /path/to/ --include \*/ --exclude \*
```

## Fixed broken venv

```console
# Check what links will be deleted first
find ~/.virtualenvs/my-virtual-env/ -type l
# Remove the symlinks in the virtualenv
find ~/.virtualenvs/my-virtual-env/ -type l -delete
# Recreate symlinks
virtualenv ~/.virtualenvs/my-virtual-env
```

## Setup virtualenvs with pyenv & pipx

```console
pyenv install python_version
pyenv global python_version
# Restart shell
pipx install --python $(which python) virtualenvwrapper
pipx install --python $(which python) virtualenvwrapper
```

## Commands to run after installing from Brewfile
```console
# Configure pipx
pipx ensurepath
# Symlink java sdk
sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
# Poetry + Oh-My-Zsh
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry
# Configure poetry
poetry config virtualenvs.in-project true
```
