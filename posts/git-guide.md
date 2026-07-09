---
title: Git 常用命令速查手册
date: 2026-07-07
tags: [Git, 工具]
excerpt: 整理日常开发中最常用的 Git 命令，涵盖基本操作、分支管理、远程仓库等场景。
---

# Git 常用命令速查手册

Git 是日常开发中必不可少的版本控制工具。本文整理了最常用的命令。

## 基础操作

### 配置

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global core.editor vim
```

### 创建仓库

```bash
# 初始化新仓库
git init

# 克隆远程仓库
git clone https://github.com/user/repo.git
```

### 暂存与提交

```bash
# 查看状态
git status

# 暂存文件
git add index.html
git add .          # 暂存所有变更
git add -p         # 交互式暂存

# 提交
git commit -m "feat: add login page"
git commit -am "fix: typo"   # 跳过暂存（仅跟踪过的文件）

# 修改上次提交
git commit --amend
```

## 分支管理

```bash
# 查看分支
git branch
git branch -r      # 远程分支
git branch -a      # 所有分支

# 创建与切换
git branch feature-login
git checkout feature-login
git checkout -b feature-login  # 创建并切换

# 合并
git checkout main
git merge feature-login

# 删除
git branch -d feature-login    # 本地
git push origin --delete feature-login  # 远程
```

## 远程仓库

```bash
# 查看远程
git remote -v

# 添加远程
git remote add origin https://github.com/user/repo.git

# 推送
git push origin main
git push -u origin main    # 设置上游

# 拉取
git pull
git fetch                 # 仅获取，不合并
```

## 查看历史

```bash
git log
git log --oneline --graph
git log --oneline -5      # 最近 5 条

git diff                  # 工作区 vs 暂存区
git diff --staged         # 暂存区 vs 上次提交
```

## 撤销操作

```bash
git restore index.html     # 撤销工作区修改
git restore --staged .     # 取消暂存
git reset --soft HEAD~1    # 撤回提交，保留修改
git reset --hard HEAD~1    # 彻底撤回
```

> **提示**：`--hard` 操作会丢失修改，谨慎使用！
