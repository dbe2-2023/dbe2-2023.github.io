+++
title = "演習環境のインストール"
description = ""
weight = 20
alwaysopen = true
+++

## 演習環境

* 以下の4つのソフトウェアが必要となる．
  * Xampp
  * Python
  * Flask
  * Mysqlclient

## Xampp

* ドキュメンテーション学科の貸与PCには，
  すでにインストールされているはず．
* Xampp が動作していることを確認する．
  * apache と MySQL のサーバが起動して緑色の表示になること．
* Xamppをインストールしていない人は，
  以下からインストーラを得てインストールする:
  * https://www.apachefriends.org/jp/index.html

## Python

* ドキュメンテーション学科の貸与PCには，
  すでにインストールされているはず．
* そうでない場合には，[別ページ](../python_install) の指示に従って，Python をインストールする

## Flask

Flask は，Python のためのウェブフレームワークである．
それが何であるかはいずれ説明する．
次のようにインストールする．

* コマンドプロンプトを起動する．
* 次のコマンドを入力する．
   ```
   pip install flask
   ```

## Mysqlclient

mysqlclient は，Python から MySQL にアクセスするためのライブラリである．

* 自分のPythonのバージョンを確認する．具体的には次のようにする．
  * コマンドプロンプトを起動する．
  * 次のコマンドを入力する．バージョンが表示される．
    ```
    python --version
    ```
* https://pypi.org/project/mysqlclient/#files にアクセスする．
* ファイル `mysqlclient-*.*.*-cp310-cp310-win_amd64.whl` をダウンロードする．
  * この例はPython 3.10 の場合である．
  * Python 3.7, 3.8, 3.9 の場合は，
    上の310を37や38や39に変えたファイルをダウンロードする．
* コマンドプロンプトを開く．
* ダウンロードした `.whl` ファイルが置いてあるフォルダを
  カレントフォルダにする．
  具体的には次のように作業する．
  * エクスプローラで，`.whl` ファイルが置いてあるフォルダを開く．
  * 下図の赤い○が書いてある付近でマウスを右クリックする．
  {{< figure src="explore.jpg" >}}
  * 「アドレスのコピー」を選択する．
  * コマンドプロンプトで `cd` と入力して，引き続いてスペースを1個入れる．
  * コマンドプロンプト上でマウスを右クリックする．パスが入力されるはず．
  * エンターキーを押す．
  * `dir` と入力して引き続いてエンターキーを押す．
    先ほどダウンロードした `.whl` ファイルがリストされていることを確認する．
* 次のコマンドを入力する．
  ```
  pip install wheel
  pip install ダウンロードした.whlファイルの名前
  ```

## 演習環境の動作確認

* MySQL サーバが動作していることを確認する．
* [envchk.zip ファイルをダウンロード](envchk.zip)
  して，適当な場所で展開する．
* 展開された `dbchk.sql` を，MySQLにインポートする．
* データベース `dbe2` ができて，
  その中に「家計簿」テーブルが有ることを確認する．
* コマンドプロンプト を開き，cd コマンドを用いて，
  envchk が展開されているフォルダをカレントフォルダにする
  (すなわち，カレントフォルダに runflask.py が存在するようにする)．
  * さきほど Mysqlclient で実行したのと同様にする．
* コマンドプロンプトで，次のコマンドを実行する．
  ```
  python runflask.py
  ```
* 以下の行が出力されていることを確認する．
  ```
  Running on http://localhost:18080/ (Press CTRL+C to quit)
  ```
* ウェブブラウザをひらき，次のURLにアクセスする．
  * http://localhost:18080/check/2013/02/11
* ブラウザ上に赤字で以下の表示が含まれていればOK
  ```
  家計簿の2013-02-11のメモの内容は「書籍を購入」です．
  ```
* コマンドプロンプトを，バツ印で閉じる．Apache と MySQLサーバを終了して，
  Xampp control panel を閉じる．
