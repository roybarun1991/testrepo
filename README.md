Git updated commands:
$ git config --global user.name "Your Name"
$ git config --global user.email "you@youraddress.com"
$ git config --global push.default matching
$ git config --global alias.co checkout
$ git init
after this:
under git init folder
mkdir ~/.ssh
cd ~/.ssh
ssh-keygen.exe
enter
enter
enter
cat id_rsa.pub
enter
enter the public ssh key to github account ssh section
create repository in github account
cd project folder
git remote add origin git@gitlab.com:roybarun1991/debuggercode.git
git push -u origin master
enter and type yes
all the files are moved into the repository
after this:
git status
git add .
git commit -m "commit"
git push
