---
title: "【Ruby】RSpec触ってみたので初歩の一手をまとめとく"
emoji: "🐕"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["ruby", "rails", "rspec"]
published: true
---

# はじめに
RSpecを使ったテスト方法の”本当にはじめの一歩”を記録しておきます！

# RSpecとは？

- Rubyのテストツール
です！

コマンドひとつでテスト出来るので便利っぽい。

# 書き方の色々
## describe/context/it/expect
`describe`はテストのグループ化を宣言します。
`context` でテストをグループ化することもできるが、`context`は条件を分けたりするときに使うことが多いらしい。
`it` はテストをexampleという単位にまとめます。

例
```ruby
describe "#message" do
    context "hogeの場合" do #条件でグループ化
        it "戻り値が正しいこと" do
        # テスト内容を書く
        end
    end
end
```

### エクスペクテーション
`expect(A).to eq B`で「AがBに等しくなることを期待する」テストになります。

例
```ruby
describe "#message" do
    context "hogeの場合" do #条件でグループ化
        it "戻り値が正しいこと" do
            expect(result[:りんご達]).to match_array [りんごA]
        end
    end
end
```

## let
インスタンス変数を`let`で置き換えることができます。
例えば`let(:hoge) { ... }` と書くと、
`{ ... }`の中の値が`hoge`として参照できるようになります！

# 最後に
触ってみた感じで、めちゃくちゃ初歩中の初歩をまとめました！
また追加していきます！