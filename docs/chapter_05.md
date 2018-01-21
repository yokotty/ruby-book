## 第５章 ハッシュやシンボルを理解する

### シンボル
- 任意の文字列と一対一に対応するオブジェクト
- ```:シンボル名``` で定義
- シンボルは Ruby の内部で整数として管理される
  - ２つの値が同じかどうか調べる場合，文字列よりも高速
- 同じシンボルであれば同じオブジェクト
  - メモリの使用効率が良い
- オブジェクトが管理するメソッド名はシンボルで管理されている

### メソッド呼び出し時の{}の省略

最後の引数がハッシュであればハッシュリテラルの {} を省略できる

### ハッシュ↔配列 (to_a，to_h)

```
[1] pry(main)> currencies = { japan: 'yen', us: 'dollear', india: 'rupee' }
=> {:japan=>"yen", :us=>"dollear", :india=>"rupee"}
[2] pry(main)> currencies.to_a
=> [[:japan, "yen"], [:us, "dollear"], [:india, "rupee"]]
[3] pry(main)> currencies_hash = currencies.to_h
=> {:japan=>"yen", :us=>"dollear", :india=>"rupee"}
[4] pry(main)> currencies_hash = Hash[currencies]
=> {:japan=>"yen", :us=>"dollear", :india=>"rupee"}
```

### 引数にハッシュ
```
# Ruby 2.0 から
def convert_length(length, from: :m, to: :m)
  (length / UNITS[from] * UNITS[to]).round(2)
end

# Ruby 2.1 からデフォルト値の省略も可能に
def convert_length(length, from:, to:)
  (length / UNITS[from] * UNITS[to]).round(2)
end
```

### **でハッシュ展開

```
h = { us: 'dollar', india: 'rupee' }
{ japan: 'yen', **h }
{ japan: 'yen' }.merge(h)

# 想定外の引数も受け取れるようにする
def buy_burger(menu, drink: true, potato: true, **others)
  puts others
end

buy_burger('fish', drink: true, potato: true, salad: true, chicken: false)  # => {:salad=>true, :chicken=>false}
```


