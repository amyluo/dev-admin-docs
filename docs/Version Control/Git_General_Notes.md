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

```
$ git config --global user.name "FirstName LastName"
$ git config --global user.email "[email]"
```
#Git Project Config Settings
```
$ git config --local user.name "FirstName LastName"
$ git config --local user.email "[email]"
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

#Author in Commit
```
# Change committed author
$ git commit --amend --author="FirstName LastName <[email]>"

# Change next commit author
$ git commit --auther="FirstName LastName <[email]>"

```

#Control git tag
```
# Add an annotation tag locally
$ git tag -a [tag_name]

# Check local tag
$ git tag --points-at

# Delete a locally tag
$ git -d [tag_name]

# Push a new tag to remote
$ git push [remote_name] [tag_name]

# Delete a remote tag not in locally
$ git push [remote_name] --delete [tag_name]

# Add an annotation tag on [commit_hast] locally
$ git tag -a [tag_name] [commit_hash]

# Push a tag to replace remote tag
$ git push [remote_name] -f [tag_name]

# Push all tags to remote
$ git push -f --tags
```

#Git rebase from 1st commit
```
$ git rebase -i --root

$ git commit --amend
$ git rebase --continue
```
#Remove files from Git commit
```
$ git reset --soft HEAD^
# or
$ git reset --soft HEAD~1
 
# Then reset the unwanted files in order to leave them out from the commit
$ git reset HEAD path/to/unwanted_file
 
# Now commit again, you can even re-use the same commit message
$ git commit -c [ORIG_HEAD] 
 
$ git commit --amend --author="John Doe <john@doe.org>"

# git has a different solution to do this. First change the file you do not want to be tracked and use the following command
$ git update-index --assume-unchanged [File_Name]
 
# And if you want to track the changes again use this command
$ git update-index --no-assume-unchanged [File_Name]
```
