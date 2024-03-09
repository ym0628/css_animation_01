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



