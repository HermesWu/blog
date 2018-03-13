# morning
#### 关闭浏览器安全策略
```
/Applications/Google Chrome Canary.app
open -a "Google Chrome Canary" --args --disable-web-security  --user-data-dir
/Applications/Google Chrome.app
```
#### Webkit 内核浏览器 background-size 失效 bug
webkit内核浏览器，背景相关bug解决办法，把属性值都放在`background:url()`后面
#### a标签导航垂直居中
`line-height`
#### margin 合并
```
块级上下文： overflow： 除了visible
```
#### 居中
```
inline-block 不可以margin auto居中，必须改成block margin
```
#### 垂直居中
`flex`
#### IDE全名
```
Integrated Development Environment:
集成开发环境（IDE，Integrated Development Environment ）是用于提供程序
开发环境的应用程序，一般包括代码编辑器、编译器、调试器和图形用户界面等工具。集成
了代码编写功能、分析
```
#### git
```
git config --global user.name xxx #方便产品经理找（怼）你
git config --global user.email yyy #方便产品经理找（怼）你
git config --global push.default simple # 本来我写的是 matching，不过想
了想可能 simple 更好
git config --global core.quotepath false #防止文件名变成数字
git config --global core.editor "vim" # 使用vim编辑提交信息
```
###### 项目坑
```
git add src/app/router/home/home.component.html
```
###### 配置git

