# 基本仕様
タイトル：I'm Juggler<br>タイプ：3リール21コマ<br>ライン数：5ライン(上段、中段、下段、右上がり、右下がり)<br>ベット：1~3枚、 MAXベット対応<br>クレジット：上限設定なし(内部変数内を上限)<br>払い出し：クレジット加算(音と数値表示での表現)<br>停止順：任意(左中右を推奨)<br>リール画像：各リール1枚の縦長画像(21コマ分) 1コマの高さは128px<br>リール回転速度：80コマ/分(1コマ0.75秒)<br>入力方法：自作コントローラー<br>
使用ライブラリ：C++17 / SFML2.6<br>
フレームレート：60fps固定(VSYNC ON)

# リール構成
## 図柄ID
`JUGGLER7`、`BAR`、`BELL`、`CLOWN`、`GRAPE`、`CHERRY`、`REPLAY`
## 各リールのストリップ
`left_reel.png`<br>

`[BELL, JUGGLER7, REPLAY, GRAPE, REPLAY, GRAPE, BAR, CHERRY, GRAPE, REPLAY, GRAPE, JUGGLER7, CLOWN, GRAPE, REPLAY, GRAPE, CHERRY, BAR, GRAPE, REPLAY, GRAPE]`<br>

`center_reel.png`<br>

`[REPLAY, JUGGLER7, GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR, GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR, GRAPE, CHERRY, CLOWN]`<br>

`right_reel.png`<br>

`[GRAPE, JUGGLER7, BAR, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY]`<br>

# 成立ライン定義
リールの表示行を `0=上, 1=中, 2=下` とし、
- Line1： `[0, 0, 0]`
- Line2： `[1, 1, 1]`
- Line3： `[2, 2, 2]`
- Line4： `[0, 1, 2]`
- Line5： `[2, 1, 0]`

# ペイテーブル
|図柄|揃い形|払い出し(3BET)|払い出し(2BET)|
|:---:|:---:|:---:|:---:|
|`REPLAY`|3連|BET戻し|BET戻し|
|`CHERRY`|左停止|1枚|7枚|
|`GRAPE`|3連|8枚|14枚|
|`CLOWN`|3連|10枚|10枚|
|`BELL`|3連|14枚|14枚|
|``|3連|REGボーナス|REGボーナス|
|``||||
