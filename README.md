# かんたんMarkdown
かんたんMarkdownは完全に単一のHTMLファイルで動作するMarkdownエディタ・プレビューアです。



## 使い方
次のURLに、もう少し詳しい説明があります。

http://tatesuke.github.io/KanTanMarkdown/



## ビルド方法
かんたんMarkdownをカスタムされる方向けに、ビルド方法を説明します。


### Grunt必須
かんたんMarkdownはGruntでビルドを行っています。開発環境にGruntを未導入なら、まずGruntを導入してください。Node.jsをインストールした後、次のコマンドでgrantを導入してください。

~~~
npm install -g grunt-cli
~~~

プロジェクトのルートディレクトリに移動して、次のコマンドで必要ファイルをインストールすれば準備完了です

~~~
npm install
~~~

### ビルド
プロジェクトのルートディレクトリに移動して、``grunt build``コマンドを実行すると、必要なファイルを圧縮・結合した後、``dist/``ディレクトリ配下にビルドしたファイルが配置されます。

~~~
grunt build
~~~

配置されるファイルは次の5つです。

* ktm-dev.html
* ktm-lite.html
* ktm-std.htm
* ktm-full.html
* kantanUpdate.js

``grunt build-dev``コマンドだと、開発用の``ktm-dev.html``のみビルドされます。

単に``grunt``のみで実行すると、``src``ディレクトリを監視し、ファイルの変更があると自動的に``ktm-dev.html``をビルドするようになります。

### ディレクトリ構成
参考のために、ディレクトリ構成を示します。

```
.
│  .gitignore
│  Gruntfile.js
│  package.json	
│  README.md
│  
├─dist------------------------ビルドしたファイルが格納されるディレクトリです。
│  │  kantanUpdate.js---------アップデート機能用のjsファイルです。
│  │  ktm-dev.html------------開発向けの非圧縮のかんたんMarkdownです
│  │  ktm-full.html-----------リリース向けのfullエディションのかんたんMarkdownです
│  │  ktm-lite.html-----------リリース向けのliteエディションのかんたんMarkdownです
│  │  ktm-std.htm-------------リリース向けのstandardエディションのかんたんMarkdownです
│  │  
│  └─temp--------------------ビルド時の一時ファイルです
│                  
├─node_modules
└─src-------------------------簡単Markdownのソースを格納するディレクトリです。
    │  ktm.html----------------かんたんMarkdownのHTML部分です
    │  
    ├─css---------------------かんたんMarkdownのCSSを格納するディレクトリです。
    │      kantan.css----------かんたんマークダウンのCSSです。
    │      hljs.css------------コードハイライトのCSSです。
    │      previewer.css-------プレビュー領域用のCSSです。
    │      
    └─js----------------------かんたんMarkdownのjsソースを格納するディレクトリです
            kantanEditor.js-----テキストエリアを拡張するjsです
            kantanMarkdown.js---かんたんMarkdownのjsです
            ・・・--------------その他かんたんMarkdownが利用するjsです。
```



## リリースノート

### v1.20160316.01

#### バグ修正
* IEでアップデート機能がうまく動いていなかった問題を修正
* モード切替時にプレビューアが先頭に戻ってしまうバグを修正

### 機能追加・変更
* JavaScriptが向こうの端末でも、Mardownは表示可能にした
* スクリーンショット取り込み添付機能を追加
* 画像簡易編集機能追加

### 内部改善
* 画像をblob urlでキャッシュすることにより、画像の読み込みを高速化した


### v1.20160305.01

#### バグ修正
* 編集／閲覧モードを切り替えるとプレビューのスクロールバーが一番上に戻ってしまう問題を修正
* 保存したファイルを開くと添付ファイルの名前変更、削除ができなかった問題を修正
* ファイルドラッグ時に枠が出なくなっていたのを修正
* ファイル名が重複を許さなくした
 * 同名のファイルを添付した時の仕様が曖昧になってしまうため

#### 機能追加
* ``attach:``記法を追加した。これにより、添付画像を表示するのにname属性でなくsrc属性を利用できるようになった。
* 添付ファイルをダウンロードできるようにした

