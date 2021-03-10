# GitAliases

## About

This repository contains some Git aliases that are useful for any project, on any computer.  These aliases are created with the following goals in mind:

1. Save typing on day-to-day Git commands/options and on common, multi-command workflows
2. Make it easy to predict an alias from the original Git commands/options, so that learning these aliases doesn't feel like re-learning the Git CLI.
3. Stay similar to the original Git commands/options, so that one doesn't become too dependent on these aliases and forget the original Git commands/options.

These aliases are grouped into the two following types.

### Shortcut Aliases

These aliases simply abbreviate existing git commands/options to save some typing (e.g., `chb` in place of `checkout --branch`).  They use the following naming conventions:

- One-two letters corresponding to the abbreviated git command (e.g., `a` for `add` or `rb` for `rebase`)
- Each letter thereafter corresponds to an option of that command (e.g., `h` for `--help` or `q` for `--quiet`).  These letters usually match the corresponding single-letter token for that option (e.g., `h` matches `-h`).  You'll be amazed how much faster you can use Git just by not having to type that hyphen!  For long or multi-word option names, two or more letters may be used (e.g., `sq` for `rebase`'s `--autosquash`).
- The option letters are ordered alphabetically by their *first* letter (e.g., `rebase --autostash --interactive` would become `rbis` because "i" comes before "s")
- Several Git commands already have really short names, in which case there are only aliases for those commands with their options.  For example, there is no alias for `git am`, but there is a `git amq` alias for `git am --quiet`.
- Here are some of the most common Shortcut Aliases that devs will probably use on a day-to-day basis:

  - `i` -> `init`
  - `rta` -> `remote add`
  - `rtv` -> `remote --verbose`
  - `cl` -> `clone`
  - `clbr` -> `clone --branch`
  - `ch` -> `checkout`
  - `chb` -> `checkout --branch`
  - `bru` -> `branch --set-upstream-to`
  - `brvv` -> `branch -vv`
  - `brd` -> `branch -d`
  - `s` -> `status`
  - `d` -> `diff`
  - `a` -> `add`
  - `aa` -> `add --all`
  - `ap` -> `add --patch`
  - `rs` -> `reset`
  - `rshd` -> `reset --hard`
  - `ce` -> `clean`
  - `cedf` -> `clean -d --force`
  - `cm` -> `commit`
  - `cmm` -> `commit --message`
  - `cma` -> `add --all && commit` (unlike `commit --all`, also commits untracked files)
  - `m` -> `merge`
  - `rb` -> `rebase`
  - `rba` -> `rebase --abort`
  - `rbi` -> `rebase --interactive`
  - `cp` -> `cherry-pick`
  - `bi` -> `bisect`
  - `bl` -> `blame`
  - `rv` -> `revert`
  - `ps` -> `push`
  - `psu` -> `push --set-upstream`
  - `pl` -> `pull`
  - `pla` -> `pull --all` (not to be confused with `plap` for `pull --append`)
  - `plr` -> `pull --rebase`
  - `rf` -> `reflog`
  - `bl` -> `blame`
  - `cfg` -> `config --global`

### Extension Aliases

These aliases "extend" the basic Git commands with one more additional commands.  They are meant to expedite common multi-command workflows, like pushing right after committing, checking out then pulling, staging all changes then running `status`, squash-committing then rebasing, etc.  Their names tend to be more cryptic, but generally follow this naming convention:

- First letter is an "x" for "eXtended".  This prevents naming conflicts with other aliases, as there are no Git commands that start with an "x" (and hopefully never will be!)
- Each letter thereafter corresponds to one of the commands or their options.  For example `git xaas` for `git add --all; git status`.  The command letters generally match those used in the Shortcut Aliases.  In some cases, for longer, multi-command Extension Aliases, the letters may be indicate the overall action being taken; for example `xmpr` is used to delete a local branch closed by a pull request on the remote and switch back to `master`, or `xdpr` to instead switch back to `dev`.

## Usage

The easiest way to use these aliases is to add an `[include]` section to your system `gitconfig` file, located at "C:\Program Files\Git\mingw64\etc\gitconfig" on 64-bit Windows 7, 8, and 10 machines and /etc/gitconfig everywhere else. The system `gitconfig` is preferable because the aliases will then be useable from every repo on your machine, which is almost always what you want. Alternatively, you can add the `[include]` section to the global `.gitconfig` in your home directory, or even to a specific repo in its local `.git/config` file (if you are unfamiliar with Git configuration file locations or syntax, checkout the [official documentation](https://git-scm.com/docs/git-config#_configuration_file)).

Whichever config file you choose to modify, add a line for each set of aliases that you want to include after the `[include]` line:

```ini
[include]
  path = C:/path/to/GitAliases/<alias>
  path = C:/path/to/GitAliases/<alias>
```

Replace `<alias>` with the actual path to an alias file in this repo that you want to include. Paths can be absolute or relative to the config file that you're modifying, and must use forward slashes ("/") **even on Windows machines**.  All Shortcut Aliases are placed in the [shortcut-aliases](shortcut-aliases/) folder, and all Extension Aliases are placed in the [extension-aliases](extension-aliases/) folder. Shortcut Alias files are named according to the command that they abbreviate, such as [add](shortcut-aliases/add), [commit](shortcut-aliases/commit), or [merge](shortcut-aliases/merge), and contain all the aliases for that command. The Extension Alias files are more spread out, usually with only one alias per file.

For example, to include all `checkout` and `rebase` aliases, as well as the Extension Alias for rebasing after a `commit --squash`, you would add the following lines to your chosen Git config:

```ini
[include]
  path = C:/path/to/GitAliases/shortcut-aliases/checkout
  path = C:/path/to/GitAliases/shortcut-aliases/rebase
  path = C:/path/to/GitAliases/extension-aliases/squash-commit
```

Remember, none of the Git aliases in this repository conflict, so you can use as many or as few of them as you like! Using `[include]` in this way, you can easily `[include]` these aliases in Git config files all over your file system. Moreover, whenever this repository is updated, you can just `git pull` the changes and have them take instant effect, without having to locate all your .gitconfigs and copy the updated aliases yourself.

If you simply want to include all of the aliases in this repo, then just paste the code below into your Git config and tweak the absolute paths (the paths shown here are mainly for my own benefit). Note that this may cause aliases to be unexpectedly added to your Git configuration the next time you pull from this repo, which could introduce conflicts with other Git aliases that you have defined personally.

```ini
[include]
    path = C:/Dan/GitAliases/shortcut-aliases/.gitconfig
    path = C:/Dan/GitAliases/extension-aliases/.gitconfig
```

## Contributing

If there are any aliases missing from this repository that you think should be added, please suggest them by opening an [Issue](https://github.com/DanwareCreations/GitAliases/issues/new?title=Add%20Alias%20For%20&lt;insert%20command%20here&gt;).
