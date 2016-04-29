# How to install pathogen for vim
Pathogen is used to manage your vim 'runtimepath' with ease. It makes it super easy to install plugins and runtime files in their own directories for vim.

## Installation

Install to ``` ~/.vim/autoload/pathogen.vim.```

```
mkdir -p ~/.vim/autoload ~/.vim/bundle && \
curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

## Runtime Path Manipulation

Add this to your vimrc:
```
execute pathogen#infect()
```

Now any plugins you wish to install can be extracted to a subdirectory under ~/.vim/bundle, and they will be added to the 'runtimepath'.
