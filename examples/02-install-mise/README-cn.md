---
description: "学完这个 Task, 你能在 GitHub Codespace 里装好 mise, 看懂它为什么被叫做开发工具的万能遥控器, 并知道遇到它的进阶功能时该怎么去问 AI."
---

# 安装 mise: 你的开发工具管理总管家

> 一句话说明这个 Task 教什么: 在 GitHub Codespace 里从零装好 mise, 这是你在这门课里要学的第一个开发工具, 后面所有工具都靠它来装.

## 1. 概览

想象一下, 你刚入职一家科技公司, 准备开始写代码. 结果发现: 一个项目需要 Python 3.11, 另一个需要 Node 20, 还有一个老项目锁死在 Python 3.9, 而且你还得装 Claude CLI 来用 AI 辅助开发.

怎么办? 一个个去官网下载安装? 版本冲突了怎么切换? 每个工具的管理方式还都不一样?

这就像家里的遥控器越来越多, 电视一个, 空调一个, 音响一个, 投影仪一个, 最后你需要一个万能遥控器来统一管理它们. mise 就是开发工具界的万能遥控器. 有了它, 你只需要学会一套命令, 就能安装, 切换, 管理几乎所有开发工具: Python, Node.js, Go, Rust, Claude CLI, 一个工具搞定全部.

> **关于 Mac 和 Windows 的一句提醒:** 这门课后面会带你把开发环境搬到 Mac 本地. mise 在 Mac 上是真正的一秒钟装好, 但如果你用的是 Windows, 同样的配置往往要折腾一个小时, 甚至遇到各种奇怪的坑. 如果你手头没有 Mac, 继续用 GitHub Codespace 也完全可以练下去, 但如果条件允许, 强烈建议尽早给自己配一台 Mac, 这会替你省下大量本该花在学习上的时间.
>
> **即使你已经有 Mac, 也建议先在这个 Task 里用 Codespace 练一遍.** Codespace 是一次性的, 搞砸了删掉重来没有任何成本; 而你的 Mac 是你每天要用的主力电脑. mise 设计得很安全, 直接在 Mac 上装第一次就把系统配置搞乱的概率几乎为零, 但对第一次接触这套工具的人来说, 先在别人的厨房里练手, 总归比直接在自己的厨房里试错更放心. 等你在 Codespace 里把这套流程走顺了, 下一个 Task 再照着同样的步骤在 Mac 上装一遍, 会又快又稳.

## 2. 学习目标

学完这个 Task, 你将能够:

1. 说清楚 mise 是什么, 以及它解决了什么问题
2. 在 GitHub Codespace 里从零安装 mise, 并让它在每次打开 Terminal 时自动启动
3. 知道 mise 还有哪些进阶功能, 以及需要时该怎样让 AI agent 帮你深入学习

---

## 3. 前置知识

- 会使用 GitHub Codespace, 能打开, 使用, 删除
- 会在 Terminal 里输入命令并按回车执行
- 理解复制粘贴操作

不需要了解 Linux, bash 或任何编程知识.

---

## 4. mise 是什么, 为什么需要它

mise (发音类似 "meez", 来自法语烹饪术语 "mise en place", 意为准备就绪) 是一个开发环境管理工具. 简单来说, 它是管理其他开发工具的工具.

传统上, 不同的编程语言和工具各有各的版本管理器: Python 有 pyenv, uv; Node.js 有 nvm, fnm; Ruby 有 rbenv; 各种 CLI 工具还要靠 npm, pipx. 这些工具都很优秀, 但它们的设计者来自不同背景, 设计哲学和命令风格都不一样. 如果你要同时用 Python, Node.js, Ruby, 就得学三套不同的工具.

mise 把这些全部统一了. 你不再需要学习五六个不同的工具, 只需要掌握 mise 这一个. 这个思路不只适用于开发工具: 在任何领域, 当你面对大量同类事物时, 都可以问自己, 有没有一个元工具或元方法, 能让我用一套方法管理所有这些. 找到并掌握那个管理其他工具的工具, 往往是事半功倍的关键.

