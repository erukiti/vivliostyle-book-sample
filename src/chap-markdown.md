---
class: chapter
---

# Markdown

VivlioStyleではHTMLもしくはMarkdownで原稿を書きます。よほど奇特な人でも無い限りMarkdownで書くことを強く推奨します。

Markdownとは、元々英語のメールなどテキストコミュニケーションでよく使われる装飾を元に、とても自然な文章っぽく、HTMLの機能の一部を実現できる書式です。とても簡単、かつ様々なところで使われているため是非とも覚えましょう。

この章では、特に断りが無い限りはMarkdownの中でも、VivlioStyleで使用可能なVFM<span class="footnote">Vivlio Fravored Markdownの略で、GitHubで使われるGFMの亜種のようなものです。</span>という書式について紹介します。

## これだけ覚えればOK

* 文
* 見出し
* インラインコード
* 強調・イタリック・取り消し線
* 箇条書きリスト
* 数字付きリスト
* コードブロック
* 表
* 脚注

### 文

Markdownにおける文は、
改行の影響を受けますが、
単に改行を入れるだけでは、
別の改行はされません。

空行を入れることで別の文とみなされるようになります。

```md
Markdownにおける文は、
改行の影響を受けますが、
単に改行を入れるだけでは、
別の改行はされません。

空行を入れることで別の文とみなされるようになります。
```

この特性をよく覚えていてください。

なお設定で、改行を無視しないようにすることも可能です。

### 見出し

技術書のような想定の文章は、普通見出しがあって文章の塊があります。

普通は「章」「節」などの階層構造になっています。たとえば、今の文章は「Markdownの章」にある「これだけおぼえればOKの節」の「見出しという小見出し」の中の文章です。

```md:見出し
# Markdown

VivlioStyleではHTMLもしくはMarkdownで原稿を書きます。よほど奇特な人でも無い限りMarkdownで書くことを強く推奨します。

## これだけ覚えればOK

* 見出し

### 見出し

技術書のような想定の文章は、普通見出しがあって文章の塊があります。
```

このような構造になっています。

### インラインコード

インラインコードとは、たとえば変数名 `worldCount` など「間違ってはいけない固有のもの」を強調するために使います。

```md:インラインコード
インラインコードとは、たとえば変数名 `worldCount` など「間違ってはいけない固有のもの」を強調するために使います。
```

このように、バッククォートで囲いましょう。バッククォートはJISキーボードなら `Shift+@` で入力できます。

### 強調・イタリック・取り消し線

**強調**や*イタリック*や、~~取り消し線~~などがあります。

```md:強調・イタリック・取り消し線
**強調**や*イタリック*や、~取り消し線~などがあります。
```

まぁ、普通使うのは **強調** くらいでしょうか？~~少し不真面目な文体なら~~取り消し線も使い勝手がいいかもしれません。

### 箇条書きリスト

箇条書きは専用の書式があります。「・」中黒を使って自前で書くのはちょっとダサいです。

* 箇条書き
* かじょうがき

```md:*による箇条書きリスト
* 箇条書き
* かじょうがき
```

```md:-による箇条書きリスト
- 箇条書き
- かじょうがき
```

`* ` もしくは `- ` で箇条書きになります。混在することも可能です。

階層構造も作れます。

* トップ
    * セカンド
        * サード
        * サード
        * サード
    * セカンド
        * サード
            * フォース
                * フィフス
                    * シックス
* トップ

```md:箇条書きの階層構造
* トップ
    * セカンド
        * サード
        * サード
        * サード
    * セカンド
        * サード
            * フォース
                * フィフス
                    * シックス
* トップ
```

どこまでも階層を作れますが、せいぜい二階層程度にしましょう。深すぎる階層は読者が混乱しがちです。

### 数字付きリスト

1. 最初にすること
1. 2番目にすること
1. 3番目にすること

```md:数字付きリスト
1. 最初にすること
1. 2番目にすること
1. 3番目にすること
```

