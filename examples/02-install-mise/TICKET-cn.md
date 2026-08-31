---
description: "一台全新的 Codespace 或电脑上, mise 命令能正常显示帮助信息, 且启动命令已经写进了 shell 的启动脚本."
---

# 安装并配置 mise

## 1. 目标

读完 README 之后, 在一个全新的 GitHub Codespace 里从零装好 mise, 并让它在每次打开 Terminal 时自动启动. 这不是照着敲一遍命令就算完, 而是要在没有教程打开的情况下, 也能凭记忆把这几步再走一遍.

---

## 2. 要做的事情

1. 新建一个 GitHub Repository, 名字随意, 例如 `mise-practice`
2. 在这个 Repository 里启动一个新的 Codespace
3. 在 Terminal 里输入 `mise`, 确认看到 `command not found`
4. 运行 `curl https://mise.run | sh` 完成安装
5. 复制粘贴安装输出里那行 `echo "eval ..."` 命令, 把 mise 的启动命令加进 `~/.bashrc`
6. 输入 `bash` 重启 Terminal, 再次输入 `mise`, 确认看到帮助信息
7. 用完之后回 GitHub 删除这个 Codespace

**预计用时:** 15 到 30 分钟

---

## 3. 检查清单

- [ ] **确认起点**: 全新 Codespace 里输入 `mise`, 显示 `command not found`
- [ ] **安装成功**: 运行安装命令后, Terminal 输出显示 mise 安装成功的信息
- [ ] **启动脚本已配置**: `~/.bashrc` 文件末尾能看到 mise 的 `eval` 启动行
- [ ] **验证生效**: 重启 Terminal 后再次输入 `mise`, 显示帮助信息而不是找不到命令
- [ ] **能讲清楚原理**: 你能说清楚为什么装完 mise 还要多一步写 `~/.bashrc`, 不写会怎么样
- [ ] **清理干净**: 练习用的 Codespace 已经删除
