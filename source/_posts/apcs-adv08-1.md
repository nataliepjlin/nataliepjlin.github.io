---
title: APCS 考古題:小群體
date: 2022-04-11 22:46:03
categories: [APCS]
tags: [小群體]
---
# 題目
https://apcs.csie.ntnu.edu.tw/wp-content/uploads/2018/12/1060304APCSImplementation.pdf

# 解題思路
把data內的元素從某不為-1的data[idx]開始跑，跑到就把該元素改成-1，跑到有標-1(開始的那個)為止
回傳有幾個被marked

# Code
## main function
```bash
def mark(data,idx):
    count=0
    while(data[idx]!=-1):
        tmp=data[idx]
        data[idx]=-1 #mark
        idx=tmp #跑到好友編號，重複迴圈
        count+=1 #計算有幾個被標記
    return count
```
## complete code
```bash
def mark(data,idx):
    count=0
    while(data[idx]!=-1):
        tmp=data[idx]
        data[idx]=-1 #mark
        idx=tmp #跑到好友編號，重複迴圈
        count+=1 #計算有幾個被標記
    return count
n=int(input())
data=list(map(int,input().split()))
marked=0
total=0 #群體總數
for i in range(n):
    if data[i]!=-1:
        marked+=mark(data,i)
        total+=1
    if marked==n:
        break #如果提早標記完就結束for迴圈
print(total)
```