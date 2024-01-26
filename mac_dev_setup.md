# A recommended dev setup for your mac

## Activate privileges

## Install homebrew

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Install iterm2

From the Hub or from brew:

```sh
brew install --cask iterm2
```

## Install oh-my-zsh

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Both iterm2 and oh-my-zsh can be greatly configured to make your shell experience much nicer!


## Install other goodies from brew

E.g:

```sh
brew install git azure-cli gh graphviz zsh-completions
```

## Install and configure pyenv

```sh
brew install pyenv

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
```

### Install python versions via pyenv
```sh
pyenv install --list | grep ' 3'
pyenv install 3.10.13
pyenv install 3.11.7
```

### Setup global python and setup local pythons in your project folders as required

```sh
pyenv global 3.11.7

cd <some-project>
pyenv local 3.10.13
```

## Install and configure pipx

```sh
brew install pipx
pipx ensurepath
```

## Install and configure poetry 

```sh
pipx install poetry

mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry

poetry config --list
poetry config virtualenvs.in-project true
poetry config virtualenvs.prefer-active-python true
```

## Install and configure virtualenv, virtualenvwrapper
```sh
pipx install --python $(which python) virtualenv virtualenvwrapper
```

And then configure:
```sh
echo 'export WORKON_HOME="$HOME"/.venvs' >> ~/.zshrc
echo 'export VIRTUALENVWRAPPER_PYTHON="$HOME/.local/pipx/venvs/virtualenvwrapper/bin/python"' >> ~/.zshrc
echo `source "$HOME/.local/pipx/venvs/virtualenvwrapper/bin/virtualenvwrapper.sh"` >> ~/.zshrc
# Restart shell
# Now you have access to commands like mkvirtualenv, rmvirtualenv, workon, deactivate
mkvirtualenv -p $(pyenv which python) <name-venv>
workon <name-venv>
```

## Install vscode 

From the hub or from brew:

```sh
brew install --cask visual-studio-code
echo 'export PATH="$PATH:/Applications/Visual Studio Code.app/Contents/Resources/app/bin"' >> ~/.zshrc
git config --global core.editor "code --wait"
```