**为什么这些工具天生就会互相冲突, 而不是凑巧没设计好.** 说一个 layman 也能懂的原理: 像 pyenv, nvm 这些版本管理器, 干的都是同一件事, 在你的电脑里放一个替身 (行话叫 shim). 你敲 `python` 这个命令的时候, 电脑实际运行的不是唯一的那个 Python, 而是这个替身, 替身再悄悄转个弯, 帮你调到当前项目需要的那个版本. 问题在于, pyenv 只认得 Python 的替身, nvm 只认得 Node 的替身, 它们各自守着自己的一亩三分地, 谁也不知道对方的存在, 更没有谁规定它们必须听同一套指挥. 装的版本管理器一多, 这些替身经常会打起来: 谁先启动, 谁的替身排在前面, 要不要读同一个配置文件, 都可能对不上. 站在 pyenv 的角度, 它没有做错任何事, 它的任务就是管好 Python, nvm 也一样, 谁也没有义务替对方考虑, 这就是为什么这个问题几乎不可能靠某一个单独的工具自己解决. mise 的做法是, 只做这一套替身机制, 但让它同时认得 Python, Node, Ruby, Rust, 乃至任意 CLI 工具, 于是你的电脑里只有一套指挥系统, 而不是五套互不认识的指挥系统在打架.

我们之后会用到 Python, Claude CLI, Node.js, uv 这些工具. 如果不用 mise, 你可能要学习四五个不同的工具来管理它们; 而学会 mise 之后, 只需要:

```bash
mise use python@3.12
mise use npm:@anthropic-ai/claude-code
```

一个命令一个工具, 全部搞定.

---

## 5. 在 Codespace 中安装 mise

整个安装过程只需要四步.

**第一步, 确认当前没有 mise.** 打开你的 GitHub Codespace 的 Terminal, 输入:

```bash
mise
```

因为这是一台全新的 Codespace, 肯定没装过 mise, 所以你会看到 `bash: mise: command not found`. 这是正常的, 说明确实需要安装它.

