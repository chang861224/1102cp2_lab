---
marp: true
title: Computer Programming II Lab 
author: Chi-Hung Chang
keywords: terminal WSL zsh Linux Makefile
url:
image: 
date: 2022-06-02
paginate: true 
math: katex
---

<style>
h2{
    position: absolute;
    top: 50px;
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
June 2, 2022

---

# Outline

- Terminal
- Makefile
- Online Judge
- LeetCode

---

# Terminal

- Ubuntu
- WSL
- Bash & zsh
- Linux Commands

---

## Ubuntu

Ubuntu 是著名的 Linux 發行版之一，也是目前最多使用者的 Linux 版本。

Ubuntu 每六個月（即每年的四月與十月）釋出一個新版本，長期支援（LTS）版本每兩年釋出一次。普通版本一般只支援9個月，但LTS版本一般能提供5年的支援。

If 如果假設你想在 Windows 作業系統外，在額外裝 Ubuntu 作業系統，你可以跟著 Reference 裡面的 [(Ubuntu)安裝Win10 Ubunto18.04 雙系統](https://medium.com/ai%E5%8F%8D%E6%96%97%E5%9F%8E/ubuntu-%E5%AE%89%E8%A3%9Dwin10-ubunto18-04-%E9%9B%99%E7%B3%BB%E7%B5%B1-a53870382df6) 進行安裝（但真的有需要再裝就好....），或者也可以安裝虛擬機（在 Reference 裡面一樣有提供連結）

---

## WSL (Windows Subsystem for Linux)

適用於 Linux 的 Windows 子系統可讓開發人員執行 GNU/Linux 環境（包括大部分的命令列工具、公用程式和應用程式），直接在 Windows 上執行，不需進行修改，不會造成傳統虛擬機器或 dualboot 設定的額外負荷。

- 執行一般的命令列工具
- 執行 Bash 命令介面指令碼和 GNU/Linux 命令列應用程式
- 使用自己的 GNU/Linux 散發套件管理員安裝其他軟體
- 使用類似 Unix 的命令列命令介面來叫用 Windows 應用程式
- 在 Windows 上叫用 GNU/Linux 應用程式

---

## WSL (Windows Subsystem for Linux)

If 如果假設你想裝的話....

- 先決條件
    - Windows 10 2004 或更新版本，或 Windows 11
    - [舊版 WSL 手動安裝](https://docs.microsoft.com/zh-tw/windows/wsl/install-manual)
- 安裝步驟
    - 以 **系統管理員** 開啟 PowerShell 或 Windows cmd（命令提示字元）
    - 查看版本清單
        ```bash
        wsl --list --online
        ```
    - 指定版本安裝
        ```bash
        wsl --install <DistroName>
        ```
    - 重新開機
    - 開機完後，系統會自己跳出視窗，把後續該安裝好的都安裝好，此時....呼吸就好

---

## WSL (Windows Subsystem for Linux)

額外的一些小癖好....

因為我實在是不太喜歡 Windows cmd 用的新細明體，所以我推薦用 **終端機**（或者叫 **terminal**）來使用 WSL！

- 可以直接在 Microsoft Store 上搜尋「終端機」或「terminal」，找到「Windows Terminal」後就進行安裝
- 當安裝好後，即可將它開啟，預設應該會是 PowerShell，可以在「設定」那邊將開啟的預設改成 WSL（當 WSL 安裝好某個版本後，應該會顯示該版本而不會事 WSL，例如 Ubuntu-20.04）

---

## Bash & zsh

- Bash
    - Bash 是一個命令處理器，通常執行於文字窗口中，並能執行使用者直接輸入的命令。Bash 還能從檔案中讀取命令，這樣的檔案稱為指令碼。和其他 Unix shell 一樣，它支援檔名替換（萬用字元匹配）、管道、here 文件、命令替換、變數，以及條件判斷和迴圈遍歷的結構控制語句
    - Bash 設定檔存在 `~/.bashrc` 裡面，歷史指令紀錄則是存在 `~/.bash_history` 內
- Z Shell
    - Z shell（Zsh）是一款可用作互動式登入的shell及指令碼編寫的命令直譯器
    - Z shell 設定檔存在 `~/.zshrc` 裡面，歷史指令紀錄存在 `~/.zsh_history` 內

---

## Bash & zsh

麒竑的推薦時間～

因為 bash 是預設的，沒意外的話 WSL 剛安裝好都會是用 bash，而我向要推薦大家也裝 zsh 來玩玩看～搞不好會發現 zsh 比 bash 好用XDD

（macOS 預設就是用 zsh，也可以跟著一起玩玩看 zsh 有什麼好玩的東西～）

---

## Bash & zsh

一些必要的套件要先裝好：`wget`、`git`、`curl`、`vim`

```bash
sudo apt install wget git curl vim -y
```

- 如果是剛安裝好的 WSL，有可能會有些套件沒有裝，下這個指令可以直接幫你裝好！
- 如果原本就有裝好的話，指令會直接顯示已安裝然後跳過，所以不用擔心衝突的部分～

---

## Bash & zsh

安裝 zsh

```bash
sudo apt install zsh -y
```

安裝 oh-my-zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

- 安裝好 oh-my-zsh 後，可以按 Enter 將預設的 shell 改成 zsh
- 如果一開始沒有預設 shell 成 zsh，但後來想要改預設成 zsh，可以下指令 `chsh -s $(which zsh)` 進行修改
- 如果沒有想要設定預設，但又想要用 zsh 的話，可以直接下指令 `zsh` 將 shell 切換成 zsh（關掉再開一次又會回復到預設的 shell）

---

## Bash & zsh

推薦幾個好用、適合安裝的主題和插件（前提是要有先裝好 zsh，且目前用的 shell 是 zsh）

- （主題）PowerLevel10k
    ```bash
    git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
    ```
- zsh-autosuggestions
    ```bash
    git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
    ```
- zsh-syntax-highlighting
    ```bash
    git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
    ```
- zsh-z（這個我沒用過XD）
    ```bash
    git clone https://github.com/agkozak/zsh-z $ZSH_CUSTOM/plugins/zsh-z
    ```

---

## Bash & zsh

插件安裝了還得啟用它才有用！！

開啟 `~/.zshrc` 編輯

```bash
vim ~/.zshrc
```

- 修改主題
    ```
    ZSH_THEME="powerlevel10k/powerlevel10k"
    ```
- 新增啟動的插件（看你有安裝什麼就寫什麼上去）
    ```
    plugins=(git zsh-autosuggestions zsh-syntax-highlighting zsh-z)
    ```

啟動！！

```bash
source ~/.zshrc
```

---

## Linux Commands

---

# Makefile

---

## Reference

- [Ubuntu（維基百科）](https://zh.m.wikipedia.org/zh-tw/Ubuntu)
- [(Ubuntu)安裝Win10 Ubunto18.04 雙系統](https://medium.com/ai%E5%8F%8D%E6%96%97%E5%9F%8E/ubuntu-%E5%AE%89%E8%A3%9Dwin10-ubunto18-04-%E9%9B%99%E7%B3%BB%E7%B5%B1-a53870382df6)
- [VirtualBox 虛擬機器安裝 Ubuntu Desktop 設定與使用教學](https://www.kjnotes.com/linux/29)
- [什麼是 Windows 子系統 Linux 版？](https://docs.microsoft.com/zh-tw/windows/wsl/about)
- [安裝 WSL](https://docs.microsoft.com/zh-tw/windows/wsl/install)
- [Bash（維基百科）](https://zh.wikipedia.org/zh-tw/Bash)
- [Z Shell（維基百科）](https://zh.wikipedia.org/zh-tw/Z_shell)
- [Ubuntu 安裝 Zsh + Oh My Zsh + Powerlevel10k 與各種插件](https://www.kwchang0831.dev/dev-env/ubuntu/oh-my-zsh)

---

# Online Judge

---

## 

---

# LeetCode

---

## 重要公告

很重要！很重要！很重要！
前半個學期的 Leetcode 加分統計到**本週日**（**2022/05/01 23:59**）！！

如果有做要加分，可以這麼做：

1. 直接找隨便一個助教，然後開你的 Leetcode 頁面給我們當場檢查（前提你要先找到我們）
2. 將你做題目的作答紀錄截圖下來，寄給或傳給任一位助教（但助教不會通靈，所以請附上你的學號）

超過時間的話，就只能跟你的分數說掰掰了喔！（← By 簡傑XD）
但這也只是加分而已啦～沒有強制一定要寫～開心就好開心就好XDD

---

# Any Question?

