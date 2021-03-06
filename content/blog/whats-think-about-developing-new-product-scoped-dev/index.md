---
title: "新規プロダクト開発で向き合おうと思っていること"
date: "2020-08-01T06:40:32.169Z"
template: "post"
draft: false
slug: "whats-think-about-developing-new-product-scoped-dev"
category: "dialy"
  #"dialy" "development" "tips"
tags:
  - "blog"
description: "新規プロダクト開発で向き合おうと思っていること"
socialImage: "/media/42-line-bible.jpg"
---

# motivation
新しくプロダクトを作っていくことになっているのですが、正直不安な面も多く感じています。
なので、不安の正体は何なのかを突き詰めると同時に、今回作っていくプロダクトについて、どういう方針で作って行こうと思っているのか、残していこうと思います。

# agenda
- 新規開発という不確実性と考えるべきパラメータと不安要素
- Product User Fitに向けて
- Sustainable Improvementに向けて
  - メンバーのOn-boarding Costの削減
  - メンバーのRetention Rateの向上

# summery
チームの経験が浅い && 明確な勝ち筋がない状態では、以下に改修可能ないし、開発したもの自体を捨てられる状態で残して置くかを考える必要がある.

# 新規開発という不確実性の考えるべきこと
今回開発していくのは、すでにあるビジネスにレバレッジをかけるための業務管理系のプロダクトを開発します。
そのため、いわゆるC向けのプロダクトを開発するより、レバレッジをかけたい数字が明確なのと、ペルソナが社内にいるということで、フィードバックを得やすく、難易度は低いと考えています。
そして、プロジェクトをすすめるにあたり、僕は直近は以下2つフェーズを前提に考えています。

- 1 Product User Fit
- 2 Sustainable Improvement


詳しくは、後ほど、後述していればと思いますが、
1はProduct Market Fit と同じような概念です。

現在の不安要素としては開発経験がすくないという要素です。
本当は、スケールするときも想定して、考えたいのですが、僕には10-100万単位のユーザーが使うプロダクトの開発に携わった経験がありません。
なので、経験からのボトルネックのになるポイントの事前察知は難しく、進みながら情報を集めて対策を打っていうという展開になると思います。


# Product User Fitに向けて
toCのプロダクトであれば、PMF(Product Market Fit)を目指すというのがよく言われていることだと思います。
しかし、今回はすでにユーザーは固定されています。
そのためいかにユーザーに気持ちよく使ってもらえるか？がキモになるので、Product User Fit という名前にしています。

そして、必要なデータだったり、連係しなければいけないAPIなど条件がすでにあります。そのため、プロダクトのドメインやDBのモデリングはある程度制限されてきます。
その上で、ユーザの工数とストレスを無くすフロントエンドを構築していくという流れになります。

上記のような前提条件のもと、技術選定で考えているのは、バックエンドは型付き言語、フロントエンドはNuxt x Typescript かなと思っています。

バックエンドの技術選定としては、前述の通りモデリングが開発開始時点である程度制限され、突発的な仕様変更は起こりにくいと考えています。そのため、スピード感をもって柔軟に仕様変更をできる動的言語よりは、堅牢な静的型付言語の方がよいと思っています。
僕はRails開発が得意ですが、型がないことによるメンテナンスのコスト、なかでもコードをよんでコード間の関係性を把握するコストが高いなぁと思っています。
今回は、サービスドメインの知識が必要になってくる業務管理系のシステムでもあるので、型があるだけでも情報を得るコストが下がるのではないかと考えています。

フロントの技術選定としては、最近はやりのtypescript と 自分が経験ある && htmlの知識があればコードを書きやすくてハードルが低いNuxt(Vue)を採用しようと思っています。
正直、フロントエンドのつよつよエンジニアを採用できる余力がないので、メンテナンスのコストが低くするためのtypescriptと、Reactよりコードを触れられる母数が多そうなNuxtを採用しようと思っています。

採用という面を考えたときに、バックエンドの言語としてGolangなどの言語を採用すると、経験があるエンジニアも少なくなり、単価も高くなってしまう印象があります。
まだスタートアップで組織ができていないんで、今後の人を採用するという変数も考える必要があるため、技術選定もそれによって変わるかもしれません。

