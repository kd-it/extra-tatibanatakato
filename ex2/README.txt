# 問題2

このディレクトリにあるDockerfileを使って、以下の挙動となるイメージを作成せよ。

1. テキスト "ex2" を出力する
2. 現在の時間を `date` コマンドで出力する(9時間ずれるのは仕様です)

## 実行例

```
$ docker build -t test . # イメージ生成
$ docker run --rm test   # イメージの実行
```

出力例(2/24 15:10実行、9時間ずれるのは正解です)

```
ex2
Fri Feb 24 06:10:55 UTC 2023
```

## ヒント

`Dockerfile` にて、CMD命令を用いるとイメージからコンテナを生成した際に渡したコマンドを実行する。
シェル(`/bin/sh`)に渡されるため、セミコロン(`;`)を用いることで複数のコマンドを連続で実行する。

例:

```Dockerfile
FROM ubuntu:jammy
CMD echo foo; echo bar
```

このイメージは起動すると

```
foo
bar
```

という出力になる。

※ vscodeで動かすとき、"Run Interactive"を利用すること(出力が確認できないため)
