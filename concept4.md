## CSSでスタイル、レイアウトする前に必要な設定（default値をリセット）

ここまできたらWebページをレイアウト、スタイルする準備がほぼ整いました。
しかし、その前にブラウザの特性について知って、それに伴った対処をしていく必要があります。

実は、ブラウザは初期設定＝defaultで自動的にmarginやpaddingといったプロパティに値を付け加えています。
私たちの把握していない`margin`や`padding`の値が勝手に存在するということなので、それをリセットせずにCSSでスタイルしていくと、なかなか思い通りのボックスモデルにならないことがよく起こります。

それを未然に防ぐために、一定の要素に対してはブラウザによるdefault値のリセットを先にCSSで設定しておきましょう。

ブラウザのdefault値をリセットするついでに、ページ全体で固定しておきたいことも設定しておきましょう。（例：文字色、文字のサイズ、フォントの種類、リンクテキストの色と擬似クラス、h1〜h6、p、imgなど）

```css
@charset "UTF-8";

/* bodyの設定 */
body {
  margin: 0;
  padding: 0;
  color: #414242; /* 全体の文字色も固定 */
  font-size: 14px; /* 全体の文字サイズも固定 */
  font-family: "ヒラギノ角ゴ ProN W3", "Hiragino Kaku Gothic ProN", sans-serif; /* フォントの種類も固定 */
}

/* リンクテキストの設定 */
a {
  color: #020d99;
}

a:visited {
  color: #5e5c5c; /* 訪問済みのリンクの色指定 */
}

a:hover {
  color: #020d99;
  font-weight: 500;
  text-decoration: none;
}

/* h1〜h6の設定 */
h1,h2,h3,h4,h5,h6 {
  margin-top: 0; /* h1〜h6にもdefault値がブラウザにより存在するためリセット */
}

/* p要素の設定 */
p {
  margin-top: 0;
  line-height: 1.0; /* 行間に適度な間を開けさせる */
}

/* 画像要素の設定 */
img {
  vertical-align: bottom; /* 余白（画像下）をリセットするため */
}
```

## 更に学ぼう

### 記事で学ぶ

- [CSS - MDN](https://developer.mozilla.org/ja/docs/Learn/CSS)

### 動画で学ぶ

- [CSS入門 #1~#19 - ドットインストール](https://dotinstall.com/lessons/basic_css_v3)
