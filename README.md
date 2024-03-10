# css_animation_01

動くWebデザインを実装しながら学習していきます。

***参考サイト***

https://coco-factory.jp/ugokuweb/

https://coco-factory.jp/ugokuweb/move01/4-1-4/



<br>

## Git管理化からinitial commit までの環境構築


```terminal
$ mkdir ~/workspace/create/css/
$ git clone git@github.com:[userName]/css_animation_01.git
※今回はリモートリポジトリを先に作り、クローンしてくる手順で行なっています。
$ cd ~/workspace/create/css/css_animation_01
$ git checkout -b dev
$ touch index.html
$ touch README.md
$ touch .ignore
```

***`.ignore`には以下を記述***

```.ignore
# macOS
.DS_Store
```


```terminal
$ git add .
$ git status -u
$ git commit -m "[Add] htmlファイルを作成"
$ git push
$ git push --set-upstream origin dev
```


<br>

## JQueryの導入

- JQueryを導入します。
- CDNで導入していきます。
- 最新バージョンは2023年に出た3.7.1のようです。
- `<head>`タグ内に`<script>`タグで記述します。


```html
<!-- index.html --> 

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
  <title>CssAnimation01</title>
</head>
```

- 画像の配置場所としてassets/imagesディレクトリを作成します。

```terminal
$ mkdir assets
$ mkdir images
```

- 任意で作成した画像を保存します。

```
~/assets/images/logo.png
```

<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/dd6958ee-3612-26a7-7413-ed43461002c8.png" alt="" width="50%" height=auto>


- 試しにJQueryでメソッドを記述してみます。

```
$ touch ~/assets/js/test.js
```

- 今回は試しに文字色を赤に変えるメソッドを記述しました。
- あくまでテストです。

```js
//spanタグの文字色を赤に変える

$(function(){
  $("span").css("color","red");  
});
```

- jsファイルにメソッドを記述したら、htmlファイルで読み込みます。
- <head>タグ内と<body>タグ、両方とも読み込んでくれました。
- どちらが良いか判断つきませんが、いったん、<body>タグに記述します。
- 作成したjsファイルを読み込むときはデフォルトだと、絶対パスではないとダメみたいです。

```html
index.html

<body>
  <h1>
    <span>CssAnimation01</span>
  </h1>

  <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
  <script src="${root}/css_animation_01/assets/js/test.js"></script>
</body>
```

<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/8b10aea1-3c58-76a3-699a-53cb1196ba30.jpeg" alt="" width="50%" height=auto>


- 無事に文字色が赤くなりました。JQuery正しく導入できたと思います。
- ここまでは普通のJavaScriptの実装みたいな感じです。
- JQueryではこのjsファイルに複雑なアニメーションの動きをけっこう簡単に実装できるコードが使えるようになるみたいです。
- ここから本番をやっていきますが、その前に一旦コミットしておきます。


<br>










<br><br><br>

## よく使うタグ

`<img src="" alt="" width="50%" height=auto>`

