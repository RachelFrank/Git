# Custom git configuration

## Install

```bash
take ~/Dev/Config

git clone <your-forked-git-repo>

cd Git

./install.sh

touch .gitconfig
```

Edit your `.gitconfig` file for yourself in `~/Dev/Config/Git`

```bash
[user]
    name = <Your name>
    username = <Your github username>
    email = <Your email>
[include]
	path = ~/Dev/Config/Git/gitcustom.txt
```

## List of Aliases

```git
unstage = reset HEAD # unstage all files
lastcommit = reset --hard # revert to the last commit
prevcommit = reset HEAD^ --hard # revert to previous commit and lose last commit

a = add
aa = add .
aac = commit -am
ai = add -i
ap = add -p
#############
app = apply
as = apply --stat
ac = apply --check
#############
ama = am --abort
amr = am --resolved
ams = am --skip
#############
b = branch
bd = branch -d
bD = branch -D
br = branch -r
bv = branch -vva
#############
bs = bisect
bsb = bisect bad
bsg = bisect good
bss = bisect start
#############
c = commit -m
cam = commit --amend --no-edit
cem = commit --allow-empty -m
caa = commit -am # add all and commit
caaam = commit -a --amend
ced = commit --allow-empty --amend
#############
ch = cherry-pick
#############
cl = clone
#############
cleanup = clean -fd
#############
d = difftool
dc = difftool --cached
dch = difftool --check
dp = difftool --patience
dcc = difftool --cached --check
ds = difftool --staged
#############
f = fetch
fa = fetch --all
fo = fetch origin
foa = fetch origin --all
fu = fetch upstream
#############
fp = format-patch
#############
fk = fsck
#############
g = grep -p
#############
i = init
ib = init --bare
#############
l = log --graph --pretty=format:'%Cblue%h%Creset %Cred(%cr) %C(bold blue)%an%C(yellow)%d %Creset %s' --abbrev-commit
la = log --graph --all --pretty=format:'%Cblue%h%Creset %Cred(%cr) %C(bold blue)%an%C(yellow)%d %Creset %s' --abbrev-commit
lb = log --graph --branches --pretty=format:'%Cblue%h%Creset %Cred(%cr) %C(bold blue)%an%C(yellow)%d %Creset %s' --abbrev-commit
ls = log --stat
#############

lsf = "!git ls-files | grep -i"
#############
m = merge
mt = mergetool
ma = merge --abort
mc = merge --continue
ms = merge --skip
m8 = merge-octopus
#############
o = checkout
ob = checkout -b
of = checkout --
oh = checkout HEAD
om = checkout master
ot = checkout --track
#############
pr = prune -v
#############
ps = push
psf = push -f
psu = push -u
pso = push origin
psao = push --all origin
psfo = push -f origin
psod = push origin --delete
psot = push origin --tags
psuo = push -u origin
psom = push origin master
psfom = push -f origin master
psuom = push -u origin master
#############
pl = pull
pla = pull --all
plu = pull -u
plo = pull origin
plp = pull upstream
plom = pull origin master
plr = pull --rebase
plrom = pull --rebase origin master
plpm = pull upstream master
#############
pr = pull --rebase
pro = pull --rebase origin
prp = pull --rebase upstream
prom = pull --rebase origin master
prum = pull --rebase upstream master
#############
rb = rebase
rba = rebase --abort
rbc = rebase --continue
rbi = rebase --interactive
rbm = rebase master
rbs = rebase --skip
#############
re = reset
# reh = reset HEAD
reh = reset --hard
rem = reset --mixed
res = reset --soft
rehh = reset --hard HEAD
remh = reset --mixed HEAD
resh = reset --soft HEAD
#############
rmc = rm --cached
#############
r = remote
ra = remote add
rrm = remote rm
rv = remote -v
rmv = remote rename
rp = remote prune
rs = remote show
rao = remote add origin
rau = remote add upstream
rso = remote show origin
rsu = remote show upstream
rp = remote prune
rpo = remote prune origin
rpu = remote prune upstream
rm = remote rename
rv = remote -v
rs = remote show
rso = remote show origin
rsu = remote show upstream
#############
ss = status -s -b
s = status  #long status

#############
st = stash
sta = stash apply
stc = stash clear
std = stash drop
stl = stash list
stp = stash pop
sts = stash save
stsh = stash show
#############
t = tag
ta = tag -am
tl = tag -l

#############
w = show
wp = show -p
wr = show -p --no-color
#############
svnr = svn rebase
svnd = svn dcommit
svnl = svn log --oneline --show-commit
#############
assume = update-index --assume-unchanged
unassume = update-index --no-assume-unchanged
assumed = "!git ls-files -v | grep ^h | cut -c 3-"
unassumeall = !git assumed | xargs git update-index --no-assume-unchanged
assumeall = "!git st -s | awk {'print $2'} | xargs git assume"
#############
ours = "!f() { git checkout --ours $@ && git add $@; }; f"
theirs = "!f() { git checkout --theirs $@ && git add $@; }; f"
#############
whois = "!sh -c 'git log -i -1 --pretty=\"format:%an <%ae>\n\" --author=\"$1\"' -"
whatis = show -s --pretty='tformat:%h (%s, %ad)' --date=short
#############
barebranch = !sh -c 'git symbolic-ref HEAD refs/heads/$1 && git rm --cached -r . && git clean -xfd' -
flat = clone --depth 1
subpull = !git submodule foreach git pull --tags origin master
subrepo = !sh -c 'filter-branch --prune-empty --subdirectory-filter $1 master' -
human = name-rev --name-only --refs=refs/heads/*
serve = !git daemon --reuseaddr --verbose  --base-path=. --export-all ./.git
snapshot = !git stash save "snapshot: $(date)" && git stash apply "stash@{0}"
```
