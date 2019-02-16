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
            今回は「オブジェクト指向」について、やっていきましょう！
            <br>
        </span>
    </div>
</body>

## オブジェクト指向とは

**オブジェクト**とは、そのまま「もの」という意味です。  
ゲームで例えると、人間、敵、装備品、快復アイテムなど、すべてものですので、それらはすべてオブジェクトとなります。

<figure class="figure-image figure-image-fotolife" title="「GUMI」も「わぬ」もオブジェクト！">[f:id:skytomo:20180830185243p:plain]<figcaption>「GUMI」も「わぬ」もオブジェクト！</figcaption></figure>

**オブジェクト指向**とは、オブジェクトを中心に考えることです。
例えば、RPGなどで、人間は名前を持ち、座右の銘を持ち、そして戦ったり、眠ることができます。  
このように、オブジェクトが **どういうデータを持っているか**（名前、座右の銘など）、**どういう操作ができるか**（戦う、眠るなど）をまとめたものがオブジェクト指向で大切なのです。

<body>
    <ul class="checklist">
        <li>オブジェクトは、「もの」と表せるもの</li>
        <li>オブジェクト指向は、オブジェクトを中心に考えることである</li>
        <li>オブジェクトがどういうデータを持っているか、どういう操作ができるかをまとめたものがオブジェクト指向で大切である</li>
    </ul>
</body>

## RPGを作ってみよう

<body>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            ええ、RPGなんて作るの？
        </span>
    </div>
    <div>
        <span class="icon-ochappa-waraase"></span>
        <span class="balloon-ochappa">
            オブジェクト指向を教えるにあたってRPGは説明しやすいんだよ<br>
            まあ、簡単なRPGを作るから、安心して。
        </span>
    </div>
</body>

### RPGの計画書

#### RPGに登場するオブジェクト

<body>
    <div>
        <span class="wrapnote">
            <p>【人間】</p>
            <p>◆どういうデータを持っているか</p>
            <p>・名前</p>
            <p>・座右の銘</p>
            <p>・体力</p>
            <p>・最大体力</p>
            <p>・レベル</p>
            <p>・経験値</p>
            <p>・お金</p>
            <p>・アイテム所持</p>
            <p>・装備</p>
            <p>◆どういう操作ができるか</p>
            <p>・攻撃</p>
            <p>・睡眠</p>
            <p>・アイテムを使う</p>
            <p>・装備をつける</p>
            <p>・経験値をゲットする</p>
            <p>・発言</p>
        </span>
        <span class="wrapnote">
            <p>【敵】</p>
            <p>◆どういうデータを持っているか</p>
            <p>・名前</p>
            <p>・体力</p>
            <p>・経験値</p>
            <p>・お金</p>
            <p>・アイテム所持</p>
            <p>◆どういう操作ができるか</p>
            <p>・攻撃</p>
        </span>
    </div>
</body>

#### 経験値との相関関係

経験値が上がれば、レベルが上がり、  
レベルが上がれば、最大HPが上がるようにします。

<body>
    <div>
        <span class="wrapnote">
            <p>最大HPの設定</p>
            <p>Lv.1→最大HP:10</p>
            <p>Lv.2→最大HP:15</p>
            <p>Lv.3→最大HP:20</p>
            <p>Lv.4→最大HP:25</p>
            <p>Lv.5→最大HP:30</p>
            <p>最大HPはレベル1上がるごと</p>
            <p>に5だけ増加します。</p>
        </span>
    </div>
</body>

経験値とレベルの相関関係は次のようにします。
[f:id:skytomo:20180830185320p:plain]
[f:id:skytomo:20180830185234p:plain]

<body>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            計画書の最後らへん難しい数式あったけど…
        </span>
    </div>
    <div>
        <span class="icon-ochappa-waraase"></span>
        <span class="balloon-ochappa">
            あまり気にしないで。
        </span>
    </div>
</body>

