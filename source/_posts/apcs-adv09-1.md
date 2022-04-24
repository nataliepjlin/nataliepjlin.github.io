---
title: APCS 10503第2題:矩陣轉換
date: 2022-04-18 23:24:25
categories: [APCS]
tags: [矩陣轉換,b965]
---


# 在寫的時候卡住的點:
1. row是橫列數量，相當於直行的長度;col是直行數量，相當於橫列的長度
2. 題目要求為「恢復」，或是說「回推」。(是b->a而不是a->b)
所以衍生出第三點🔻
3. 給的指令要反著做

# 覺得可以沿用的方法:
1. 很混亂的時候代測資數字
2. 拿紙筆寫下來!

# Code

## Function可改善處
1. flip其實可以用reverse就好
```bash
def flip(data):
    data.reverse()
    return data
```
或用
```bash
output=[]
for i in data[::-1]:
    output.append(i)
```
也可以

## Complete Code
```bash
#data=[[1, 1], [3,1],[1,2]]
#ddata=[[1,2,3],[4,5,6]]
#print("init=",data)
def flip(data):
    row=len(data)#有幾個橫列(直行長度),2
    col=len(data[0])# 3
    for i in range(col):
        for j in range(row//2):
            data[j][i],data[row-1-j][i]=data[row-1-j][i],data[j][i]
    #print("data=",data)
    return data
def rotate(data):
    row=len(data)#有幾個橫列(直行長度),2
    col=len(data[0])# 3
    data2=[[0]*row for _ in range(col)]
    #print(data2)
    for i in range(row):#2,用r命名會比較清楚
        for j in range(col):#3,用c命名會比較清楚
            data2[j][i]=data[i][col-1-j]
            #print("data2=",data2)
            #或用data2[col-j-1][i]=data[i][j]
    return(data2)
#ddata=rotate(ddata)
#ddata=rotate(ddata)
#ddata=flip(ddata)
#print(ddata)
r,c,m=map(int,input().split())
data=[list(map(int,input().split())) for _ in range(r)]
commands=list(map(int,input().split()))
for i in range(len(commands)-1,-1,-1):
    if commands[i]==0:
        data=rotate(data)
        #print("nc,nr",col,row)
    if commands[i]==1:
        data=flip(data)
print(len(data),len(data[0]))
for i in range(len(data)):
    print(*data[i])
```
