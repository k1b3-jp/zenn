---
title: "【SEO】「検出 - インデックス未登録」を解決する"
emoji: "🤔"
type: "tech"
topics: ["seo", "google", "searchconsole"]
published: true
---

# 起こったこと
半年以上経ってもクローリングされてなかったので、サーチコンソール確認したら「検出 - インデックス未登録」となっていた...見たことなかったので解決の顛末を残します。

# 解決方法
早速結論ですが、Google Search Consoleの「URLを検査」より、インデックス登録をリクエストしましょう！
私の場合は2日後にインデックス登録を確認できました！

## そもそも「検出 - インデックス未登録」とは？
Googleがクロールする前の状態です！
したがって、コンテンツの質の判断すらされていないです💦
（最初はページの質を疑ったのですが...）

# 試したこと
* noindex等かかってないか確認
* サイトマップ送信
* 待つ！
で、変化がなかったので直接インデックス登録をリクエストしました。

# インデックス登録のリクエスト方法
https://developers.google.com/search/docs/advanced/crawling/ask-google-to-recrawl?hl=ja#use-the-url-inspection-tool-just-a-few-urls

# 補足
インデックス登録のリクエスト、ページが少ない場合は良いのですが
大量に未登録だった場合は全てポチポチするわけにはいきません笑

その場合はIndexing APIの利用を検討すると良いかもしれません。
参考記事
https://tensei-shinai.com/2022/03/07/not-indexed/

GCP登録いやだあああああああ！という人は妥協案で、WordPressのプラグイン「[PubSubHubbub](https://ja.wordpress.org/plugins/pubsubhubbub/)」なんかを導入してみるのも良いかもしれません！

# 参考
https://support.google.com/webmasters/thread/126984169/%E6%A4%9C%E5%87%BA-%E3%82%A4%E3%83%B3%E3%83%87%E3%83%83%E3%82%AF%E3%82%B9%E6%9C%AA%E7%99%BB%E9%8C%B2%E3%81%AE%E6%95%B0%E3%81%8C%E5%A4%9A%E3%81%8F%E3%80%81%E3%82%A4%E3%83%B3%E3%83%87%E3%83%83%E3%82%AF%E3%82%B9%E3%81%95%E3%82%8C%E3%81%AA%E3%81%84%E3%82%B1%E3%83%BC%E3%82%B9%E3%81%8C%E5%A4%9A%E3%81%84?hl=ja