DOTLINK PROJECT
===
# shim dotfiles through `.env` per-directory config? (dynamic symlinking)
# merge with existing
# combine through source/include where possible
# rollback management
# command-line shortcut to add a named file as a source:
```
$> dotlink add --to='.zshrc' /Users/example/extra_stuff.zsh
	Do you wish to alias, copy, move, or reference the target file '/Users/example/extra_stuff.zsh' [Acmrq]? s
```

NOTES
---
### dotlink example
```
.dotlink
├── .linkrc
├── .brewfile
├── .default-gems
├── .zshrc/
│   ├── .link
│   ├── flandy.zsh
│   ├── extra_files/
│   │   └── personal.sh
│   └── zsh.local
│
└── .zsh-custom/
    ├── integrations.zsh
    ├── ssh-autocomplete.zsh
    └── utilities.zsh
```

* `.link` file causes dotlink to merge files in this directory and its subdirectories using the parent dirname as the target filename
	- can contain optional configuration arguments

```yaml
#.link
---
	target-path: $HOME/.config/
	target-name: .sublimerc
	sources:
		- /Users/example/Desktop/example_source.sh
		- /Users/example/something_else.txt
		- /Users/shared/bad_idea_to_include
```

* `.linkrc` is the master rc file that configures dotlink itself

```yaml
#.linkrc
---
	auto-dot: true	   # add a dot to any non-hidden file when installing to destination
	auto-source: true  # attempt to use "source" or "include" statements where appropriate, instead of concatenating files
	overwrite: true    # replace files found at the intended destination; 'false' causes fatal error if file found at dest
	use-links: true	   # create files locally, symlink to destination
	sort-alpha: true   # false = numeric sort
```
