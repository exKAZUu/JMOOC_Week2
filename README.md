# JMOOC_Week2

## 1コマ目

### 全ての文字を赤文字に変えるJavaScriptプログラム

```
$('*').css('color', 'red')
```

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
