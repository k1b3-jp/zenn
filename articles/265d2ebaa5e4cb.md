---
title: "【Swiper】同ページ内にサムネイル付きスライダーを自動生成する"
emoji: "🏃"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["swiper","javascript","html"]
published: true
---

# 要件
- Swiperを使用したスライドを含む要素をループ出力する
- Swiperはサムネイルとメインのスライドが連動する
- Swiperの挙動は全て同様のもの

# コード
## マークアップ
`class="slider-wrap"`でメインのスライダーとサムネイルのスライダーを囲みます。
`id="slider-wrap"`や`id="slider-main"`を用意しているのは、後述する処理でclass名に連番が付与されるためです。全てのスライドで同様のスタイルが適用されるように用意しました。

```html:index.html
<!-- ループ出力される要素 -->
<div class="slider-wrap" id="slider-wrap">
    <!-- メインのスライダー -->
    <div class="slider-main" id="slider-main">
        <ul class="swiper-wrapper">
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
        </ul>
        <!-- 前後の矢印 -->
        <div class="swiper-button-prev" id="swiper-button-prev"></div>
        <div class="swiper-button-next" id="swiper-button-next"></div>
    </div>
    <!-- サムネイルのスライダー -->
    <div class="slider-thumb" id="slider-thumb">
        <ul class="swiper-wrapper">
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
            <li class="swiper-slide">
                <img src="http://placekitten.com/640/480" alt="">
            </li>
        </ul>
    </div>
</div>
```

## swiperの設定
`.slider-wrap`の数だけ各要素に01から連番を振るループを組むことで個別にSwiperを書くことを避けています。


```js:main.js
window.onload = function () {
    var sliderWrap = document.querySelectorAll('.slider-wrap');
    var sliderThumb = document.querySelectorAll('.slider-thumb');
    var sliderMain = document.querySelectorAll('.slider-main');
    var sliderNext = document.querySelectorAll('.swiper-button-next');
    var sliderPrev = document.querySelectorAll('.swiper-button-prev');
    for (let i = 0; i < sliderWrap.length; i++) {
        var num = ('00' + (i + 1)).slice(-2);
        sliderWrap[i].className += (num);
        sliderThumb[i].className += (num);
        sliderMain[i].className += (num);
        sliderNext[i].className += (num);
        sliderPrev[i].className += (num);
        //サムネイル用のスライダー指定
        var swiperThumb = new Swiper('.slider-thumb' + (num), {
            slidesPerView: 3,
            spaceBetween: 7,
        });
        //メインのスライダー指定
        var swiperMain = new Swiper('.slider-main' + (num), {
            loop: true,
            centeredSlides: true,
            slidesPerView: 1,
            thumbs: {
                swiper: swiperThumb,
            },
            // 前後の矢印
            navigation: {
                nextEl: '.swiper-button-next' + (num),
                prevEl: '.swiper-button-prev' + (num),
            },
        });
    }
}

```

# CodePen

@[codepen](https://codepen.io/kotaro-jp/pen/wvyRVBg)
@[codepen](https://codepen.io/_k1b3/pen/wvyRVBg)

https://codepen.io/_k1b3/pen/wvyRVBg