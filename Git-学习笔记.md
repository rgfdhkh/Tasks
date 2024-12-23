# Git 学习笔记



## 一 、What is Git ?  And 起源小故事😃

**Git 是一个开源的==分布式版本控制系统==，用于敏捷高效地处理任何或小或大的项目。**

**Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个==开放源码的版本控制软件==。**

*很多人都知道，Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。*

*Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？*

*事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！*

*你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。*

*不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。*

*安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。*

*Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：*

*Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。*

*Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。*

*历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。*



## 二 、Git 与SVN的区别

Git不仅仅是个版本控制系统，它也是个==内容管理系统==(CMS)，==工作管理系统==等。

那SVN又是什么呢？

#### **下面是我搜索到的一些关于SVN的介绍及一些特点**和局限性

SVN（Subversion）是一个开源的==集中式版本控制系统==，由Apache软件基金会维护。它被广泛用于软件配置管理和版本控制，允许多个开发者协作开发项目，同时跟踪文件和目录的变更历史。

SVN 的一些关键特点：

1. **集中式版本控制**：所有的版本信息都存储在一个中央服务器上的==单一仓库中==，客户端通过检出（checkout）操作获得工作副本。

2. **原子提交**：SVN 支持原子性提交，即一次提交包含多个文件的变更，要么全部成功，要么全部失败。

3. **分支和标签**：SVN 支持创建分支和标签，用于开发新功能或发布版本。

4. **变更跟踪**：SVN 能够跟踪文件的添加、删除、修改和移动操作。

5. **冲突解决**：在多个开发者对同一文件进行更改时，SVN 可以帮助识别和解决冲突。

6. **权限管理**：SVN 允许管理员设置访问控制，以限制对仓库的访问。

7. **命令行界面**：SVN 提供了一个功能丰富的命令行界面，用于执行版本控制操作。

8. **图形用户界面**：除了命令行，SVN 也有多种图形用户界面（GUI）客户端可供选择。

9. **兼容性**：SVN 可以与多种工具和集成开发环境（IDE）集成，如 Eclipse、Visual Studio 等。

10. **跨平台**：SVN 可以在多种操作系统上运行，包括 Windows、Linux 和 macOS。

尽管 SVN 提供了许多有用的功能，但它也有一些局限性，比如分支管理不如分布式版本控制系统（如 Git）灵活。因此，尽管 SVN 仍然是许多项目的选择，Git 等分布式版本控制系统因其灵活性和强大的分支管理功能而越来越受欢迎。

在学习中我了解到，Git 和 SVN是两种流行的版本控制系统，它们在设计理念和工作方式上有一些显著的不同。以下是它们之间的一些

#### **主要区别：**

1. **分布式 vs 集中式**：
   
   - **Git** 是一个分布式版本控制系统，意味着每个开发者的本地仓库都是一个完整的版本库，包含了完整的历史记录和代码。这使得在没有网络连接的情况下也能进行大部分版本控制操作。

     <img src="https://liaoxuefeng.com/books/git/what-is-git/svn-vs-git/decentralized.jpg" alt="distributed-repo" style="zoom: 67%;" />
   
     <center>Git是介样子的☝️</center>
   
   - **SVN** 是一个集中式版本控制系统，所有的历史记录和代码都存储在一个中央服务器上。开发者的本地副本只是代码的一个镜像，没有完整的历史记录。
   
     <img src="https://liaoxuefeng.com/books/git/what-is-git/svn-vs-git/centralized.jpg" alt="central-repo" style="zoom:80%;" />
   
     <center>SVN是介样子的☝️</center>
   
2. **数据存储方式**：
   
   - **Git** 将内容**以对象的形式存储**，每个文件的变更都会生成一个新的对象，并用 **SHA-1 哈希值**(查了，没看懂😭😭😭)来标识。这种方式使得 Git 能够高效地处理**大量的小文件**和**频繁的提交**。
   - **SVN** 则是将文件的**元数据**存储在 `.svn` 文件夹[^1]中，这种方式使得 SVN 在处理**大文件**和**二进制文件**时更加高效。
   