1. 进入 https://github.com/settings/keys
2. 如果页面里已经有一些 key，就点「delete」按钮把这些 key 全删掉。如果没有，就往下看
2. 点击 New SSH key，你需要输入 Title 和 Key，但是你现在没有 key，往下看
2. 打开 Git Bash
1. 复制并运行 rm -rf ~/.ssh/* 把现有的 ssh key 都删掉，这句命令行如果你多打一个空格，可能就要重装系统了，建议复制运行。
1. 运行 ssh-keygen -t rsa -b 4096 -C "你的邮箱"，注意填写你的邮箱！
1. 按回车三次
1. 运行 cat ~/.ssh/id_rsa.pub，得到一串东西，完整的复制这串东西
1. 回到上面第 3 步的页面，在 Title 输入「我的第一个 key」
1. 在 Key 里粘贴刚刚你你复制的那串东西
1. 点击 Add SSH key
1. 回到 Git Bash


#### 本地使用
###### 初始化
1. 创建目录作为我们的项目目录：mkdir git-demo-1
1. 进入目录 cd git-demo-1
1. git init，这句命令会在 git-demo-1 里创建一个 .git 目录
1. ls -la 你就会看到 .git 目录，它就是一个「仓库」，不要进去看，这仓库里面有毒，别进去！
1. 在 git-demo-1 目录里面添加任意文件，假设我们添加了两个文件，分别是 index.html 和 css/style.css
1. 运行 git status -sb 可以看到文件前面有 ?? 号，这个 ?? 表示 git 一脸懵逼，不知道你要怎么对待这些变动。
1. 使用 git add 将文件添加到「暂存区
1. 再次运行 git status -sb，可以看到 ?? 变成了 A
1. 使用 git commit -m "信息" 将你 add 过的内容「正式提交」到本地仓库（.git就是本地仓库），并添加一些注释信息，方便日后查阅
1. 你可以一个一个地 commit
1. 再再次运行 git status -sb，发现没有文件变动了，这是因为文件的变动已经记录在仓库里了。
1. 这时你使用 git log 就可以看到历史上的变动

###### 日常操作
```
git push -u origin :hostex-v-w
git push -u origin hostex-v-w:hostex-v-w
git log --all --oneline
git add . && git commit -m'pc端首页，宽度100%,修改1'
git status -sb

运行 git status -sb 可以看到文件前面有 ?? 号
这个 ?? 表示 git 一脸懵逼，不知道你要怎么对待这些变动。
git add . 意思是把当前目录（.表示当前目录）里面的变动都加到「暂存区」
再次运行 git status -sb，可以看到 ?? 变成了 A
A 的意思就是添加，也就是说你告诉 git，这些文件我要加到仓库里
使用 git commit -m "信息" 将你 add 过的内容「正式提交」到
本地仓库（.git就是本地仓库），并添加一些注释信息，方便日后查阅
再再次运行 git status -sb，发现没有文件变动了，这是因为文件的变
动已经记录在仓库里了。
```
###### 文件改动
1. 此时你如果想让改动保存到仓库里，你需要先 git add css/style.css 或者也可以 git add .
1. 注意，由于这个 css/style.css 以前被我们 add 过，你往文章上面看，我们是 add 过 css/style.css 的，所以此处的 git add 操作可以省略，但我建议你使用 git 的前一个月，不要省略 git add。
1. 换句话说，每一次改动，都要经过 git add 和 git commit 两个命令，才能被添加到 .git 本地仓库里。
1. 再次运行 git status -sb 发现 M 有红色变成了绿色，红色和绿色有啥区别呢？别管它们的区别，记住我说的，先 add，再 commit，等你熟练之后再去理解区别。
1. 先形成肌肉记忆，在去形成大脑记忆！
1. 运行 git commit -m "更新 css/style.css"，这个改动就被提交到 .git 本地仓库了。再说一次，不要去 .git 目录里面，那里的东西你一无所知。
1. 再再次运行 git status -sb，会发现没有变更了，这说明所有变动都被本地仓库记录在案了。
1. 这里来透露一下 git status -sb 是什么意思：git status 是用来显示当前的文件状态的，哪个文件变动了，方便你进行 git add 操作。-sb 选项的意思就是，SB都能看懂，哈，这是开玩笑，-s 的意思是显示总结（summary），-b 的意思是显示分支（branch），所以 -sb 的意思是显示总结和分支。

###### 本地使用git总结
1. git init，初始化本地仓库 .git
1. git status -sb，显示当前所有文件的状态
1. git add 文件路径，用来将变动加到暂存区
1. git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
1. 如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。别看本教程废话那么多，其实就这一句有用！先 add 再 commit，行了，你学会 git 了。
1. git log 查看变更历史

#### 本地仓库上传到github

###### 小tips
```
看图，点击 SSH 按钮，点击 SSH 按钮，点击 SSH 按钮，我想你现在肯定不会忘了点击 SSH 按钮了吧~~~~
如果不点击这个按钮，你就会使用默认的 HTTPS 地址。但是千万不要使用 HTTPS 地址，因为 HTTPS 地址使用
起来特别麻烦，每次都要输入密码，而 SSH 不用输入用户名密码。
为什么 SSH 不用密码呢，因为你已经上传了 SSH public key。还记得吗？如果不记得，翻到本文第一部分
「配置 GitHub」章节。

得到新的命令 git remote add origin git@github.com:xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxx/git-demo-1.git，复制并运行它
复制第二行 git push -u origin master，运行它
刷新当前页面，你的仓库就上传到 GitHub 了！是不是特别简单？只要你按照我说的做，一丝不苟，即可。
```

###### 总结
1. git clone git@github.com:xxxx，下载仓库
1. git init，初始化本地仓库 .git
1. git status -sb，显示当前所有文件的状态
1. git add 文件路径，用来将变动加到暂存区
1. git commit -m "信息"，用来正式提交变动，提交至 .git 仓库
1. 如果有新的变动，我们只需要依次执行 git add xxx 和 git commit -m 'xxx' 两个命令即可。别看本教程废话那么多，其实就这一句有用！先 add 再 commit，行了，你学会 git 了。
1. git log 查看变更历史

###### 上传更新
1. git add 文件路径
1. git commit -m "信息"
1. git pull （相信我，你一定会忘记这一个命令）
1. git push

###### git大法
1. git remote add origin git@github.com:xxxxxxx.git 将本地仓库与远程仓库关联
1. git remote set-url origin git@github.com:xxxxx.git 上一步手抖了，可以用这个命令来挽回
1. git branch 新建分支
1. git merge 合并分支
1. git stash 通灵术
1. git stash pop 反转通灵术
1. git revert 后悔了
1. git reset 另一种后悔了
1. git diff 查看详细变化
2. 美化git ` git log --all --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative`

#### 命令行技巧
###### ~/.bashrc
###### 自动运行
1. 首先 touch ~/.bashrc 创建一下这个文件
1. start ~/.bashrc 选用编辑器编辑这个文件，内容为 echo 'Hi'
1. 你也可以用命令行编辑文件 echo "echo 'hi'" >> ~/.bashrc
1. 关闭退出 Git Bash，然后打开 Git Bash，是不是看到了 Hi，这说明每次进入 Git Bash，就会优先运行 ~/.bashrc 里面的命令
1. 重新编辑 ~/.bashrc，内容改为 cd ~/Desktop，重启 Git Bash，有没有发现默认就进入桌面目录了？

###### alias
1. 在 ~/.bashrc 里新增一行 alias f="echo 'frank is awesome'"，等于号两边不能有空格，你最好一个字都不要错。
1. 运行 source ~/.bashrc，作用是执行 ~/.bashrc
1. 运行 f，就会看到 frank is awesome
1. 也就是说，现在 f 就是 echo 'frank is awesome' 的缩写了，利用这个技巧，我们可以把很多常见的命令缩写一下，比如

#### iterm
###### 快捷键
1. ⌘ + Click：可以打开文件，文件夹和链接
1. ⌘ + n：新建窗口
1. ⌘ + t：新建标签页
1. ⌘ + w：关闭当前页
1. ⌘ + 数字 & ⌘ + 方向键：切换标签页
1. ⌥⌘ + 数字：切换窗口
1. ⌘ + enter：切换全屏
1. ⌘ + d：左右分屏
1. ⇧⌘ + d：上下分屏
1. ⌘ + ;：自动补全历史记录
1. ⇧⌘ + h：自动补全剪贴板历史
1. ⌥⌘ + e：查找所有来定位某个标签页
1. ⌘ + r & ⌃ + l：清屏
1. ⌘ + /：显示光标位置
1. ⌥⌘ + b：历史回放
1. ⌘ + f：查找，然后用 tab 和 ⇧ + tab 可以向右和向左补全，补全之后的内容会被自动复制， 还可以用 ⌥ + enter 将查找结果输入终端
1. 选中即复制，鼠标中键粘贴 

###### 坑
1. 不要随便用ps1
2. tree command not found 
    ```
    win: 删除ps1配置，sudo apt-get install tree   which tree
    mac: 安装 homebrew brew install tree which tree
    ```

#### 脚本

###### 写一个脚本

1. 找个地方新建文件，后缀随意，一般来说脚本的后缀是 .sh。我喜欢把脚本放在 ~/local 目录里。（我知道你没有这个目录，创建这个目录不就行了）

```
mkdir ~/local
cd ~/local
touch demo.txt
```

2. 编辑 demo.txt，内容如下

```
 mkdir demo
 cd demo
 mkdir css js
 touch index.html css/style.css js/main.js
 exit
```

3. （Windows 用户请跳过这一步）给 demo.sh 添加执行权限 `chmod +x demo.txt`

4. 在任意位置执行 `sh ~/local/demo.txt` 即可运行此脚本

```
cd ~/Desktop
sh ~/local/demo.txt
你会看到当前目录里多出一个 demo 目录，demo 目录里面还有一些文件
好了，这个 demo.txt 就是你写出的第一个 Bash 脚本了。
```

5. 将 ~/local 添加到 PATH 里
```
`cd ~/local; pwd` 得到 local 的绝对路径
创建 ~/.bashrc：`touch ~/.bashrc`
编辑 ~/.bashrc：`start ~/.bashrc`，在最后一行添加 `export PATH="local的绝对路径:$PATH"`
source ~/.bashrc
之前你要运行 `sh ~/local/demo.txt`，现在你只需要运行 demo.txt 就行了（想想为什么，道理显而易见）
```

6. demo.txt 的后缀 .txt 很无聊，删掉它

```
    mv ~/local/demo.txt ~/local/demo
    现在你只要运行 demo 就能执行该脚本了
```

###### 细节
1. PATH的作用
    你每次在 Bash 里面输入一个命令时（比如 ls、cp、demo），Bash 都会去 PATH 列表里面寻找对应的文件，如果找到了就执行。
2. 使用 type demo 可以看到寻找过程
3. 使用 which demo 可以看到寻找结果
4. 文件后缀的作用：毫无作用
5. 你以为一个文件以 .exe 结尾就一定可以双击吗？你以为一个文件以 .png 结尾就一定是图片吗？图样图森破

###### 添加参数，判断

```
if [ -d $1 ]; then
  echo 'error: dir exists'
  exit
else
  mkdir $1
  cd $1
  mkdir css js
  touch index.html css/style.css js/main.js
  echo 'success'
  exit
fi
```
执行 `demo && echo '结束'`

#### Node.js写脚本

上面我们写的脚本叫做 Bash Script（Bash脚本）。

JS 的全称叫做 JavaScript（Java脚本），虽然 JS 和 Java 没什么关系，但是 JS 依然是一种脚本。

1. 我们在 Bash 命令行里输入 Bash 命令，也可以在 Node.js 命令行里输入 JS 命令（<kbd>Ctrl</kbd> + <kbd>D</kbd> 退出）
2. Bash 脚本能做的事情，JS 脚本也能做。(sh demo.sh 对应 node demo.js）

###### JS切换目录

    ```
console.log(process.cwd()) // 打印当前目录
// process.chdir('~/Desktop'); // 这句话不行的，因为 JS 不认识 ~ 目录
process.chdir("/Users/frank/Desktop")
console.log(process.cwd()) // 打印当前目录
console.log 相当于echo
    ```
    js脚本创建目录
    ```
    Google nodejs create dir
    et fs = require("fs")
    fs.mkdirSync("demo")
    ```
    js脚本创建文件
    ```
    let fs = require('fs')
    fs.writeFileSync("./index.html", "")
    ```
    js脚本重写demo.sh
    ```
    1. 创建 ~/local/jsdemo.js 内容如下
    var fs = require('fs')

    var dirName = process.argv[2] //你穿的参数是从第二个开始的

    fs.mkdirSync("./" + dirName) //mkdir $1
    process.chdir("./" + dirName) //cd $1
    fs.mkdirSync('css') //mkdir css
    fs.mkdirSync('js') //mkdir js

    fs.writeFileSync("./index.html", "")
    fs.writeFileSync("css/style.css", "")
    fs.writeFileSync("./js/main.js","")

    process.exit(0)
    2.（Windows 用户跳过这一步）给 jsdemo.js 加上执行权限 chmod +x ~/local/jsdemo.js
    3. cd ~/desktop
    4. node ~/local/jsdemo.js zzz
    zzz 目录创建成功
    ```

    ```
    if [ -d $1 ]; then
        ho ‘$! 已经存在’
        exit
    else
        mkdir $1
        cd $1
        mkdir css js
        touch index.html css/style.css js/main.js
        echo \<\!DOCTYPE\> >> index.html
        echo \<title\>hello\</title\> >> index.html
        echo \<h1\>Hi\</h1\> >> index.html
        echo h1\{color\: red\;\} >> css/style.css
        echo var string \= \”Hello World\” >> js/main.js
        echo alert\(string\) >> js/main.js
        exit
    fi

    ```

###### shebang

我们每次执行 ~/local/jsdemo.js 都要用 node 来执行，能不能做到不加 node 也能执行呢（也就是指定执行环境），可以，在 jsdemo.js 第一行加上这一句即可：
`#!/usr/bin/env node`
1. 然后你就可以直接用 ~/local/jsdemo.js zzz 了（省得输入 node 了）。
1. 如果你已经把 ~/local 加入了 PATH，那么甚至可以直接输入 jsdemo.js zzz 来执行。
1. 如果你再把 jsdemo.js 的后缀 .js 去掉，就可以直接 jsdemo zzz 了。
注意，你每次执行前最好删掉 zzz 目录，以免发生冲突。








