---
title: Day3 今天是520 Git就是我的情人
date: 2026-05-20
excerpt: Git 關於多人協作、版本控制與常用指令
image: /images/image7.png
tags: [git reset, git reflog, git merge, git rebase]
---
  話說今天是520，單身的我也沒和人有過情人節的回憶，趁這個機會了解一下情人節的由來與意義。  
  不查不知道，一查嚇一跳，在台灣可以跟情人節相關的節日有<strong>14個</strong>，台灣主流的情人節則是 2月14日西洋情人節、3月14日白色情人節以及農曆七月初七的七夕情人節。
  如果情人節都算國定假日的話，那代表我一年休14天，換算成勞基法的特休年資，我需要累積2年以上的年資...  
  如果把維持兩性之間的關係，視為一份工作的話，那在一起前兩年都是不合法的，到了第三年開始才變成正式員工，期望各位都能夠找到一份就算不合法，也願意繼續一起度過時光的那個人
  

## git reset 回到過去
<h5>讓分支回到過去某一刻，並且決定要不要進行修改</h5>
基本指令如下:

<code>git reset <commit></code> 回到過去的某個commit (預設為 --mix)  

```git reset --soft <commit>``` 回到過去的某個commit(add後的狀態)  
```git reset --hard <commit>``` 回退一個commit,變更直接丟棄
```git reset <檔名>``` 從站存區移到工作區效果等於```git restore --staged <檔名>```  
```git reset HEAD^``` 回到上一個commit  
```git reset HEAD~n```回到上n個 commit  
```git reset <commit>^``` 回到某commit 的上一步  

## git reflog 查看紀錄
<h5>查看所有Head的移動紀錄，包含所有操作</h5>  
<mark>git log 看歷史，git reflog 救人命。</mark>  

即使 git reset --hard 後「消失」的 commit，這裡還找得到  
只存在本地，不會推到遠端  
預設保留 90 天  

``` git reflog<分支名>``` 查看某個分支的紀錄  
```git reflog -n 5``` 只顯示最近5筆  




## git merge 合併分支
<h5>將另一個分支合併到當前分支</h5>  
將目前分支跟目標分支合併  
<strong>目前的分支會往前推</strong>    
 
基本指令如下:

```git merge <分支名>``` 將另一個分支合併到當前分支  
```git merge -ff <分支名>``` 允許 fast-forward(預設行為)同上  
```git merge git merge --no-ff <分支名>``` 強制建立 merge commit(不用 fast-forward)   
```git merge --abort``` 取消merge(發生衝突時)
```git merge --no--ff -m "message" <branch>``` 強制建立 merge commit並指定訊息(不用 fast-forward)>  
<mark>誰要往前走，HEAD就在誰身上</mark>   

## git rebase
<h5>將目前分支嫁接到某分支之後</h5>  
<strong>rebase會改變commit的歷史紀錄</strong>  
 基本指令如下:  

 ```git rebase <分支名>``` 將目前分支嫁接到某分支之後  
 ```git rebase --continue``` 解決衝突，繼續解下一個commit衝突  
 ```git rebase --abort``` 中止將目前分支嫁接到某分支之後  
 ```git rebase --skip``` 跳過解當前衝突commit  
 <mark>誰要往前走，HEAD就在誰身上</mark>




