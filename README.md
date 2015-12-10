# 概要 Overview
RPGツクールMV用のプラグイン置き場です。

# 利用規約 Terms of use
MITライセンスです。

ソース内の「Copyright (c) chunkof」「@author chunkof」を残しておいてもらえれば、利用、改変、再配布は自由です。

[LICENSE.txt](LICENSE.txt)

# Plugins

## [ユーティリティ関数群 Utility](utility)
 - イベント条件として使うことを想定したユーティリティ関数群。
 - 「特定の時間帯限定」「特定の曜日限定」といったイベントが作成しやすくなる。

## キャッシュ制御 Cache control
Webで公開しているゲームについて、内容を更新したのに
「キャッシュ残りによって更新が反映されない」という現象を防止する。
 - [キャッシュ制御(簡易版) Cache control light](cachecontrol_light)
  - 形式
    - プラグイン
  - 対象
    - ゲームデータファイル(data/\*.json)
  - 方式
    - データベース：キャッシュを使用しない。
    - マップやイベント：versionIdが異なる場合はキャッシュを使用しない。


 - [キャッシュ制御 Cache control](cachecontrol_easy)
  - 形式
    - gulp + スクリプト
  - 対象
    - ゲームデータファイル(data/\*.json)
    - 本体スクリプト(\*.js)
    - プラグイン(plugins/\*.js)
    - その他index.htmlで直接読み込んでいるもの(css、icon)
  - 方式
    - ファイルの中身に変更があった場合はキャッシュを使用しない。
