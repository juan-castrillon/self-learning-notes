every commit has a hash (unique id)
every commit references a parent (where it came from)
(except the first)

Work is not linear (different contexts, one thing i make breaks another people work)

alternate timelines for the project
changes do no affect other branches

# Master (main) branch
- Main (default) branch of any repo
- Normally treated by people as the "official branch" not to mess with
- From git is just another branch

# HEAD
- Pointer refers to the current "location" in the repo. It points to a branch reference

In which timeline am i?

Branch reference is where the branch is (last commit)

Brnahces are just a reference to a certain commit

# git branch
Show all branches
With a name creats a new branch (Does not switch) based in the current HEAD

`git branch -d name` Deletes branches
    - Cannot be the current branch
    - It requires the branch to be merged into the upstream (this can be overriden with `-D`)

`git branch -m new_name` changes the name of the current branch

# git switch
Switch between branches
Has to exist
`git switch -c name` creates a new one and switch

# git checkout
Switch between branches
Older than switching, does a lot of things
`git checkout -b name` creates a new one and switch

> Uncommited changes will be lost if switching branches (can be stashed). Only if the changes conflict, for example new files that dont exist, will just come to the new branch

# Merging

Incorporate changes from one branch to another

- We merge to where HEAD is
  
1. MOve to receiving branch (`switch`)
2. `git merge source-branch`

## Fast forward merge
- Branch just catches up
- NO conflicts, the other one has extra commits
- Moves head some number of commits

## Merge commit
- MOre common
- There is commits in the target branch that are not in the source
- Can be automatically merged or not, depending if conflicts
- Makes a commit. Normallt asks for a commit message

### Conflicts
- Git cannot merge automatically and have to be resolved manually
1. Open the file
2. Edit the file to remove conflicts
3. Remove markers 
4. Add changes and commit