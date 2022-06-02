---
title: ".animateに同じclass名の要素を複数渡したい！"
emoji: "📦"
type: "tech"
topics: ["css", "javascript"]
published: true
---

JavaScriptで.animateに同classを複数要素渡すことがあったので備忘録。

`result`classを持つ要素を全て取得して、それらにアニメーションをさせたい場合...

```js:ダメな例
var resultItems = document.querySelectorAll(".result");
resultItems.animate(
	{
		opacity: [
			"1",
			"0.2",
			"1",
		]
	},
	{
		duration: 500
	}
);
```

と、そのままやりたくなるのですが、これでは動きません💦
`querySelectorAll`が配列で取得して渡されるので`forEach`を使って配列の要素それぞれに`.animate`させる処理にします。

```js:動く例
var resultItems = document.querySelectorAll(".result");
resultItems.forEach(function (item) {
	item.animate(
		{
			opacity: [
                            "1",
                            "0.2",
                            "1",
                        ]
                 },
                 {
                        duration: 500
                 }
	)
});
```
