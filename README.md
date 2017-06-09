# GitAliases

## About
This repository contains some git aliases that are useful for any project, on any computer.  Most of the aliases simply abbreviate existing git commands/options to save some typing (e.g., `chb` in place of `checkout --branch`), while others combine several git commands into one (e.g., `aas` in place of `git add -A; git status;`).  The aliases are grouped into separate files by the commands that they shorten, such as [add](add), [commit](commit), [merge](merge), etc.  None of the git aliases in this repository conflict, so you can use as many or as few of them as you like!

## Usage
The easiest way to use these aliases is to add an `[include]` section to your global .gitconfig file (located at "C:\Users\\&lt;UserName&gt;\.gitconfig" on Windows 7, 8, and 10 machines).  The global .gitconfig is preferable because the aliases will be useable from every repo on your machine, which is almost always what you want.  After the `[include]` line, add a line for each file whose aliases you want included in your .gitconfig, such as:

    path = C:/path/to/GitAliases/checkout

to include the `git checkout` aliases.  `path` must be an absolue path to an alias file, and must use forward slashes ("/").  Using `[include]` in this way allows you to have .gitconfig files that are always up-to-date with this repository, and you can easily `[include]` these aliases in as many other .gitconfig files as you want.  Whenever this repository is updated, you can just `git pull` to get the updated aliases in every one of your .gitconfig files, rather than locating the changes and copying/creating them yourself.

For reference, the following lines would include every alias file in this repository into your .gitconfig.  You can just paste this into your .gitconfig and remove any lines that you don't want.
```
[include]
    path = C:/path/to/GitAliases/add
    path = C:/path/to/GitAliases/branch
    path = C:/path/to/GitAliases/checkout
    path = C:/path/to/GitAliases/clone
    path = C:/path/to/GitAliases/commit
    path = C:/path/to/GitAliases/config
    path = C:/path/to/GitAliases/diff
    path = C:/path/to/GitAliases/fetch
    path = C:/path/to/GitAliases/help
    path = C:/path/to/GitAliases/log
    path = C:/path/to/GitAliases/merge
    path = C:/path/to/GitAliases/pull
    path = C:/path/to/GitAliases/push
    path = C:/path/to/GitAliases/rebase
    path = C:/path/to/GitAliases/remote
    path = C:/path/to/GitAliases/reset
    path = C:/path/to/GitAliases/revert
    path = C:/path/to/GitAliases/stash
    path = C:/path/to/GitAliases/status
    path = C:/path/to/GitAliases/tag
```

## Contribute
If there are any aliases missing from this repository that you think should be added, please suggest them by filing an [Issue](https://github.com/DanwareCreations/GitAliases/issues/new?title=Add%20Alias%20For%20&lt;insert%20command%20here&gt;).
