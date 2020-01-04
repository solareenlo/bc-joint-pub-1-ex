# ブロックチェーン合同誌#1の練習用リポジトリ

- 技術書典8で配布するブロックチェーン合同誌#1の練習用リポジトリです。
- [Re:VIEW](https://github.com/kmuto/review) を Docker 内で動かして製本します。
- このリポジトリで Re:VIEW を試してみて、うまく行きそうなら、Taro Yamada までご連絡ください。

## 前提条件

- git
- GitHub アカウント
- Dokcer
- テキストエディタ

## Usage
```bash
git clone git@github.com:solareenlo/bc-joint-pub-1
cd bc-joint-pub-1

# 下記の『ファイル説明』と『記事の出し方』と『Re:VIEW の書き方』を参考に記事を作成する

# pdf を作成する
sudo docker run --rm --mount type=bind,source=$(pwd),target=/work vvakame/review:4.0 /bin/sh -c "cd /work && rake pdf"
# docker-compose を使って pdf を作成する
sudo docker-compose run --rm review rake pdf

# epub を作成する
sudo docker run --rm --mount type=bind,source=$(pwd),target=/work vvakame/review:4.0 /bin/sh -c "cd /work && rake epub"
# docker-compose を使って epub を作成する
sudo docker-compose run --rm review rake epub
```

## ファイル説明
- `/contents` ディレクトリが `.re` ファイルの置き場。
- `/images` ディレクトリが画像ファイル置き場。
- `catalog.yml` が目次ファイル。

## 記事の出し方
1. `master` ブランチから適当にブランチを切ります。
2. `/contents` ディレクトリ内に自分の記事ファイル `your-name.re` を追加します。
3. `catalog.yml` ファイルの `CHAPS` に `your-name.re` を追加します。
4. 執筆します。
    - フォーマットは [Re:VIEW(v4.0)](https://github.com/kmuto/review/tree/v4.0.0)
    - 画像ファイルは `/images` ディレクトリに適当にサブディレてクリを作成してください。
5. `atogaki.re` ファイルに執筆者紹介を書きます(例は `atogaki.re` ファイルにあります)。
6. プッシュして PR を作ります(特にフォーマットはありません)。
7. 編集係がレビューして、削除して、マージされます。

## Re:VIEW の書き方
- [Re:VIEW フォーマットガイド](https://github.com/kmuto/review/blob/master/doc/format.ja.md)
- [Re:VIEW 記法チートシート](https://qiita.com/froakie0021/items/b0f4ba5f242bbd571d4e)
- [Re:VIEW チートシート](https://gist.github.com/erukiti/c4e3189dda179a0f0b73299fb5787838)
- [Re:VIEW wiki](https://github.com/kmuto/review/wiki)

## 表紙と裏表紙
- 電子版を作成するときには表紙と裏表紙を設定します。
- 設定するには `config.yml` の `/images/cover.png` と `/images/backcover.png` を配置して、`coverimage` と `backcover` のコメントアウトを外すだけ。

## License
Main part of Re:VIEW is applied GNU Lesser General Public License (LGPL).
See [COPYING](https://github.com/kmuto/review/blob/master/COPYING) file.

Exception:

* doc/*: MIT License. See [LICENSE](https://github.com/kmuto/review/blob/master/doc/LICENSE) file.
* jumoline.sty, vendor/jumoline: The LaTeX Project Public License. See [LPPL](https://github.com/kmuto/review/blob/master/vendor/jumoline/lppl.txt) file.
* plistings.sty, vendor/plistings: MIT License. See [LICENSE](https://github.com/kmuto/review/blob/master/vendor/plistings/LICENSE) file.
* gentombow.sty, vendor/gentombow: BSD License. See [LICENSE](https://github.com/kmuto/review/blob/master/vendor/gentombow/LICENSE) file.
* jsbook.cls, vendor/jsclasses: BSD License. See [LICENSE](https://github.com/kmuto/review/blob/master/vendor/jsclasses/LICENSE) file.

## References
- [kmuto/review](https://github.com/kmuto/review)
- [vvakame/docker-review](https://github.com/vvakame/docker-review)
- [vvakame/docker-review/doc/windows-review.md](https://github.com/vvakame/docker-review/blob/master/doc/windows-review.md)
- [solareenlo/docker-review](https://github.com/solareenlo/docker-review)
- [mixi-inc/techbookfest](https://github.com/mixi-inc/techbookfest)
- [TechBooster/ReVIEW-Template](https://github.com/TechBooster/ReVIEW-Template)
- [engineers-lt/rooting-book-2](https://github.com/engineers-lt/rooting-book-2)
