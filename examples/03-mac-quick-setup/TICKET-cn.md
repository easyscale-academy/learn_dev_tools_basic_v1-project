---
description: "Mac 上装好 VS Code, Terminal 或 Ghostty, GitHub Desktop 三件套, Documents 下有一个 GitHub 文件夹, 并且能在 Terminal 里用 pwd, ls, cd 自由移动."
---

# Mac 本地开发环境搭建验收

## 1. 目标

在自己的 Mac 上把日常开发要用的三件套装齐, 并且真正理解 Terminal 是什么, 而不是只会照抄命令. 读完 README 不算完, 得真的在 Terminal 里敲几条命令, 感受一下自己在文件系统里移动的过程.

如果暂时没有 Mac, 先继续用 Codespace 完成后面的课程, 等有 Mac 之后再回来补这个 Task.

---

## 2. 要做的事情

1. 从官网下载并安装 VS Code, 打开确认没有报错
2. 安装 Ghostty, 或者确认愿意使用系统自带的 Terminal
3. 下载并安装 GitHub Desktop, 用自己的 GitHub 账号登录
4. 在 Documents 下创建一个名为 `GitHub` 的文件夹
5. 打开终端, 依次运行 `pwd`, `ls`, `cd Documents`, `pwd`, `cd ..`, 观察每一步的输出变化
6. 用 `mise` 命令确认它在本地终端里依然可用

**预计用时:** 30 到 60 分钟

---

## 3. 检查清单

- [ ] **VS Code 已安装**: 能从 Applications 打开 VS Code, 没有报错
- [ ] **终端可用**: Ghostty 或系统自带的 Terminal 至少有一个能正常打开并输入命令
- [ ] **GitHub Desktop 已配置**: 安装完成并且已经登录自己的 GitHub 账号
- [ ] **项目文件夹存在**: `~/Documents/GitHub/` 这个文件夹确实存在
- [ ] **会用基本命令**: 你能在终端里用 `pwd` 看清自己在哪, 用 `cd` 切换到别的文件夹, 再用 `cd ..` 回去
- [ ] **mise 在本地生效**: 在终端里输入 `mise`, 显示的是帮助信息而不是找不到命令
- [ ] **说得清为什么用 Terminal**: 你能用自己的话说清楚, 为什么开发工具大多先有命令行版本, 图形界面是后来加的
