+++
date = '2026-07-08T16:50:30+08:00'
draft = false
title = 'My First Post'
image = "/IMG_5905.jpg"
tags = ["Hello", "study"]
description = "測試用文章"
+++
我的第一篇文章

# 這是什麼鬼東西？
一段乍看之下像是文章，但仔細一瞧全無道理的文字組合。

# 這能幹嘛？
給做版面設計的人在版面上塞入一些文字，觀察版面填入文字之後的效果。

另外，有些人以看這種東西為樂。
有沒有其他類似的東西？
當然有：

亂數假文產生器
MoreText（注意網址改了，要打 https://more.iter.tw/sentences.json）
中文假字生成器
有沒有 API 可以用？
支援參數:

format: html、plain、json，輸出格式，預設為 html
size: 1~2000 的正整數，預設為 200
type: 文字類型，預設為 default（白話文）。支援類型如下：
default（白話文）
wenyan（文言文）
poem5（五言詩）
poem7（七言詩）
name（姓名）
miew（「喵」）
wala（「哇啦」）
wenzi（「文字」）
範例：

# 直接取得純文字
curl -s 'https://textgen.cqd.tw?format=plain&size=300'

# 取得 JSON 格式回應
curl -s 'https://textgen.cqd.tw?format=json&size=500' | jq -r .text 
假文怎麼做的？
蒐集大量中文文章，排除非文字符號後算出 1-gram / 2-gram / 3-gram 的頻率統計，把三者次數加權（3-gram 出現十次的意義比 1-gram 出現十次大得多）之後取出加權分數前一萬名。最後以分數為準做加權隨機取樣，連續取到文字數量足夠為止。

標點符號與斷行則是每次取字之後丟骰子決定，機率高低是憑感覺亂設。

...看不懂
不重要，沒關係，看得懂的人都怪怪的。