### v1.20160229.01

#### 機能追加・修正
* CSSカスタマイズ機能を追加

### v1.20160227.03

#### 機能追加・修正
* オンラインメニューのバージョン表記にエディションも併記されるようにしました
 * (今回はアップデート機能のテストのための小規模なリリースです)

### v1.20160227.02

#### バグ修正
* アップデートするとエディション情報が消えてフルエディションになってしまう問題を修正

### v1.20160227.01

#### バグ修正
* Firefoxで閉じるボタンなどの文言が変わらない問題を修正

#### 機能追加・修正
* アップデート機能を追加(実験的機能)

#### 内部改善
* js圧縮など

### v1.20160221.01

#### バグ修正
* プレビューを隠しているのに保存すると表示されてしまう問題を修正
* Home, End, PageUp, PageDownでのカーソル移動後のUndoの挙動を改善
* IEでの保存の挙動を改善
* かんたんMarkdownをインポートした時に自動プレビューされない問題を修正
* IEでプレビュー時にborderが消えてしまう問題を改善
* Firefoxでcodeが長すぎるとスクロールバーが表示されるのを改善

#### 機能追加・修正
* 見出しリンク機能を追加
* 閲覧・編集モード切り替え時のプレビューの位置を改善

### v1.20160216.01
#### 機能追加・修正
* オンラインメニューを追加しました。
* 旧バージョンインポート機能を追加しました
* 編集モードから閲覧モードに切り替えたとき、プレビューにフォーカスが当たるようにしました。
 * これにより、閲覧モード切替時にキーボードでプレビューのスクロールが可能になります。
* 誤解をまねくので、「同期」という文言を「プレビュー」に修正しました。
* 

#### 内部改善
* シンタックスハイライト・シーケンス図・フローチャートのjsを削除しても正しく動くようにしました
 * →リリース作業の容易化のため

### v1.20160214.03

#### バグ修正
* Firefoxでタイトルがundefinedになるバグを修正
* 保存時のモードによって次開いた時の初期状態が変わってしまうバグを修正
* 閲覧専用モードなのに編集モードに切り替わってしまうバグを修正

### v1.20160214.02

#### 機能追加・修正
* エディションを導入しました
 * ファイルサイズが最も小さいLiteエディション
 * 中くらいのStandardエディション
 * 最も大きいFullエディション

#### 内部改善
* jQuery依存排除により、Fullエディションでファイルサイズを約100Kb削減しました

### v1.20160214.01

#### バグ修正
* ctrl+s(cmd+s)で保存しても、保存されていないことになるバグを修正

#### 機能追加・修正
* エディタに変更があるとタイトルに「*」マークを付ける機能を追加
* 空のファイルは初期状態を編集モードにした

### v1.20160213.01

#### バグ修正
* キャレットが画面外に出てもスクロールバーが追従しないことがある問題を解決
* 特定の条件でキャレットが想定外の位置に飛んでしまう問題を解決

### v1.20160209.01

#### バグ修正
* Ctrl+Vを押しっぱなしにして連続ペーストした時にUndoが効かなくなる問題を解決

#### 機能追加・修正
* 初期状態では添付ファイル領域を表示させないようにした
* ファイルをドロップした時に添付ファイル領域を開くようにした

### v1.20160208.01

#### 仕様変更
* 「添付ファイルを隠す・表示する」、「プレビューを隠す・表示する」のショートカットキーをAltに変更  
Ctrl+→などは普通カーソル移動に割り当てられているため

### v1.20160207.01

