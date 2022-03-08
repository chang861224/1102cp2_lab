---
marp: true
title: Computer Programming II Lab 
description: Git accounts sign up
author: Chi-Hung Chang
keywords: git GitHub
url:
image: 
date: 2022-02-17
paginate: true 
math: katex
---

<!--
  backgroundImage: "linear-gradient(to bottom, #C4E1FF, #84C1FF)"
-->

<style>
h2{
    position: fixed;
    top: 40px;
}

img[alt~="left"] {
    display: block;
    margin: auto auto auto 30px;
}

img[alt~="center"] {
    display: block;
    margin: 0 auto;
}

img[alt~="right"] {
    display: block;
    margin: auto 30px auto auto;
}
</style>

# Computer Programming II Lab
張麒竑
Feb 17, 2022

---

# Outline

- 版本控制系統 - Git
    - Git
    - GitHub
    - 基本操作
    - 參考資料

- LeetCode
    - 辦個帳號來玩玩看吧

- 歡樂的解題時間(?)
    - LeetCode 1. Two Sum
    - OJ

---

# 版本控制系統 - Git

![center h:100](../assets/git-logo.png)

---

## Git

- Git 可以把檔案的狀態作為更新歷史記錄保存起來。因此可以把編輯過的檔案復原到以前的狀態，也可以顯示編輯過內容的差異。

- 當有人想將編輯過的舊檔案上傳到伺服器、覆蓋其他人的最新檔案時，系統會發出警告，因此可以避免在無意中覆蓋他人的編輯內容。

---

## Git

![center h:400](../assets/git-workflow.png)

---

## 基本操作

- 在自己的 GitHub 上面創建一個資料夾
![center h:350](../assets/github-create-repo.png)

---

## 基本操作

- 將 GitHub 上面的資料夾下載到自己的電腦 Local 端
    ```bash
    git clone <repository_url>
    ```

    ```bash
    (^o^) [cch] [~/Documents] $ git clone git@github.com:chang861224/1102cp2.git
    Cloning into '1102cp2'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
    Receiving objects: 100% (3/3), done.
    (^o^) [cch] [~/Documents] $ ls -l
    drwxrwxr-x  3 cch cch  4096 Feb 16 21:45 1102cp2
    drwxrwxr-x  5 cch cch  4096 Feb 16 16:27 1102cp2_lab
    (^o^) [cch] [~/Documents] $
    ```

---

## 單人多裝置（多分支）

**情劇：當你會在不同裝置上（ex. 筆電、桌機公司電腦....etc）開發同一個專案**

- 更新專案到最新版本
    - 如果 local 端沒有專案資料夾：把 GitHub 上的資料夾 clone 下來
    - 如果 local 端已有專案資料夾：**更新到最新版本**
        ```bash
        git pull 
        ```
- 編輯檔案（coding time....）
- 提交更新版本
- 上傳到 GitHub

---

## 單人多裝置（多分支）

如果你沒有更新的話....

---

## 單人多裝置（多分支）

上傳的時候就會噴錯誤訊息

---

## 單人多分支

**情境：當你在相同/不同裝置上開發銅一個專案，且會出現多種差異版本**

- 更新專案到最新版本
- **確認分支**
    ```bash
    git branch                  # 查看所處分支
    git branch <branch_name>    # 新增分支
    git checkout <branch_name>  # 切換分支
    git merge <branch_name>     # 合併分支
    ```
- 編輯檔案（coding time....）
- 提交更新版本
- 上傳到 GitHub
    ```
    git push origin <branch_name>
    ```

---

## 單人多分支

---

## 單人多分支

---

## 多人多分支

**情境：當有多個人在相同/不同裝置上開發同一個專案** $\Rightarrow$ 會出現多種版本差異

- 將 GitHub 上的專案 fork 到自己的資料夾下
- 更新專案到最新版本
    - 如果 local 端沒有專案資料夾：把 GitHub 上的資料夾 clone 下來
    - 如果 local 端已有專案資料夾：**更新到最新版本**
        ```bash
        git pull <remote_name>
        ```
- 確認遠端
    ```bash
    git remote      # 顯示你的遠端名稱
    git remote -v   # 顯示你的遠端名稱及所用的網址
    git remote add <remote_name> <URL>      # 新增遠端版本庫
    ```

---

## 多人多分支

**情境：當有多個人在相同/不同裝置上開發同一個專案** $\Rightarrow$ 會出現多種版本差異

- 確認分支
    ```bash
    git branch      # 查看所處分支
    git branch <branch_name>        # 新增分支
    git checkout <branch_name>      # 切換分支
    git merge <branch_name>         # 合併分支
    ```
- 編輯專案（coding time....）
- 提交更新版本
- 上傳到 GitHub
    ```bash
    git push <remote_name> <branch_name>
    ```
- **在 GitHub 上面發 PR（Pull Request）給原始資料夾擁有者**

---

## 多人多分支

---

## 多人多分支

---

## Bonus Time

**這些動作要在今天 23:59 前完成，才會有 bonus 喔！**

1. 在 GitHub 上面找到 chang861224/1102CP2_Lab0310 這個資料夾
2. 將這個資料夾 fork 到你自己的 GitHub 上
3. 將你 fork 來的這個資料夾 clone 到你的電腦 local 端
4. 創建一個 branch，名稱是「**NCCU_<你的學號>**」
5. 在這個 branch 裡面新增一個檔案，檔名是「Lab0310_<你的學號>.txt」，檔案內容則是找一首歌，把歌名和歌詞貼過來
6. 在 commit 打「<你的學號>: <歌名>」
7. 將更新後的這個分支 push 到你自己的 GitHub 上，然後發一個 PR 給我

註：要在「**你的 branch 上傳然後發 PR**」，而不是直接在你的 main 分支上傳！

---

## Reference

- [遠端多人合作開發－單分支](https://kingofamani.gitbooks.io/git-teach/content/chapter_5/pull.html)
- [連猴子都能懂的Git入門指南](https://backlog.com/git-tutorial/tw/stepup/stepup1_1.html)
- [30 天精通 Git 版本控管](https://github.com/doggy8088/Learn-Git-in-30-days/blob/master/zh-tw/README.md)
- [Git Tutorial](https://git-scm.com/docs/gittutorial)

