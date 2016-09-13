# git-memo
記錄一些自己常用(一直忘記)的Git指令與使用技巧

## 基本指令

### Git設定

##### 在一台電腦上第一次設定git時，需要先設定使用者名稱以及電子郵件帳號 (加上`--global`使之成為全域設定，讓之後相關操作皆會採用此次設定不須再重複輸入)
```bash
git config --global user.name "username"
git config --global user.email "username@example.com"
```
### 檔案操作

##### 將當前工作目錄中沒被ignore的新檔案以及已追蹤且修改的檔案加入staged area（不包含被移除的檔案）
```bash
git add .
```

##### 將當前工作目錄中已經被追蹤且沒被ignore的已修改檔案加入staged area（不包含新檔案、包含被移除的檔案）
```bash
git add -u
```

##### `git add.` + `git add -u`
```bash
git add -A
```

##### 捨棄還沒staged的檔案當前的改變
```bash
git checkout -- [file-name]
```

##### unstage檔案
```bash
git reset HEAD [file-name]
```

##### 修改還沒push到遠端的commit message
```bash
git commit --amend
```

##### 修改已經push到遠端的commit message
參考[這裡](https://help.github.com/articles/changing-a-commit-message/#amending-older-or-multiple-commit-messages)

### 分支操作

##### 創建新分支
```bash
git branch [branch-name]
```

##### 切換分支
```bash
git checkout [branch-name]
```

##### 刪除分支
```bash
git branch -d [branch-name]
```
##### 刪除遠端分支
```bash
git push [remote-name] :[branch-name]
```

##### 列出所有本地分支
```bash
git branch
```

##### 列出所有本地和遠端分支
```bash
git branch -a
```

##### 將本地分支push到遠端分支並追蹤(讓之後的push或pull操作可以省略參數)
```bash
git push -u [remote-name] [branch-name] # -u為--set-upstream的簡寫
```
上面的指令是以下指令的省略，代表local-branch-name與remote-branch-name相同
```bash
git push -u [remote-name] [local-branch-name]:[remote-branch-name]
```
⚠ 上面的指令不要寫成`git push -u [remote-name] :[remote-branch-name]`，這樣做會將遠端分支刪除!!

##### 列出本地分支追蹤的遠端分支
```bash
git branch -vv
# 輸出會類似: master 5d7c182 [origin/master] Initial commit
# 當本地分支已經成功追蹤遠端分支，會將追蹤的遠端分支顯示在commit hash與commit message之間，在這邊就是[origin/master]
# 在git 1.8.3之後追蹤的遠端分支預設會以藍色字體強調
```

### Rebase
[Git-rebase 小筆記](https://blog.yorkxin.org/2011/07/29/git-rebase) ⬅ 講的超好，大推

### 查看Difference
題外話: 預設的git diff介面其實不是很直覺，可以考慮安裝[diff-so-fancy](https://github.com/so-fancy/diff-so-fancy)來讓他美麗一點

##### 顯示當前的工作目錄中還沒加入staged area的更改 (已經改動但是還沒加入staged area的檔案的變動)
```bash
git diff
```
##### 顯示在staged area的檔案與上一次commit (HEAD)之間的差別
```bash
git diff --cached
```

##### 顯示當前的工作目錄與上一次commit (HEAD)之間的差別
```bash
git diff HEAD
```
## 工具

##### SourceTree
- 免費GUI工具，功能強大
- 內建支援git-flow

## GitHub使用

##### 在commit message關掉issue
可以在commit message中使用特定關鍵字加上issue number去關掉issue，例如commit meesage:`Fix #1`，會將編號1的issue關掉，GitHub會記錄關掉此issue的commit版號，詳細說明參考[這裡](https://help.github.com/articles/closing-issues-via-commit-messages/)。