## とりあえず構造体で作ってみる

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            コウちゃんとりあえず簡単に構造体を使ってRPGを実装してみて。
            <br> 部分的でいいから。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            はいよ
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>
#include <math.h>

using namespace std;

struct Human {
	/* どういうデータがあるか */
	string name; // 名前
	string motto; // 座右の銘
	int HP; // 体力
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
	int EXP; // 経験値
	int money; // お金
};

// 初期化
void init(Human& human) {
	human.name = "";
	human.motto = "";
	human.HP = 10;
	human.maxHP = 10;
	human.level = 1;
	human.EXP = 0;
	human.money = 0;
}

// キャラクターの状態を表示
void info(Human human) {
	cout
	<< "◆名前：" << human.name
	<< "◆座右の銘：" << human.motto
	<< "◆体力：" << human.HP << "/" <<  human.maxHP
	<< "◆レベル：" << human.level
	<< "◆経験値：" << human.EXP
	<< "◆所持金：" << human.money
	<< endl;
}

// 発言
void say(Human human, string str) {
	cout << human.name << "「" << str << "」" << endl;
}

int main() {
	// 宣言
	Human player;

	// 初期化
	init(player);

	// 名前の設定
	player.name = "コウちゃん";

	// キャラクターの状態を表示
	info(player);

	// 発言
	say(player, "せっかくだから、俺はこの赤の扉を選ぶぜ！");

	return 0;
}
```

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            どう？
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            うん、いいと思うよ
        </span>
    </div>
</body>

## クラスを使って作ってみる

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            構造体では、どういうデータを持っているかまとめることができたのでした。
            <br> では、私がこれからC++で新たに追加された「クラス」というものを使ってコウちゃんの書いたソースコードを変えていきます。
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>

using namespace std;

class Human {
public:
	/* どういうデータがあるか */
	string name; // 名前
	string motto; // 座右の銘
	int HP; // 体力
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
	int EXP; // 経験値
	int money; // お金
	
	// コンストラクタ（初期化）
	Human() {
		name = "";
		motto = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// デストラクタ
	~Human() {
	}
	
	/* どういう操作ができるか */
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆座右の銘：" << motto
		<< "◆体力：" << HP << "/" << maxHP
		<< "◆レベル：" << level
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// 発言
	void say(string str) {
		cout << name << "「" << str << "」" << endl;
	}
};

int main() {
	// 宣言＆初期化
	Human player;

	// 名前の設定
	player.name = "コウちゃん";

	// キャラクターの状態を表示
	player.info();

	// 発言
	player.say("せっかくだから、俺はこの赤の扉を選ぶぜ！");

	return 0;
}
```
<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            あ、なんか変わった
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そう、`struct`が`class`になっているところと、`class`だと「どういうデータを持っているか」と「どういう操作ができるか」がどっちもまとまっているのよ。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            なるほど、C言語の構造体は**データ**しかまとめられなかったけど、C++のクラスは**データ**と**動作**をまとめることができるのね！
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            そゆこと。
        </span>
    </div>
</body>

はい、おちゃっぱちゃんの言う通り、C言語の構造体では**データ**しかまとめられませんが、C++のクラスは**データ**と**動作**をまとめることができるのです。
<figure class="figure-image figure-image-fotolife" title="Cの構造体、C++のクラス">[f:id:skytomo:20180830185241p:plain]<figcaption>Cの構造体、C++のクラス</figcaption></figure>
具体的にRPGで例えるとこんな感じです。
<figure class="figure-image figure-image-fotolife" title="RPGで例えるとこんな感じ">[f:id:skytomo:20180830185239p:plain]<figcaption>RPGで例えるとこんな感じ</figcaption></figure>

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            クラスの中にある関数を**メンバ関数**といいます。
            <br> メンバ関数は構造体のときと同じように、`player.メンバ関数()`と書くことができます。
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            あと、`class`で宣言した実体のことを**インスタンス**といいます。
            <br> 例えば、`Human player`とした場合、`Human`がクラスという「人間の設計書」で、それを元に作られたオブジェクトが`player`というインスタンス、ということです。
        </span>
    </div>
