#### 克隆仓库到本地的个人PC

首先到远程仓库中，点击 `Clone or download` 按钮，选择使用 `Use SSH`，然后点击复制链接按钮 ![16](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151156950.png/wm)

因为之前已经关联过个人PC的 `SSH` 公钥，所以直接在命令行中使用以下命令就可以克隆仓库到本地

```bash
#命令用法：git clone "你复制的仓库链接"
$ git clone git@github.com:shiyanlou-001/shiyoulou-001.git  
```

查看仓库内容，确定已经克隆到本地 ![17](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151177919.png/wm)





#### 3.2.1 添加／修改

要把一个文件添加或者更新内容到本地索引中，可以使用 `git add` 命令，命令的用法是 `git add <文件名|路径名>`，具体步骤如下

创建一个新的 `txt` 文件，文件的内容就写“这是一个新的文件” ![20](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151229111.png/wm)

将这个文件移动到仓库下，并用 `git add` 命令添加到本地索引库中 ![21](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151248549.png/wm)

#### 3.2.2 删除

要把仓库里的文件删除掉，可以使用 `git rm` 命令，用法是 `git rm [-rf] <文件名|路径>`，具体步骤如下

这里我们可以用一开始就存在的 `README.md` 文件来做实验，我们敲入 `git rm README.md`，然后可以发现文件已经删除了 ![22](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151264637.png/wm)

#### 3.2.3 撤销

要把仓库里的改动撤销回克隆下来的状态（注意，如果改动之后执行了提交就无法再撤销，只能从远程仓库重新克隆一份到本地），可以使用 `git reset` 命令，具体步骤如下

比如我们要把刚才删除的 `README.md` 文件给还原回来，就可以在仓库目录下，敲入 `git reset --hard HEAD` 来回退 ![23](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151281192.png/wm)

`cat` 一下，可以发现文件已经恢复了 ![24](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151294779.png/wm)



在仓库的每一次改动操作之后，推送同步到远程仓库之前，都需要对这一次或这一批次的操作做提交，命令为 `git commit`，用法是 `git commit -m "你的提交备注"`，只有做好提交动作，才可以开始推送改动到远程仓库同步

因为我之前已经撤销了仓库的改动，这里就重新创建一个新的文件，内容就写“测试”两个字，然后提交改动 ![25](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151312652.png/wm)





当我们提交了仓库的改动后，就可以开始推送改动的内容到远程仓库了，可以使用 `git push` 命令来推送，用法是 `git push [-u] origin <分支名>`，分支名默认是 master 具体步骤如下

第一次推送改动可以使用 `-u` 参数，使用之后会绑定你这一次的仓库分支名，这样的话下一次推送就不需要加上分支名了，如图，使用之后回提示已经绑定好分支，而且因为我们是 `HTTPS` 协议方式来克隆的仓库，所以每一次同步操作都需要输入用户名和密码 ![26](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151328349.png/wm)

然后我们到远程仓库去看一下，可以发现这个文件已经推送上来了，并且对应的行会显示之前提交操作的备注 ![27](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151341805.png/wm)



#### 3.6.1 查看仓库改动

首先我们可以通过 `git fetch` 命令查看有哪一些新改动，用法是在仓库目录下敲入 `git fetch origin` ![29](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151369594.png/wm)

#### 3.6.2 下拉仓库同步

确认好更新的内容后，下一步就是把更新给同步到本地仓库中了，通过 `git pull` 命令来实现，具体用法是 `git pull origin <分支名>`，分支名默认是 master，再查看一下目录，可以看到已经同步好了 ![30](https://doc.shiyanlou.com/document-uid472892labid3163timestamp1499151384192.png/wm)







初始化 git 库。

```
$ git init
```

用户配置（可选）：

```
$ git config --global user.name "你的用户名"
$ git config --global user.email "你的邮箱地址"
```

这一步不做也没关系，用户名和邮箱是你提交`commit`时的签名，在 Github 的仓库页面上会显示这次提交的用户，如果不做设置就会默认为该仓库的拥有者，做了则根据邮箱来匹配用户。



先在本地仓库做一次代码提交：

```
$ git add .
$ git commit -m 'commit my cv'
```

在项目页面找到你的仓库地址后输入：

```
$ git remote add origin 你的远程仓库地址
$ git push -u origin master
```