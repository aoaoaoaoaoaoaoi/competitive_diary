# コンテスト
2021/04/17<br>
[第二回日本最強プログラマー学生選手権](https://atcoder.jp/contests/jsc2021?lang=ja)

# 記録
## 総合
|  順位  |  パフォーマンス  | レーティング |
| ---- | ---- | ---- |
|  2304th / 4003  |  608  | 674 → 668 (-6) |

## 提出
|  時間  |  問題  | 結果 |
| ---- | ---- | ---- |
|  2021-04-17 18:09:37  |  D  | WA |
|  2021-04-17 18:07:22  |  D  | WA |
|  2021-04-17 17:15:29  |  C  | AC |
|  2021-04-17 16:33:30  |  B  | AC |
|  2021-04-17 16:16:34  |  A  | AC |

# 心がけたこと
* 単純に考えること<br>
 → 計算量が多くなってもTLEしないならその方がいい<br>
* コード量を減らす（自分で書いたり考える部分を減らす）<br>

# 詳細
## [A問題](https://atcoder.jp/contests/jsc2021/tasks/jsc2021_a)
### [提出コード](https://atcoder.jp/contests/jsc2021/submissions/21807343)
```
	int main(void)
	{
		double x, y, z; cin >> x >> y >> z;
		double u = (y / x) * z;
		int ans = ((int)u == u) ? (int)u - 1 : (int)u;
		cout << ans << endl;
	}
```

### コメント
[解説](https://atcoder.jp/contests/jsc2021/editorial/1103)が (Y * ( Z / X )) → ((Y * Z) / X )) で同じ値段だから ((Y * Z - 1) / X ))<br>
感覚がよく分からないけど、Xは1以上なので引く数は1以下であれば同じ答えになるはず<br>
1番数が単純だから1を引いていると思う<br>

## [B問題](https://atcoder.jp/contests/jsc2021/tasks/jsc2021_b)
### [提出コード](https://atcoder.jp/contests/jsc2021/submissions/21814665)
```
	int main(void)
	{
		int n, m; cin >> n >> m;
		vector<int>a(n);
		vector<int>b(m);
		for (int i = 0; i < n;++i) {
			cin >> a[i];
		}
		for (int i = 0; i < m;++i) {
			cin >> b[i];
		}
		vector<int>result;
		std::set_difference(a.begin(),a.end(), b.begin(),b.end(),inserter(result,result.end()));
		std::set_difference(b.begin(), b.end(), a.begin(), a.end(), inserter(result, result.end()));
		sort(result.begin(), result.end());
		for (int i = 0; i < result.size();++i) {
			cout << result[i];
			cout << " ";
		}
	}
```

### コメント
ループして差分とろうと思ったけど、C++にも差分とるのあるはずと思ってググった<br>
[set_difference](https://cpprefjp.github.io/reference/algorithm/set_difference.html)を使用した<br>
[解説](https://atcoder.jp/contests/jsc2021/editorial/1104)は[set_symmetric_difference](https://cpprefjp.github.io/reference/algorithm/set_symmetric_difference.html)を使用している<br>
こちらの方が一発なのでよさげ

## [C問題](https://atcoder.jp/contests/jsc2021/tasks/jsc2021_c)
### [提出コード](https://atcoder.jp/contests/jsc2021/submissions/21822527)
```
	int main(void)
	{
		int a, b; cin >> a >> b;
		
		//あり得る数
		int able = (int)(b - a);
		int ans = 1;
		for (int i = able; 0 < i; --i) {
			int w = b / i;
			int shita = (w - 1) * i;
			int ue = w * i;
			if (a <= shita && shita <= b && a <= ue && ue <= b) {
				ans = i;
				break;
			}
		}
		cout << ans << endl;
	}
```

### コメント
* はまりそうになった<br>
初め素因数分解で段階的に出てくる整数をmapに入れて、複数個あったら答えっていう方法にしてたけど<br>
素因数分解では全ての約数を得ることはできない（全ての素因数を割り出して組み合わせることで可能になる）<br>
sample3で気づいたからsampleに助けられたけど、最近のはまりパターンになる可能性大きかった<br>

* 時間<br>
解法を思いつくまでに時間かかりすぎた<br>
範囲内の最大の数を2で割ったときが最大の約数になると思ってて、約数については何となくいけてたけど<br>
範囲の大きさによって決まるところまではなかなかいかなかった<br>

* [解説](https://atcoder.jp/contests/jsc2021/editorial/1105)<br>
```if((A + c - 1) / c < B / c)``` で判定していてシンプル<br>
```(A + c - 1)```の```c - 1``` はA以上の範囲で最低のものを探すから<br>
つまり（A以上の範囲で最低のもの）＜（B以下の範囲）になる

## [D問題](https://atcoder.jp/contests/jsc2021/tasks/jsc2021_d)
### 提出コード

### コメント
* 時間<br>
解法を思いつくまでに時間かかりすぎた<br>
残り5分くらいで分かった<br>
初め値を固定するのかなと思って 1,1,1,1 みたいな書き出しをしてた<br>
普通に組み合わせ問題の書き出しをすればよかった<br>
「いくつ（組み合わせが）あるでしょうか」は書き出し<br>

* modint
今回は10^9だから単純にループしてmodしてもTLEだった<br>
modpowしないといけなかった<br>
modintのライブラリ使うか、modpowするか