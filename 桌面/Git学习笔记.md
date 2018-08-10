
git推荐 文档    https://www.cnblogs.com/wang_yb/p/3867221.html
                        https://www.cnblogs.com/best/p/7474442.html
                        https://www.cnblogs.com/vman/articles/Git_cmds.html
                        https://www.liaoxuefeng.com  廖雪峰
https://blog.csdn.net/ltstud/article/details/79043052
https://blog.csdn.net/weixin_38399962/article/details/79712379   IDEA+GIT
https://blog.csdn.net/lovelife527386108/article/details/80457051
https://blog.csdn.net/mingyundezuoan/article/details/79677032
https://www.cnblogs.com/junhuawang/p/7054745.html
https://blog.csdn.net/sszgg2006/article/details/73342566
https://blog.csdn.net/tomatozaitian/article/details/73515849
https://blog.csdn.net/adarcy/article/details/77206190    git 连接 github.com 


1.克隆代码
    git clone ssh://gitolite@192.168.1.169/mt7620a.git ./mt7620a  克隆版本库，取名为m7620a
    
    git checkout -b develop origin/develop 检测develop分支
    
2.开始修改代码前，应该更新develop分支
        git checkout   develop    切换分支
        git pull origin develop   更新最新代码
      
3 .进行代码修改，都应该创建新的分支 。例如开发一个新的功能，创建一个feature-xxx分支，它是从develop分支上面分出来的：
    git checkout -b feature--xxxdevelop 基于develop分支创建一个新的分支
4. push 代码前,再次更新代码： 
    git checkout develop 
    git pull origin develop  更新最新代码
5. 代码修改完成之后，合并分支代码到develop分支:
    git checkout develop
    git merge [--no-ff] feature-xxx 将分支上的改变合并到develop分支
    git branch -d feature-xxx 删除feature 分支
6. 把本地的develop分支推送到origin上的$name分支：
    git push origin develop:$name

    release开发步骤
    如果 origin 使用了release分支,开发者开始修改代码前和push代码前要和origin上的release分支同步，直到release分支结束.
1.检测release分支、
        git fetch origin  查看最新节点
        git checkout -b release-xxx origin/release-xxx 检测release
2.修改代码前，本地release分支和origin上的release分支同步代码:
        git checkout release-xxx   
        git  pull origin release-xxx 与origin的release分支代码同步
3.创建一个新的分支来修改代码，它是从release 分支上面分出来的:
        git checkout -b fixbug-xxx release-xxx
        /*在fixbug-xxx分支上修改代码*/        
4.push代码前,本地的最新的的开发分支再次和origin上的最新的开发分支同步代码。
        4.1一般步骤
            git checkout release-xxx
            git pull origin release-xxx 与origin的release分支同步代码
        4.2 如果开始修改代码前本地release分支以经在和origin上的release分支同步,但在push代码前origin的release分支已经删除了,在push代码前本push代码前本地的release分支英和origin的develop 分支同步:
            git checkout release-xxx
            git pull origin develop:release-xxx 与origin的develop分支代码同步
5.代码修改完成后，合并分支代码到release分支
        git checkout release-xxx
        git merge[-no-ff] fixbug-xxx 代码合到release分支
        git branch -d fixbug -xxx 
6.本地的release分支push到origin上的$name分支:
    git push origin release-xxx:$name push修改到origin上的$name分支
7.软件发布后，删除release分支
    git remote prune origin origin 的relase分支结束后，本地同步origin已删除分支
    git branch -d release-xxx 删除本地release分支
