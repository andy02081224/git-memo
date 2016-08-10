# git-memo
記錄一些自己常用(一直忘記)的Git指令與使用技巧

## 基本指令

#### 修改還沒push到遠端的commit message
```bash
git commit --amend
```

#### 修改已經push到遠端的commit message
參考[這裡](https://help.github.com/articles/changing-a-commit-message/#amending-older-or-multiple-commit-messages)


## GitHub使用

#### 在commit message關掉issue
可以在commit message中使用特定關鍵字加上issue number去關掉issue，例如commit meesage:`Fix #1`，會將編號1的issue關掉，GitHub會記錄關掉此issue的commit版號，詳細說明參考[這裡](https://help.github.com/articles/closing-issues-via-commit-messages/)。

