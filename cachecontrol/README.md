# Cache Control

Web公開しているゲームに更新をかけても、キャッシュファイルが残っていて更新が反映されないことがあります。
それを防止するためのgulpファイル+スクリプトのセットです。

##方式

クエリパラメータとしてハッシュ値を付与します。例えば「Map001.json」というファイルをロードするとき、直前でファイル名を「Map001.json?v=ハッシュ値」に差し替えます。

## 対象
 - index.htmlで直接読み込んでいるファイル。
 - プラグイン(js/plugins/\*.js)
 - ゲームデータ(data/\*.json)

## 使用方法

### 準備
 - Gulpのインストール
 - index.htmlがキャッシュされないようにしておく(メタタグやサーバの設定などで)

### 初回

  1. gulpfile.jsのdevlop_dirにプロジェクトフォルダのパスを設定。

  1. index.htmlのplugins.jsとmain.jsの間にスクリプトを追加。

    ```html
    <script type="text/javascript" src="js/plugins.js"></script>
    <script type="text/javascript" src="js/chunkof_FileHashList.js"></script>
    <script type="text/javascript" src="js/chunkof_CacheControl.js"></script>
    <script type="text/javascript" src="js/main.js"></script>
    ```

  1. $ npm install

  1. $ gulp

    chunkof_FileHashList.jsは、このタイミングで生成されます。

### 2回目～

  1. $ gulp

## Mecanism

1. [gulp-hash-creator](https://www.npmjs.com/package/gulp-hash-creator)でファイル名とハッシュ値のリストを生成。

2. [gulp-static-hash](https://www.npmjs.com/package/gulp-static-hash)でindex.htmlから読み込んでいるファイルにハッシュ値を付与。

3. プラグインやデータのロード時に1.で生成したハッシュ値を付与。

1.と2.はgulpがやって、3.はゲームを起動したときに行われます。