8.HEAD指向的版本就是当前版本,因此,Git允许我们在版本的历史之间穿梭,使用用命
令 git reset --hard commit_id 。
9. 穿梭前,用用 git log 可以查看提交历史,以便确定要回退到哪个版本
10. 要重返未来,用用 git reflog 查看命令历史,以便确定要回到未来的哪个版本。
11.查看进行的操作 $ cat readme.txt
12.提交后,用用“ git diff HEAD -- readme.txt ”命令可以查看工工作区和版本库里里面面最新版本的区
13.第1步:创建SSH Key。在用用户主目录下,看看有没有.ssh目录,如果有,再看看这个目录下
        有没有id_rsa和id_rsa.pub这两个文文件,如果已经有了,可直接 跳到下一一步。如果没有,打
        开Shell(Windows下打开Git Bash),创建SSH Key:
        $ ssh-keygen -t rsa -C "youremail@example.com"
        你需要把邮件地址换成你自自己己的邮件地址,然后一一路回⻋车,使用用默认值即可,由于这个Key
        也不是用用于军事目的,所以也无无需设置密码。
        如果一一切顺利的话,可以在用用户主⺫目目录里里找到.ssh⺫目目录,里里面面有id_rsa和id_rsa.pub两个文文
        件,这两个就是SSH Key的秘钥对,id_rsa是私钥,不能泄露出去,id_rsa.pub是公钥,可
        以放心心地告诉任何人人。
        第2步:登陆GitHub,打开“Account settings”,“SSH Keys”⻚页面面:
        然后,点“Add SSH Key”,填上任意Title,在Key文文本框里里粘贴id_rsa.pub文文件的内容:
14. 强制合并  git pull origin master --allow-unrelated-histories 
15.$ git log --graph --pretty=oneline --abbrev-commit     命令可以看到分支合并图
16.branch
        Git鼓鼓励大大量使用用分支:
        查看分支:git branch
        创建分支:git branch name
        切换分支:git checkout name
        创建+切换分支: git checkout -b name
        合并某分支到当前分支: git merge name
        删除分支: git branch -d name
17.Git分支十十分强大大,在团队开发中应该充分应用用。
        合并分支时,加上 --no-ff 参数就可以用用普通模式合并,合并后的历史有分支,能看出来曾经
        做过合并,而而fast forward合并就看不出来曾经做过合并。
17.$ git stash 隐藏工作空间
用 git stash list 查看:
$ git stash list
恢复指定的stash,用用命令:
$ git stash apply stash@{0}
18.多人协作
因此,多人人协作的工工作模式通常是这样:
1. 首首先,可以试图用用 git push origin branch-name 推送自自己己的修改;
2. 如果推送失败,则因为远程分支比比你的本地更新,需要先用用 git pull 试图合并;
3. 如果合并有冲突,则解决冲突,并在本地提交;
   1) 没有冲突或者解决掉冲突后,再用用 git push origin branch-name 推送就能成功!
        如果 git pull 提示示“no tracking information”,则说明本地分支和远程分支的链接关系没
        有创建,用用命令 git branch --set-upstream branch-name origin/branch-name 。
        这就是多人人协作的工工作模式,一一旦熟悉了,就非非常简单。
        小小结
      ▪ 查看远程库信息,使用用 git remote -v ;
      ▪ 本地新建的分支如果不推送到远程,对其他人人就是不可⻅见的;
      ▪ 从本地推送分支,使用用 git push origin branch-name ,如果推送失败,先用用git pull抓取远程的新提交;
      ▪ 在本地创建和远程分支对应的分支,使用用 git checkout -b branch-name origin/branch-name ,本地和远程分支的名称最好一一致;
      ▪ 建立立本地分支和远程分支的关联,使用用 git branch --set-upstream branch-name origin/branch-name ;
      ▪ 从远程抓取分支,使用用 git pull ,如果有冲突,要先处理冲突
19.git rebase --abort   放棄當前操作 ,会取消所有本地操作，包括本地修改的文件 已经commit内容。但可以解决Rebaseing 异常
20.然后,敲命令 git tag name 就可以打一一个新标签:
$ git tag v1.0
可以用用命令 git tag 查看所有标签:
$ git tag
    以用用 git show tagname 查看标签信息:
$ git show v0.9
    可以看到,“v0.9”确实打在“add merge”这次提交上。
    还可以创建带有说明的标签,用用-a指定标签名,-m指定说明文文字:
21.$ git tag -a v0.1 -m "version 0.1 released" 3628164
还可以通过-s用用私钥签名一一个标签:
$ git tag -s v0.2 -m "signed version 0.2 released" fec145a git tag -d v0.1
        • 命令 git push origin tagname 可以推送一一个本地标签;
        • 命令 git push origin --tags 可以推送全部未推送过的本地标签;
        • 命令 git tag -d tagname 可以删除一一个本地标签;
        • 命令 git push origin :refs/tags/tagname 可以删除一一个远程标签
