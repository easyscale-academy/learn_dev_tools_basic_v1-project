---
description: "学完这个 Task, 你能在 Mac 上装好 VS Code, Terminal 或 Ghostty, GitHub Desktop 这三件套, 看懂 Terminal 到底是什么, 并搭好一套干净的项目文件夹结构."
---

# Mac 本地开发环境快速搭建

> 一句话说明这个 Task 教什么: 把开发的主战场从 GitHub Codespace 搬回你自己的 Mac, 装好三件基本工具, 并学会用 Terminal.

## 1. 概览

恭喜你完成了上一个 Task, 装好了 mise. 你现在已经拥有了一个万能遥控器来管理开发工具.

之前你一直在用 GitHub Codespace. Codespace 很棒, 它就像一个云端的一次性工作间, 你可以放心大胆地折腾, 搞砸了大不了删掉重来, 对刚开始学习的人来说是一个非常安全的练习场.

但现在你已经学会了 mise. 有了 mise, 在本地电脑上安装和管理开发工具变得又简单又安全, 因为 mise 会帮你把所有工具都管理得井井有条, 不会把你的系统搞乱. 所以现在是时候把主战场搬回你自己的 Mac 了.

顺带说清楚一件事: 这三件套不是专门为程序员准备的. 现在 AI agent 已经强大到可以帮你写代码, 改配置, 自动化各种日常工作, 你完全可以不学任何编程语言, 只靠这几件工具搭好舞台, 让 AI agent 在上面替你干活. 学这些工具的意义是: VS Code 让你看得见 AI 改了什么; Terminal 让 AI (以及你自己) 有地方运行命令; GitHub Desktop 则给你一颗后悔药, 不管 AI 帮你改坏了什么, 你都能一键退回改之前的样子. 开发者当然也用这一整套东西, 但这门课已经把门槛拉到最低, 不懂编程完全不影响你把它们用起来.

---

## 2. 学习目标

学完这个 Task, 你将能够:

1. 在 Mac 上装好 VS Code, Terminal (或 Ghostty), GitHub Desktop 这三件基本工具
2. 说清楚 Terminal 是什么, 为什么每个开发者都绕不开它, 并能用几个最基本的命令在文件系统里移动
3. 理解 User Folder 的概念, 建立一个清爽的项目文件夹结构

---

## 3. 前置知识

- 完成了上一个 Task, 已经理解 mise 是做什么用的
- 有一台 Mac. 如果暂时没有, 可以继续用 GitHub Codespace 完成后面的课程, 但这个 Task 里 "装本地软件" 的部分需要跳过, 等有 Mac 之后再回来补

---

## 4. 为什么现在换成本地开发

本地开发的好处很明显: 速度快, 不用等 Codespace 启动, 打开电脑就能干活; 文件就在你电脑上, 随时可以找到; 不受网络影响, 断网了照样写代码; 也不用担心 Codespace 的免费时长用完.

当然, Codespace 你以后还是可以继续用. 当你想尝试一些新东西, 又不想影响本地环境的时候, 开一个 Codespace 练练手, 仍然是个很好的选择. 所以我们的策略是: 日常开发用本地, 探索新东西用 Codespace.

本地开发需要哪些工具呢? 其实就三样东西: 一个终端, 一个代码编辑器, 一个 Git 管理工具. 我们一个个来装.

---

## 5. Terminal 是什么, 为什么每个开发者都要会用

在装任何东西之前, 先把 Terminal 这件事讲清楚, 因为它是你接下来要用的所有工具 (mise, git, python, Claude Code) 共同的入口.

Terminal, 中文常叫终端或命令行, 就是那个只有文字, 没有图标的黑色窗口. 你在里面打字, 按回车, 电脑就执行一条命令. 听起来比鼠标点点点原始, 但它有几个图形界面很难替代的优点:

- **精确**: 鼠标点击是模糊的, 敲一条命令是精确的. 你上一个 Task 里输入的 `mise use python@3.12`, 就没有办法靠点鼠标完成
- **可复制**: 一条命令可以原样复制给同事, 写进文档, 或者交给 AI agent 执行; 一连串鼠标操作很难描述清楚
- **是几乎所有开发工具的默认语言**: mise, git, npm, Python, Claude Code, 这些工具首先都是命令行程序, 图形界面只是后来加上去的外壳

Mac 自带一个叫 Terminal 的应用, 能用, 界面比较朴素. 在 Terminal 或任何一个终端应用里, 你实际打交道的是一个叫 shell 的程序 (前面提到过的 bash, zsh 都是 shell), 它负责读懂你打的命令并执行.

