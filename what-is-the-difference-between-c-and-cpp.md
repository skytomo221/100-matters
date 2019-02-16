[:contents]

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            こんにちは、プログラミング初心者の「**コウちゃん**」です。
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            こんにちは、プログラミングのことなら、お茶の子さいさい、「**おちゃっぱちゃん**」です。
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            今回は「C言語とC++って何が違うの？」について、やっていきましょう！
            <br>
        </span>
    </div>
</body>

## CとC++の違い

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            C言語とC++って結局何が違うの？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            簡単に言うと、古くなってしまった昔のC言語に
            **増築**するような形で、 新しく機能をC言語に追加したものが「C++」なんです。
            <br>
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            っていうことは、C++は
            **C言語の進化版**ってこと？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            そゆこと
            <br>
        </span>
    </div>
</body>

Wikipediaにも書いてあるように、C++は 1983年にベル研究所のコンピュータ科学者のビャーネ・ストロヴストルップが、 C言語の拡張として開発しました。 拡張はクラスの追加に始まり、仮想関数、多重定義、多重継承、 テンプレート、例外処理といった機能がどんどん追加されていきました。

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            C++はC言語の拡張なので、
            **C言語で書けるソースコードは、 C++でも書けます。**
            <span style="font-size: 80%">（何気にココ重要！）</span>
            <br>
        </span>
    </div>
</body>

<body>
    <ul class="checklist">
        <li>C++はC言語の進化版</li>
        <li>C言語で書けるソースコードは、 C++でも書ける</li>
    </ul>
</body>

## C++での入出力関数

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            コウちゃん、C言語で「Hello World!」って表示するプログラム書ける？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-kou-oko"></span>
        <span class="balloon-kou">
            おうおう、それくらい私だって、お茶の子さいさいだぞ。
            <br> 舐めてもらっちゃ困るな！
            <br>
        </span>
    </div>
</body>

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
```

<body>
    <div>
        <span class="icon-kou-jitome"></span>
        <span class="balloon-kou">
            ほらよ
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa-waraase"></span>
        <span class="balloon-ochappa">
            そんなに怒らなくても…
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そうだね、正解。
            <br>これをC++で書くと、どんな感じになるかというと…
            <br>
        </span>
    </div>
</body>

```c
#include <iostream>

int main() {
	std::cout << "Hello World!" << std::endl;
    return 0;
}
```

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            こうなります。
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            おお、結構違う
            <br>
        </span>
    </div>
</body>

### iostreamについて

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            この`iostream`って何？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            C言語では文字列を出力するときは`printf`、 文字列を入力するときは`scanf`を使っていたけれど、これを使うには`stdio.h`を`#include`しなければならなかったでしょう？
            <br> C++では、文字列を出力するときは`cout`、 文字列を入力するときは`cin` を使い、これらを使うときは`iostream`を`#include`しなければならないのです。
            <br>
        </span>
    </div>
    <div>
        <span class="icon-kou-knyacki"></span>
        <span class="balloon-kou">
            なるほど
            <br>
        </span>
    </div>
</body>

<body>
    <ul class="checklist">
        <li>C++で入出力関数を使うときは`iostream`を`#include`する</li>
    </ul>
</body>

### coutについて

```c
#include <iostream>

int main() {
	std::cout << "Hello World!\n" << std::endl;
    return 0;
}
```

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            先程言ったように、C++で文字列を出力するときは、`cout`を使います。
            <br> `cout`はcharactor outputの略です。 具体的に`cout`の後に`<<`（左シフト演算子）を書き、その後に表示したい文字列を出力できます。 <br>
        </span>
    </div>
    <span class="wrapnote">
        <p>本来なら`<<`は左シフト演算子ですが、</p>
        <p>C++で出力するときに使われるこの演算子は、</p>
        <p>特別に**出力演算子**や、**挿入演算子**、</p>
        <p>または**インサータ**などと呼ばれています。</p>
    </span>
</body>

```c
#include <iostream>

int main() {
	std::cout << "Hello" << " " << "World!" << std::endl;
    return 0;
}
```

複数の文字列を表示したいときも、このように<<演算子を繋げて、書くことができます。

```c
#include <iostream>

int main() {
	std::cout
	<< "Melody in the sky" << std::endl
	<< std::endl
	<< "Raindrops have been falling down from gray colored" << std::endl
	<< "sky and now they ran into my heart" << std::endl
	<< "This high wall painted black is cutting off all my view" << std::endl
	<< "and even blocking sunlight from me" << std::endl
	<< std::endl;
    return 0;
}
```

長い文章を表示するときは、このように複数行に分けて書く手法もあります。  
（スマホで見ている方は横にして見ると読みやすいと思います。）

<body>
    <div>
        <span class="icon-kou-kyupi"></span>
        <span class="balloon-kou">
            さっきからずっとわかんないだけど、この`endl`はなに？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa-waraase"></span>
        <span class="balloon-ochappa">
            説明してなかったね。ごめんごめん。
            <br> `endl`を使うと、改行になるのよ。
            <br> だから、C++で改行を出力したいときは、`endl`を使います。
            <br>
        </span>
    </div>
    <span class="wrapnote">
        <p>`endl`のように関数に挿入したり、関数から抽出</p>
        <p>したりする値で特別な効果を持つもののことを</p>
        <p>**マニピュレータ**といいます。</p>
    </span>
</body>

<body>
    <ul class="checklist">
        <li>C++で文字列を出力するときは`cout`を使う</li>
        <li>C++で改行を出力するときは`endl`を使う</li>
        <li>出力するときに使う演算子を出力演算子という</li>
        <li>マニピュレータとは、関数に挿入したり、関数から抽出したりする値で特別な効果を持つもののことである</li>
    </ul>
