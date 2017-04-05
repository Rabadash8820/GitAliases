# GitAliases

## About
This repository contains some git aliases that are useful on any computer, for any project.  The aliases are located in [aliases.txt](aliases.txt).  None of the git aliases in this repository conflict, so you can use as many or as few of them as you like.  For best results, you should include these aliases in your _global_ .gitconfig file (located at "C:\Users\<UserName>\.gitconfig" on Windows 7, 8, and 10 machines).  That way, the changes will apply to every repo on your machine, which is almost always what you want.

## Usage
There are three primary ways to get these aliases onto your own machine:
1. Copy the aliases that you want from [aliases.txt](aliases.txt), and paste them into your target .gitconfig file (machine-level, user-level, repository-level, etc.).  This method allows you to pick and choose only the aliases that you want.  Be sure to paste the aliases after the `[alias]` line of your target .gitconfig file, and make sure that there is whitespace (tabs or spaces) before each alias.
2. Create the aliases manually in your target .gitconfig file.  At the git command line, type `git config --<location> alias.<alias-name> <alias-body>`, replacing `<location>` with something like `--global` or `--local`, `<alias-name>` with the name of the alias you want, and `<alias-body>` with the value of that alias.  See the [Git documentation](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases) for complete `git config` usage instructions.
3. Clone this repository, and include a reference to [aliases.txt](aliases.txt) inside your target .gitconfig file.  To do this, add the following lines to your target .gitconfig:
```
[include]
  path = /path/to/your/clone/aliases.txt
```
where `path` is the absolue path to aliases.txt, using forward slashes ("/").  This method allows you to have a .gitconfig that is always up-to-date with this repository with minimal effort, and you can `[include]` aliases.txt in as many other .gitconfig files as you want.  Whenever we update this repository's .gitconfig, you can just `git pull` to get the updated aliases in every one of your .gitconfig files, rather than locating the changes and copying/creating them yourself.  Note, though, that this method will give you _all_ of the aliases, rather than just the few that you might actually want.  
