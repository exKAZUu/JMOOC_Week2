# JMOOC Week2

本ページは[「はじめてのP」](https://lms.gacco.org/courses/course-v1:gacco+ga068+2016_08/courseware/2d7b0bb5b1854e948f4dc5ed69443e82/)のWeek2の補足資料です。以下の目的で本ページを作成しました。

- 講義サイトの原稿が全角文字を利用しており、コピー＆ペーストでJavaScriptのプログラムを実行できない問題に対処する目的
- 講義中ではほとんど解説していないJavaScriptプログラムの詳細について説明する目的（今後、徐々に加筆修正していきます。）
  - ただし、本講義はJavaScript言語の仕様やプログラミングの詳細を説明することを目的としておらず、プログラミングのパワフルさや面白さに触れていただくことを目的としているため、完全にプログラムの意味を理解する必要はございまん。

## 目次
- (1コマ目)[./README.md#1コマ目]
  - 全ての文字を赤文字に変えるJavaScriptプログラム

## 1コマ目

1コマ目の目的は、ビットくんを大きくすることで、プログラミング面白いかもと思っていただくことです。

### 全ての文字を赤文字に変えるJavaScriptプログラム

```
$('*').css('color', 'red')
```

- `$('*')` はビットくんのツイートページを構成する全ての要素（画面上に表示される全ての部品）を取得する命令です。
- `.` はドットの左側の値（レシーバー）が所有するドットの右側の変数や関数（プロパティ）を参照するという意味です。
- したがって、このプログラムの意味は、ビットくんのツイートページを構成する全ての要素が所有する`css`関数を呼び出すということです。
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

2コマ目の目的は、命令を実行する順序がプログラム全体の意味に大きく影響することを理解していただくことです。
また、課題を通して、ゴールとなるプログラムの実行結果を実現するために、命令の順序を考える体験をしていただきます。

### 先頭から2番目のツイートを1番目に移動するJavaScriptプログラム

```
e = $('li.stream-item').eq(1); e.parent().prepend(e)
```

- 2番目のツイート以外の順序は変わりません。
- 1番目のツイートは押し出されて、2番目のツイートになります。
- そのため、2番目のツイートと1番目のツイートが入れ替わります。

### 先頭から3番目のツイートを1番目に移動するJavaScriptプログラム

```
e = $('li.stream-item').eq(2); e.parent().prepend(e)
```

### 2番目のツイートを動かしてから、3番目のツイートを動かすJavaScriptプログラム（上記2プログラムのまとめ）

```
e = $('li.stream-item').eq(1); e.parent().prepend(e)
e = $('li.stream-item').eq(2); e.parent().prepend(e)
```

### 3番目のツイートを動かしてから、2番目のツイートを動かすJavaScriptプログラム

```
e = $('li.stream-item').eq(2); e.parent().prepend(e)
e = $('li.stream-item').eq(1); e.parent().prepend(e)
```

## 3コマ目

3コマ目の目的は、ループ（繰り返し）という概念について理解していただくことです。

### 1番目のツイートを赤文字に変えるJavaScriptプログラム

```
$('li.stream-item').eq(0).css('color', 'red')
```

### 2番目から5番目までのツイートを赤文字に変えるJavaScriptプログラム

```
$('li.stream-item').eq(1).css('color', 'red')
$('li.stream-item').eq(2).css('color', 'red')
$('li.stream-item').eq(3).css('color', 'red')
$('li.stream-item').eq(4).css('color', 'red')
```

### ループで1番目から5番目までのツイートを赤文字に変えるJavaScriptプログラム

```
for (i = 0; i < 5; i++) {
  $('li.stream-item').eq(i).css('color', 'red')
}
```

### ループで2番目から4番目までのツイートを緑文字に変えるJavaScriptプログラム

```
for (i = 1; i < 4; i++) {
  $('li.stream-item').eq(i).css('color', 'green')
}
```

## 4コマ目

4コマ目の目的は、条件分岐という概念について理解していただくことです。

### 1から10番目のツイートのうち、いいねの数が0個のツイートを半透明にするJavaScriptプログラム

```
for (i = 0; i < 10; i++) {
  e = $('li.stream-item').eq(i)
  if (e.find('.IconTextContainer:last').text() == 0) {
    e.css('opacity', 0.2)
  }
}
```

### 1番目から10番目のツイートのうち、ビットくんがつぶやいたツイートを赤色にそれ以外を緑色に変えるJavaScriptプログラム

```
for (i = 0; i < 10; i++) {
  e = $('li.stream-item').eq(i)
  if (e.find('.fullname').text().indexOf('ビット') >= 0) {
    e.css('color', 'red')
  } else {
    e.css('color', 'green')
  }
}
```

## 5コマ目

5コマ目の目的は、関数という概念について理解していただくことです。

### 指定したツイートを赤文字に変える`changeColor`関数を定義するJavaScriptプログラム

```
function changeColor(n) {
  $('li.stream-item').eq(n).css('color', 'red')
}
```

### `changeColor`関数で1番目と3番目のツイートを赤文字に変えるJavaScriptプログラム

```
changeColor(0)
changeColor(2)
```

### 指定したツイートのいいねを数える`countLike`関数を定義するJavaScriptプログラム

```
function countLike(n) {
  return Number($('li.stream-item').eq(n).find('.IconTextContainer:last').text());
}
```

### `countLike`関数で1番目と4番目のツイートのいいねを数えるJavaScriptプログラム

```
countLike(0)
countLike(3)
```

### ループと`countLike`関数で1番目から10番目までのツイートのいいねの数の合計を計算するJavaScriptプログラム

```
sum = 0
for (i = 0; i < 10; i++) {
  sum += countLike(i)
}
```
