git-prompt-addyellow
====================

Quick update to git-prompt.sh and sample git_ps1 to enable easy colo{riz,uris}ed bash prompt (tcsh/zsh not done).

Prompt looks like;

![dennis@f42bae530ccb:~/gitplay(main*%=)$](https://raw.githubusercontent.com/dennisyau1885/git/master/contrib/completion/git-prompt-moreyellow.gif)

```
u@h:<dir>(<branch><flags>)$

     u@h : green (default)
     dir : blue  (default)
 
         { red       : untracked/unstaged changes
branch = { yellow    : staged (not commited) changes
         { green     : nothing to commit/clean working tree
 
         { red *     : unstaged file(s)
         { yellow +  : staged file(s)
         { blue $    : stashed file(s)
         { red %     : untracked file(s)
 flags = { 
         { green =   : branch is up to date
         { yellow >  : branch is ahead, push needed
         { red <     : branch is behind, pull needed
         { red <>    : branch has diverged, pull/merge needed
 
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
cat <<EOD >>~/.bashrc
for f in ~/git-prompt/*; do
  . \$f
done
EOD
```

Change git status add/updated staged files output to be yellow in ~/.gitconfig for consistency 
```bash
git config --global color.status.added yellow
git config --global color.status.updated yellow
```

Logout/Login
```bash
newgrp -
```
