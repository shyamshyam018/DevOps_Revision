git init : empty repo is created and a .git file is added whihc is hidden 
in order to see it , we can use the ls -a commands
and in order to see whats inside the .git file 
we can use ls .git , which gives us HEAD , description , info ,refs , hooks ,config , objects

in order to go back to the partuclar commit and remove all above commit we can use the 
git reset sha-checksum


i have modiifed some codebase , but i want them later but not now 
so have thwem in the backstage and bting them when needed , usage STASH
git stash

when we want those chnges to come back we can use the git stash pop

when the changes are not needed anymore we can clear the stash using git stash clear

git remote -v shows the remote repo connected to the current project

its not recommedn to commit on the main branch 
so we create a new branch using git branch feature-1 , git checkout feature-1

from where we have forkled the project si caklled the ustrean url



when we have stashed or made an y commit changes and push something new , we have to force push it using 
git push origin main -f


when we ahve to be in update with teh new changes made in the remote repo of forked repo , we can mnaintain upstream changes using 
git checkout main
git fetch --all --prune 
or 
git pull upstream main

git reset --hard upstream/main


merge conflicts , squash commits

merges all commit before done 
git rebase -i head-checksum


