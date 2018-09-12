添加用户名
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

显示当前目录pwd
把这个目录变成Git可以管理的仓库：git init

第一步，用命令git add告诉Git，把文件添加到仓库：
git add text.txt

第二步，用命令git commit告诉Git，把文件提交到仓库：
git commit 
简单解释一下git commit命令，-m后面输入的是本次提交的说明
git commit -m "这次改动的说明"

git status命令可以让我们时刻掌握仓库当前的状态
git status

git diff查看修改内容
git diff

git log命令可以告诉我们提交的历史记录
git log
如果嫌输出信息太多，看得眼花缭乱的，可以试试加上--pretty=oneline参数：
$ git log --pretty=oneline

在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
git reset命令可以回退版本
$ git reset --hard HEAD^（这个是回退到上一版本）
在这种情况下打印git log就看不到最新的提交历史了，如果想返回去需要在没关Git的时候找到最新的commit ID号，比如（commit 6146ec8c7d5a8156a11c7af2ca7650828faf15a3），不用全部输入，输入前几位数就可以
git reset --hard 6146ec

手动把文件恢复到上一个版本的状态。git checkout -- file可以丢弃工作区的修改：
git checkout -- readme.txt
命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。

如果你要是把这个文件git add提交到暂存区了就要用命令git reset HEAD <file>可以把暂存区的修改撤销掉（unstage），重新放回工作区：
git reset HEAD readme.txt
如果你提交到版本库可以回退到上一个版本，。不过，这是有条件的，就是你还没有把自己的本地版本库推送到远程。还记得Git是分布式版本控制系统吗？我们后面会讲到远程版本库，一旦你把stupid boss提交推送到远程版本库，你就真的惨了……

一般情况下，你通常直接在文件管理器中把没用的文件删了，或者用rm命令删了：
rm test.txt
这个时候，Git知道你删除了文件，因此，工作区和版本库就不一致了，git status命令会立刻告诉你哪些文件被删除了：
现在你有两个选择，一是确实要从版本库中删除该文件，那就用命令git rm删掉，并且git commit：
git rm test.txt
git commit -m "remove test.txt"
另一种情况是删错了，因为版本库里还有呢，所以可以很轻松地把误删的文件恢复到最新版本：
git checkout -- test.txt
git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。

创建远程仓库
第1步：创建SSH Key。在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
ssh-keygen -t rsa -C "1171326259@qq.com"
你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。
如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：
为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。
最后友情提示，在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去。

添加远程库
现在的情景是，你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。
首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库：
在Repository name填入XXXXXXXX，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库：
目前，在GitHub上的这个XXXXXX仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。
现在，我们根据GitHub的提示，在本地的XXXXXX仓库下运行命令：
git remote add origin git@github.com:Z-yuan（账户名）/XXXXX（仓库名）.git
把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
git push -u origin master
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
从现在起，只要本地作了提交，就可以通过命令：
git push origin master
SSH警告
当你第一次使用Git的clone或者push命令连接GitHub时，会得到一个警告：
The authenticity of host 'github.com (xx.xx.xx.xx)' can't be established.
RSA key fingerprint is xx.xx.xx.xx.xx.
Are you sure you want to continue connecting (yes/no)?
这是因为Git使用SSH连接，而SSH连接在第一次验证GitHub服务器的Key时，需要你确认GitHub的Key的指纹信息是否真的来自GitHub的服务器，输入yes回车即可。

创建与合并分支