</body>

<figure class="figure-image figure-image-fotolife" title="人間という設計図（クラス）から鏡音リン（インスタンス）が生成される様子">[f:id:skytomo:20180830192802p:plain]<figcaption>人間という設計図（クラス）から鏡音リン（インスタンス）が生成される様子</figcaption></figure>

クラスにはクラス名と同じ名前の特別なメンバ関数が2つあります。  
今回の場合は、`Human`ですので、`Human()`と`~Human()`がそれにあたります。  
`Human()`はインスタンスが生成された直後に呼び出されて処理されます。いわゆる初期化と同じです。このメンバ関数は**コンストラクタ**といいます。  
`~Human()`は逆にインスタンスが破棄されるときに呼び出されて処理されます。このメンバ関数を**デストラクタ**といいます。  
これによって`Human player`という宣言がされた瞬間に`Human()`が呼び出されて、初期化されるのです。

<body>
    <ul class="checklist">
        <li>クラスはデータと動作をまとめることができる</li>
        <li>クラスの中にある関数をメンバ関数という</li>
        <li>クラスで宣言した実体のことをインスタンスという</li>
        <li>コンストラクタはインスタンスが生成されるときに呼び出されて処理されるメンバ関数である</li>
        <li>デストラクタはインスタンスが破棄されるときに呼び出されて処理されるメンバ関数である</li>
    </ul>
</body>

## thisと関数のオーバーロード

おちゃっぱちゃんが書き換えたソースコードをさらに書き換えてみましょう。

```c
#include <iostream>
#include <string>

using namespace std;

class Human {
public:
	/* どういうデータがあるか */
	string name; // 名前
	string motto; // 座右の銘
	int HP; // 体力
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
	int EXP; // 経験値
	int money; // お金
	
	// コンストラクタ（初期化）
	Human() {
		name = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// コンストラクタ（初期化）
	Human(string name) {
		this->name = name;
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// デストラクタ
	~Human() {
	}
	
	/* どういう操作ができるか */
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆座右の銘：" << motto
		<< "◆体力：" << HP << "/" << maxHP
		<< "◆レベル：" << level
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// 発言
	void say(string str) {
		cout << name << "「" << str << "」" << endl;
	}
};

int main() {
	// 宣言＆初期化（名前の設定）
	Human player("コウちゃん");

	// キャラクターの状態を表示
	player.info();

	// 発言
	player.say("せっかくだから、俺はこの赤の扉を選ぶぜ！");

	return 0;
}
```

今度はコンストラクタがふたつになっていますね。  
実は、C++では関数名が同じでも、引数の型や数が異なっていれば、複数宣言することができます。  
このことを**関数のオーバーロード**といいます。

2つ目のコンストラクタに`this`というキーワードがあります。
この`this`は、生成するインスタンス自身を格納する特別な変数です。

<body>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            どゆことー
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            `Human(string name)`の仮引数は何？
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            え…、それは`string`型の`name`という引数だけど、
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            じゃあ、`player`というインスタンスはどういうデータを持ってる？
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            いろいろあるけど、`name`とか`motto`とか。
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そう、でも`Human(string name)`の中では`name`って言ったら、仮引数の`name`になるでしょう？
            <br> `player`が持っているデータの`name`を呼び出せないよね。だから`this`というのを使えば、`player`が持っているデータの`name`を呼び出せるようにしたんだ。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            なるほど～？
        </span>
    </div>
</body>

<body>
    <ul class="checklist">
        <li>引数が異なる関数を作ることを関数のオーバーロードという</li>
        <li>`this`は生成するインスタンス自身を格納する特別な変数である</li>
    </ul>
</body>

## 不正な書き込みを禁止する