# Sustainable Improvementに向けて
ここで考えていくのは、使われるプロダクトになったときに、継続的に改善を回せる体制をつくるということを考えるパートです。
主に、
1. メンバーのOn-boarding Costの削減
2. メンバーのRetention Rateの向上

を考えます。

## メンバーのOn-boarding Costの削減
On-boarding を考えたときに、ソフトウェアの構造とビジネスオペレーションの構造を把握できる仕組みが必要だと思っています。
すでに既に述べたように、ソフトウェアの構造を把握しやすい仕組みの一つとして、型付言語の採用があると思います。

その上で、さらに考えることは、
- データのモデリングを常に可視化して、オブジェクトオリエンテドな開発をしやすくする。(DDD的な開発)
- ビジネス側のオペレーションフローモデルととソフトウェアのモデルを可視化して、ビジネスとソフトウェアの関係性を把握しやすくする。
- テストをもとに、一つのfucntionのインターフェイスと、期待されているアウトプットを把握できるようにしておく。

などを考えています。
テストを書くなどは当たり前といえば当たり前なのですが、工数の問題もあり、テストをキレイににあらゆるレイヤーですべて書くことは不可能だと思っています。
そのため、リソースが足りなくなることも想定し主に粒のさじ加減に関する指針が必要だと思っています。
以前、テストの粒度はE2Eに近い範囲で初期は書いておいて、あとから粒度が細かいUnit Testなどを入れておけばいいと思っていましたが、それだとメンテナンスが恐ろしく大変だということに気づかされました。


## メンバーのRetention Rateの向上
メンバーが自分の会社で継続的に働いてもらうことを、どのように設計するかも重要です。
僕の中では以下2つに分けて考えています。

- 会社全体として
- エンジニア組織として

会社としての方向性について、今抱いている課題感としては事業がソフトウェアをつくるというところから入っていないため、組織としてエンジニアリングについての共通言語が少ないことです。
そのため、今ある会社の文化とエンジニアの文化をどうマージしていくか？が直近の目標になります。
指針としては、もともこうもない形になってしまいますが、お互いの歩み寄りをどう作っていくか？になります。
そのため、これからエンジニアとして参加してもらえるような方は、技術だけでなく、ビジネスサイドへ積極的にコミュニケーションをとって自ら改善していけるような人に参加していただきたいと思っています。
また、そのような人がより働きやすいように、共通言語をつくっていく仕組みや、前述したビジネスのオペレーションをモデリングし可視化できるような仕組みを作っていき、コミュニケーション摩擦を少なくしていきたいと考えています。

先程はビジネスサイドもふくめ仕事をどう作っていくか？のレイヤーの話をしましたが、エンジニアリング組織としての話はどう充実感を持ってもらって実行していくか？という話になります。
端的に表現をすると、楽しくコードを書く環境をどう作るとよいかなっと考えています。

この点に関してはグーグルの、自分で書いたコードが多ければ多いほど、プロダクトに対する愛着がわき、組織的な面でプラス効果がはたらくというという話が参考になるかなと思っています。
なので、手を入れられなくなる状態を状態をなくして行くという行為が必要になると考えています。
これは前のセクションで書いたとおり、適度な粒度のテストを書いていくというのがアクションになると思います。

またここで、手を入れるとは、ただ単に改修をしやすいとかだけでなく、そもそも作り返ることを可能にしたいという意図もあります。
同じこと言ってしまいますが、インターフェイスと求めているアウトプットを明確にしていくことが重要だと思っています
そのためにも、通信にはインターフェイスが常に更新され続けるSwagger, g-rpc だったり、内部ロジックにはInterfaceを定義できる型付言語を採用するのがよいのかなと思っています。

## あとがき
自分の課題感としては、未来への解像度が薄いことです。
こう書いている自分もいまいちパッとしていないなぁと思っていますが、一応今の時点で頭にあることを吐き出してみました。

こうかいていみると、当たり前のことをつらつらと書いてしまったなと思いました。
当たり前のことを当たり前にやるのが難しいというのが人間の特性ですね。
