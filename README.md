# git-memo
記錄一些自己常用(一直忘記)的Git指令與使用技巧

## 基本指令

#### 在一台電腦上第一次設定git時，需要先設定使用者名稱以及電子郵件帳號 (將上--global使之成為全域設定，讓之後相關操作皆會採用此次設定不須再重複輸入)
```bash
git config --global user.name "username"
git config --global user.email "username@example.com"
```


#### unstage已經提交的檔案
```bash
git reset HEAD filename
```

#### 捨棄還沒stage的檔案當前的改變
```bash
git checkout -- filename
```

#### 修改還沒push到遠端的commit message
```bash
git commit --amend
```

#### 修改已經push到遠端的commit message
參考[這裡](https://help.github.com/articles/changing-a-commit-message/#amending-older-or-multiple-commit-messages)


## GitHub使用

#### 在commit message關掉issue
可以在commit message中使用特定關鍵字加上issue number去關掉issue，例如commit meesage:`Fix #1`，會將編號1的issue關掉，GitHub會記錄關掉此issue的commit版號，詳細說明參考[這裡](https://help.github.com/articles/closing-issues-via-commit-messages/)。