#### バグ修正
* 再編集時1単語目でUndoするとカーソルが1文字目に戻ってしまう問題を修正(#66)


### v1.20160206.01

#### バグ修正
* コード中の<html>など特定のタグ文字列が保存時に消えてしまう問題を修正

#### 機能追加
* SafariやIE9など、保存ができない端末向けに「閲覧専用モード」を設けた
* オートインデントを導入
* 行選択でのインデント、アウトデントを導入
* MacOS向けのショートカットキーを追加

#### 内部修正
* テキストエリア周りのコードを改善

### v1.20160205.01

#### バグ修正
* IE, Firefoxにおいてtabキーが効かなくなっていたのを修正

### v1.20160204.02

#### バグ修正
* undoの挙動が不安定だったのを修正。これに伴いオートインデント機能を停止した

### v1.20160204.01

#### バグ修正
* 文章が横幅を超えてしまった時横スクロールバーが出てしまっていたが、改行するようにした

####機能追加・改善
* 閲覧モード時にプレビューの表示・非表示を切り替えられるようにした。
* エディタにオートインデント機能を追加した


### v1.20160203.01

#### 機能追加・改善
* ESCキーでを編集・閲覧モード切り替えられるようにしました
* 添付ファイル領域を表示非表示できるようにしました

#### 内部改善
* 一部のコードを改善しました

### v1.20160202.01
#### バグ修正
* firefoxでスクロールバー固定が効いていなかったのを修正
* 添付ファイル操作後に画面を閉じるとき、警告が出ていなかったのを修正

#### 機能追加、改善

* noscriptを追加

### v1.20160201.02

####バグ修正
* Firefoxで保存できていなかった致命的なバグを修正
* 閲覧モード時に保存をするとプレビューが真っ白になってしまう問題を修正

### v1.20160201.01

#### バグ修正
* IEで動作しなくなっていたバグを修正
* 横幅の大きなシーケンス図、フローチャットを描画したときにスクロールバーが二重に出てしまう問題を解決
* Firefoxで編集モード時にスクロールバーが二重に出ている問題を解決

#### 改善
* 閲覧モード時のレイアウトを改善しました

### v1.20160130.01

####バグ修正
・初期起動時にシンタックスハイライトが効いていないバグを修正

### v1.20160129.02

#### 仕様変更
* ファイルサイズの肥大化を防ぐため、保存時previewerの中身を削除するようにした

### v1.20160129.01

#### バグ修正
* 保存するとエディタやプレビューのスクロールバーが動いてしまう問題を解決
* ファイル末尾に不要タグが溜まっていく不具合を修正

#### 機能追加
* 自動更新のon/off機能を追加した

### v1.20160128_03

#### バグ修正

* 印刷時レイアウトが激しく崩れる問題を修正

### v1.20160128_02

#### 改善
* 閲覧モード時に横幅が大きすぎたので改善 

### v1.20160128_01

#### 改善
* h1がなくなった時のタイトルを[無題]にした

#### 機能追加
* info, warn, alertクラスを使うことで、青、黃色、赤枠を使えるようにした
* sequenceクラス,flowクラスを使うことでjs-sequence-diagramsとflowchart.jsを利用できるようにした


### v1.20160127_03

#### バグ修正
* スクロールバーが最下部で固定されないバグを修正

### v1.20160127_02

#### 改善
* プレビュー領域が最下部にある時は、内容更新後も最下部に固定するようにした
 + テキストエリアとプレビューのスクロールバー同期は難しそうだだったのでその代替案として
* 添付ファイルを削除する前にプロンプトを表示するようにした
* ソースコードハイライトの自動言語判定をやめ、手動指定にした

### v1.20160127_01

#### バグ修正
* 画像名を変更すると画像を表示できなくなっていたのを修正
* 画像名変更時にid属性から値を引っ張ってきているのを修正
* hrが表示されない不具合を解決

#### 機能追加、改善
* シンタックスハイライト導入
* テーブルの罫線が2重になっていたのを修正

#### 内部改善
* 画像をscriptタグに埋め込むとき、画像名はname属性に埋め込むようにした
* js内でファイルドラッグ時のスタイル適応をハードコーディングしていたのをやめた

### v1.20160126_01
* 保存のたびに</body>の前の改行が増えていくバグを修正
* MITライセンスとしました
* タブキーでタブが入力されるようにした

### v1.20160125_01
* ファイルを開いた時点では閲覧モードになるようにした
* 初期モードは閲覧モードにした
* 複数ファイル添付時の名前がおかしい問題を解決
* IEでも保存できるようにした

### v1.20160124_01
* リリース