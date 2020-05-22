## はじめに
本リポジトリはパロディであり、[ojichat](https://github.com/greymd/ojichat) をForkしたものです。
作者はオカマをよく知らないので、偏見がたくさん詰まっています。
以上を踏まえた上でお楽しみ下さい。

## なんだこれは

おかまやオネエがLINEやメールで送ってきそうな文を生成するコマンド。

## 開発環境

```bash
$ go version
go version go1.12 darwin/amd64
```

## インストール

```bash
go get -u github.com/54m/kamachat
```

環境変数`GO111MODULE=on`をセットしている場合は、以下のようにインストールする。

```bash
GO111MODULE=off go get -u github.com/54m/kamachat
```

## 使い方

```bash
$ kamachat -h
Usage:
  kamachat [options] [<name>]

Options:
  -h, --help      ヘルプを表示.
  -V, --version   バージョンを表示.
  -e <number>     絵文字/顔文字の最大連続数 [default: 4].
  -p <level>      句読点挿入頻度レベル [min:0, max:3] [default: 0].
```

そのまま実行すると文言が出力される。

```bash
$ kamachat
ヤッホー😍😃トモヒロっち、元気かな⁉😜⁉️🤔アタイは、近所に新しくできたホスト😎✌に行ってきたよ。味はまぁまぁだったかナ💕
```

文言には特定の人名が含まれることもあるが、第一引数で指定可能。

```bash
$ kamachat 山田
山田ちゃん、オハヨウ〜(^з<)😚（笑）山田ちゃんも今日も2時までお仕事かナ❓寒いけど、頑張ってね(＃￣З￣)🙂💤
```

`-p` オプションの数字を大きくする(最大3)することで文章に句読点が含まれやすくなる。
中身がまるでおじさんの文章には句読点が多い傾向が見られるため、より実際の状況を模したユースケースに対応できる。


```bash
$ kamachat -p 3 アタイとアンタと大五郎
アタイと、アンタと、大五郎ﾁｬﾝ、オッハー❗(^_^)🎵アタイと、アンタと 、大五郎ﾁｬﾝにとって、素敵な、1日に、なります、ようニ😘
```

`-e` オプションの数字を大きくすることで、絵文字/顔文字がより連続で含まれやすくなる。
一部のおかまやオネエの文章にはそれらが多用される傾向があるためである。
また、引数を0とすることで真面目なおかまにもなる。
より柔軟に実際の状況を模したユースケースに対応できる。

```bash
$ kamachat -e 10
おはよー、！チュッ😚😘😘😃☀ 😆❗😚😆(^з<)

$ kamachat -e 0
ヤッホー。堅ちゃん、元気かな。堅ちゃんにとって素敵な1日になりますようニ。
```

また、適宜、文節の終わりが最大2文字までカタカナとなる活用がされる。
これにより実際の状況を模したユースケースに(ry

```bash
$ kamachat
...ご要望とかはあるのかな❗💕😚😘😜❓

$ kamachat
...ご要望とかはあるのカナ❗🎵😆💕❓😜
```

## Dockerコンテナ版
おかまやオネエで環境を汚したくない、Goの実行環境を持っていないなどの状況でもお手軽におかまになるために、Dockerコンテナでもkamachatを用意した ( [54mch4n/kamachat](https://hub.docker.com/r/54mch4n/kamachat) )。

### 使い方

- `docker run --rm -i 54m/kamachat:latest` はオプション等を含めて全て `kamachat` と同じ動きをする。

```
$ docker run --rm -i 54m/kamachat:latest
ヤッホー(^з<)🎵（笑）村上サァン、元気かな😜⁉️土曜日は仕事〜❗❓村上サァン😚😃♥ 💗元気、ないのかなァ(^▽^;)💦大丈夫⁉😜⁉️✋❓❓
```

- `kamachat 平井堅` と同じ動きをする
```
$ docker run --rm -i 54m/kamachat:latest 平井堅
平井堅ｻｧﾝ、久しぶり(^з<)(^з<)そういえば、昨日は例のおかまバー♂に行ってきたよ。結構いい雰囲気だったから、オススメだよ😚😚😍
```

## ライセンス

MIT
