## 第４章 配列や繰り返し処理を理解する

### RGB変換プログラム

0.to_s(16)
255.to_s(16)

```
# 0埋め (桁数, 埋める文字)
.rjust(2, '0')
```

### 要素取得

```
a = [1, 2, 3]
a[-1] #=> 3
a.last #=> 3
a.last(2) #=> [2, 3]
a.first #=> 1
a.first(2) #=> [1, 2]
a[1, 2] #=> [2, 3]
```

### 要素変更
- 負の添字で値の代入をする場合は元の配列の長さを超えるとエラーになる

```
a = [1, 2, 3]
a[-4] =10 
#=> IndexError: index -4 too small for array; minimum: -3
        from (irb):27
        from /usr/local/var/rbenv/versions/2.4.2/bin/irb:11:in `<main>'
```

- 開始位置と長さを指定して置き換え

### 要素連結
- concat は元の配列が破壊的変更
- \+ は非破壊

### splat展開

- \* を付けると配列が展開される

```
e, *f = 100, 200, 300 => [100, 200, 300]
e => 100
f => [200, 300]
```

- *可変長引数

### ミュータブル／イミュータブル

- イミュータブル
    - 数値（Integer, Float） 
    - シンボル（Symbol）
    - true/false（TrueClass, FalseClass）
    - nil

## ブロック
### 添字付き繰り返し

- each_with_index
- each.with_index
- map.with_index
- delete_if.with_index

each/map/delete_if などは Enumrator オブジェクトを返す

- with_index(1)
    - インデックスを0以外からスタート

### do...end と {} の結合度

- {} の結合度は強いため，引数付きメソッド呼び出しで{}をブロックとして使う場合はメソッド引数の()を省略できない

```
# a.delete(100) → ブロック呼び出し
a.delete(100) do
  'NG'
end

# delete(100) {'NG'} → ブロック呼び出し
a.delete 100 {'NG'} → 100 {'NG'} と解釈されて構文エラー
```


