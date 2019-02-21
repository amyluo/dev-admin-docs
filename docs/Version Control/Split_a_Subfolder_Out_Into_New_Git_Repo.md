##1. Open a terminal app
##2. Clone source repo into a new local repo
```
$ git clone https://github.com/USERNAME/REPOSITORY-NAME
```
##3. Change the current working directory ot your cloned repository
```
$ cd REPOSITORY-NAME
```
##4. To filter out the subfolder from the rest of the files in the repository, run `git filter-branch`, supplying this information
- `FOLDER-NAME`: The folder within your project that you'd like to create a separate repository from.`
- `BRANCH-NAME`: The default branch for you current project, for example, `master` or `gh-pages`.
```
$ git filter-branch --prune-empty --subdirectory-filer FOLDER-NAME BRANCH-NAME
```
The repository should now only contain the files that were in your subfolder.
##5. Create a new repository on GitHub. And copy newly created repository URL.
```
https://github.com/USERNAME/NEW-REPOSITORY-NAME.git
```
##6. Using newly created remote repository URL to replace your old git remote setup.
```
$ git remote -v
> origin  https://github.com/USERNAME/REPOSITORY-NAME.git (fetch)
> origin  https://github.com/USERNAME/REPOSITORY-NAME.git (push)

$ git remote set-url origin https://github.com/USERNAME/NEW-REPOSITORY-NAME.git

$ git remote -v
# Verify new remote URL
> origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (fetch)
> origin  https://github.com/USERNAME/NEW-REPOSITORY-NAME.git (push)
```
##7. Push your changes to the new repository on GitHub
```
$ git push -u origin BRANCH-NAME
``` 


------------------------------------------------------------------------
Reference to [Splitting a subfolder out into a new repository
](https://help.github.com/en/articles/splitting-a-subfolder-out-into-a-new-repository)