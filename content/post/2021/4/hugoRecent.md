---
title: "HugoでRecentとかを別ページにして毎回ページが更新されるのを防ぐ"
description: ""
date: "2021-04-23T07:35:46Z"
thumbnail: ""
categories:
  - "プログラミング"
tags:
  - "HUGO"
  - "プログラミング"
---
このブログはgithub ActionsでHugoを実行してgithub pagesで出来てる。<br>
Hugoは静的なサイトを作るソフトだから、右のサイドバーとかの内容も静的なものだから、記事を作るたびに更新される。<br>
そうなるとサイドバーを使ってるページ全てのファイルが更新されることになる。単にファイルをホストしてるだけなら気にならなかったと思うが、githubでやってるせいで毎回大量のファイルがコミットされるのが気になった。<br>
だからHugoのContent Typesを使って一部のファイルだけ更新してそれ以外を読み込むようにした。<br>
<!--more-->
Hugoではmdファイルのフロントマターにtypeを指定すると、layoutsフォルダ内のそのtype名のテンプレートを使うようになる。
[Hugo's Lookup Order](https://gohugo.io/templates/lookup-order/)
```md
---
date: "2010-01-1T00:00:00+09:00"
type: "recentframe"
url: "recent.html"
---
```

これを利用して、サイドバーの無い、サイドバーの中身が張られたページを作る。<br>
作り方は使用してるテーマのサイドバーの部分から引っ張ってくればいい<br>

そうしたらそのページをifrmaeタグで今まで読み込んでた部分と置き換えればとりあえずやりたいことは達成できる。<br>

見た目は気が向いたら凝る。

あ、これだめだ。iframeの中のリンクはiframeのウィンドウが変わるだけなのか。まあ、やりたいことはこんな感じ

追記
target="_parent"をつければよかった。