</body>

### 名前空間について

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            今更なんだけど、`std::cout`とか`std::endl`の`std::`っていうのは何？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            それは名前空間といって、同じ関数名が衝突しないようにあるんだよ。
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            どゆことー？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            例えば、同じクラスの「伊藤さん」と、B組の「伊藤さん」がいたとします。 すると、「伊藤さん」だけだと、どちらの「伊藤さん」なのか区別がつきません。 そこで「同じクラスの伊藤さん」、「B組の伊藤さん」とそれぞれ呼ぶことで、 混乱しなくて済みました。
            <br> プログラミングでも、もし自分で`cout`関数を作ったとしたら、 `std`の`cout`関数と名前がダブってしまうでしょう？
        </span>
    </div>
    <span class="wrapnote">
        <p>2つ以上の関数名や、変数名が重なっていること</p>
        <p>を「**衝突する**」と表現します。</p>
        <p>ここでは「名前空間によって、同じ関数名が</p>
        <p>あっても衝突を防ぐ」という話をしています。</p>
    </span>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            だから、`std`の`cout`っていう意味で、`std::cout`って書いてんだ。
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そうです。
            <br> ちなみに`::`のことを**スコープ解決演算子**といいます。
            <br> `std`という名前空間はおそらくstandardの略で、そこにはC++が標準で提供している関数やテンプレートがまとまっています。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            でもさ、
            <br>
        </span>
    </div>
</body>

```c
#include <iostream>

int main() {
	std::cout << "Hello World!" << std::endl;
	std::cout << "Hello World!" << std::endl;
	std::cout << "Hello World!" << std::endl;
	std::cout << "Hello World!" << std::endl;
	std::cout << "Hello World!" << std::endl;
    return 0;
}
```

<body>
    <div>
        <span class="icon-kou-waraase"></span>
        <span class="balloon-kou">
            これ、毎回`std`って書くの大変じゃない？
            <br>だいたい間違っても独自のcout関数なんて宣言しないし。
            <br>衝突しないように気をつければいいんじゃない？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そうだね。先程のたとえ話でいうと、同じクラスの人同士で「伊藤さん」って言ったら普通「同じクラスの伊藤さん」になるのと同じ感覚だね。
            <br>そういうときは、`using namespace 名前空間`とすることで、その名前空間を省略して使うことができるようになります。
        </span>
    </div>
</body>

```c
#include <iostream>

using namespace std;

int main() {
	cout << "Hello World!" << endl;
	cout << "Hello World!" << endl;
	cout << "Hello World!" << endl;
	cout << "Hello World!" << endl;
	cout << "Hello World!" << endl;
	return 0;
}
```

<body>
    <div>
        <span class="icon-kou-wara"></span>
        <span class="balloon-kou">
            すっきり！
            <br>
        </span>
    </div>
</body>


<body>
    <ul class="checklist">
        <li>名前空間は、関数などの集合を分割することで衝突の可能性を低減しつつ参照を容易にする概念である。</li>
        <li>名前空間を省略するときは`using namespace`を使う</li>
    </ul>
</body>

### string型について

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            C言語では文字列を扱うとき`char str[]`とか`char *str`とか宣言してましたね。
            <br> しかし、C++には`string`型（文字列型）という便利な型があります。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            具体的にどう便利なの？
            <br>
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            それはこれから、話していきましょう。
        </span>
    </div>
</body>

#### string型の基本的な使い方

```c
#include <iostream>
#include <string>

using namespace std;

int main() {
	string hello = "Hello";
	cout << hello << endl;
}
```

その前に、`string`型の基本的な使い方を見ましょう。  
上記のプログラムは`string hello`で宣言と同時に`"Hello"`を代入し、`cout`で表示するプログラムです。  
実行結果はこの通り。  
なお、`string`型を使うには`string`を`#include`する必要があります。

実行結果

```実行結果
Hello
```

#### 連結できる

```c
#include <iostream>
#include <string>

using namespace std;

int main() {
	string hello = "Hello";
	string world = "World";
	string hello_world = hello + " " + world + "!";
	cout << hello_world << endl;
}
```

こんなふうに足し算で文字列を連結できます。

実行結果

```実行結果
Hello World!
```

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            ね？便利でしょ？
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            あら、ほんと
            <br>
        </span>
    </div>
</body>

#### string型をconst char*型に変換したいとき

そんなときは`const char* chars = str.c_str();`で`const char*`型に変換できます。

#### char*型をstring型に変換したいとき

逆はもっと簡単。  
`string str = std::string(chars);`とキャストすれば`string`型に変換できます。

<body>
    <ul class="checklist">
        <li>C++には`string`型（文字列型）がある</li>
        <li>`string`型を使うには`string`を`#include`する必要がある</li>
        <li>足し算で文字列を連結できる</li>
        <li>`const char* chars = str.c_str();`で`const char*`型に変換できる</li>
        <li>`string str = std::string(chars);`で`string`型に変換できる</li>
    </ul>
</body>

### cinについて

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            まだ`cin`について話してないね！
            <br>`cin`はC言語の`scanf`と同じ役割を果たします。
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>

using namespace std;

int main() {
	string str = "";
	cin >> str;
	cout << str;
}
```

`cout`と演算子の向きが逆なので気をつけましょう。

<body>
    <ul class="checklist">
        <li>入力関数は`cin`を使う</li>
    </ul>
</body>

## 最後に

これでCとC++の違いの説明は終わりです。  
お疲れ様でした。

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            ではまた次の機会に！
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            ばいばい！
        </span>
    </div>
</body>