3. **分支管理**：
   
   - **Git** 的分支非常轻量级，创建和合并分支都非常**快速和简单**。Git 鼓励开发者频繁地使用分支来进行功能开发和实验。
   - **SVN** 的分支管理相对**复杂和缓慢**，创建分支需要复制整个项目的历史，这在大型项目中可能会非常耗时。
   
4. **全局版本号**：
   
   - **SVN** 有一个**全局的版本号**（Revision）[^2]，每次提交都会增加这个版本号，使得追踪变**更变得简单**。
   - **Git** 没有全局版本号，每个提交都是通过 SHA-1 哈希值来标识的。虽然这提供了**更高的灵活性**，但也意味着需要通过其他方式（如标签）来追踪特定的版本。
   
   ###### ***各有各的优势和劣势***
   
5. **内容完整性**：
   
   - **Git** 使用 SHA-1 哈希算法来确保内容的完整性，这使得 Git 在处理代码时非常安全，<u>即使在网络问题或磁盘故障的情况下也能保持数据的完整性</u>。
   - **SVN** 也提供了数据完整性的保护，但<u>不如 Git 那样强大和灵活</u>。
   
6. **非线性开发**：
   
   - **Git** 支持非线性开发，<u>开发者可以在不同的分支上并行工作，然后合并他们的工作</u>。
   - **SVN** 虽然也支持并行开发，但由于其分支管理的复杂性，这在 SVN 中不如在 Git 中常见。
   
7. **合并和冲突解决**：
   - **Git** <u>提供了强大的合并和冲突解决工具，使得合并不同分支的工作变得相对简单</u>。
   - **SVN** 在合并和冲突解决方面不如 Git 强大，尤其是在处理复杂的合并时。

8. **社区和生态系统**：
   
   - **Git** 拥有一个**非常活跃的社区和丰富的生态系统**，提供了大量的工具和集成选项。
   - **SVN** 也有一个稳定的社区，但相对来说，生态系统没有 Git 那么丰富。

总的来说，Git 和 SVN 各有优势，选择哪一个取决于团队的需求、工作流程和项目类型。Git 的灵活性和强大的分支管理功能使其成为许多开发者的首选，尤其是在需要频繁迭代和协作的项目中。而 SVN 的集中式管理对于需要严格控制访问权限和变更的项目来说可能更加适合。



## 三 、 在Windows上安装Git

##### 1、在Windows上使用Git，可以从[Git官网](https://git-scm.com/downloads "https://git-scm.com/downloads")直接下载安装程序，然后按默认选项安装即可。

##### 2、安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功咯！🎊🎊🎊

