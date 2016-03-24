
##CSSの設計
---

###設計思想例

- SMACSS

	[https://app.codegrid.net/entry/smacss-1](https://	app.codegrid.net/entry/smacss-1 "https://app.codegrid.net/entry/smacss-1")
	[http://qiita.com/matsui-a/items/9b9188904d160a3ec223](http://qiita.com/matsui-a/items/9b9188904d160a3ec223 "http://qiita.com/matsui-a/items/9b9188904d160a3ec223")
	

- BEM

	[https://app.codegrid.net/entry/bem-basic-1](https://app.codegrid.net/entry/bem-basic-1 "https://app.codegrid.net/entry/bem-basic-1")

- OOCSS

	[https://github.com/stubbornella/oocss/wiki](https://	github.com/stubbornella/oocss/wiki "https://	github.com/stubbornella/oocss/wiki")

	[http://takazudo.github.io/blog/entry/2012-12-10-	oocsssass.html](http://takazudo.github.io/blog/entry/	2012-12-10-oocsssass.html "http://takazudo.github.io/	blog/entry/2012-12-10-oocsssass.html")
	
	[https://app.codegrid.net/entry/oocss-1](https://app.codegrid.net/entry/oocss-1 "https://app.codegrid.net/entry/oocss-1")
	
	

- FLOCSS

	[https://github.com/hiloki/flocss](https://	github.com/hiloki/flocss "https://github.com/hiloki/	flocss")

- MCSS

	[http://operatino.github.io/MCSS/ja/](http://operatino.github.io/MCSS/ja/ "http://operatino.github.io/MCSS/ja/")


###簡単な解説
####SMACSS(Scalable and Modular Architecture)

	■カテゴライズ
	1.ベース　--- サイト全体で要素そのもののデフォルトスタイル
	2.レイアウト --- ページのエリア分け
	3.モジュール --- 再利用可能なパーツ
	4.状態（ステート）--- 特定の状態によってスタイルを上書きする。
						状態の切りかえはJavascript
	5.テーマ --- テーマ管理用のCSS
	
	■良い点
	・読み込む必要のない CSS ファイルを特定しやすい
	・CSS ファイルが再利用可能
	■難しい点
	・テーマファイルの独立のさせにくさ
		例)
			<!--
				heading_border => #444
				{theme name}_border => red
			-->

			<h2 class="heading_border
			{theme name}_border">Hello</h2>
	
		＊やり方次第では上書きしにくい箇所がある？？
		
	・HTML 内で それぞれの要素に振るクラスが多くなる可能性がある

	・レイアウト、モジュールカテゴリーの分けにくさ
		モジュールごとにルールを決めたり等
		少しハードルが高い？

	
####BEM(Block、Element、Modifier)

	■カテゴライズ
	1.Block ⇒ 塊
	2.Element ⇒ 要素
	3.Modifier(kyeとvalueで表す) ⇒ 状態（変化）

	■BEMのルール
	BlockとElementの区切りはアンスコ2個（__）
	BlockまたはElementとModifierの区切りはハイフン2個（--）
	ModifierのKeyとValueの区切りはアンスコ1個(_)
	BlockやElementを2つ以上の単語で表す時はハイフン1個(-)
	
	■良い点
	・HTMLとCSSは、いつでもデザインの変化に対応できる
	・プログラマーとフロントエンドエンジニアは、お互いのコードに貢献し合える
	・皆が同じ言語でやりとりできるので、コミュニケーションが取りやすくなる
	■難しい点
	・外部の人間が入りづらい、習得までの時間など
	・ElementやModifierの名前が冗長になりがち

####OOCSS(Object-oriented)
	BOOTSTRAPっぽい書き方
	レゴ的な発想で書いていく
	
####FLOCSS(Foundation、Layout、Object)
	OOCSSやSMACSS、BEM、SuitCSSのコンセプトを取り入れた、モジ	ュラーなアプローチのためのCSS構成案です。
	
	■カテゴライズ
	1.Foundation ⇒ イニシャライズ CSS
	2.Layout　⇒　ヘッダー・フッターなどのレイアウト部分
	3.Object　⇒　その他メインコンテンツの各部品など

####MCSS(Multilayer)	
	BEMとOOCSSの原理を基にしています
	レイヤーベースでcssを書くやり方です
	