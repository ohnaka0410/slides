---
marp: true
theme: gaia
class:
  - invert
paginate: true
footer: "by **yuki.ohnaka＠no4**"
---

<!--
_class:
  - lead
-->

<!-- ![bg left:40% 30%](./assets/logo.png) -->

![h:200px](./assets/logo.png)

# ?

---

<!--
_class:
  - lead
-->

<!-- ![bg left:40% 30%](./assets/logo.png) -->

![h:200px](./assets/logo.png)

# CSS Architecture

---

![bg right:30% 70%](https://storage.googleapis.com/zenn-user-upload/avatar/6463cc0b43.jpeg)

# About Me

- yuki ohnaka
- 株式会社ナンバーフォー 🍀
  - **Front-end** / Server-side / Native-App engineer
- Vue / React / TypeScript / Java / PHP / Kotlin / Swift / Python / Docker / Ansible ...
- [Qiita](https://qiita.com/yuki0410_) / [Zenn](https://zenn.dev/yuki0410)

---

# 良い CSS Architecture とは？

- 予測しやすい
- 再利用しやすい
- 保守しやすい
- 拡張しやすい

出典: [CSS Architecture](https://philipwalton.com/articles/css-architecture/)

---

![bg contain](./assets/unknown.png)
(c) 2017 niewals

---

<!--
_class:
  - lead
-->

# CSS 設計をするときの 7 つのポイント

---

## 1. コンテンツとスタイリングは疎結合にする

```html
<!-- no good 👎 -->
<article class="article">
  <h2 class="article__title">title</h2>
</article>
```

```css
/** no good 👎 */
.article h2 {
  /** */
}
```

---

## 1. コンテンツとスタイリングは疎結合にする

```html
<!-- good 👍 -->
<article class="article">
  <h2 class="article__title">title</h2>
</article>
```

```css
/** good 👍 */
.article__title {
  /** */
}
```

---

## 2. 影響範囲を無闇に拡げない

```css
/** no good 👎 */
#main-nav > div {
  /** */
}

/** good 👍 */
.main-nav__section {
  /** */
}
```

---

## 3. 親に関わらず動くようにする

```css
/** no good 👎 */
#main-nav .article {
  /** */
}

/** good 👍 */
.article {
  /** */
}
```

---

## 4. 詳細度を無闇にあげない

```css
/** no good 👎 */
#main-nav ul li ul li div {
  /** */
}

/** good 👍 */
.main-nav-sub-list__inner {
  /** */
}
```

---

## 5. 影響範囲が想像できるクラス名

```html
<!-- no good 👎 -->
<article class="article">
  <h2 class="title">title</h2>
</article>
```

```css
/** no good 👎 */
.article .title {
  /** */
}
```

---

## 5. 影響範囲が想像できるクラス名

```html
<!-- good 👍 -->
<article class="article">
  <h2 class="article__title">title</h2>
</article>
```

```css
/** good 👍 */
.article__title {
  /** */
}
```

---

## 6. 見た目・機能・役割が想像できるクラス名

```css
/** no good 👎 */
.title1 {
  /** */
}

/** good 👍 */
.page-title {
  /** */
}
```

---

## 7. コンポーネントにマージンを持たせない

```css
/** no good 👎 */
.article {
  margin-left: 20px;
}

/** good 👍 */
.article-container {
  display: grid;
  column-gap: 20px;
}
.article {
  /** */
}
```

---

<!--
_class:
  - invert
  - lead
-->

## さぁ、やってみよう

---

<!--
_class:
  - lead
-->

## チームで開発するためには、具体的なルールが必要

---

## 既存の CSS を設計を取り入れる

- **BEM (MindBEMding)**
- OOCSS
- SMACSS
- FLOCSS
- Enduring CSS (ECSS)

必要に応じてカスタムする場合はある。

---

<!--
_class:
  - invert
  - lead
-->

# ご清聴ありがとうございました 👏👏👏

---

<!--
_class:
  - lead
-->

# @おまけ

---

<!--
_class:
  - lead
-->

# CSS Architecture は必要か？

---

## 最近 CSS の周辺環境 は便利になってきている

- scoped CSS (Vue)
- CSS Modules (with React)
- CSS in JS (with React)
- styled-components (with React)
- Utility first CSS FW (tailwind)
- with Web Components

もう CSS Architecture なんてどうでもいいのでは？🤔

---

## 引き続き CSS Architecture は必要

- 解決できていない課題もある
- モダンな開発以外の開発案件もまだたくさんある
- CSS Architecture で考慮していた要素が、別（コンポーネント設計など）に移っただけなので、考えなければいけないことは一緒。

---

<!--
_class:
  - lead
-->

# シングルクラス VS マルチクラス

---

<!--
_class:
  - invert
  - lead
-->

## 抽象的過ぎないマルチクラスがおすすめ
