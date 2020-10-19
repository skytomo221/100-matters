# 2回目以降、画像とビデオのインポートができないときの対処法

iPhone から写真を取り込もうとしたときに、次の画像が出てきてしまいました。

<figure class="figure-image figure-image-fotolife" title="「0個の新しい画像とビデオが見つかりました」と表示され、画像と動画のインポートができない">[f:id:skytomo:20201020081703p:plain]<figcaption>「0個の新しい画像とビデオが見つかりました」と表示され、画像と動画のインポートができない</figcaption></figure>

どうやら一度、インポートした写真やビデオは再び読み込めなさそうです。調べてみると Yahoo! 知恵袋にこんなことが書かれていました。

[https://detail.chiebukuro.yahoo.co.jp/qa/question_detail/q1148135161:embed:cite]

> 再度調べたところ恐らくレジストリに画像保存した情報が書き込まれているようです。レジストリを削除しない限り、「画像の取り込み（Windows使用）」では1度取り込みした画像の再度の取り込み無理のようです。

じゃあレジストリいじればいいのか、と思い、さらに調べたら、解決方法を見つけました。

[http://yoshiakk.cocolog-nifty.com/blog/2013/11/windowsiphonepc.html:embed:cite]

> 【Windows7/8/8.1/10】
> キャッシュファイルは、「`C:ユーザー\ユーザー名\AppData\Local\Microsoft\Photo Acquisition`」にある「`PreviouslyAcquired.db`」。
> 
> 【Windows Vista】
> キャッシュファイルは、「`C:\Users\[username]\AppData\Local\Microsoft\Windows Photo Gallery`」にある「`Pictures.pd4`」。

**このキャッシュファイルを消すだけでいい**そうです。レジストリなんかいじらなくても良かったですね。

ちなみにAppDataが表示されない方は隠しファイルが見れるように設定を変更する必要があります。設定の変更は簡単で、以下の画像の通りに、①表示を押し→②隠しファイルにチェックをつけます。

<figure class="figure-image figure-image-fotolife" title="①表示を押し→②隠しファイルにチェックをつける">[f:id:skytomo:20201020202344p:plain]<figcaption>①表示を押し→②隠しファイルにチェックをつける</figcaption></figure>

キャッシュファイルを消したところ、無事に写真とビデオをインポートできるようになりました。良かった。

<figure class="figure-image figure-image-fotolife" title="キャッシュファイルを消した後の様子。「3644個の新しい画像とビデオが見つかりました」と表示され、再びインポートできるようになっている。">[f:id:skytomo:20201020201309p:plain]<figcaption>キャッシュファイルを消した後の様子。「3644個の新しい画像とビデオが見つかりました」と表示され、再びインポートできるようになっている。</figcaption></figure>
