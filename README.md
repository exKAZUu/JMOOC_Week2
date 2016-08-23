# JMOOC Week2

本ページは「はじめてのP」のWeek2の補足資料です。以下の情報を提供することが目的です。

- 講義サイトの原稿が全角文字を利用しており、コピー＆ペーストでJavaScriptのプログラムを実行できない問題に対処する目的
- 講義中ではほとんど解説していないJavaScriptプログラムの詳細について説明する目的
  - ただし、本講義はJavaScript言語の仕様やプログラミングの詳細を説明することを目的としておらず、プログラミングのパワフルさや面白さに触れていただくことを目的としているため、完全にプログラムの意味を理解する必要はございまん。

## 目次
- 1コマ目
  - 全ての文字を赤文字に変えるJavaScriptプログラム

## 1コマ目

### 全ての文字を赤文字に変えるJavaScriptプログラム

```
$('*').css('color', 'red')
```

- `$('*')` はビットくんのツイートページを構成する全ての要素（画面上に表示される全ての部品）を指す命令です。
- `.` はドットの左側の値（レシーバーと呼ぶ）が所有するドットの右側の変数や関数（プロパティと呼ぶ）を参照するという意味になります。
- 今回は、ビットくんのツイートページを構成する全ての要素が所有する`css`という関数を呼び出すということです。
- [`css`関数](http://semooh.jp/jquery/api/css/css/name%2C+value/)は、Webページを表現しているHTML文書に対して、[Cascading Style Sheets (CSS)](https://ja.wikipedia.org/wiki/Cascading_Style_Sheets) という仕様に則して、Webページのデザインを変える関数です。


### ツイートの中身の文字だけを青文字に変えるJavaScriptプログラム

```
$('li.stream-item .js-tweet-text').css('color', 'blue')
```

### ビットくんの画像を大きくするJavaScriptプログラム

```
bitkun = $('.ProfileAvatar-image')
size = bitkun.width()
timer = setInterval(() => {
  size *= 1.005
  bitkun.width(size)
  bitkun.height(size)
  if (size > 1000) {
    clearInterval(timer)
  }
}, 10)
```

## 2コマ目


### 全ての文字を赤文字に変えるJavaScriptプログラム

```
e = $('li.stream-item').eq(1); e.parent().prepend(e)
```
