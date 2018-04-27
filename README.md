# GitAliases

## About
This repository contains some Git aliases that are useful for any project, on any computer.  Our aliases are created with the following goals in mind:
1. Save typing on day-to-day Git commands/options and on common, multi-command workflows
2. Make it easy to predict an alias from the original Git commands/options
3. Stay similar to the original Git commands/options, so that it is easy to remember the original commands/options on machines without these aliases.

We group our aliases into the two following types.

### Shortcut Aliases
These aliases simply abbreviate existing git commands/options to save some typing (e.g., `chb` in place of `checkout --branch`).  They use the following naming conventions:
- One-two letters corresponding to the abbreviated git command (e.g., `a` for `add` or `rb` for `rebase`)
- Each letter thereafter corresponds to an option of that command (e.g., `h` for `--help` or `q` for `--quiet`).  These letters usually match the corresponding single-letter token for that option (e.g., `h` matches `-h`); you'd be suprised what a time-saver it is not to type that hyphen!  For long or multi-word option names, two or more letters may be used (e.g., `sq` for `rebase`'s `--autosquash`).
- The option letters are ordered alphabetically by their *first* letter (e.g., `rebase --quiet --edit-todo` would become `rbetq` because "et" comes before "q")
Several Git commands already have really short names, in which case we only create aliases for those commands with their options.  For example, there is no alias for `git am`, but there is a `git amq` alias for `git am --quiet`.
Here are some of the most common examples that we foresee devs using on a day-to-day basis:
  
  - `i` for `init`
  - `rta` for `remote add`
  - `rtv` for `remote --verbose`
  - `cl` for `clone`
  - `clbr` for `clone --branch`
  - `ch` for `checkout`
  - `chb` for `checkout --branch`
  - `bru` for `branch --set-upstream-to`
  - `brvv` for `branch -vv`
  - `brd` for `branch -d`
  - `s` for `status`
  - `d` for `diff`
  - `a` for `add`
  - `aa` for `add --all`
  - `ap` for `add --patch`
  - `rs` for `reset`
  - `rsh` for `reset --hard`
  - `cm` for `commit`
  - `cmm` for `commit --message`
  - `cma` for `commit --all`
  - `m` for `merge`
  - `rb` for `rebase`
  - `rba` for `rebase --abort`
  - `rbi` for `rebase --interactive`
  - `rv` for `revert`
  - `ps` for `push`
  - `psu` for `push --set-upstream`
  - `pl` for `pull`
  - `pla` for `pull --all` (not to be confused with `plap` for `pull --append`)
  - `plr` for `pull --rebase`
  - `rf` for `reflog`
  - `bl` for `blame`
  - `cfg` for `config --global`

### Extension Aliases

These aliases "extend" the basic Git commands with one more additional commands.  They are meant to expedite common multi-command workflows, like pushing right after committing, stashing before a checkout, staging all changes then running `status`, squash-committing then rebasing, etc.  They're names are generally more cryptic, but generally follow this naming convention:
- First letter is an "x" for "eXtended".  This prevents naming conflicts with other aliases, as there are no Git commands that start with an "x" (and hopefully never will be!)
- Each letter thereafter corresponds to one of the commands or their options.  For example `git xstch` for `git stash save $1; git checkout` then `checkout`, or `xcmrbsq` for `git commit --squash $1; git rebase --autosquash`.  The command letters generally match those used in the Shortcut Aliases.

Some common examples include:

