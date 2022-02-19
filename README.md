git-prompt-morecolors
=====================

Quick update to git-prompt.sh and sample git_ps1 to enable easy colo{riz,uris}ed bash prompt (tcsh/zsh not done).

Prompt looks like;

![dennis@f42bae530ccb:~/gitplay(main%*+=)$](https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git-status.png)

```
u@h:<dir>(<branch><flags>)$

     u@h : green (default)
     dir : blue  (default)

         { dim       : untracked files
         { red       : unstaged changes
branch = { yellow    : staged (not commited) changes
         { green     : nothing to commit/clean working tree
 
         { dim %     : untracked file(s)
         { red *     : unstaged file(s)
         { yellow +  : staged file(s)
         { blue $    : stashed file(s)
 flags = { 
         { red <>    : branch has diverged, pull/merge needed
         { red <     : branch is behind, pull needed
         { yellow >  : branch is ahead, push needed
         { green =   : branch is up to date

 $       : Turns to red ! if last exit code was non zero
 ```
 
Quick Install
=============

Make a directory and grab the required files 
```bash
mkdir ~/git-prompt && cd $_
wget https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash
wget https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git-prompt.sh
wget https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git_ps1
```

Source the new files into your profile
```bash
echo 'for f in ~/git-prompt/*; do . $f ; done' >>~/.bashrc
```

Change git status add/updated staged files output to be yellow in ~/.gitconfig for consistency 
```bash
git config --global color.status.added yellow
git config --global color.status.updated yellow
git config --global color.status.untracked dim
```

Logout/Login
