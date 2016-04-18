#[SKIYAKI Coding Rule]

---

##全般的なスタイルルール

###プロトコル
	埋め込みリソースからプロトコル表記（http:,https:）を省略する。

	```html
	<!-- NG -->
	<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

	<!-- OK -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
	```

###CDNはなるべく使わないようにする
	EXTRAの仕様上、書くことは少ないですが
	外部のものは極力使わずローカルに落として使用して下さい
	例）
	```
	<!-- NG -->
	<script src="http://code.jquery.com/jquery-1.11.1.min.js"></script>

	<!-- OK -->
	<script src="/js/goldenbomber/jquery-1.11.1.min.js"></script>
	```
---

##一般的な書式ルール

###インデント
	タブでインデントする。
	スペ２、スペ４等でインデントしている場合はタブに変換する。

	```html
	<ul>
		<li>Fantastic</li>
		<li>Great</li>
	</ul>
	```

###大文字/小文字
	小文字のみ使用する。alt属性など値が文字列の場合は除く。

	```html
	<!-- NG -->
	<A HREF="/">Home</A>

	<!-- OK -->
	<img src="google.png" alt="Google">
	```

###文末のスペース
	文末のスペースを削除する。

	```html
	<!-- NG -->
	<p>What?_</p>

	<!-- OK -->
	<p>Yes please.</p>
	```

---

##全般的なメタルール

###エンコード
	エンコードは、UTF-8（BOM無し）を使う。

###コメント
	必要に応じてコードの説明を記述する。全部に書けというわけではない。

---

##HTMLのスタイルルール

###ドキュメントタイプ
	HTML5を使うこと。以下で始まる形式で書く。XHTML5はNG。

	```html
	<!DOCTYPE html>
	```

