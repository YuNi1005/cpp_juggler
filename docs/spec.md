# 基本仕様
タイトル：I'm Juggler<br>タイプ：3リール21コマ<br>ライン数：5ライン(上段、中段、下段、右上がり、右下がり)<br>ベット：1~3枚、 MAXベット対応<br>クレジット：上限設定なし(内部変数内を上限)<br>払い出し：クレジット加算(音と数値表示での表現)<br>停止順：任意(左中右を推奨)<br>リール画像：各リール1枚の縦長画像(21コマ分) 1コマの高さは128px<br>リール回転速度：80コマ/分(1コマ0.75秒)<br>入力方法：自作コントローラー<br>
使用ライブラリ：C++17 / SFML2.6<br>
フレームレート：60fps固定(VSYNC ON)

# リール構成
## 図柄ID
`JUGGLER7`、`BAR`、`BELL`、`CLOWN`、`GRAPE`、`CHERRY`、`REPLAY`

```
enum SymbolID {
    JUGGLER7,
    BAR,
    BELL,
    CLOWN,
    GRAPE,
    CHERRY,
    REPLAY
};
```

## 各リールのストリップ
`left_reel.png`<br>

`[BELL, JUGGLER7, REPLAY, GRAPE, REPLAY, GRAPE, BAR, CHERRY, GRAPE, REPLAY, GRAPE, JUGGLER7, CLOWN, GRAPE, REPLAY, GRAPE, CHERRY, BAR, GRAPE, REPLAY, GRAPE]`<br>

`center_reel.png`<br>

`[REPLAY, JUGGLER7, GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR, GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR, GRAPE, CHERRY, CLOWN]`<br>

`right_reel.png`<br>

`[GRAPE, JUGGLER7, BAR, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY]`<br>

```
struct ReelStrip {
    std::vector<SymbolID> symbols;
};

ReelStrip left  = { {BELL, JUGGLER7, REPLAY, GRAPE, REPLAY, GRAPE, BAR, CHERRY, GRAPE, REPLAY,GRAPE, JUGGLER7, CLOWN, GRAPE, REPLAY, GRAPE, CHERRY, BAR, GRAPE, REPLAY, GRAPE} };

ReelStrip center = { {REPLAY, JUGGLER7, GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR,GRAPE, CHERRY, REPLAY, BELL, GRAPE, CHERRY, REPLAY, BAR, GRAPE, CHERRY, CLOWN} };

ReelStrip right  = { {GRAPE, JUGGLER7, BAR, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE,CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY, GRAPE, CLOWN, BELL, REPLAY} };
```

# 成立ライン定義
```
const std::vector<std::array<int, 3>> paylines = {
    {0, 0, 0},  // 上段
    {1, 1, 1},  // 中段
    {2, 2, 2},  // 下段
    {0, 1, 2},  // 右下がり
    {2, 1, 0}   // 右上がり
};
```

# ペイテーブル
```
struct PayTableEntry {
    std::vector<SymbolID> pattern;
    int payout_3bet;
    int payout_2bet;
};

std::vector<PayTableEntry> payTable = {
    {{REPLAY, REPLAY, REPLAY}, 0, 0},        // 再遊技
    {{CHERRY, CHERRY, CHERRY}, 1, 7},        // チェリー
    {{GRAPE, GRAPE, GRAPE}, 8, 14},
    {{CLOWN, CLOWN, CLOWN}, 10, 10},
    {{BELL, BELL, BELL}, 14, 14},
    {{JUGGLER7, JUGGLER7, BAR}, -1, -1},     // REG
    {{JUGGLER7, JUGGLER7, JUGGLER7}, -2, -2} // BIG
};
```