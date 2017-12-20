## 第２章 Ruby の基礎を理解する

### すべてがオブジェクト

```
/\d+/.to_s => "(?-mix:\\d+)"
/\d+/.class => Regexp
```

### 文字列

- 文字列中の式展開
    - ダブルクオートで展開
    - バックスラッシュでエスケープ

    ```
    name = 'Alice'
    puts "Hello, #{name}!"
    puts "He said, \"Don't speak.\"" 
    ```

- 「ダブルクオートを使う必要性がない場合はシングルクオートを使う」というコーディング規約がある場合も

### 数値

- 数値 ↔ 文字列への暗黙キャストはされない

    ```
    1 + '10'.to_s
    1 + '10.5'.to_f

    number = 3
    'Number is ' + number.to_s
    "Number is #{number}"  # 式展開では自動的に to_s メソッドが呼ばれる
    ```

- 少数の丸め誤差
    - Raditional（有理数）クラスを使うと期待通りの結果が得られる

    ```
    0.1 * 3.0 == 0.3 #=> false
    0.1 * 3.0 <= 0.3 #=> false
    0.1r * 3r == 0.3
    0.1r * 3r <= 0.3
    ```

### 真偽値

- false または nil であれば偽，それ以外は真
    - nil? メソッドを使うかオブジェクトをそのまま真偽値にするか

### 論理演算子

- && は || よりも優先度が高い

    ```
    t1 = true
    t2 = true
    f1 = false
    f2 = false
    t1 && t2 || f1 && f2
    (t1 && t2) || (f1 && f2)
    ```
    
### if文

- if が戻り値を返す
    ```
    country = 'italy'
    greeting =
               if country == 'japan'
                 'こんにちは'
               elsif country == 'us'
                 'Hello'
               elsif country == 'italy'
                 'ciao'
               else
                 '???'
               end
    greeting #=> 'ciao'
    ```

### %記法

```
%q!hoge! # hoge をシングルクオートで囲んでいる
%Q!hoge! # hoge をダブルクオートで囲んでいる（改行文字や式展開が利用可）
%!hoge! # hoge をダブルクオートで囲んでいる
%?hoge?
%{hoge} # 任意の記号を区切り文字として利用可
```

### 10進数以外の整数リテラル
```
0b11111111 #2進数 0b
0377 # 8進数 0
0xff # 16進数 0x
```

### 数値クラス
- Numeric（数値）
    - Integer, Float, Rational, Complex

### ！で終わるメソッド
- 慣習として「使用する際は注意が必要」という意味を持つ
   - 破壊的メソッド：upcase!, reverse!
   
### 式(Expression)と文(Statement)

- 式：値を返し，結果を変数に代入できるものが式
- 文：値を返さず，変数に代入しようとすると構文エラーになるものが文

### 擬似変数

```
nil
true
false
self
__FILE__
__LINE__
__ENCODING__
```

### 参照渡し

```
a = 'hello'
b = 'hello'
a.object_id #=> 70228332612480
b.object_id #=> 70228332565520
a == b #=> true
a.equal?(b) #=> false
```

### require_relative

- 実行しているディレクトリがパスの起点になる
