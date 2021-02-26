# はてなブログで記事の投稿日・更新日を人類紀元にする

備忘録です。

人類紀元とは、人間の文明の始まりに近い紀元前10001年を0年として数える紀年法です。
簡単に言うと西暦に10000年を足した値が人類紀元です。
人類紀元（HE）のことを知らない方はこれを見れば、何がいいのかわかるでしょう。

[https://www.youtube.com/watch?v=czgOWmtGVGs:embed:cite]

さて今回ははてなブログで記事の投稿日および更新日を人類紀元にします。

## 記事の投稿日を人類紀元にする方法

まず、西暦表示で投稿日をおしゃれしたい場合は以下の記事が役に立ちます。
[https://blog.minimal-green.com/entry/2017/01/30/190200:embed:cite]

それで、記事の投稿日を人類紀元にするには、
はてなブログの設定のデザインCSSに以下の文を追加でコピペすればOKです。

```css
/*!
 * Show entry date in the Human Era for Hatena Blog v1.0.0
 * Date: 12021-02-27
 * Created by skytomo (https://100-matters.hatenablog.jp/)
 * Released under the CC0 license:
 * https://creativecommons.org/publicdomain/zero/1.0/deed.ja
 */
.entry-date .date-year::before {
    content: '1';
}
```

まあ、これだと19999年（西暦で9999年）までしかうまく表示できないのですが、
それは19999年になったらまた考えましょう。

## 記事の更新日を人類紀元にする方法

すでに記事の更新日を西暦で表示できる前提で話していきます。

もしも、記事の更新日を西暦で表示できていない場合は以下の記事を参考にしてください。
[https://www.tomomore.com/entry/hatenablog-date-modified:embed:cite]

さて、そしたら、

```javascript
var $container = $('<div></div>', {'class': 'lastmod'}).text(lastmod.replace(/T.*0/,""));
```

のところを

```javascript
var $container = $('<div></div>', {'class': 'lastmod'}).text('1' + lastmod.replace(/T.*0/,""));
```

に変えればいいだけです。
簡単ですね。

## まとめ

投稿日や更新日を人類紀元にするのは難しいと思いましたが、
案外簡単にできるものですね。

それでは、いい人類紀元ライフを～
