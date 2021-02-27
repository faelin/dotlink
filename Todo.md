DOTLINK PROJECT
===
# shim dotfiles
# dynamic linking
# merge with existing

NOTES
---
example dotlink

.dotlink
├── .linkrc
├── .brewfile
├── .default-gems
├── .editorconfig
├── .flake8
├── .gitconfig
├── .p10k.zsh
├── .zshrc
│   ├── .link       << caused dotlink to merge files in this directory and its subdirectories using the parent dirname as a filename
│   ├── flandy.sh
│   └── zsh.local
├── .tmux.conf
└── .zsh-custom
    ├── integrations.zsh
    ├── ssh-autocomplete.zsh
    └── utilities.zsh