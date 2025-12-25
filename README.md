# lualatex-kobe-template

LaTeX（ラテフ）は、レポートや学術論文などの文書作成に適したフリーの組版制御ソフトです。数式や図表の自由な配置編集や、自動的な目次や索引の作成、相互参照の構築など、文書作成のさまざまな機能を備えています。

このレポジトリは、本テンプレートは神戸大学市民工学部の論文様式に準拠した、lualatexを使った論文作成のためのテンプレートです。lualatexは、Lua言語を組み込んだLaTeXエンジンであり、従来のpLaTeXやupLaTeXに比べて柔軟性と拡張性が向上しているらしいです。

---

- [lualatex-kobe-template](#lualatex-kobe-template)
  - [0. Overleafを用いる場合](#0-overleafを用いる場合)
  - [1. VSCodeの環境設定](#1-vscodeの環境設定)
    - [1.1 VSCodeとLatexのインストール](#11-vscodeとlatexのインストール)
    - [1.2 VSCodeの拡張機能の追加](#12-vscodeの拡張機能の追加)
    - [1.3 setting.jsonの設定](#13-settingjsonの設定)
    - [1.4 OSの再起動](#14-osの再起動)
  - [2. 運用方法](#2-運用方法)
    - [2.1 本レポジトリのダウンロード](#21-本レポジトリのダウンロード)
    - [2.2 latexのコンパイル](#22-latexのコンパイル)
  - [3. 参考文献の作り方](#3-参考文献の作り方)
    - [1. 手書きする](#1-手書きする)
    - [2. Google ScholarからBibTeX形式でエクスポートする](#2-google-scholarからbibtex形式でエクスポートする)
    - [3. 文献管理ツール（Zotero, Mendeleyなど）を用いる](#3-文献管理ツールzotero-mendeleyなどを用いる)
  - [4. 各ディレクトリの説明](#4-各ディレクトリの説明)
  - [5. 「、」「。」を「，」「．」で置き換える](#5-をで置き換える)
    - [5.1 環境設定を使う](#51-環境設定を使う)


## 0. Overleafを用いる場合

[**Overleaf**](https://ja.overleaf.com/)とは、ChromeやSafariなどのWebブラウザで起動するクラウド型Latexエディタである。基本無料で利用することができ、ローカルPCの環境構築は不要。

Overleafを用いる場合、以下の記事を参考する。

- [いますぐLatexを始めたいならOverleafを使おう](https://qiita.com/nagampere/items/7407a0b7952b0e3708ed)

## 1. VSCodeの環境設定

VS CodeはLaTeX環境としておすすめ。「LaTeX Workshop」によるリアルタイムPDFプレビュー、自動補完、エラー表示が可能で、効率的に作業が進められる。
さらに、軽量で動作が速く、拡張機能やAI連携、Gitによるバージョン管理も可能。

参考

- [【自研究室向け】LaTeX+VSCode環境構築 2023年版](https://qiita.com/fuku_uma/items/e5ad46125a9612320273)
- [LaTeX Workshop を使いこなす](https://qiita.com/Yarakashi_Kikohshi/items/a9357dd469320ffb65a0)
- [VSCode で最高の LaTeX 環境を作る](https://qiita.com/rainbartown/items/d7718f12d71e688f3573)

---

### 1.1 VSCodeとLatexのインストール

**MacOSの場合**  
homebrewでいずれもインストールできます。ターミナルから以下のコードを実行してください。

```bash
# VSCode の導入
brew install visual-studio-code --cask 
# LaTeX環境(GUI無)の導入
brew install --cask mactex-no-gui 
# 管理者権限でLaTeXパッケージの更新
sudo tlmgr update --self --all 
# 管理者権限で用紙サイズの変更
sudo tlmgr paper a4 
```

MacOSでhomebrewを使っていない人はいますぐ使えるようになってください。  
これが使えるようになると、今後の全ての環境構築が圧倒的に楽になります。  

- [【macOS版】初心者でもわかる！Homebrewのインストール手順を徹底解説](https://zenn.dev/inablog/articles/5e790c9fbdad20)
- [2024年版 Homebrew完全ガイド：macOSのパッケージマネージャーを使いこなす](https://qiita.com/yu_uk/items/73654985fb1caeab4cec)


**Windowsの場合**  
動作確認をしていないので、以下の資料を読んでインストールしてください。  
[【大学生向け】LaTeX完全導入ガイド Windows編 (2022年)](https://qiita.com/passive-radio/items/623c9a35e86b6666b89e)

---

### 1.2 VSCodeの拡張機能の追加

VSCodeは、拡張機能をインストールすることで便利にカスタマイズできるIDE(総合開発環境)である。Latex運用に必要な拡張機能は以下の通り。

| 必要度    | 拡張機能名                                | 主な機能              |
| ------ | ------------------------------------ | ----------------- |
| ⭐︎⭐︎⭐︎ | Latex Workshop                       | latexコンパイルの自動化    |
| ⭐︎⭐︎   | Japanese Language Pack for VS Code   | VSCodeのGUIを日本語に変更 |
| ⭐︎     | Github Copilot & Github Copilot Chat | AIコードアシスタントの利用    |
| ⭐︎     | Character Count (j4ng5y)             | 全角対応の文字数カウンター     |

拡張機能の追加手順は以下の通り。

1. アクティビティバーの拡張機能マークをクリックする（四角が4つあるマーク）
2. インストールしたい拡張機能を検索する
3. 拡張機能を選ぶ
4. インストールをクリックする

参考

- [Visual Studio Codeに入れるべき拡張機能【2024年最新版】](https://qiita.com/qrrq/items/0e116a59743874d18cb1)
- [Visual Studio Code（VSCode）の設定をしてみた](https://qiita.com/TS1engineer/items/1b54f65ee87cb49582f5)

---

### 1.3 setting.jsonの設定

setting.jsonを編集し、拡張機能「Latex Workshop」の詳細設定を行う。手順は以下の通り。

1. 左下の歯車マークから「設定」を開き、右上の「設定(JSON)を開く」をクリック
2. settings.jsonが開かれるので、本レポジトリの同名ファイルの中身をコピペする。
3. 

LaTeX Workshop ではビルド設定を「Tool」と「Recipe」という2つで考える。

- Tool: 実行される1つのコマンド。コマンド (command) と引数 (args) で構成される。("latex-workshop.latex.recipes" で定義)
- Recipe: Tool の組み合わわせを定義する。Tool の組み合わせ (tools) で構成される。("latex-workshop.latex.tools" で定義)

Toolの主要なコマンドは以下の通り。

- `lualatex`: LuaLaTeXエンジンで.texファイルをコンパイルし、PDFを生成する。
- `biber`: 参考文献データベース(.bibファイルなど)を処理し、引用情報を生成する。
- `bibtex`: biberと同様に参考文献データベースを処理するが、古典的な環境で互換性を重視する場合に使用される。
- `pdflatex`: 英語のみで最小構成のLaTexエンジンで、luaLaTex同様に.texファイルをコンパイルする。
- `platex`: 日本語組版に特化したLaTeXエンジンで、luaLaTex同様に.texファイルをコンパイルする。
- `pbibtex`: platex用の参考文献データベースを処理する。
- `dvipdfmx`: DVIファイルをPDFに変換する。

Windowsの場合は[こちら](https://qiita.com/fuku_uma/items/e5ad46125a9612320273#:~:text=VSCode%E3%81%AE%E8%A8%AD%E5%AE%9A-,Windows%E3%81%AE%E5%A0%B4%E5%90%88,-Mac%E3%81%AE%E5%A0%B4%E5%90%88)を参考にする。

参考
- [【LaTeX】初心者向けエンジンと文書クラスについて](https://qiita.com/kou-JP/items/60b63963f2ae7fdefddd)


---

### 1.4 OSの再起動

新たにパスの追加やsetting.jsonの編集をした場合は、念の為OSを再起動しておくと良い。

---

## 2. 運用方法

### 2.1 本レポジトリのダウンロード

本レポジトリ「lualatex-kobe-template」をダウンロードする方法は大きく2つ。

1. zipファイルを直接ダウンロードする
   1. [lualatex-kobe-template](https://github.com/nagampere/lualatex-kobe-template)にアクセスする
   2. 緑色の「< > Code▽」をクリックし、「Download ZIP」を実行
2. Githubからフォーク(forkする)
   1. [lualatex-kobe-template](https://github.com/nagampere/lualatex-kobe-template)にアクセスする
   2. 「< > Code▽」の右上にある「Fork」をクリックし、lualatex-kobe-templateをコピーした新たなレポジトリ(ホストは自身)を作成する
   3. 新たなレポジトリをgit cloneでローカルに読み込む

**何故Githubを使った方が良いのか？**

1. **バージョン管理が容易**
   - 過去の変更履歴を保存し、特定のバージョンに戻すことが可能。
   - 変更点が明確になり、誰が何を修正したかを把握できる。
2. **バックアップとしての活用**
   - GitHubにリポジトリを保存することで、データが安全に保管される。
   - ローカルPCのトラブルやデータ消失のリスクを軽減。
3. **複数デバイスでの作業が可能**
   - クラウド上のリポジトリを利用することで、どのデバイスからでも最新状態にアクセスできる。
   - 自宅や研究室など、環境を問わず作業を続行可能。
4. **GitHub copilotの援助**
   - 分からないコードやエラーに対して、説明や修正をVSCode内で求められる。
   - コードを書き始めると、次に書くべきコードを予測して提案してくれる。

Gitの使い方については以下を参照

- [Githubリポジトリのfork（フォーク/派生）の使い方・clone（クローン）との使い分け](https://www.kagoya.jp/howto/rentalserver/webtrend/githubfork/)
- [【Git】Git初期設定 for Mac OS](https://qiita.com/mmikri/items/89508e9435339fcb97e1)
- [【入門】VSCodeとGitHubの連携手順・使い方をわかりやすく解説](https://www.kagoya.jp/howto/rentalserver/webtrend/vscode/)
- [サル先生のGit入門](https://backlog.com/ja/git-tutorial/)

### 2.2 latexのコンパイル

main.texをコンパイルしてPDFファイルを作成する方法は大きく2つ。

1. latex-workshopタブから実行する
   1. 任意のtexファイルを開く
   2. 左のタブに「TEX」と表記されたlatex-workshopのタブをクリックして開く
   3. 「コマンド」内の「LaTeXプロジェクトをビルド」をクリックでPDFを更新
   4. 「LaTeX PDFを表示」をクリックしてPDFを開く
2. texファイルを保存して自動更新する
   1. 任意のtexファイルを開く
   2. 「control + S」でファイルを保存する

settings.jsonの設定で、保存時に自動でPDFが保存される。  
動作が重いときは、settings.jsonの"latex-workshop.latex.autoBuild.run"を"off"にする。  
もしくは、main.texを\documentclass[report, 12pt, a4paper, draft]{jsbook} にしてdraftモードを有効にし、画像の出力を省略する。

---

## 3. 参考文献の作り方

引用文献は、3_backmatter/references.bibにBibTeX形式で追加する。追加方法は以下の3通り。

1. **手書きする**
2. **Google ScholarからBibTeX形式でエクスポートする**
3. **文献管理ツール（Zotero, Mendeleyなど）を用いる**

### 1. 手書きする

3_backmatter/references.bibは、`article`(学術論文)・`book`(書籍)・`incollection`(書籍セクション)・`misc`(その他)の4種のBibTeXエントリに対応している。これを参考にして、引用文献を手書きで追加する。

**また、日本語の文献を追加する場合は、必ず`langid = {japanese}`を指定する。これにより、日本語特有の表記ルール（著者名の順序、句読点など）が適用される。**

```latex
@article{misono2014, %論文のCitation Key（識別子）
  author  = {{御園, 一} and {山田, 隆司}}, % 著者名（姓と名は連結させるかカンマを打つ）
  title   = {日本の社会資本が地域別生産性に与える効果の再検証}, % 論文タイトル
  journal = {日本大学経済学部経済集志}, % 雑誌名
  volume  = {83}, % 【任意】巻数
  number  = {2}, % 【任意】号数
  pages   = {107--132}, % 【任意】ページ範囲
  year    = {2014}, % 発行年
  langid  = {japanese} % 言語設定（日本語の場合はjapanese/jpn/jp, 英語の場合は不要）
}

@book{mitsui2010, % 書籍のCitation Key（識別子）
  author  = {W.S. ロースター}, % 著者名
  translator  = {三井, 清}, % 【任意】翻訳者名
  title   = {社会資本整備の経済効率性からみた公共投資のあり方}, % 書籍タイトル
  publisher = {学文社}, % 出版社
  edition = {2}, % 【任意】版数
  volume  = {9}, % 【任意】巻数
  pages   = {302}, % 【任意】ページ範囲
  year    = {2010}, % 発行年
  langid  = {japanese} % 言語設定（日本語の場合はjapanese/jpn/jp, 英語の場合は不要）
}

@incollection{kim2013, % 書籍セクションのCitation Key（識別子）
  author  = {Kim, Minsoo}, % 著者名
  title   = {The effect of public capital on total factor productivity in East Asia}, % セクションタイトル
  booktitle = {Infrastructure and economic development}, % 書籍タイトル
  publisher = {Elsevier}, % 出版社
  edition = {2}, % 【任意】版数
  volume = {3}, % 【任意】巻数
  pages   = {137--156}, % 【任意】ページ範囲
  year    = {2013}, % 発行年
  langid  = {japanese} % 言語設定（日本語の場合はjapanese/jpn/jp, 英語の場合は不要）
}

@misc{yamano2024, % その他のCitation Key（識別子）
  author  = {山野, 浩一}, % 著者名
  title   = {公共投資の経済効果に関する実証分析の動向}, % タイトル
  journal = {日本都市研究所}, % 【任意】誌名(webサイトのタイトル),
  year    = {2024}, % 【任意】発行年
  howpublished = {https://www.stat.go.jp/data/chiri/1-1.html}, % 【任意】URL
  urldate = {2025-01-21}, % 【任意】アクセス日
  langid  = {japanese} % 言語設定（日本語の場合はjapanese/jpn/jp, 英語の場合は不要）
}
```

### 2. Google ScholarからBibTeX形式でエクスポートする

Google Scholarでは、論文や書籍のBibTeX形式での引用情報を簡単に取得できる。手順は以下の通り。

1. [Google Scholar](https://scholar.google.com/)にアクセス。
2. 検索バーに引用したい文献のタイトルや著者名を入力して検索。
3. 検索結果から目的の文献を見つけ、引用マーク（"）をクリック。
4. 表示される引用形式の中から「BibTeX」を選択。
5. 表示されたBibTeXコードをコピーし、3_backmatter/references.bibファイルに貼り付け。

### 3. 文献管理ツール（Zotero, Mendeleyなど）を用いる

文献管理ツールとは、論文や書籍の情報を一元管理し、引用情報を簡単に取得できるソフトウェアである。代表的なツールにはZoteroやMendeleyがある。ソフトウェア内で作成した文献リストをBibTeX形式でエクスポートし、3_backmatter/references.bibとして保存できる。ソフトウェア内で更新された情報は、自動で.bibファイルに反映されるため、引用情報の管理が非常に楽になる。

**注意点** : ZoteroやMendeleyで日本語文献を管理する場合、デフォルトの設定では正しい「Citation Key」が生成されない。例えば、漢字を中国語として変換した謎の英語がデフォルトで出力される。
例：「有村(2020)」→「youcun2020」

日本語対応のための設定を含め、詳しくはコチラの記事を参考

- [日本語文献用のBetter BibTeXの引用キー（citation key）の設定](https://qiita.com/shiro_takeda/items/dfb857e69aa8ed2cc977)
- [Zoteroから参考文献リストを自動エクスポートする (PandocとZoteroで参考文献：前編)](https://zenn.dev/sky_y/articles/pandoc-advent-2020-bib1)

---

## 4. 各ディレクトリの説明

```{bash}
lualatex-kobe-template
├── 0_preamble
│   ├── macros.tex             # カスタムコマンド・マクロ定義
│   ├── packages.tex           # 使用するパッケージ
│   └── settings.tex           # ドキュメント設定
├── 1_frontmatter
│   ├── abstractEN.tex         # 英文要旨
│   ├── abstractJP.tex         # 和文要旨
│   ├── contents.tex           # 目次・図表目次
│   └── title.tex              # タイトル
├── 2_mainmatter
│   ├── chapter1.tex           # 第1章の内容
│   ├── chapter2.tex           # 第2章の内容
│   ├── chapter3.tex           # 第3章の内容
│   ├── chapter4.tex           # 第4章の内容
│   └── chapter5.tex           # 第5章の内容
├── 3_backmatter
│   ├── acknowledgements.tex   # 謝辞
│   ├── appendix.tex           # 付録
│   ├── citations.tex          # 参考文献リスト
│   ├── kucivil.bbx            # 引用文献リストの設定ファイル（神戸大学市民工学標準）
│   ├── kucivil.cbx            # 引用番号スタイルの設定ファイル（神戸大学市民工学標準）
│   └── references.bib         # 参考文献リスト
├── digest
│   └── settings.tex           # 要旨のドキュメント設定
├── figure                     # 図専用
├── log                        # ログファイルや中間生成物
├── output                     # 出力ファイル
├── table                      # 表専用
├── template                   # テンプレート関連
├── README.md                  # はじめに読むファイル
├── digest.pdf                 # 要旨の最終出力物(ignore)
├── digest.tex                 # 要旨のメインファイル
├── main.pdf                   # 本文の最終出力物(ignore)
├── main.tex                   # 本文のメインファイル（全体をまとめる）
└── settings.json              # VSCodeのsettingsファイル
```

---


## 5. 「、」「。」を「，」「．」で置き換える

日本語で理系論文を書く際、「、」「。」を「，」「．」で置き換えることが一般的である。
ありがちな変換方法として、「、」「。」を対象に検索&置換があるが、予め楽に変換できるように設定することをオススメする。

### 5.1 環境設定を使う

1. 「システム環境設定」を開く
2. 「キーボード」タブを開く
3. 「テキスト入力」を編集する
4. 「日本語ーローマ字入力」から「句読点の種類」を変更する

参考

- [M1 MacBookを買ったので設定しながらのメモ（２）](https://zenn.dev/dannchu/articles/d595b55f0864ab)

