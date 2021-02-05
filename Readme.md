# クラン内共有文書テンプレート

クラン内共有文書のテンプレート。

## 使い方

`document.tex` を書き換えてビルドを行う。ビルド手順は後述。

### 環境

`platex`, `dvipdfmx` を利用できる環境が必要。

環境がない場合は[W32TeX](https://www.ms.u-tokyo.ac.jp/~abenori/soft/abtexinst.html)等を用いて環境を構築する。

### ビルド

`dvi`, `pdf` ファイルのビルド方法を解説する。

#### 手動

##### Windows10

`build.bat` を実行するか、以下のコマンドを実行する。

```
platex document.tex
dvipdfmx document.dvi
```

##### その他

`build.sh` を実行するか、以下のコマンドを実行する。

```
platex document.tex
dvipdfmx document.dvi
```

#### VSCode

[Run on Save (emeraldwalk)](https://marketplace.visualstudio.com/items?itemName=emeraldwalk.RunOnSave)をインストールする。

##### Windows10

デフォルト設定の状態で保存時にビルドが行われる。

##### その他

`.vscode/settings.json` の `cmd` 項目を `build` から `./build.sh` に変更することで、保存時にビルドが行われる。

### 書き方

`\date` 内に制定時の文書番号を記述する場合は、 `\documentnumber` を使用しない。

章には `\section` を使用する。

節以下には `\subsection`、 `\subsubsection` や、 `enumerate環境` を用いる。

```latex
% enumerate環境の使い方
\begin{enumerate}[label=(\arabic*)]
    \item foo
    \item bar
    \begin{enumerate}[label=\aiu*.]
        \item hoge
        \item fuga
        \begin{enumerate}[label=(\aiu*)]
            \item a
            \item b
        \end{enumerate}
    \end{enumerate}
\end{enumerate}
```

附則内は `\kou` を用いて項分けする。