`1. ` から始まるものは数字付きリストになります。このとき、じつは数字は適当でも大丈夫です。全部 `1. ` でもいい感じに解釈してくれます。もちろん著者が頑張って正しい数字にしてもいいです。

### コードブロック

コードブロックとは、ソースコードの提示などに使います。

```ts
// TypeScript
const hoge = "ほげ"
```

````md:コードブロック
コードブロックとは、ソースコードの提示などに使います。

```ts
// TypeScript
const hoge = "ほげ"
```
````

ちなみにコードブロックの中でコードブロックを書きたい場合は、外側のコードブロックのバッククォートの数を増やしましょう。

`````md
ちなみにコードブロックの中でコードブロックを書きたい場合は、外側のコードブロックのバッククォートの数を増やしましょう。

````md
コードブロックとは、ソースコードの提示などに使います。

```ts
// TypeScript
const hoge = "ほげ"
```
````
`````

コードブロックは ` ``` ` で囲ったブロックです。` ```ts ` ` ```typescript ` や ` ```md ` ` ```markdown `のように、言語の種類を与えると、その言語として解釈し色分けをしてくれます。

またそのコードの名称を与えることもできます。

```ts:変数定義
const hoge = "ほげ"
```

````md:変数定義という名称を与えた
```ts:変数定義
const hoge = "ほげ"
```
````

コードブロックが横に長い場合は自動的に改行が入ります。

```
寿限無寿限無五却のすりきれ海砂利水魚の水行末雲来末風来末食う寝る処に住む処藪ら柑子の藪柑子パイポパイポパイポのシューリンガンシューリンガンのグーリンダイグーリンダイのポンポコピーのポンポコナーの長久命の長助
```


### 表

名前|対応書式|拡張子|特徴
---|--------|-----|----
Re:VIEW|Re:VIEW専用フォーマット|.re|技術同人誌を書くのに、最も完成されたソフト
VivlioStyle|Markdown|.md|CSS組版で自由度の高い本を書けるソフト

* <a href="#table" data-ref="tbl"></a>
* <a href="#table" data-ref="fig"></a>

```md:表 {id=table}
名前|対応書式|拡張子|特徴
---|--------|-----|----
Re:VIEW|Re:VIEW専用フォーマット|.re|技術同人誌を書くのに、最も完成されたソフト
VivlioStyle|Markdown|.md|CSS組版で自由度の高い本を書けるソフト
```

### 脚注

本文とはズレた内容や、リンク先などを脚注に書くことが多いと思います<span class="footnote">脚注を読むのが楽しみという人も一定いるかもしれませんが、読まない人も一定数いるのでご注意を。</span>。

```md:脚注
本文とはズレた内容や、リンク先などを脚注に書くことが多いと思います<span class="footnote">脚注を読むのが楽しみという人も一定いるかもしれませんが、読まない人も一定数いるのでご注意を。</span>。
```

<div class="column">
<div class="column-title">歴史</div>

Markdownと似たようなことをする書式は実は無限といえるくらいあります。たとえばWikipediaは、MediaWikiというシステムで動いていて、MediaWikiの書式があります。また、Wikiの元祖であるWikiWikiWebの書式もありますしWiki系の書式は数十種類以上あります。

元々様々な書式が乱立していて、互換性に苦しんでいたため、Markdownという「人類の共通言語」が登場したことは、当時の界隈にとって重要なことでした。

GitHub, Notion, Confluence他、様々なシェアトップのツールが、Markdown記法を採用しています。SlackなんかはMarkdownのサブセットを採用しています。

オリジナルのMarkdownは200x年に登場したもので、オリジナルの作者はそれ以上の改良をやらなかったため、様々な方言が生み出されました。

これはWikiと同じ悪夢を生み出すかと思われましたが、GitHubという巨大勢力によりGitHub Flavored Markdownが、ほぼ業界標準になっています。

</div>