###HTMLのバリデート
	可能な限り適切なHTMLを記述すること。
	そうでないとパフォーマンスが低下するような場合でない限りは、ちゃんと書く。
	[「W3C HTML validator」](http://validator.w3.org/nu/)などの検証ツールを使用する。

	```html
	<!-- NG -->
	<title>Test</title>
	<article>This is only a test.</article>

	<!-- OK -->
	<!DOCTYPE html>
	<meta charset="utf-8">
	<title>Test</title>
	<article>This is only a test.</article>
	```

###セマンティックに書く（意味が通じるコーディングをする）
	目的に応じてHTMLを記述する。
	見出しならhx要素、段落ならp要素、アンカーならa要素など目的に応じたHTML要素を使う（「HTMLタグ」という言い方は間違い）。
	リンクならa要素で書く。onclickのようなJavaScriptな振る舞いのものを要素の属性に入れない。

	```html
	<!-- NG -->
	<div onclick="goToRecommendations()">All recommendations</div>

	<!-- OK -->
	<a href="recommendations/">All recommendations</a>
	```

###マルチメディアの代替コンテンツ
	マルチメディアの要素には、代替コンテンツを提供する。
	画像には、意味のある代替テキストをalt属性として、動画・オーディオコンテンツにはキャプションを記述する。
	装飾的な用途の場合など意味を持たない画像については、代替テキストは記述せずにalt=“"とする。

	```html
	<!-- NG -->
	<img src="spreadsheet.png">

	<!-- OK -->
	<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
	```

###構成要素の分離
	文書構造・見た目・振る舞いは、分離すること。
	見た目に関するものはスタイルシートに、振る舞いに関するものはスクリプトへ移して記述する。

	```html
	<!-- NG -->
	<!DOCTYPE html>
	<title>HTML sucks</title>
	<link rel="stylesheet" href="base.css" media="screen">
	<link rel="stylesheet" href="grid.css" media="screen">
	<link rel="stylesheet" href="print.css" media="print">
	<h1 style="font-size: 1em">HTML sucks</h1>
	<p>I’ve read about this on a few sites but now I’m sure:
	<u>HTML is stupid!!1</u>
	<center>I can’t believe there’s no way to control the styling of
	my website without doing everything all over again!</center>

	<!-- OK -->
	<!DOCTYPE html>
	<title>My first CSS-only redesign</title>
	<link rel="stylesheet" href="default.css">
	<h1>My first CSS-only redesign</h1>
	<p>I’ve read about this on a few sites but today I’m actually
	doing it: separating concerns and avoiding anything in the HTML of
	my website that is presentational.</p>
	<p>It’s awesome!</p>
	```

###実体参照
	不要な実体参照は使用しないこと。
	UTF-8においては、—（&mdash）・”（&rdquo）・☺（&#x263a）のような文字は実体参照を使う必要はない。
	HTMLで特別な意味を持つ文字（ < や & など）は例外。

	```html
	<!-- NG -->
	The currency symbol for the Euro is &ldquo&eur&rdquo.

	<!-- OK -->
	The currency symbol for the Euro is “€”.
	```

###タグの省略、をしない
	省略できるタグも省略しない。

	```html
	<!-- NG -->
	<!DOCTYPE html>
	<title>Spending money, spending bytes</title>
	<p>Sic.

	<!-- OK -->
	<!DOCTYPE html>
	<html>
	<head>
		<title>Saving money, saving bytes</title>
	</head>
	<body>
		<p>Qed.</p>
	</body>
	</html>
	```

###終了タグの省略
	省略できる終了タグ（閉じタグ）は省略する。
	[HTMLにて終了タグがいるタグいらないタグ・・の話とか](http://vllv.us/Junk/htmlTag/)

	```html
	<!-- NG -->
	<input type="text" name="name" size="30" maxlength="20"></input>

	<!-- OK -->
	<input type="text" name="name" size="30" maxlength="20">
	```

###type属性
	CSSとJavaScriptのtype属性は省略する。
	HTML5ではデフォルトの言語として解釈されるため。

	```html
	<!-- NG -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">

	<!-- OK -->
	<link rel="stylesheet" href="//www.google.com/css/maia.css">
	```

	```html
	<!-- NG -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>

	<!-- OK -->
	<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
	```

---

##HTMLの書式ルール

###HTMLガイドライン
	・段落テキストには`<p>`を使うこと。連続した`<br />`は決して使わない。
	・リスト形式には`<ul>`、`<ol>`や`<dl>`を使う。`<div>`や`<p>`を組み合わせて使うようなことはしない。
	・テキストが付随するすべてのフォーム要素には`<label>`を使うべき。ラジオボタンやチェックボックスは特に。
	・属性を囲む引用符は省略可能だが、可読性のために属性は引用符で囲むこと。

	```html
	<p class="line note" data-attribute="106">This is my paragraph of special text.</p>
	```

	・`<thead>`、`<tfoot>`、`<tbody>`と`<th>`（scope属性も）を適宜使用すること。

	```html
	<table summary="This is a chart of invoices for 2011.">
		<thead>
			<tr>
				<th scope="col">Table header 1</th>
				<th scope="col">Table header 2</th>
			</tr>
		</thead>
		<tfoot>
			<tr>
				<td>Table footer 1</td>
				<td>Table footer 2</td>
			</tr>
		</tfoot>
		<tbody>
			<tr>
				<td>Table data 1</td>
				<td>Table data 2</td>
			</tr>
		</tbody>
	</table>
	```

###全般的な書式
	ブロック要素・リスト要素・テーブル要素は改行してから記述し、それらの子要素にはインデントを入れる。
	横並びリストなど改行による空白が問題になる場合は、li要素をすべて一行で書いてもOK。

	```html
	<blockquote>
		<p><em>Space</em>, the final frontier.</p>
	</blockquote>

	<ul>
		<li>Moe</li>
		<li>Larry</li>
		<li>Curly</li>
	</ul>

	<table>
		<thead>
			<tr>
				<th scope="col">Income</th>
				<th scope="col">Taxes</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>$ 5.00</td>
				<td>$ 4.50</td>
			</tr>
		</tbody>
	</table>
	```

---

##CSSスタイルルール

##ファイル構成
	クラスベースではなくファイルベースで表示を入り分ける
	ファイル構成は、コードの視認性を良くするため、
	下記を基盤として作成をお願い致します

	CSS
	|_ import.css.sass ... import用css 標準でimportしておくファイル
	|_ valiables.css.sass ... 変数や関数、mixin等で使用するsassを格納するファイル
	|_ app
	|_common.css.sass ... 共通の項目で使用するファイル
	|_header.css.sass ... headerを使用するファイル
	|_footer.css.sass ... footerのスタイルを使用するファイル
	|_module.css.sass ... パーツとして複数回使用する等を重点においたclassを記載するファイル
	|_○○○.css.sass ... 各テーマに合わせてネームして使用して下さい。

	※ commonとmoduleの違い ...
	汎用的に使用する a タグや、h1 などの見出し要素、その他、汎用的なクラスのCSSをcommon、パーツとして再利用できるCSSをmoduleへ
	記載する

###CSSのバリデート
	可能な限り適切なCSSを記述すること。
	CSSバリデーターにバグがある場合や独自の構文を必要としない限りは、ちゃんと書く。
	HTML同様[W3C CSS validator](http://jigsaw.w3.org/css-validator/)などのツールで検証する。

###idは使用しない
	idにスタイルは極力使用しない。classにスタイルを付与すること

###classの命名
	class名にはちゃんと意味の分かる名前を使うこと。
	見た目を反映したものやそれが何を表しているか不可解な名前ではなく、要素の目的や役割を反映した名前を付ける。
	また、classの命名はbootstrapの書き方に合わせた命名が望ましい。

	```css
	/* NG: 意味が分からん */
	.yee-1901 {}

	/* OK: 役割を表してる */
	.gallery {}
	.login {}
	.video {}

	/* OK: 汎用的な名前 */
	.aux {}
	.alt {}
	```

###classの命名スタイル
	意味の分かる範囲でできるだけ短いclass名を使う。
	短くしすぎて意味がわからなくなるようなのはNG。

	```css
	/* NG */
	.navigation {}
	.atr {}

	/* OK */
	.nav {}
	.author {}
	```

###タイプセレクタの記述
	class名にタイプセレクタは記述しない。
	パフォーマンスを考慮して不要な子孫セレクタも避ける。
	これはなるべくならって感じだな。

	```css
	/* NG */
	ul.example
	div.error

	/* OK */
	.example
	.error
	```

###ショートハンドプロパティ
	ショートハンドで書ける場合はショートハンドを使うが、
	できるだけ可読性をあげる用途の場合はつかわなくてもいい


	```css
	/* OK */
	border-top: 0
	font: 100%/1.6 palatino, georgia, serif
	padding: 0 1em 2em

	/* OK */
	border-top-style: none
	font:
		family: palatino, georgia, serif
		size: 100%
	line-height: 1.6
	padding:
		bottom: 2em
		left: 1em
		right: 1em
		top: 0
	```

###「0」と単位
	値が「0」なら単位を省略する。

	```css
	margin: 0
	padding: 0
	```

###小数点の頭の「0」
	小数点の頭の「0」は省略する。

	```css
	font-size: .8em
	```

###HEX形式のカラーコード
	HEX形式のカラーコードで3文字で表記できるものは3文字にする。

	```css
	/* NG */
	color: #eebbcc

	/* OK */
	color: #ebc
	```

###プレフィックス（接頭辞）
	class名には固有の接頭辞を付ける。（オプション）
	大規模なプロジェクトの場合や、外部サイトに埋め込まれるコードを開発する場合など、class名が重複しないように接頭辞（名前空間など）付ける。
	bootstrapに準じて、接頭辞の後ろに-（ハイフン）を付けて繋げる。
	IDなどは_を使用する(JSの利用を想定)

	```css
	.
	.adw-help /* AdWords */
	.maia-note  /* Maia */
	```

###class名の区切り文字

	class名の別々の単語はアンダースコアで繋ぐ。

	```css
	/* NG: [demo]と[image]が繋がってる */
	.demoimage {}

	/* OK: ハイフンで繋がってる */
	.error-status {}


###CSSハック
	ユーザーエージェント別の対応のためにCSSハックを使う前に別の方法を試してみること。
	CSSハックは、ユーザーエージェントごとの違いを吸収するためには簡単で魅力的な方法だけど、プロジェクト全体のコードの品質を落とすことにもなるので「最後の手段」として考えること。

	---

##CSS書式ルール

###プロパティの記述順序
	アルファベットの順に記述する。
	ベンダープレフィックスは無視する。ただし、例えば-moz接頭辞は-webkitの前に来る、などの順序は保つこと。

	```css
	border: 1px solid
	-moz-border-radius: 4px
	-webkit-border-radius: 4px
	border-radius: 4px
	color: black
	text-align: center
	```

###ブロック単位のインデント
	SASSはインデントが囲いと直結するため
	ブロック単位でコードをインデントする。

	```css
	@media screen, projection
		html
			background: #fff
			color: #444
	```

###プロパティの終端
	SASSはセミコロンいらないです

	```css
	/* NG */
	.test
		display: block
		height: 100px

	/* OK */
	.test
		display: block
		height: 100px
	```

###セレクタとプロパティの分離
	別々のセレクタとプロパティは改行して書くこと。

	```css
	/* NG */
	a:focus, a:active {
		position: relative top: 1px
	}

	/* OK */
	h1,
	h2,
	h3 {
		font-weight: normal
		line-height: 1.2
	}
	```

	---
