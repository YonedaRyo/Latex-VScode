# ローカルでLatex環境を作成したい時に
このレポジトリはWindows環境でVScodeをコードエディタとした際のLatex環境構築を前提としています

## VScodeのインストール
ここは既に使っていると思うので割愛します．．    
一応ここからインストールできます．  
[Visual Studio Code](https://code.visualstudio.com/)

## TeX Liveのインストール
[TeX Live](https://www.tug.org/texlive/acquire-netinstall.html)をこのサイトからinstall-tl-windows.exeをクリックしてインストールする
![スクリーンショット 2023-11-09 12 30 05](https://github.com/YonedaRyo/Latex-VScode/assets/107024163/821013b0-da98-41f9-8e83-c76bce165f83)

インストールされた.exeファイルをクリックし，TeX Liveのインストールを始める 
![.exe実行](https://github.com/YonedaRyo/Latex-VScode/assets/107024163/e56ad00c-bbac-400d-b794-3ffdeda73a79)
警告文が出ると思いますがそのまま無視してもらって大丈夫です．少し待てば次の画像の画面に遷移します．  
![インストール](https://github.com/YonedaRyo/Latex-VScode/assets/107024163/b1f0c689-be40-4bb6-a8b8-0ba96bb318b4)
何も変える必要なければ，インストールをクリックしてインストールを開始します．完了まで1時間程度かかります．．．
<img width="346" alt="3" src="https://github.com/YonedaRyo/Latex-VScode/assets/107024163/f8937a6a-98fe-4ed2-b620-534ef5668921">
これで一旦TeX Liveのインストールは完了  
### LaTeXの起動確認
コマンドプロンプト上でlatexと打ってみて，画像のようになればOK!
<img width="464" alt="4" src="https://github.com/YonedaRyo/Latex-VScode/assets/107024163/8cbb1709-08a5-4b1a-b7d5-026e18c6a14a">

## VScodeの拡張機能のインストール
![vscode拡張](https://github.com/YonedaRyo/Latex-VScode/assets/107024163/562d51db-f874-47b3-9558-331a53332530)
LaTeX Workshopをインストールする
LaTeX Workshopを入れて.texのファイルを開くと左側にTEXと書かれた拡張機能が追加されます.
ここまで出来れば，ローカル環境でVScodeをコードエディタとして使用したLaTeXの基本環境が構築できました！！

# これをしておくと便利なこと
## VScodeのsettings.jsonを書き換えてLaTeXのレシピを作っておく
何も設定していないと，せっかく環境作っても便利じゃない．．  
そこで，自分がよく使うLaTeXレシピを作っておいて１クリックでコンパイルする．  
例えば，修論や卒論ではbibtexを使うと便利なのでそれ用のレシピとか  
```
"latex-workshop.latex.tools": [
        {
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ],
            "name": "bibtex",
        },
        {
            "command": "ptex2pdf",
            "args": [
                "-interaction=nonstopmode",
                "-l",
                "-ot",
                "-kanji=utf8 -synctex=1",
                "%DOC%.tex"
            ],
            "name":"ptex2pdf",
        },
],
 "latex-workshop.latex.recipes": [
 {
    "name": "ptex2pdf",
    "tools": [
        "ptex2pdf"
    ]
 },
 {
    "name": "ptex2pdf -> pbibtex -> ptex2pdf*2",
    "tools": [
        "ptex2pdf",
        "pbibtex",
        "ptex2pdf",
        "ptex2pdf"
    ]
 },
]
```
latex-workshop.latex.toolsにはLaTeXツールを，latex-workshop.latex.recipesにはレシピを記述しておく．  
"name": "ptex2pdf -> pbibtex -> ptex2pdf*2"はbibtexを使うときによく使います．ただし，pLaTeXも古いのでその内ダメになると思う．
めんどくさかったら，僕が使うレシピをまとめたsettings.jsonがあるので使ってください．

## 自分がどのLaTeXエンジンを使っているか知りたい時
hello.texを使用して確認することができます．
自分がよく使うのはplatex+dvifmxの組み合わせです．
![hikaku](https://github.com/YonedaRyo/Latex-VScode/assets/107024163/816e90b6-f8d7-4df3-ab6e-e257ffaa77c0)
