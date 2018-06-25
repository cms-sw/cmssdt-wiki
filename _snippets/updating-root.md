# Updating root

```bash
#clone root repo from https://github.com/root-project/root.git
git clone https://github.com/root-project/root.git
cd root/
#add a remote that mathces cms-sw/root and check the remotes
git remote add cms git@github.com:cms-sw/root (git remote add gudrutis git@github.com:gudrutis/root)
    root/root-master -> cms/root-master   
    root/(latest-patche) -> cms/other-root
git remote
#check the latest short commit name from https://github.com/root-project/root.git and create branch name after it
git rev-parse --short HEAD  #it gives the short hash
#create new branch name with the short hash, in this case bb96255
git checkout -b cms/bb96255 #creates the branch and checks it out
#go to https://github.com/cms-sw/cmsdist/blob/IB/CMSSW_9_1_X/root6/root.spec 
#fetch the  from cms-sw/root remote (named cms) on the top of whats in root using the "%define branch cms/92bc04f" line from the root.spec file (in this case cms/92bc04f)
git fetch cms cms/92bc04f:cms/92bc04f
git log --pretty=short 92bc04f..cms/92bc04f #returns the commits and their author, use the commit hash to cherry-pick it
git-cherry-pick 9d8dd301a8ce825cae5f295567ba9f4e02cd7da4 #cherry-picks the last commit from cms-sw/root on the top of root repo
#check the branch to make sure it's after the name of root's latest commit short hash
git branch
#if it matches the new created branch, push it on cms-sw/root
git push cms cms/bb96255
#this commit goes to cms-sw/root
#change the current branch name and tag name at https://github.com/mrodozov/cmsdist/blob/IB/CMSSW_9_1_X/root6/root.spec with branch name after the short hash of latest root commit and tag name after the full hash name from git rev-parseHEAD (keeping in mind we first used that command before fetching the cms remote)
#check the version number from here https://github.com/root-project/root/blob/master/build/version_number and also change it if it's different
#make the pull request to cms-sw/cmsdist
#ask the bot to test it with "please test" command
```



