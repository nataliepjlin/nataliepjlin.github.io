---
title: APCS 考古題:數字龍捲風
date: 2022-04-12 19:48:12
categories: [APCS]
tags: [數字龍捲風]
---
# Code

## main function: 輸入邊長、開始方向，製造1dlist，記錄每步的方向
```bash
#n=5
#d=0#left
#3 4 2 1 4
#4 2 3 8 9
#2 1 9 5 6
#4 2 3 7 8
#1 2 6 4 3
###
#3
#1
#4 1 2
#3 0 5
#6 7 8
#012587634
#order list,input:方向、邊長;output:1dlist_每步的方向[0,1,2,2,3,3,0,0,0,1,1,1,2,2,2,2,3,3,3,3,0,0,0,0]
def order(r,d):
    odlist=[]
    direction=(d+4-1)%4 #1.下面下面迴圈會換方向(+1)所以要先-1 2.像是4可以被歸0
    count=1 #單方向走幾步。如果走n-1步已經是最多了，不用n*n和len(odlist)比 **這種方法會算不到追加
    while(count<=n-1):
        for _ in range(2):#每個長度走2次
            direction=(direction+4)%4
            odlist.append(direction)
    count+=1
    #最後一個長度會走3次，要再追加
    direction=(direction+4)%4
    for _ in range(n-1):
        odlist.append(direction)
    return odlist
```
## complete code
```bash
def order(r,d):
    odlist=[]
    direction=(d+4-1)%4
    count=1 
    while(count<=n-1):
        for _ in range(2):
            direction=(direction+4)%4
            odlist.append(direction)
        count+=1
    direction=(direction+4)%4
    for _ in range(n-1):
        odlist.append(direction)
return odlist

r=int(input())
d=int(input())
datas=[]#2d
x,y=r//2,r//2
for i in range n:
    data=list(map(int,input().split()))
    datas.append(data)
steps=order(r,d)
print(datas[x][y])
for step in steps:#注意x是直的，y是橫的!
    if step==0:
        y-=1 #不能只print(datas[x-1][y])，會記錄不到x,y變化
    if step==1:
        x-=1
    if step==2:
        y+=1
    if step==3:
        x+=1
    print(datas[x][y],end="")
```