## Usage
The easiest way to use these aliases is to add an `[include]` section to your system `gitconfig` file, located at "C:\Program Files\Git\mingw64\etc\gitconfig" on 64-bit Windows 7, 8, and 10 machines and /etc/gitconfig everywhere else.  The system `gitconfig` is preferable because the aliases will then be useable from every repo on your machine, which is almost always what you want.  Alternatively, you can add the `[include]` section to the global `.gitconfig` in your home directory, or even to a specific repo in its local .git/config file (if you are unfamiliar with Git configuration file locations or syntax, checkout the official [documentation](https://git-scm.com/docs/git-config#_configuration_file)).

Whichever config file you choose to modify, add a line for each set of aliases that you want to include after the `[include]` line:

```
[include]
  path = C:/path/to/GitAliases/{aliases}
  path = C:/path/to/GitAliases/{aliases}
```

Replace `{aliases}` with the actual paths to the aliases in this repo that you want to include.  All paths must be absolute path, not relaive, and must use forward slashes ("/"), even on Windows machines.  All Shortcut Aliases are placed in the [shortcut-aliases](shortcut-aliases/) folder, and all Extension Aliases are placed in the [extension-aliases](extension-aliases/) folder.  Shortcut Alias files are named according to the command that they abbreviate, such as [add](shortcut-aliases/add), [commit](shortcut-aliases/commit), [merge](shortcut-aliases/merge), etc.  The Extension Alias files are more disparate, often with only one alias per file.  So, for example, to include all `checkout` and `rebase` aliases, as well as our Extension Aliases for listing and modifying aliases, you would add the following lines to your chosen Git config:

```
[include]
  path = C:/path/to/GitAliases/shortcut-aliases/checkout
  path = C:/path/to/GitAliases/shortcut-aliases/rebase
  path = C:/path/to/GitAliases/extension-aliases/alias-config
```

Remember, none of the Git aliases in this repository conflict, so you can use as many or as few of them as you like!  Using `[include]` in this way allows you to keep your aliases up-to-date with this repository, and you can easily `[include]` these aliases in as many other Git config files as you want.  Whenever this repository is updated, you can just `git pull` to get the updated aliases in every one of your .gitconfig files, rather than locating the changes and copying/creating them yourself.

For reference, the following lines would include every alias file in this repository into your Git config.  You can just paste this into your Git config, tweak the paths, and remove any lines that you don't want.  (The absolute paths used here are mainly for the benefit of our Danware contributors).
```
[include]
    # SHORTCUT ALIASES
    path = C:/Danware/Other/GitAliases/shortcut-aliases/add
    path = C:/Danware/Other/GitAliases/shortcut-aliases/branch
    path = C:/Danware/Other/GitAliases/shortcut-aliases/checkout
    path = C:/Danware/Other/GitAliases/shortcut-aliases/clone
    path = C:/Danware/Other/GitAliases/shortcut-aliases/commit
    path = C:/Danware/Other/GitAliases/shortcut-aliases/config
    path = C:/Danware/Other/GitAliases/shortcut-aliases/diff
    path = C:/Danware/Other/GitAliases/shortcut-aliases/fetch
    path = C:/Danware/Other/GitAliases/shortcut-aliases/help
    path = C:/Danware/Other/GitAliases/shortcut-aliases/log
    path = C:/Danware/Other/GitAliases/shortcut-aliases/merge
    path = C:/Danware/Other/GitAliases/shortcut-aliases/pull
    path = C:/Danware/Other/GitAliases/shortcut-aliases/push
    path = C:/Danware/Other/GitAliases/shortcut-aliases/rebase
    path = C:/Danware/Other/GitAliases/shortcut-aliases/remote
    path = C:/Danware/Other/GitAliases/shortcut-aliases/reset
    path = C:/Danware/Other/GitAliases/shortcut-aliases/revert
    path = C:/Danware/Other/GitAliases/shortcut-aliases/stash
    path = C:/Danware/Other/GitAliases/shortcut-aliases/status
    path = C:/Danware/Other/GitAliases/shortcut-aliases/tag
    
    # EXTENSION ALIASES
    path = C:/Danware/Other/GitAliases/extension-aliases/add-all-status
    path = C:/Danware/Other/GitAliases/extension-aliases/alias-config
    path = C:/Danware/Other/GitAliases/extension-aliases/checkout-push
    path = C:/Danware/Other/GitAliases/extension-aliases/close-pull-request
    path = C:/Danware/Other/GitAliases/extension-aliases/squash-commit
```

## Contributing
If there are any aliases missing from this repository that you think should be added, please suggest them by opening an [Issue](https://github.com/DanwareCreations/GitAliases/issues/new?title=Add%20Alias%20For%20&lt;insert%20command%20here&gt;).