• 
22.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
yangxiong@yangxiong-System-Product-Name:~/桌面$ git mv SpringBoot-Fresh基础培训.ppttx 
用法：git mv [<选项>] <源>... <目标>

    -v, --verbose         冗长输出
    -n, --dry-run         演习
    -f, --force           强制移动/重命令，即使目标存在
    -k                    跳过移动/重命名错误

yangxiong@yangxiong-System-Product-Name:~/桌面$ git rmm SpringBoot-Fresh基础培训.pptx 
git：'rmm' 不是一个 git 命令。参见 'git --help'。

最相似的命令是
	rm
yangxiong@yangxiong-System-Product-Name:~/桌面$ git rm SpringBoot-Fresh基础培训.pptx 
error: 下列文件索引中有变更
    桌面/SpringBoot-Fresh基础培训.pptx
（使用 --cached 保留本地文件，或用 -f 强制删除）
yangxiong@yangxiong-System-Product-Name:~/桌面$ git rm -cached SpringBoot-Fresh 基础培训.ptx 
error: did you mean `--cached` (with two dashes ?)
yangxiong@yangxiong-System-Product-Name:~/桌面$ git rm --cached SpringBoot-Fresh基础培训.pptx 
rm '桌面/SpringBoot-Fresh基础培训.pptx'
yangxiong@yangxiong-System-Product-Name:~/桌面$ cd 书籍/
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ ls
 Git                                   Log4j文档.docx
 hibernate_validator_reference.pdf     mybatis-doc.pdf
 hibernate_validator_referenceZh.pdf   oss-sdk-intl-zh-2018-06-29.pdf
 Java常用类与方法大全.doc              spring-boot-reference.pdf
 Java常用算法手册.pdf                  springboot帮助手册.docx
'Java核心技术(卷1）第8版.pdf'          spring-framework-reference.pdf
 Java核心技术（卷2）第8版.pdf          spring-security-reference.pdf
 Java设计模式（疯狂Java联盟版）.chm    阿里巴巴Java开发手册（详尽版）.pdf
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git add springboot帮助手册.docx
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git commit -m 'springboot帮助手册'
[master （根提交） 3ddaca7] springboot帮助手册
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 "\346\241\214\351\235\242/\344\271\246\347\261\215/springboot\345\270\256\345\212\251\346\211\213\345\206\214.docx"
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push origin master
Username for 'https://github.com': 1941456312@qq.com
Password for 'https://1941456312@qq.com@github.com': 
To https://github.com/yangxiongj/java
 ! [rejected]        master -> master (fetch first)
error: 无法推送一些引用到 'https://github.com/yangxiongj/java'
提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远程变更
提示：（如 'git pull ...'）。
提示：详见 'git push --help' 中的 'Note about fast-forwards' 小节。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push doc master
fatal: 'doc' does not appear to be a git repository
fatal: 无法读取远程仓库。

请确认您有正确的访问权限并且仓库存在。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git show
commit 3ddaca70ae3509965097e40b61fad3898cc6255c (HEAD -> master)
Author: 1941456312@qq.com <yangxiong@ubuntu>
Date:   Tue Jul 17 18:20:18 2018 +0800

    springboot帮助手册

diff --git "a/\346\241\214\351\235\242/\344\271\246\347\261\215/springboot\345\270\256\345\212\251\346\211\213\345\206\214.docx" "b/\346\241\214\351\235\242/\344\271\246\347\261\215/springboot\345\270\256\345\212\251\346\211\213\345\206\214.docx"
new file mode 100644
index 0000000..e1f6488
Binary files /dev/null and "b/\346\241\214\351\235\242/\344\271\246\347\261\215/springboot\345\270\256\345\212\251\346\211\213\345\206\214.docx" differ
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$  git push master
fatal: 'master' does not appear to be a git repository
fatal: 无法读取远程仓库。

请确认您有正确的访问权限并且仓库存在。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push origin master
Username for 'https://github.com': 1941456312@qq.com
Password for 'https://1941456312@qq.com@github.com': 
To https://github.com/yangxiongj/java
 ! [rejected]        master -> master (fetch first)