![install-git-on-windows](https://liaoxuefeng.com/books/git/install-git/win.jpg)

**安装完成后，还需要最后一步设置，在命令行输入：**

==（空格注意不要漏了！！！）==

```plain
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

例：

![              ](D:/Users/%E4%B8%81%E5%B8%B8%E6%9D%B0/Desktop/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20241107223117.png)



## 四 、创建版本库（仓库）

#### 版本库是什么

版本库又名**仓库**（Repository），你可以简单理解成一个**目录**，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”。

#### **如何创建一个版本库**

##### 第一步，选择一个合适的地方，创建一个空目录：

```plain
$ mkdir learngit
$ cd learngit
$ pwd
/合适的位置=>空目录/
```

`pwd`命令用于显示当前目录。

##### 第二步，通过`git init`命令把这个目录变成Git可以管理的仓库：

```plain
$ git init
Initialized empty Git repository in /合适的位置/
```

Git瞬间就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），可以发现当前目录下多了一个`.git`的目录（到目录中去看 没有的话点击上方的“查看”->“显示”->“隐藏的项目”），这个目录是Git来跟踪管理版本库的，==但没事千万不要手动修改这个目录里面的文件，不然<u>改乱了，就把Git仓库给破坏了</u>==。



*注：使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。*



## 五 、添加文件到版本库

在此之前，首先这里再明确一下，所有的版本控制系统，**其实只能跟踪文本文件的改动**，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。<u>而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来</u>，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。

不幸的是，Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动的，前面我们举的例子只是为了演示，如果要真正使用版本控制系统，就要以纯文本方式编写文件。

因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的UTF-8编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。

*==注意==：千万不要使用Windows自带的**记事本**编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们在每个文件开头添加了0xefbbbf（十六进制）的字符，会遇到很多不可思议的问题，比如，网页第一行可能会显示一个“?”，明明正确的程序一编译就报语法错误，等等，都是由记事本的弱智行为带来的。**建议下载 [Visual Studio Code](https://code.visualstudio.com/) 代替记事本，不但功能强大，而且免费！***



编写一个`readme.txt`文件，内容如下：

```plain
Git is a version control system.
Git is free software.
```

==一定要放到`**learngit**`目录下（子目录也行）==，<u>因为这是一个Git仓库，放到其他地方Git再厉害也找不到这个文件。</u>

*和把大象放到冰箱需要3步相比，把一个文件放到Git仓库只需要两步。*

* 第一步，用命令`git add`告诉Git，把文件添加到仓库：

```plain
$ git add readme.txt
```

执行上面的命令，没有任何显示，这就对了，Unix的哲学是“没有消息就是好消息”，说明添加成功。

* 第二步，用命令`git commit`告诉Git，把文件提交到仓库：

```plain
$ git commit -m "wrote a readme file"
[master (root-commit) eaadf4e] wrote a readme file
 1 file changed, 2 insertions(+)
 create mode 100644 readme.txt
```

简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

*注：**嫌麻烦不想输入`-m "xxx"`行不行？***

*<u>“ ==哒咩哦== ”🙅🙅‍♂️🙅‍♀️****</u>*

**这是很重要的，不能不写，未来做项目，是很重要的习惯，会让人知道你改了些什么bug**

######  *git commit -m 作用：*

1. ***基本用途**   - `git commit -m`是Git工具中用于提交代码更改的命令组合。`git commit`命令本身是将暂存区（通过`git add`命令添加文件后的区域）的内容提交到本地仓库的操作。`-m`是一个选项，用于提供提交消息（commit message）。   - 提交消息是对这次提交所做更改的一个简短描述。例如，你可以写“修复了登录页面的密码验证漏洞”或者“添加了新的用户注册功能”等。这些消息可以帮助你和其他开发人员在查看提交历史时，快速了解每次提交的主要内容。* 
2.  ***重要性***   
   * ***代码审查**：当团队成员进行代码审查时，清晰的提交消息能够让审查者快速明白提交的意图。比如，一个包含多个文件修改的复杂提交，如果没有好的提交消息，审查者可能需要花费大量时间去理解每个文件的修改目的。而有了准确的提交消息，如“重构数据库查询逻辑以提高性能”，审查者就可以直接关注这个重点。*
   * ***版本回退和历史追溯：**在项目开发过程中，可能会出现需要回退到某个特定版本的情况。通过查看提交消息，可以更容易地确定要回退到哪个版本。例如，如果发现新功能引入了严重的错误，你可以通过提交消息查找在添加该功能之前的一个稳定版本进行回退。假设提交消息记录了“更新支付系统接口”，当支付系统出现问题时，你可以根据这些消息追溯相关的更改。* 
   * ***项目协作和沟通**：对于一个多人协作的项目，提交消息是团队成员之间沟通的重要方式。它可以让其他成员了解你的工作进展和意图，促进团队协作的效率。例如，当一个成员看到另一个成员提交的消息是“合并分支A到主分支以整合新功能”，就能够理解代码库的更新情况。*

`git commit`命令执行成功后会告诉你：

`1 file changed`：1个文件被改动*（我们新添加的文件）*；

`2 insertions`：插入了两行内容*（文件有两行内容）*。



## 六、Git基本操作的了解

#### **基本操作包括：**

- **初始化仓库**：
  `git init` 初始化一个新的Git仓库。
- **检出仓库**：
  `git clone [url]` 克隆一个远程仓库到本地。
- **添加文件**：
  `git add [file]` 添加文件到<u>暂存区</u>[^3]。
- **提交更改**：
  `git commit -m "commit message"` 提交暂存区的文件到仓库。
- **查看状态**：
  `git status` 查看文件状态。
- **分支管理**：
  `git branch [branch-name]` *创建* 新分支，
  `git checkout [branch-name]` *切换* 分支。
- **合并分支**：
  `git merge [branch-name]` 合并指定分支到当前分支。
- **查看日志**：
  `git log` 查看提交历史。
- **撤销操作**：
  `git reset` 可以撤销提交或修改。*==记忆点:<reset：重建 ~~ 撤销提交或修改>==*



## 七、进一步学习GitHub的使用

GitHub是一个基于Git的代码托管平台，提供了额外的功能，如项目管理、代码审查、CI/CD[^4]等。

**与他人协同做项目的基本流程：**

- **Fork项目**[^5]：在GitHub上找到你想要贡献的项目，点击Fork按钮，复制该项目到你的GitHub账户下。
- **克隆Fork的项目**：使用`git clone`命令克隆你的Fork版本的仓库到本地。
- **创建分支**：在本地创建一个新的分支来开发你的功能或修复。
- **推送更改**：将你的更改推送到你的远程Fork仓库。
- **创建Pull Request (PR)**：在GitHub上，向你Fork的项目提交一个Pull Request，请求将你的更改合并到原项目中。
- **代码审查**：项目维护者会审查你的PR，并可能要求你进行修改。
- **合并PR**：一旦PR被接受，维护者会将你的更改合并到主分支。



## 八、使用Git Bash将本地项目推送到远程Github仓库

**Git Bash**是一个在Windows上模拟Unix的命令行工具，<u>它允许你使用Git命令</u>。

**基本步骤包括：**

- **初始化Git仓库**：在项目目录中打开Git Bash，运行`git init`。
- **添加远程仓库**：使用`git remote add origin [url]`将远程仓库地址添加到你的本地仓库。
- **推送到远程仓库**：使用`git push -u origin main`将本地的更改推送到远程仓库的主分支。



## 九、认清GitHub和Git的关系

* **Git**：是一个开源的分布式版本控制系统，用于跟踪文件的更改。

* **GitHub**：是一个基于Web的Git仓库托管服务，提供了额外的工具和功能，如项目管理、代码审查、CI/CD等。









## 另：注释

[^1]:是 Subversion（简称 SVN）版本控制系统用来存储版本控制元数据的地方。 
[^2]:指的是在整个系统或软件中通用的版本标识。它可以用来确定软件或系统在某个特定时间点的整体版本状态。
[^3]:在 Git 中，暂存区（Staging Area）是一个非常重要的概念。它就像是一个 “中间地带”，位于工作区（Working Directory）和本地仓库（Local Repository）之间。当你在工作区对文件进行修改后，需要先将这些修改添加到暂存区，然后才能将暂存区的内容提交到本地仓库。可以把它想象成一个准备提交的文件清单。你可以选择将工作区中的部分文件或者全部文件的修改添加到这个清单中，在提交的时候，实际上是将暂存区中的内容作为一个整体提交到本地仓库。
[^4]:CI/CD 是持续集成（Continuous Integration）和持续部署（Continuous Deployment）的简称。持续集成是指频繁地将开发人员的代码合并到一个共享的代码仓库中，并自动运行一系列的测试和构建过程，以确保代码的质量和稳定性。例如，开发团队中的成员在完成一部分功能开发后，将代码提交到代码仓库，持续集成系统会自动触发构建、测试等流程，快速发现代码中的问题。持续部署则是在持续集成的基础上，自动将通过测试的代码部署到生产环境或其他目标环境中，实现快速交付软件的目的。这样可以大大缩短软件的发布周期，提高开发效率和软件的质量。
[^5]:指的是在软件开发中，对一个已有的项目进行复制，从而创建一个新的独立项目分支。通常在开源项目中，开发者可以 Fork 别人的项目来进行修改、改进或者基于其进行新的开发。例如在 GitHub 等代码托管平台上，开发者可以很方便地 Fork 一个感兴趣的项目，然后在自己的 Fork 版本上进行开发工作。
