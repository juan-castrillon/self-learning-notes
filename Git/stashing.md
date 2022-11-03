`git stash`

- Convinience Method

- When you have uncommited changes in a branch and need to change to another
  - Avoids taking the changes with you (assuming they dont conflict)


- Save changes without commiting to be able to move between branches

- `git stash`
  - Takes all uncommited changes and saves them and reverts them
  - short for `git stash save`

- `git stash pop`
  - Brings changes back that are stashed

- `git stash apply`
  - Same as pop but does not removed changes on the stash
  - Good if some changes need to be applied in multiple branches

- We can have a stack of stashes
  - Just keep calling `git stash`
  - They are accessible in the order they were put in
  - `git stash list`
  - `git stash apply stash@{2}`
  - `git stash drop stash@{2}`


`git stash clear` drops all stashes and changes