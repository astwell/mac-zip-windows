# mac-zip-windows

mac で作った ZIP ファイルを送ったら、お客様からこんな問い合わせ受けたことありませんか？

- ZIP ファイルが文字化けしていて読めない
- \_\_MACOSX フォルダは何の意味があるの？
- もらった ZIP ファイルをすべて展開すると予期しないエラーになって解凍できない
- テキストファイルが詰まっていて読みにくい。

mac-zip-windows の windowszip で解決できます。

# windowszip って何？

mac で圧縮ファイル(zip 形式)を作る PHP プログラムです。

- windows で文字化けしません
- \_\_MACOSX フォルダを作りません、.DS_store ファイルを除外します
- windows の禁止文字が含まれたファイルを自動で検出します。
- ShiftJIS にない文字を自動で検出します。
- .txt ファイルを自動で windows の改行に変換します。

# Fork による改変点

- 実行すると、追加で zip ファイルを暗号化したうえでそのパスワードをクリップボードにコピーします。-n オプションを使うと暗号化しません。
- 作成される zip ファイル名を`hogehoge.txt.zip`ではなく、`hogehoge.zip`としています。

Fork の経緯については<a href="https://k8sinfo.com/2019/07/03/mac-windows-zip-with-encryption/">こちら</a>。

# Fork による改変点 2

- macOS Catalina からは OS 標準の PHP に ZipArchive Class が存在しないため、brew でインストールされる php を利用することにした。

```
$ brew update
$ brew install php
$ brew link php
```

- スクリプトでの利用が行いやすいように、 P オプションを追加してパスワードを引数で渡せるようにした。
- 圧縮後のファイルをパラメータで指定できるようにした。

```
$ windowszip -P PASSWORD 圧縮後のファイル.zip 圧縮したいファイル
```

# どうやって使うの？

windowszip をダウンロードまたはコピペしてください。

パスの通った場所にファイルをコピーしてください。

以下コマンドで実行許可を与えます。

<code>\$ chmod +x windowszip </code>

ターミナルから以下のように圧縮ファイル(zip 形式)を作ることができます。

<code>\$ windowszip 圧縮したいフォルダ または　圧縮ファイル</code>

圧縮対象のフォルダ、またはファイルが存在するパスに、同じファイル名に拡張子.zip を付与したファイルを作成します。

# macOS のサービスに追加することでさらに便利になります。

こちらのサイトで詳しいやり方をご紹介しています。

<a href="http://fanblogs.jp/macyarounanoka/archive/274/0">fanblogs.jp/macyarounanoka</a>