刚接触 Terminal, 记住下面这几个命令就够用了:

| 命令 | 作用 | 例子 |
| :--- | :--- | :--- |
| `pwd` | 显示你当前在哪个文件夹 | `pwd` |
| `ls` | 列出当前文件夹里的文件和子文件夹 | `ls` |
| `cd` | 切换到某个文件夹 | `cd Documents` |
| `cd ..` | 回到上一级文件夹 | `cd ..` |
| `clear` | 清空屏幕, 不影响已经运行的东西 | `clear` |

有一件事值得提前说清楚: Terminal 里没有回收站. 用命令删除的文件通常是直接消失, 找不回来. 这门课不会教你用命令删文件, 但了解这一点, 会让你在 Terminal 里操作时更谨慎.

学会这几个命令, 你就能在 Terminal 里认路了. 至于更高级的用法, 比如给常用命令起别名 (alias), 定制 zsh 的主题和插件, 或者用 oh-my-zsh 这类框架把 Terminal 变得更好看更好用, 这门课不会展开教. 更好的做法是带着你的实际场景去问 AI agent, 比如:

> 我在 Mac 上用 Terminal (或 Ghostty), 刚学会 `cd`, `ls` 这几个基本命令. 我想让我的 Terminal 用起来更顺手, 比如给几条常用命令起个别名, 或者了解一下 oh-my-zsh 这类插件框架值不值得装. 请先问我平时最常敲哪些命令, 再针对性地教我怎么配置, 每一步讲清楚具体在改哪个文件.

---

## 6. 工具一: VS Code, 代码编辑器

VS Code, 全称 Visual Studio Code, 是目前最流行的代码编辑器. 如果你在 GitHub Codespace 里写过东西, 你已经见过它了, Codespace 里用的正是网页版的 VS Code. 现在我们要在 Mac 上装一个本地版.

安装方法:

1. 打开浏览器, 访问 [code.visualstudio.com](https://code.visualstudio.com)
2. 点击 Download 按钮, 下载 Mac 版
3. 下载完成后, 打开 `.dmg` 文件, 把 VS Code 拖到 Applications 文件夹里
4. 去 Applications 文件夹里双击打开 VS Code

本地的 VS Code 界面和 Codespace 里的几乎一模一样, 以后你用它打开项目文件夹, 编辑代码, 体验是一致的.

---

## 7. 工具二: Ghostty 或系统自带 Terminal

上一节讲的 Terminal 概念, 落到 Mac 上有两个具体的选择. Mac 自带一个叫 Terminal 的应用, 能用. 如果你想要一个颜值更高, 体验更好的终端, 可以试试 **Ghostty**, 它速度快, 界面好看, 而且完全免费. 如果你觉得系统自带的够用了, 完全可以跳过这一步, 直接用自带的.

安装方法:

1. 打开浏览器, 访问 [ghostty.org](https://ghostty.org)
2. 下载 Mac 版本
3. 下载完成后, 打开 `.dmg` 文件, 把 Ghostty 拖到 Applications 文件夹里
4. 去 Applications 文件夹里双击打开 Ghostty

打开后试着输入 `mise` 看看, 如果你之前在 Mac 上已经装好了 mise, 这里应该能看到帮助信息. 以后不管是用 mise 装工具, 还是运行 Python, Claude Code 这些命令, 都在这个窗口里操作.

---

## 8. 工具三: GitHub Desktop, Git 管理工具

GitHub Desktop 是一个图形界面的 Git 管理工具, 让你不用记 Git 命令, 点点鼠标就能管理代码的版本.

安装方法:

1. 打开浏览器, 访问 [desktop.github.com](https://desktop.github.com/download/)
2. 下载 Mac 版本
3. 下载完成后, 安装并打开
4. 用你的 GitHub 账号登录

装好以后, 你就可以用它来 clone 项目到本地, 也可以把本地的修改同步回 GitHub.

这里就是前面说的后悔药: GitHub Desktop 会记录每一次改动, 不管是你自己改的, 还是 AI agent 帮你改的. 改坏了, 打开 GitHub Desktop 的 History, 找到改动之前的那个版本, 一键就能退回去. 这也是为什么这门课不担心 AI 帮你改错东西, 有这颗后悔药兜底, 放心大胆地让 AI 干活就行.

---

## 9. 关于 User Folder, 你的文件都放在哪

在开始用这些工具之前, 先聊一个基础概念, User Folder, 用户文件夹.

打开 Mac 的 Finder, 你会在左边栏看到 Documents, Downloads, Desktop 这些常见文件夹, 它们都在一个地方, 叫做你的 User Folder. 电脑在设计上假设可能有多个人使用同一台电脑, 每个人都是一个 User, 有自己独立的文件夹存放各自的东西, 只不过你的个人电脑一般只有你一个人用.

你的 User Folder 路径是:

```text
/Users/你的用户名/
```

比如你的用户名是 `alice`, 那就是 `/Users/alice/`. 你的 Documents, Downloads 其实就是 `/Users/alice/Documents`, `/Users/alice/Downloads`.

知道了这个概念之后, 建议你在 Documents 下面创建一个叫 `GitHub` 的文件夹, 专门用来存放从 GitHub clone 下来的项目:

```text
/Users/你的用户名/
  Documents/
    GitHub/
      project-a/
      project-b/
      learn-xxx/
```

每个子文件夹就是一个 Git 仓库. 这样组织起来很清爽, 你所有的项目都在一个地方, 一目了然. 用 GitHub Desktop clone 项目的时候, 它会问你要把项目放在哪里, 选这个 `GitHub` 文件夹就好.

---

## 10. 接下来用 mise 装什么

现在你的 Mac 上已经有了三件套: VS Code 写代码, Ghostty 或 Terminal 跑命令, GitHub Desktop 管理项目. 接下来的课程会用到 Python 和 Claude Code, 这些都可以用 mise 装:

```bash
mise use python@3.12
mise use npm:@anthropic-ai/claude-code
```

分分钟就能在你的电脑上跑起来.

---

## 11. 练习

### 练习 1: 三件套齐活, 并在 Terminal 里走一遍

**目标:** 把三件套装齐, 并证明你能在 Terminal 里找到路.

**怎么做:**

1. 安装 VS Code, 打开确认没有报错
2. 安装 Ghostty, 或者确认你会用系统自带的 Terminal
3. 安装 GitHub Desktop 并登录
4. 打开终端, 依次输入 `pwd`, `ls`, `cd Documents`, `pwd`, `cd ..`
5. 在 Documents 下创建 `GitHub` 文件夹

**你会观察到:**

每敲一条命令, 终端提示符前面显示的路径都会跟着变化, 这就是 `pwd` 在告诉你你现在的位置.

> **关键洞见:** 迷路了不用怕, `pwd` 随时能告诉你身在何处, `cd ..` 随时能带你回头.

---

## 12. 回顾: 我们学到了什么

- 日常开发用本地, 探索新东西用 Codespace, 两者互补
- 三件套, VS Code 加 Terminal (或 Ghostty) 加 GitHub Desktop, 代码编辑, 命令行, 项目管理一套搞定
- Terminal 不是可有可无的装饰, 它是 mise, git, Python, Claude Code 这些工具共同的默认入口, `pwd`, `ls`, `cd` 是最基础的三个动作
- 在 Documents/GitHub/ 下统一管理项目, 每个子文件夹就是一个 Git 仓库

---

## 13. 导师寄语

**为什么这个练习重要:**

之前用 Codespace, 就像在别人的厨房里做饭, 食材和工具都是现成的, 但用完还得收拾走人. 现在你在自己的 Mac 上搭好了开发环境, 这就是你自己的工作台了: VS Code 是切菜板, Terminal 是灶台, GitHub Desktop 是储物柜, mise 是帮你管理所有厨具的助手.

**关键洞见:**

- 刚开始可能会担心, 在本地装这些东西会不会搞乱电脑. 放心, 有了 mise, 你的开发工具都被管理得整整齐齐, 真正需要小心的只有 Terminal 里的删除操作
- Terminal 现在看起来陌生, 但它是你接下来这门课, 乃至以后所有开发工作里最常打交道的窗口, 值得现在就花点时间熟悉它

**下一步:**

下一个 Task 会带你打开一个 GitHub 项目文件夹, 学会用 VS Code 找到文件, 复制它的路径, 这是你和 AI agent 沟通的基础.

---

## 14. 速查

**Terminal 基本命令:**

```bash
pwd        # 我在哪
ls         # 这里有什么
cd 目标文件夹  # 去那里
cd ..      # 回上一级
```

**关键路径:**

- `/Users/你的用户名/`: 你的 User Folder
- `/Users/你的用户名/Documents/GitHub/`: 建议存放所有 Git 项目的地方

**下载地址:**

- VS Code: [code.visualstudio.com](https://code.visualstudio.com)
- Ghostty: [ghostty.org](https://ghostty.org)
- GitHub Desktop: [desktop.github.com](https://desktop.github.com/download/)