error: 无法推送一些引用到 'https://github.com/yangxiongj/java'
提示：更新被拒绝，因为远程仓库包含您本地尚不存在的提交。这通常是因为另外
提示：一个仓库已向该引用进行了推送。再次推送前，您可能需要先整合远程变更
提示：（如 'git pull ...'）。
提示：详见 'git push --help' 中的 'Note about fast-forwards' 小节。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin master
warning: 没有共同的提交
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
展开对象中: 100% (4/4), 完成.
来自 https://github.com/yangxiongj/java
 * branch            master     -> FETCH_HEAD
 * [新分支]          master     -> origin/master
fatal: 拒绝合并无关的历史
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push origin master
Username for 'https://github.com': 1941456312@qq.com       
Password for 'https://1941456312@qq.com@github.com': 
To https://github.com/yangxiongj/java
 ! [rejected]        master -> master (non-fast-forward)
error: 无法推送一些引用到 'https://github.com/yangxiongj/java'
提示：更新被拒绝，因为您当前分支的最新提交落后于其对应的远程分支。
提示：再次推送前，先与远程变更合并（如 'git pull ...'）。详见
提示：'git push --help' 中的 'Note about fast-forwards' 小节。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin master
来自 https://github.com/yangxiongj/java
 * branch            master     -> FETCH_HEAD
fatal: 拒绝合并无关的历史
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin/master
fatal: 'origin/master' does not appear to be a git repository
fatal: 无法读取远程仓库。

请确认您有正确的访问权限并且仓库存在。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull master
fatal: 'master' does not appear to be a git repository
fatal: 无法读取远程仓库。

请确认您有正确的访问权限并且仓库存在。
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin master
来自 https://github.com/yangxiongj/java
 * branch            master     -> FETCH_HEAD
fatal: 拒绝合并无关的历史
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin master –allow-unrelated-histories
fatal: Couldn't find remote ref –allow-unrelated-histories
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git pull origin master --allow-unrelated-histories 
来自 https://github.com/yangxiongj/java
 * branch            master     -> FETCH_HEAD
Merge made by the 'recursive' strategy.
 .gitignore | 23 +++++++++++++++++++++++
 README.md  |  2 ++
 2 files changed, 25 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push origin master
Username for 'https://github.com': 1941456312@qq.com
Password for 'https://1941456312@qq.com@github.com': 
对象计数中: 7, 完成.
Delta compression using up to 4 threads.
压缩对象中: 100% (5/5), 完成.
写入对象中: 100% (7/7), 105.84 KiB | 6.23 MiB/s, 完成.
Total 7 (delta 0), reused 0 (delta 0)
To https://github.com/yangxiongj/java
   733ef51..f6f3510  master -> master
yangxiong@yangxiong-System-Product-Name:~/桌面/书籍$ git push origin master

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


23.git remote命令用于管理主机名。
与一个远程仓库建立绑定关系
现在,我们根据GitHub的提示示,在本地的learngit仓库下运行行命令:
$ git remote add origin git@github.com:用户名/learngit.git(仓库名.git,在下载的路径中找就可以了)

删除分支恢复教程 https://blog.csdn.net/fdipzone/article/details/50616386

idea+git https://blog.csdn.net/autfish/article/details/52513465 

忽略文件 https://blog.csdn.net/qq_18601953/article/details/78395852

修改提交过后的内容 https://blog.csdn.net/sodaslay/article/details/72948722

Git 中.gitignore 使用和.gitignore 无效的解决方法 https://www.jianshu.com/p/e5360fa04152

git 笔记 https://github.com/michaelliao/learngit/commit/7afa768ed9138541484d6de4307055d7fe937046

git 命令大全 https://www.jianshu.com/p/590c88295a8c

git 取消mager https://blog.csdn.net/dliteng163com/article/details/52176027

中文乱码问题
git config --global core.quotepath false
export LESSCHARSEt=UTF-8
开启颜色显示
git config --global color.ui true

git status -s

成一行显示
$ git log --pretty=oneline

去某一分支
git reset --hard commit_id

拒绝合并无关的历史 
git branch --set-upstream-to=origin/master master   建立关联
git pull --allow-unrelated-histories    (忽略版本不同造成的影响)


##git 学习路线
    创建 远程仓库 可以在 github    码云 等建免费的远程仓库账号
    创建好帐号创建 ssh-key  将key放到远程仓库里
    git remote命令用于管理主机名  连接远程仓库
    学习基础命令
    创建分支 切换分支 add commit push pull   fetch 等等    看上面就可以了
    学习时光穿梭机
    学习异常处理


    
