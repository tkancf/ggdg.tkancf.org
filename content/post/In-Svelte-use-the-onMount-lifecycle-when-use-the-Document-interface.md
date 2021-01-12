---
title: "Svelteで Document インターフェイスを使いたい時は onMountライフサイクルを使う"
date: 2021-01-10T23:20:40+09:00
categories: [tech]
tags: [Svelte, JavaScript, Frontend]
thumbnail: "images/avatar2020.jpg"
description: "Svelteで Document インターフェイスを使う方法"
draft: false

---

**※注意!! 動作検証はしてますが、勉強不足により、この方法がベストなのか分かってないです。参考程度にお願いいたします。**

## 何がしたいか

こういうHTMLから

```html
<div id="text">Text</div>
```

文字列 "Text" を取得したい。

JavaScriptで普通にやるなら以下のように書けば良いが、Svelteではそうはいかなかった

```js
let t = document.getElementById('text');
console.log(t.textContent);
```

## どうすればいいか

onMountライフサイクルを使って、以下のように書けばOK ([REPLでの動作確認](https://svelte.dev/repl/6ae127160841452285c1e9386ff649cf?version=3.31.2))

```svelte
<script>
    import { onMount } from 'svelte';
    onMount(() => {
        let t = document.getElementById('text');
        console.log(t.textContent);
    });
</script>

<div id="text">Text</div>
```

## あとがき

Web Frontend 周辺何も分からないので、最近Svelteに手を出してみています。  
世界ではReactが流行っているようですが、なにかのタイミングでSvelteを見たときにEasyな気配がして選びました。

まだTutorialを読んでいる途中ぐらいの段階ですが、公式ドキュメントも充実しているので印象は良いです。  
以前はサポートしていなかったようですが、現在はTypeScriptもサポートされています。  
今年中にSvelte + Sapperでアプリを作れたら嬉しいなーというお気持ちです。