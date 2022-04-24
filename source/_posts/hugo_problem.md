---
title: Hugo 疑難雜症
categories: [Hugo]
tags:
---
## POST SCSS failed:
1. 到「沒空白」的資料夾下面(像 `Natalie Lin` 名字中間有空格就不行)
2. 安裝本土npm, 不能是global
3. 看README有沒有要求要複製 `package.json` 、 `npm postcss` 之類的或其他東西

## 網址/404 not found:
確定有沒有貼成repo的網址:(

## 有git submodule
怎麼看:
git clone 之後cd進去裡面會顯示(main)或(master)
解決方式:
直接Download Zip不要用clone

## 連結到<username.github.io/img>而不是<username.github.io/repo/img>
怎麼看:
Go to files 之後檢查 public裡面的網址
可以解決的方式:
😀在全域`config.toml`加上`canonifyURLs = "true"`
😐在path url前加 `/repo ` (`repo`要換成專案名稱)
😥丟到主頁(username.github.io)下面

## 有功能不會動(這次是search function)
解方同上

## “TOCSS … this feature is not available in your current Hugo version”
解決方式:
On the release page, look for archives with extended in the name.
如何確認是否安裝:
run `hugo version` and look for the word `extended`.

## 加入categories 頁面失敗
[問題](https://discourse.gohugo.io/t/tags-and-categories-dont-link-to-the-posts-under-that-category-or-tag/38107)
解決方式:
第10行改成 `{{range .Data.Pages}}`