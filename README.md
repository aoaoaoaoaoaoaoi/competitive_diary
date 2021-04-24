# 基本

* 計算量よりも単純であること（複雑なものはバグる）

* なるべく書かない（コード量が多いほどバグる）



# その他

* 組み合わせ問題

  組み合わせ問題の基本である書き出すを行うこと（いくつあるでしょうか）

* 感覚で解かない

  取り得る値をある程度考える、小さい数、大きい数、中途半端な数

  場合分け

* 階乗（！）

  DFS

  C++だと[next_permutation](https://qiita.com/siser/items/a91022071b24952d27d9)でもいける

* ceil

  ```(n1 / (n2 - 1)) / n2```が使用できるのは整数のみ

  基本はceilを使用する

* vector

  vectorは普通に渡しても参照にならない