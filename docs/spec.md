# 基本仕様
タイトル：I'm Juggler<br>タイプ：3リール21コマ<br>ライン数：5ライン(上段、中段、下段、右上がり、右下がり)<br>ベット：1~3枚<br>
リール画像：各リール1枚の縦長画像(21コマ分) 1コマの高さは128px<br>
使用ライブラリ：C++ / SFML2.6<br>
フレームレート：60fps固定

# リール構成
## 図柄ID
`JUGGLER7`、`BAR`、`BELL`、`CLOWN`、`GRAPE`、`CHERRY`、`REPLAY`
## 各リールのストリップ
`left_reel.png`<br>
`[BELL, JUGGLER7, REPLAY, GRAPE, REPLAY, GRAPE, BAR, CHERRY, GRAPE, REPLAY, GRAPE, JUGGLER7, CLOWN, GRAPE, REPLAY, GRAPE, CHERRY, BAR, GRAPE, REPLAY, GRAPE]`<br>

`center_reel.png`<br>
``
`right_reel.png`<br>
``