**第二步, 运行安装命令.** Codespace 是 Linux 环境, 按照 [mise 官方文档](https://mise.jdx.dev/getting-started.html), 安装命令是:

```bash
curl https://mise.run | sh
```

`curl` 是一个下载工具, 这行命令的意思是从 mise.run 这个网址下载安装脚本, 然后运行它. 安装完成后, 输出里会有一行以 `echo` 开头的提示, 这一行很关键, 后面第三步要用到.

**第三步, 让 mise 每次自动启动.** 这是最容易被漏掉的一步. 你看到的那行 `echo "eval ..."` 命令, 是 mise 在告诉你, 如果想每次打开 Terminal 都能直接用 mise, 就要把它的启动命令写进启动脚本. 复制粘贴执行它, 完整命令类似:

```bash
echo "eval \"$(/home/codespace/.local/bin/mise activate bash)\"" >> ~/.bashrc
```

`~/.bashrc` 是一个开机自动运行脚本, 每次你打开 Terminal 或输入 `bash` 重新进入 bash, 系统都会自动执行这个脚本里的所有命令. `eval "$(...mise activate bash)"` 是 mise 的启动命令, 不运行它 mise 就像睡着了一样无法使用. 而 `echo "..." >> ~/.bashrc` 就是把引号里的内容追加到 `~/.bashrc` 文件末尾. 这样以后每次打开 Terminal, mise 都会自动启动.

**第四步, 重启 Terminal, 验证安装.** 输入 `bash` 重新启动一个 bash 会话, 它会自动执行 `~/.bashrc` 里的内容. 然后再次输入 `mise`, 如果看到帮助信息而不是 `command not found`, 就说明安装成功了.

这件事在同一台机器上一辈子只需要做一次. 以后这台 Codespace 只要还在, mise 就随时可用.

---

## 6. 关于 bash 和 zsh 的小知识

GitHub Codespace 默认使用 [bash](https://www.gnu.org/software/bash/). 如果你用的是 Mac 电脑的 Terminal, 默认是 [zsh](https://www.zsh.org/). 两者非常相似, 但配置文件不同: bash 的启动脚本是 `~/.bashrc`, zsh 的是 `~/.zshrc`.

所以如果你将来在 Mac 上安装 mise, 安装过程完全一样, 只是最后要把启动命令加到 `~/.zshrc` 而不是 `~/.bashrc`. mise 会自动识别你的 shell 类型并给出正确的提示, 不用担心记错.

---

## 7. mise 的进阶功能, 遇到了怎么问 AI

这个 Task 只教你装上 mise 并跑通最基本的用法, 但 mise 本身能做的事情远不止这些. 比如:

- 用 `mise.toml` 文件把整个项目要用的工具版本固定下来, 团队成员 clone 项目后一条命令就能装齐所有依赖
- 用 `[tasks]` 定义项目级的自定义任务 (这门课的 repo 根目录就有一份 `mise.toml`, 里面已经定义了几个 task, 可以打开看看)
- 管理环境变量, 插件, 以及和 direnv 这类工具的配合
- 装各种 coding agent 的命令行版本, 比如 Claude Code, Codex CLI, Antigravity CLI. 这一点在 Codespace 里格外有用, 因为 Codespace 没有图形界面, 装不了这些 coding agent 的 IDE 或桌面版, 但它们的命令行版本完全可以用 mise 装, 装完就能在这个 Task 学过的 Terminal 里直接用

这些进阶功能这门课不会展开教. 更好的做法是: 你遇到具体需求的时候, 直接把场景告诉你的 AI agent, 让它现场教你. 比如你可以这样问:

> 我在用 mise 管理开发工具, 已经会基本的 `mise use` 命令了. 我想了解 `mise.toml` 里的 `[tasks]` 是怎么定义和运行的, 能不能给我举一两个贴近日常开发的例子, 再讲讲和直接写 shell 脚本相比它的好处是什么.

如果你在 Codespace 里, 想用上某个 coding agent 的命令行版本, 也可以直接问:

> 我在 GitHub Codespace 里, 没有图形界面, 想用 mise 装一个 coding agent 的命令行版本, 比如 Codex CLI 或者 Antigravity CLI. 请告诉我具体用 mise 怎么装它, 装完之后怎么验证能正常用.

这两条提示词都不到一百个字, 但足够让 AI agent 顺着你当下的水平往下教, 比任何一份写死的教程都更贴合你的实际需要.

---

## 8. 练习

### 练习 1: 从零安装一遍 mise

**目标:** 在一个全新的 Codespace 里, 独立完成 mise 的安装和配置, 不看教程也能凭记忆做完大半.

**怎么做:**

1. 新建一个 GitHub Repository, 名字随意, 例如 `mise-practice`
2. 在这个 Repository 里启动一个新的 Codespace
3. 按上面第 5 节的步骤安装并配置 mise
4. 验证 `mise` 命令能正常显示帮助信息
5. 用完之后回到 GitHub 把这个 Codespace 删除, 释放资源

**你会观察到:**

第二次做这件事会比第一次快很多, 因为你已经理解了每一步在做什么, 而不是照抄命令.

> **关键洞见:** 一次装好, 长期受益. 只要这台 Codespace 或者这台电脑还在, mise 就一直可用, 不需要反复安装.

---

## 9. 回顾: 我们学到了什么

- mise 是一个统一管理开发工具版本的元工具, 用一套命令代替了 pyenv, nvm, rbenv 这些各自为政的版本管理器
- 安装 mise 只需要一行 `curl` 命令, 但别忘了把启动命令写进 `~/.bashrc` 或 `~/.zshrc`, 否则重启 Terminal 后就找不到它了
- mise 还有很多进阶功能, 用到的时候直接带着场景去问 AI agent, 比啃文档更快

---

## 10. 导师寄语

**为什么这个练习重要:**

很多人学完安装会想, 不就是装个工具吗, 为什么第一课就要学这个. 但这里有一个更深层的认识: 在任何领域, 找到并掌握那个管理其他工具的工具, 往往是事半功倍的关键. 这门课后面会陆续用到 Python, Node.js, Claude Code, 每一个都可以用 mise 一行命令装好, 你可以把精力放在真正要学的东西上, 而不是在工具管理上浪费时间.

**关键洞见:**

- 磨刀不误砍柴工, 先花一点时间学最好的那把刀, 之后所有的树都砍得更快
- 遇到教程没教的功能, 先想想能不能直接问 AI, 而不是自己去啃官方文档

**下一步:**

下一个 Task 会带你把开发环境从 Codespace 搬到自己的 Mac 上, 到时候 mise 会继续陪着你, 帮你在本地装好 Python 和 Claude Code.

---

## 11. 速查

**安装命令:**

```bash
curl https://mise.run | sh
```

**让 mise 自动启动 (bash):**

```bash
echo "eval \"$(mise activate bash)\"" >> ~/.bashrc
```

**验证安装:**

```bash
mise
```

**装一个工具:**

```bash
mise use python@3.12
```

**关键文件:**

- `~/.bashrc`: Codespace 上 bash 的启动脚本, mise 的启动命令写在这里
- `~/.zshrc`: Mac 上 zsh 的启动脚本, 以后在 Mac 上装 mise 会写在这里
