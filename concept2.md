## セレクタ：class属性指定

先ほどのCSSの書き方の基本では以下のようになっていました。

```css
h2 {
  color: red; /* 文字色の表示（赤色に指定） */
}
```

ただ、これではHTMLファイルにある全ての`h2`要素全てに対して、文字の色を赤くする表示の指定が適応されてしまいます。
特定の箇所だけ文字の色を赤から別の色にしたいという場合にはどうするのでしょうか？

特定の箇所に適応させたい表現指定がある場合は、HTMLのclass属性を利用して指定していきます。

例えば以下の例を見てみましょう。

```html
<h2>赤色のH2</h2>
<h2 class="yellow-font">黄色のH2</h2>
```
```css
/* 全てのh2の文字色を赤に指定 */
h2 {
 color: red;
 font-size: 20px;
}
/* このh2だけは文字色を黄色に指定 */
h2.yellow-font {
 color: yellow;
 font-size: 20px;
}
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/ypou6bmg/6/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

上記の例の場合、HTMLで2つ目の`h2`のみ`class="yellow-font"`とclass名を指定しています。こうすることで`h2.yellow-font`に定義されたスタイルを適用しています。

classを利用してCSSを定義する場合は、必ず`.`をclass名の前につけて書くようにしましょう。

class属性の書き方には、`h2`要素限定でなく、どんな要素でも`class="yellow-font"`属性を持った全ての要素の表現を指定することができます。

例として`class="yellow-font"`要素をもつ、`p`と`h1`も文字色を黄色にしたい場合がそれに当たります。

```html
<h2>黒色のh2要素です。</h2>
<h2 class="yellow-font">黄色のh2要素です。</h2>
<p>黒色のp要素です。</p>
<p class="yellow-font">黄色のp要素です。</p>
```

```css
/* h2はclass="yellow-font"の属性ではないので赤色で表示される */
h2 {
  color: black;
  font-size: 24px;
}

p {
  color: black;
  font-size: 18px;
}

/* class="yellow-font"の属性を持つ要素は、全て文字色を黄色に指定 */
.yellow-font{
  color: yellow;
}
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/om2pky08/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

書き方をおさらいすると以下のようになります。

```css
.class名 {
  プロパティ: 値;
}
```

## セレクタ：id属性指定

id属性も基本的にはclass属性と同じですが、書き方だけ少し違います。class属性が`".class名"`となるのに対し、id属性は`"#id名"`となります。

## セレクタ：子孫セレクタ

子孫セレクタを使用すると、HTMLの構成に基づいた指定をすることで、より詳細なCSSの指定をすることができます。
例えば以下の例を見ていきましょう。

```html
<h1>通常のh1です。</h1>
<article class="post">
  <h1>直接の子孫にあたるh1です。</h1>
  <div>
    <h1>
      直接の子孫にあたらないh1です。
    </h1>
  </div>
</article>
```

この例の場合ですと、postというクラスが適用されたarticle要素の中にh1要素が含まれています。このように、ネストされた要素のCSS指定をすることを子孫セレクタと呼びます。子孫セレクタを利用してCSS指定をするには次のようにします。

```css
article.post h1 {
  color: blue;
  font-size: 32px;
}
```

このようにして、`article.post`の中に含まれるh1要素のCSSを定義することが出来ます。

また、直接の子孫のみを指定するには`>`を利用することが出来ます。例えば上記の例で直接の子孫にあたる`h1`とそうでない`h1`で少しフォントサイズを変えてみましょう。

```css
article.post h1 {
  color: blue;
  font-size: 32px;
}

article.post > h1 {
  color: blue;
  font-size: 42px;
}
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/f8dyg725/5/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

尚、CSSは2つのものが同時に適用出来る場合、後に書かれたものが優先されます(上書き保存)。そのため上記のCSS定義で`article.post h1 {...}`と`article.post > h1 {...}`の上下を入れ替えると両方に`font-size: 42px;`が適用されてしまうので注意してください。jsFiddle上でも自分で確かめてみましょう。

## セレクタ：擬似クラス

擬似要素では、リンクやボタン要素にカーソルを合わせると色が変わるといった、それぞれの「状態」によってスタイルを変えることができます。

リンクテキストにカーソルを合わせると色が変化する擬似クラスを例にしてみます。
リンクテキストの要素である、 `<a>` タグ要素は維持しますが、「カーソルが合わさった」状態(ホバーといいます)と、「カーソルを外す/カーソルを合わせる前」状態とで `<a>` タグのスタイルを変化させる必要があります。

```css
a { /* カーソルを外す/カーソルを合わせる前 */
  color: #0404ff;
}
a:hover { /* カーソルが合わさった状況 */
  color: #fccd05;
}
```

表示は以下のようになります。

ホバー前:

![疑似グラス例: ホバー前](./images/pseudo.png)

ホバー時:

![疑似グラス例: ホバー時](./images/pseudo_hover.png)

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/2dcnwaeo/2/embedded/html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>