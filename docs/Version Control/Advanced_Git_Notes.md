#Command: git filter-branch
```
# example command to split composer/composer doc/ subfolder into a new repository
$ git filter-branch --prune-empty --subdirectory-filter doc master
```
Brief help
```
$ git filter-branch [--setup <command>] [--subdirectory-filter <directory>] [--env-filter <command>]
   	[--tree-filter <command>] [--index-filter <command>]
   	[--parent-filter <command>] [--msg-filter <command>]
   	[--commit-filter <command>] [--tag-name-filter <command>]
   	[--original <namespace>]
   	[-d <directory>] [-f | --force] [--state-branch <branch>]
   	[--] [<rev-list options>...]
```

#Command: git archive
```
$ git archive [<options>] <tree-ish> [<path>...]
$ git archive --list
$ git archive --remote <repo> [--exec <cmd>] [<options>] <tree-ish> [<path>...]
$ git archive --remote <repo> [--exec <cmd>] --list

    --format <fmt>        archive format
    --prefix <prefix>     prepend prefix to each pathname in the archive
    -o, --output <file>   write the archive to this file
    --worktree-attributes
                          read .gitattributes in working directory
    -v, --verbose         report archived files on stderr
    -0                    store only
    -1                    compress faster
    -9                    compress better

    -l, --list            list supported archive formats

    --remote <repo>       retrieve the archive from remote repository <repo>
    --exec <command>      path to the remote git-upload-archive command
```

#Command: git reflog
```
$ git reflog [ show | expire | delete | exists ]
```
