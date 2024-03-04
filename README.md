# apptainer_emacs28

## Build

To create a container image file, run the following command

``` sh
git clone https://github.com/oogasawa/apptainer_emacs28
cd apptainer_emacs28
sudo apptainer build apptainer_emacs28.sif emacs28.def
```

## Installing Doom Emacs

As per the official Doom Emacs github repository, delete the ~/.emacs.d directory and execute the following commands

``` sh
git clone --depth 1 https://github.com/doomemacs/doomemacs ~/.emacs.d
```

Run the `doom install` command as follows, noting that the `EMACS` environment variable must be defined.

``` sh
alias emacs="apptainer exec apptainer_emacs28.sif emacs"
export EMACS="apptainer exec apptainer_emacs28.sif emacs"
~/.emacs.d/bin/doom install
```

When this is executed, the output will be as follows.

``` sh
$ ~/.emacs.d/bin/doom install
Installing Doom Emacs!

- Skipping ~/.doom.d/ (already exists)
  - Skipping init.el (already exists)
  - Skipping config.el (already exists)
  - Skipping packages.el (already exists)
Generate an envvar file? (see `doom help env` for details) (y or n)
[1]+ Stopped~/.emacs.d/bin/doom install 
```

This is where it waits for input and becomes a background process. If you run `fg 1` to return to foreground processing and then type y, it will continue to run.

``` sh
$ fg 1
~/.emacs.d/bin/doom install
y
> Generating envvars file
  ✓ Generated ~/.emacs.d/.local/env
Installing plugins
> Installing straight...
> Installing packages...
  > Updating recipe repos...
  > Cloning use-package... Cloning use-package... > Cloning emacsmirror-mirror...
  - Checked out use-package: a6e856418d2ebd053b34e0ab2fda328abeba731c
  > Building use-package...
  > Building use-package > Building bind-key...
  > Building use-package...
  > Cloning auto-minor-mode...
  - Checked out auto-minor-mode: 17cfa1b54800fdef2975c0c0531dad34846a5065
  > Building auto-minor-mode...
  > Cloning gcmh...
  - Checked out gcmh: 0089f9c3a6d4e9a310d0791cf6fa8f35642ecfd9
（Omit the following)
```

This completes the installation of doom emacs.

## Running doom emacs

Define an alias and run doom emacs as follows to start doom emacs.

``` sh
alias emacs="apptainer exec apptainer_emacs28.sif emacs"
emacs -nw
```


---

## ビルド

コンテナイメージファイルを作成するには以下のコマンドを実行する。

``` sh
git clone https://github.com/oogasawa/apptainer_emacs28
cd apptainer_emacs28
sudo apptainer build apptainer_emacs28.sif emacs28.def
```


## Doom Emacsのインストール

[Doom Emacsの公式 github リポジトリ](https://github.com/doomemacs/doomemacs#install)にあるとおり、
`~/.emacs.d`ディレクトリを削除した上で、以下のコマンドを実行する。

``` sh
git clone --depth 1 https://github.com/doomemacs/doomemacs ~/.emacs.d
```

以下のようにして`doom install`コマンドを実行する。`EMACS`環境変数を定義することが必要であることに注意。

``` sh
alias emacs="apptainer exec apptainer_emacs28.sif emacs"
export EMACS="apptainer exec apptainer_emacs28.sif emacs"
~/.emacs.d/bin/doom install
```

これを実行すると、以下のような出力になる。

``` sh
$ ~/.emacs.d/bin/doom install
Installing Doom Emacs!

- Skipping ~/.doom.d/ (already exists)
  - Skipping init.el (already exists)
  - Skipping config.el (already exists)
  - Skipping packages.el (already exists)
Generate an envvar file? (see `doom help env` for details) (y or n)
[1]+  Stopped~/.emacs.d/bin/doom install 
```

ここで入力待ちとなるところでバックグラウンド処理になってしまう。
ここで`fg 1`を実行してフォアグラウンド処理に戻したところで`y`を入力すると続きが実行される。


```
$ fg 1
~/.emacs.d/bin/doom install
y
> Generating envvars file
  ✓ Generated ~/.emacs.d/.local/env
Installing plugins
> Installing straight...
> Installing packages...
  > Updating recipe repos...
  > Cloning use-package... emacsmirror-mirror...
  - Checked out use-package: a6e856418d2ebd053b34e0ab2fda328abeba731c
  > Building use-package...
  > Building use-package > Building bind-key...
  > Building use-package...
  > Cloning auto-minor-mode...
  - Checked out auto-minor-mode: 17cfa1b54800fdef2975c0c0531dad34846a5065
  > Building auto-minor-mode...
  > Cloning gcmh...
  - Checked out gcmh: 0089f9c3a6d4e9a310d0791cf6fa8f35642ecfd9
（以下省略)
```

これでdoom emacsのインストールが完了する。

## doom emacsの実行

エイリアスを定義して、以下のように実行するとdoom emacsが起動する。

``` sh
alias emacs="apptainer exec apptainer_emacs28.sif emacs"
emacs -nw
```
