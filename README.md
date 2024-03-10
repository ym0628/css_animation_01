# css_animation_01

動くWebデザインを実装しながら学習していきます。
今回はロゴアニメーションの実装を目指します。

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


## CSSアニメーションの実装

- ここから本番
- CSSアニメーションを実装していきます


### ***<font color="salmon">まずはCSSを読み込む記述</font>***

- headタグ内に記述します。

```html
<!-- index.html -->
<link rel="stylesheet" href="./assets/css/style.css">
```

- 次に指定したCSSがまだ作られていないので作ります。

```terminal
$ touch assets/css/style.css
```

- 次に、ロゴ画像をhtmlで読み込ます
- CSSスタイルと同様、headタグ内に配置します

```html
<!-- index.html -->
<link rel="logo" href="./assets/images/logo.png">
```

- 画像がきちんと読み込まれたのでいったんOKとします

<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/7e676994-0959-db39-b93d-1693af773c03.jpeg" alt="" width="50%" height=auto>



<br>

### ***<font color="salmon">ロゴアニメーションの実装</font>***

***idnex.html***

- ひとまずこちらのページのソースコードをコピペします

https://coco-factory.jp/ugokuweb/move01/4-1-4/

- そこから不要な記述を削除したり微調整します。


***styles.css***

- 次にCSSにスタイルを実装します


***loading.js***

- 次にJSファイルを新規作成して実装します
- JQueryを使い、ロゴ画像の表示とフェードアウトを表現します
- なお、前回までに実装した`test.js`は不要なので一旦コメントアウトします



<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/eca70823-7965-cc1e-c2b6-954faab3c22a.jpeg" alt="" width="50%" height=auto>

- フェードアップしての表示はしてくれましたが、フェードアウトはしてくれません
- また、フェードアウト後の「ローディング後、この画面が見えます。」と表示されません
- どうやらJSの読み込みファイルを指定し忘れていました
- htmlの`script`タグの読み込みファイルを`loading.js`に差し替えました
- ついでに画像も別のSVG画像に差し替えてみました（なお、普通にpngファイルでもいけました

<br>


<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/5a174fb2-cc3d-4042-20d1-e96f4f0abd8f.jpeg" alt="" width="50%" height=auto>

- 2秒でロゴがフェードアウトして3秒でindex.htmlのbodyタグのテキストが表示される

<img src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3486945/983e2ac4-3c47-f7f9-23ac-3e4ba8670c8c.jpeg" alt="" width="50%" height=auto>

- これで思い通りの挙動を実現できました
- 以下、ソースコードになります


### ***<font color="salmon">ソースコード</font>***


```html
<!-- index.html -->

<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <!--==============レイアウトを制御する独自のCSSを読み込み===============-->
  <link rel="stylesheet" href="./assets/css/style.css">
  <link rel="logo" href="./assets/images/logo.png">
  <title>CssAnimation01</title>
</head>
<body>
  <div id="splash">
    <div id="splash_logo">
      <img src="./assets/images/react_logo.svg" alt="" width=25% height=auto class="fadeUp">
    </div>
  </div>

  <main>
    <div id="container">
      <p>ようこそ</p>
      <!--/container-->
    </div>
  </main>
  
  <!--==============JQuery読み込み（CDN読み込みと自作jsファイルの2つ）===============-->
  <script src="https://code.jquery.com/jquery-3.7.1.min.js"></script>
  <script src="/Users/matsuzakayuuta/workspace/create/css/css_animation_01/assets/js/loading.js"></script>
</body>
</html>
```

```css
/* styles.css　*/

@charset "utf-8";

/*========= LoadingのためのCSS ===============*/

/* Loading背景画面設定　*/
#splash {
    /*fixedで全面に固定*/
  position: fixed;
  width: 100%;
  height: 100%;
  z-index: 999;
  background:#333;
  text-align:center;
  color:#fff;
}

/* Loading画像中央配置　*/
#splash_logo {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* Loading アイコンの大きさ設定　*/
#splash_logo img {
  width:260px;
}

/* fadeUpをするアイコンの動き */

.fadeUp{
animation-name: fadeUpAnime;
animation-duration:0.5s;
animation-fill-mode:forwards;
opacity: 0;
}

@keyframes fadeUpAnime{
  from {
    opacity: 0;
  transform: translateY(100px);
  }

  to {
    opacity: 1;
  transform: translateY(0);
  }
}



/*========= レイアウトのためのCSS ===============*/

#container{
    font-size: 5rem;
    width:100%;
    height: 100vh;
    background: #ccc;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
}

a{
    color: #333;
}

a:hover{
     text-decoration: none;   
}
```

```js
// loading.js
// logoの表示
$(window).on('load',function(){
  $("#splash").delay(3000).fadeOut('slow');//ローディング画面を3.0秒（3000ms）待機してからフェードアウト
  $("#splash_logo").delay(2000).fadeOut('slow');//ロゴを2.0秒（2000ms）待機してからフェードアウト
});
```

<br>

## 感想

- CSSアニメーションが簡単にできました
- また、JQueryのメソッドを扱うのは初めて(？)だったので迷いそうでしたが、参考サイト様のおかげでそこまで迷わずに実装することができてよかったです
- `動くWebデザインアイディア帳` 最高です!!!ありがとうございました!!!
- 大体の実装の感じは掴めたので、今度は`TypeScript`と`Next.js`でCSSアニメーションを実装できるように挑戦していきます
- Next.jsとJQueryは共存できるのか？
- よくわかりませんが、調べながら挑戦していきます




<br><br><br>

## よく使うタグ

`<img src="" alt="" width="50%" height=auto>`

`***<font color="salmon">テキスト</font>***`

