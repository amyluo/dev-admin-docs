#Git Global Config Settings
```
[user]
    name = FirstName LastName
    email = [email]
[color]
    ui = auto
[gc]
    autoDetach = false
[core]
    autocrlf = input
    editor = vim
    excludesfile = [path_to]/.gitignore_global
[credential]
    helper = cache --timeout=10

[status]
    submoduleSummary = true
[http]
    sslVerify = false
```

#Advanced Commands: git remote
```
# Replace an exist remote URL
$ git remote set-url --add <name> <newurl>
$ git remote set-url [--push] <name> <newurl> [<oldurl>]

# Delete an exist remote URL
$ git remote set-url --delete <name> url>

# Rename an remote
$ git remote rename <old> <new>

$ git remote set-head <name> (-a | --auto | -d | --delete | <branch>) 

$ git remote add [-t <branch>] [-m <master>] [-f] [--tags | --no-tags] [--mirror=<fetch|push>] <name> <url>
$ git remote prune [-n | --dry-run] <name>
$ git remote [-v | --verbose] update [-p | --prune] [(<group> | <remote>)...]
$ git remote get-url [--push] [--all] <name>
```

#