```c
int main() {
	// 宣言＆初期化（名前の設定）
	Human player("コウちゃん");

	// キャラクターの状態を表示
	player.info();

	// 発言
	player.say("せっかくだから、俺はこの赤の扉を選ぶぜ！");

	// キャラクターの状態をメチャクチャにする
	player.HP = 1000;
	player.level = 100;
	player.money = 100;

	// キャラクターの状態を表示
	player.info();

	return 0;
}
```

<body>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            おちゃっぱちゃん何してるの
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            悪者になりきって、不正にレベルを100に上げたりとか、お金を100Gに増やしたり、最大HPが10なのにHPを1000にしたりしてみた。
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            ちょ、やめたげて～
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            でもね、こうやって、意図的に不正にデータを書き換えるだけではなくて、本人とは不本意に間違えてクラス内部にデータしてしまうことがあるんだよ。例えば、導線がむき出しのスマホがあったとしよう。利用者が間違えて導線に触れて、データが壊れてしまうでしょう？こういうふうに、いつでもどこでもクラス内部にアクセスできるということは、非常にバグの起きやすい危険な状態なのよ。
        </span>
    </div>
    <div>
        <span class="icon-kou-kyupi"></span>
        <span class="balloon-kou">
            う～ん。どうしよう。
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            さっきの例えでいうと、導線がむき出しになったスマホは、導線がむき出しにならないように内部に**隠蔽化**すればいいよね。こういうふうに不正なアクセスができないようにすることを**隠蔽化する**というのだけれど、プログラミングにも勝手にアクセスできないように**アクセシビリティ**というものがあるのよ。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            アクセシビリティ？
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>

using namespace std;

