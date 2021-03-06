title: チーム開発
date: 2017-11-30 00:00
tags: Refactoring

---

最近ブログサボってて久し振りの投稿になります。
というのも業務で大規模リファクタリングを行っていて忙しくてなかなか時間が取れませんでした。
このリファクタリングを通してチーム開発の良さ、楽しさをあらためて感じました。

大規模リファクタリングした動機としては、現状のコードが個人のフリーライティングで書かれた部分が多く、
システムを把握するのに時間がかかり、どこにどう実装 or 修正すればよいのか迷う状態でした。
今後メンバーが増えて行く中で開発スピードの維持しながら開発規模を拡大していくためには設計から見直す必要があり、
DDDのレイヤー化アーキテクチャーでシステム設計を再考していきました。
作業内容としては、メンバー3名で設計やコーディング規約など事前にある程度決めて1ヶ月半ぐらいひらすらリファクタする感じでした。

### チーム開発のやってよかったこと

#### ・ よく議論したこと

リファクタ時に、設計がどうしても合わない部分や見直したい部分というのは出てきます。
その際に、どうすべきかを設計者などが決めずに議論して決めれてたことが良かったと思ってます。
設計者は大体ここはこうすべきっていう一般的な知見は持ってますが、議論して問題を堀り下げていくと
それが合っていなかったり、こうした方が良かったということも多々ありました。
また議論することでメンバーが何か気になりながらコーディングせずに納得した感じで作業できるのも良いと思いました。
このコードなんか統一されてないよなーとか思ってるコードでも何も議論せずにモヤモヤした気持ちのままと議論した上での
結果であればストレスの持ち方が違います。
そして、こうした何でも議論しやすい環境を作るのがチーム開発では特に大事だと感じました。

#### ・ 特にタスク担当を決めなかったこと

結果オーライ的なとこがあるのですが、明確なタスク担当決めずにタスク終了したら次のタスクを取るみたいな流れで
作業してたので(得意不得意出ますが)各メンバーがシステムの広範囲の把握することができました。
終って見るとメンバーがシステム構成など全体を理解するのによい機会となってました。

#### ・ エンジニア全員でできたこと

もともと3人しかいかなったので全員でやるのは自然な流れだったのですが、
設計やコーディング規約を決めていくとメンバーへ理解してもらえるまでレビューなどで伝えていかなければなりませんが
メンバー全員に入ってもらうことで決めたことに対する共通認識を持てるので以降の作業がスムーズになります。
もう少し大きい組織だったとしても、別チームのメンバーにも入れ替わりでサポートに入ってもらい認識の共有するのはアリかと。

#### ・ 1人で抱えこまなかったこと

これは自分に対してなのですが、これまで一人でリファクタを進める機会が多く、大規模なリファクタをずっとやってると
全然進捗が進まなかった日やゴールの遠さに心が折れそうになる日もあり精神的に不安になる時がありました。
チームでリファクタを進めると、自分の進みが悪くても他のメンバーが頑張ってくれてたりしてするので進捗的にも非常に助かり、
精神的に不安になることは少なくゴールに向って良いモチベーションを維持することができました。
メンバーを信頼することやチーム開発の良さを感じれました。

#### ・ 一緒にご飯に行ったこと

昼も夜も一緒に食事してたのでチームの結束力が強くなった(と感じてます)
実は一番大事なとこだっと思ってます。(コミュニケーション大事)


### 所感

ただ振られたタスクを個人個人が淡々とこなしていくのはチーム開発でなく
チームが同じ目的意識を持って進めることができるのが本当のチーム開発だなとあらためて感じました。
これまでいろんなプロジェクトでチーム開発してきましたがこうゆう気持ちになれるプロジェクトは
久々でしたのでとても良い経験をさせてもらいました。
