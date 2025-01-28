
**Status:**  #Complete
**Tags:** [[version-control]]

# Git Commands Reference

## Initializing and Configuring a Repository
- `git init`  
  *Initializes a repository.*

## Viewing Repository Status and History
- `git log`  
  *Shows commit history.*
- `git status`  
  *Shows the current status of the repository.*

## Staging and Committing Changes
- `git add <file_name>` or `git add .`  
  *Stages files for commit.*
- `git commit -m "<message>"`  
  *Commits changes with a message.*

## Cloning and Connecting Remote Repositories
- `git clone <https>`  
  *Clones a repository from the provided URL.*
- `git remote add origin https://github.com/TanKaizokuO/learning-js.git`  
  *Connects your repository to a remote origin.*

## Fetching and Pushing Changes
- `git push -u origin main`  
  *Pushes changes to the main branch.*
- `git fetch <https>`  
  *Fetches changes from the remote repository.*
- `git pull <https>`  
  *Pulls changes (equivalent to `fetch` + `merge`).*

## Working with Branches
- `git branch`  
  *Shows available branches.*
- `git branch <name>`  
  *Creates a new branch.*
- `git checkout <name>`  
  *Switches to a different branch.*
- `git merge nav-bar`  
  *Merges the `nav-bar` branch into the current branch.*
- `git branch -d <name>`  
  *Deletes the specified branch.*

## Viewing Changes
- `git diff`  
  *Displays changes in your project.*
- `git diff <commit id>..<commit id>`  
  *Compares differences between two commits.*

## Stashing Changes
- `git stash`  
  *Temporarily saves uncommitted changes, allowing you to switch branches or work on other tasks without losing progress. The changes are stored in a "stash" and can be reapplied later.*

## Rebase
- `git rebash`  
  *Rebase your branch with the latest changes.*

## Creating New Files
- `touch <file_name.extension>`  
  *Creates a new file.*

## References