class Human {
private:
	/* どういうデータがあるか */
	string name; // 名前
	string motto; // 座右の銘
	int HP; // 体力
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
	int EXP; // 経験値
	int money; // お金
public:
	// コンストラクタ（初期化）
	Human() {
		name = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// コンストラクタ（初期化）
	Human(string name) {
		this->name = name;
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// デストラクタ
	~Human() {
	}
	
	/* どういう操作ができるか */
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆座右の銘：" << motto
		<< "◆体力：" << HP << "/" << maxHP
		<< "◆レベル：" << level
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// 発言
	void say(string str) {
		cout << name << "「" << str << "」" << endl;
	}
};

int main() {
	// 宣言＆初期化（名前の設定）
	Human player("コウちゃん");

	// キャラクターの状態を表示
	player.info();

	// 発言
	player.say("せっかくだから、俺はこの赤の扉を選ぶぜ！");

	// キャラクターの状態をメチャクチャにする
	player.HP = 1000; //compile error
	player.level = 100; //compile error
	player.money = 100; //compile error

	// キャラクターの状態を表示
	player.info();

	return 0;
}
```

アクセシビリティとは変数やメンバ関数のアクセス設定のことを示します。  
クラス内部で`public:`と書かれた場所より下に宣言された変数やメンバ関数は、**どこからでもアクセス可能**になりますが、
`private:`と書かれた場所より下に宣言された変数やメンバ関数は、**クラス内部からしかアクセスできなく**なります。
もし、アクセシビリティが`private`になっている変数やメンバ関数にクラス外部からアクセスしようとすると、コンパイルエラーになります。

<body>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            でも、そうすると、座右の銘とか何にも変更できなくなっちゃうよ。
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そう。だから、`public`なメンバ関数を介して間接的に変更するんだ。
        </span>
    </div>
    <div>
        <span class="icon-kou-maru"></span>
        <span class="balloon-kou">
            間接的に変更する…？
        </span>
    </div>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            そう。例えば、レベルを直接上げることはできないけど、経験値を取得することによって間接的にレベルを上げることができるでしょ？
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            なるほど…！
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            じゃあ、早速ソースコードを書いていきましょう！
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>

using namespace std;

class Human {
private:
	/* どういうデータがあるか */
	string name; // 名前
	string motto; // 座右の銘
	int HP; // 体力
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
	int EXP; // 経験値
	int money; // お金
public:
	// コンストラクタ（初期化）
	Human() {
		name = "";
		motto = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// コンストラクタ（初期化）
	Human(string name) {
		this->name = name;
		motto = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// デストラクタ
	~Human() {
	}
	
	/* どういう操作ができるか */
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆座右の銘：" << motto
		<< "◆体力：" << HP << "/" << maxHP
		<< "◆レベル：" << level
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// 発言
	void say(string str) {
		cout << name << "「" << str << "」" << endl;
	}
	
	// 座右の銘の設定（セッター）
	void set_motto(string motto) { this->motto = motto; }
	
	// 座右の銘の取得（ゲッター）
	string get_motto(void) { return this->motto; }
	
	// 経験値をゲットする
	void add_EXP(int EXP) {
		if (EXP < 0) return;
		this->EXP += EXP;
	}
};

int main() {
	// 宣言＆初期化（名前の設定）
	Human player("コウちゃん");
	
	// 座右の銘の設定
	player.set_motto("せっかくだから、俺はこの赤の扉を選ぶぜ！");

	// キャラクターの状態を表示
	player.info();

	// 座右の銘の取得
	cout << "■座右の銘：" << player.get_motto() << endl;
	return 0;
}
```
`set_motto`のように`private`な変数に格納されているデータをメンバ関数越しに設定するためにある、メンバ関数のことを**セッター（setter）**といいます。
また、`get_motto`のように`private`な変数に格納されているデータをメンバ関数越しに取得するためにある、メンバ関数のことを**ゲッター（getter）**といいます。

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            どうせだから、ここで経験値が上がったらレベルが上がり、レベルが上ったら最大HPが上がるように実装しよう！
        </span>
    </div>
    <div>
        <span class="icon-kou-wara"></span>
        <span class="balloon-kou">
            おう！
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>
#include <math.h>

using namespace std;

class Human {
private:
    /* どういうデータがあるか */
    string name; // 名前
    string motto; // 座右の銘
    int HP; // 体力
    int maxHP; // 最大の体力（レベルによって変わる）
    int level; // レベル
    int EXP; // 経験値
    int money; // お金
public:
    // コンストラクタ（初期化）
    Human() {
        name = "";
        motto = "";
        HP = 10;
        maxHP = 10;
        level = 1;
        EXP = 0;
        money = 0;
    }
    
    // コンストラクタ（初期化）
    Human(string name) {
        this->name = name;
        motto = "";
        HP = 10;
        maxHP = 10;
        level = 1;
        EXP = 0;
        money = 0;
    }
    
    // デストラクタ
    ~Human() {
    }
    
    /* どういう操作ができるか */
    
    // キャラクターの状態を表示
    void info() {
        cout
        << "◆名前：" << name
        << "◆座右の銘：" << motto
        << "◆体力：" << HP << "/" << maxHP
        << "◆レベル：" << level
        << "◆経験値：" << EXP
        << "◆所持金：" << money
        << endl;
    }
    
    // 発言
    void say(string str) {
        cout << name << "「" << str << "」" << endl;
    }
    
    // 座右の銘の設定（セッター）
    void set_motto(string motto) { this->motto = motto; }
    
    // 座右の銘の取得（ゲーター）
    string get_motto(void) { return this->motto; }
    
    // 経験値をゲットする
    void add_EXP(int EXP) {
        if (EXP < 0) return;
        this->EXP += EXP;
        calc_level();
    }
    
    // レベルの計算
    void calc_level(void) {
        level = sqrt(2.0*(EXP+1.0)/3.0+289.0/36.0)-17.0/6.0 + 1.0;
        maxHP = 5 + 5 * level;
    }
    
    // 次のレベルに上がるための計算
    void calc_next_level(void) {
        int needEXP = (3.0*level*level/2.0 + 17.0*level/2.0) - EXP;
        cout << "次のレベルに上がるまであと" << needEXP << "の経験値が必要です。" << endl;
    }
};

int main() {
    // 宣言＆初期化（名前の設定）
    Human player("コウちゃん");

    // キャラクターの状態を表示
    player.info();

    // 次のレベルに上がるための計算
    player.calc_next_level();

    // 経験値をゲットする
    player.add_EXP(10);

    // キャラクターの状態を表示
    player.info();

    // 次のレベルに上がるための計算
    player.calc_next_level();

    return 0;
}
```

<body>
    <ul class="checklist">
        <li>クラス内部へのアクセスの制限度合いをアクセシビリティという</li>
        <li>クラス内部に勝手にアクセスしないようにすることを隠蔽化という</li>
        <li>`public`はどこからでもアクセス可能である</li>
        <li>`private`はクラス内部のみアクセス可能である</li>
    </ul>
</body>

## 継承について

```c
class Enemy {
private:
    string name;
    int HP;
    int EXP;
    int money;
};
```

敵クラスを宣言すると、こんな感じになりますが、
よく見ると人間クラスと共通点がいくつかあります。

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            オブジェクト指向には**継承**という概念があります。例えば、「生物」というオブジェクトと、「人間」というオブジェクトがあるとき、明らかに「人間」は「生物」の部分集合ですよね。人間なら必ず生物としての性質も持っているはず。つまり、「人間」は「生物」に対して可能な操作と「人間」の持つ属性（データ）をそのまま引き継ぎます。このようなとき、「人間は生物を**継承する**」とか「生物は人間から**導出される**」と表現します。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            じゃあ、生物クラスを作って、人間クラスと敵クラスをそれぞれ導出すればいいわけか！
        </span>
    </div>
    <div>
        <span class="icon-ochappa-wara"></span>
        <span class="balloon-ochappa">
            そゆこと
        </span>
    </div>
</body>

[f:id:skytomo:20180830185325p:plain]

```c
#include <iostream>
#include <string>
#include <math.h>

using namespace std;

// 生物クラス（基底クラス）
class Creature {
protected:
    string name; // 名前
    int HP; // 体力
    int EXP; // 経験値
    int money; // お金
public:
    // 死んでいるか判定（trueなら死んでいる。falseなら生きている。）
    bool is_dead(){
        return (HP==0)?true:false;
    }
    // ダメージを受ける
    void damage(int point) {
        HP -= point;
        cout << name << "はダメージ" << point << "を食らった！" << endl;
        if (HP<0) {
            HP=0;
            cout << name << "は死んでしまった…！死んでしまうとは情けない" << endl;
        }
    }
};

// 人間クラス
class Human : public Creature{
private:
    /* どういうデータがあるか */
    string motto; // 座右の銘
    int maxHP; // 最大の体力（レベルによって変わる）
    int level; // レベル
public:
    // コンストラクタ（初期化）
    Human() {
        name = "";
        motto = "";
        HP = 10;
        maxHP = 10;
        level = 1;
        EXP = 0;
        money = 0;
    }
    
    // コンストラクタ（初期化）
    Human(string name) {
        this->name = name;
        motto = "";
        HP = 10;
        maxHP = 10;
        level = 1;
        EXP = 0;
        money = 0;
    }
    
    // デストラクタ
    ~Human() {
    }
    
    /* どういう操作ができるか */
    
    // キャラクターの状態を表示
    void info() {
        cout
        << "◆名前：" << name
        << "◆座右の銘：" << motto
        << "◆体力：" << HP << "/" << maxHP
        << "◆レベル：" << level
        << "◆経験値：" << EXP
        << "◆所持金：" << money
        << endl;
    }
    
    // 発言
    void say(string str) {
        cout << name << "「" << str << "」" << endl;
    }
    
    // 座右の銘の設定（セッター）
    void set_motto(string motto) { this->motto = motto; }
    
    // 座右の銘の取得（ゲーター）
    string get_motto(void) { return this->motto; }
    
    // 経験値をゲットする
    void add_EXP(int EXP) {
        if (EXP < 0) return;
        this->EXP += EXP;
        calc_level();
    }
    
    // レベルの計算
    void calc_level(void) {
        level = sqrt(2.0*(EXP+1.0)/3.0+289.0/36.0)-17.0/6.0 + 1.0;
        maxHP = 5 + 5 * level;
    }
    
    // 次のレベルに上がるための計算
    void calc_next_level(void) {
        int needEXP = (3.0*level*level/2.0 + 17.0*level/2.0) - EXP;
        cout << "次のレベルに上がるまであと" << needEXP << "の経験値が必要です。" << endl;
    }
    
    // 寝る
    void sleep() {
        HP = maxHP;
        cout << name << "は睡眠を取った。zzZ..." << endl;
    }

};

// 敵クラス
class Enemy : public Creature {
private:
    string name;
    int HP;
    int EXP;
    int money;
public:
};

int main() {
    // 宣言＆初期化（名前の設定）
    Human player("コウちゃん");

    // キャラクターの状態を表示
    player.info();

    // キャラクターにダメージ5
    player.damage(5);

    // キャラクターの状態を表示
    player.info();

    // キャラクターが寝る
    player.sleep();

    // キャラクターの状態を表示
    player.info();

    // 次のレベルに上がるための計算
    player.calc_next_level();

    return 0;
}
```

クラスを継承する側を**子クラス**とか**派生クラス**、クラスを継承される側を**親クラス**とか**基底クラス**といいます。  
C++ではクラスを継承するとき`class 子クラス : public 親クラス`というふうにクラスを宣言することによって継承することができます。

<body>
    <div>
        <span class="icon-ochappa"></span>
        <span class="balloon-ochappa">
            今のソースコードでは「生物クラス」を宣言して、「人間クラス」と「敵クラス」はそれを継承するようにしたよ。その他に人間が睡眠を取ると体力が快復するようにしたりしたよ。
        </span>
    </div>
    <div>
        <span class="icon-kou"></span>
        <span class="balloon-kou">
            どうせなら、敵クラスを更に継承してボスキャラクラスとか雑魚キャラクラスを作ろうよ
        </span>
    </div>
    <div>
        <span class="icon-ochappa-waraase"></span>
        <span class="balloon-ochappa">
            そうだね
        </span>
    </div>
</body>

```c
#include <iostream>
#include <string>
#include <math.h>

using namespace std;

// 生物クラス（基底クラス）
class Creature {
protected:
	string name; // 名前
	int HP; // 体力
	int EXP; // 経験値
	int money; // お金
public:
	// 死んでいるか判定（trueなら死んでいる。falseなら生きている。）
	bool is_dead(){
		return (HP==0)?true:false;
	}
	// ダメージを受ける
	void damage(int point) {
		HP -= point;
		cout << name << "はダメージ" << point << "を食らった！" << endl;
		if (HP <= 0) {
			HP = 0;
			cout << name << "は死んでしまった…！死んでしまうとは情けない" << endl;
		}
	}
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆体力：" << HP
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// ゲッターの一覧
	string get_name() {return name;}
	int get_HP() {return HP;}
	int get_EXP() {return EXP;}
	int get_money() {return money;}
};

// 人間クラス
class Human : public Creature{
private:
	/* どういうデータがあるか */
	string motto; // 座右の銘
	int maxHP; // 最大の体力（レベルによって変わる）
	int level; // レベル
public:
	// コンストラクタ（初期化）
	Human() {
		name = "";
		motto = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// コンストラクタ（初期化）
	Human(string name) {
		this->name = name;
		motto = "";
		HP = 10;
		maxHP = 10;
		level = 1;
		EXP = 0;
		money = 0;
	}
	
	// デストラクタ
	~Human() {
	}
	
	/* どういう操作ができるか */
	
	// キャラクターの状態を表示
	void info() {
		cout
		<< "◆名前：" << name
		<< "◆座右の銘：" << motto
		<< "◆体力：" << HP << "/" << maxHP
		<< "◆レベル：" << level
		<< "◆経験値：" << EXP
		<< "◆所持金：" << money
		<< endl;
	}
	
	// 発言
	void say(string str) {
		cout << name << "「" << str << "」" << endl;
	}
	
	// 座右の銘の設定（セッター）
	void set_motto(string motto) { this->motto = motto; }
	
	// 座右の銘の取得（ゲーター）
	string get_motto(void) { return this->motto; }
	
	// 経験値をゲットする
	void add_EXP(int EXP) {
		if (EXP < 0) return;
		this->EXP += EXP;
		calc_level();
	}
	
	// レベルの計算
	void calc_level(void) {
		level = sqrt(2.0*(EXP+1.0)/3.0+289.0/36.0)-17.0/6.0 + 1.0;
		maxHP = 5 + 5 * level;
	}
	
	// 次のレベルに上がるための計算
	void calc_next_level(void) {
		int needEXP = (3.0*level*level/2.0 + 17.0*level/2.0) - EXP;
		cout << "次のレベルに上がるまであと" << needEXP << "の経験値が必要です。" << endl;
	}
	
	// 寝る
	void sleep() {
		HP = maxHP;
		cout << name << "は睡眠を取った。zzZ..." << endl;
	}

	//攻撃
	void attack(Creature& creature) {
		cout << name << "は" << creature.get_name() << "にダメージ" << level << "を与えた。" << endl;
		creature.damage(level);
	}
	
	//敵の経験値やお金を押収
	void seizure(Creature& creature) {
		money += creature.get_money();
		EXP += creature.get_EXP();
		cout << name << "は" << creature.get_money() << "Gを手に入れた" << endl;
		cout << name << "は" << creature.get_EXP() << "EXPを手に入れた" << endl;
	}
};

// 敵クラス
class Enemy : public Creature {
protected:
	int attack_power; // 攻撃力
public:
	// 攻撃
	void attack(Creature& creature) {
		cout << name << "は" << creature.get_name() << "にダメージ" << attack_power << "を与えた。" << endl;
		creature.damage(attack_power);
	}
};

// ぞぬ（雑魚キャラ）
class Zonu : public Enemy {
public:
	Zonu() {
		name = "ぞぬ";
		HP = 5;
		EXP = 5;
		money = 1;
		attack_power = 1;
	}
};

// わぬ（ボスキャラ）
class Wanu : public Enemy {
public:
	Wanu() {
		name = "わぬ";
		HP = 100;
		EXP = 100;
		money = 20;
		attack_power = 10;
	}
};

int main() {
	// 宣言＆初期化（名前の設定）
	Human player("コウちゃん");
	Zonu zonu;

	while (1) {
		// プレイヤーの情報
		player.info();
		// 敵の情報
		zonu.info();
		// プレイヤーの攻撃
		player.attack(zonu);
		// 敵が死んだら終わり
		if (zonu.is_dead()) break;
		// プレイヤーの情報
		player.info();
		// 敵の情報
		zonu.info();
		// 敵の攻撃
		zonu.attack(player);
		// プレイヤーが死んだら終わり
		if (player.is_dead()) break;
	}
	// 敵の経験値やお金を回収
	player.seizure(zonu);
	// プレイヤーの情報
	player.info();

	return 0;
}
```

<body>
    <ul class="checklist">
        <li>あるクラスの操作やデータを別のクラスに引き継ぐことを継承という</li>
        <li>クラスを継承する側を子クラスまたは派生クラスという</li>
        <li>クラスを継承される側を親クラスまたは基底クラスという</li>
        <li>`class 子クラス : public 親クラス`でクラスを継承する</li>
    </ul>
</body>

## 最後に

これでオブジェクト指向の説明は終わりです。  
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
