# Tutorial -Git チュートリアル-
gitの基本的な使い方をマスターしよう
コマンドが一杯出てくるけど、基本的にGUIツールを使うので全部覚える必要は無し

# Gitをインストールしよう
https://git-scm.com/downloads

ここからWindows用のgitクライアントをダウンロードしてインストール

https://qiita.com/manabu-watanabe/items/ecf1b434baf305adaa00

ここを参考にしてインストール

# 初期設定

完了したらGitBashを起動しましょう(デスクトップで右クリック->Git Bash Here)
![スクリーンショット 2020-10-21 173229](https://user-images.githubusercontent.com/15999897/96694414-6a6cd580-13c3-11eb-8896-4ac45e6b57c4.png)

そしたらいつもの黒い画面が開きます。

ちなみにこれはWindowsのコマンドプロンプトでは無く、Bashです

そしたら以下のコマンドを上から順に実行していきましょう

`git config --global user.name "githubに登録したユーザー名"`

`git config --global user.email "githubに登録したメールアドレス"`

`git config --global core.quotepath false`

これでgitの初期設定は完了

# 公開鍵・秘密鍵生成

次にgithubとssh接続するために公開鍵、秘密鍵を生成します。

同じくさっきのbashで作業していきます。

`mkdir ~/.ssh`

`cd ~/.ssh`

`ssh-keygen -t rsa -C 'githubに登録したメールアドレス'`

そしてEnterを3回押します。
(keyを生成するかの応答、パスフレーズ(空だと無し)、確認パスフレーズ(同じく空))

そして公開鍵を確認します。

`cat ~/.ssh/id_rsa.pub` (この際 id_rsaファイルは秘密鍵になるので絶対に公開しないこと)

`ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDjG108faFBVVKvsWqHwu2PtSW4Xfufwb52MAo7uYaT/XsMrAXNnUDnWbjzcXq+2kJWjmpZQ6l+j1YIwGyyupYx4CBL/Sel366kj81naTRDHRrlaaXr7jaPTVuWtDrRvMmJqB3zm9A4Mp819xD8HbtJGiJRIs2sgGABcC6KQLVjAgGkXSeYfEAFUVRJc6kH8s5PH26r2ORUby4/HeWXdEsHXS4wklCgmoD1PCL8GocoOW6mmwAOEGL8uuoQC4Hq5Mlhk90oTkwD7JhOUC3WODBif8CSOHMlOY5qaLf8LIEdFup1cdA1dazYJyRkPyhYQlI3wyyksJMIH0LhzNI2/fMLTMOyMHrFsZwckf+Xx1tOeQZiUMNIFZZOehjV0r1PhG5n+4BAkErm63zawybrGDXFM6dBjYUPkoJUuK6i6IY7YktlkkS9/flYfT/Sxdti5fnpPRaO+xqIIyl1Ble6wcW82SxAYkBy24r5HbKEH5Zvey7fTvw9sp3fsLKiJizLlfM= rusuke@t-net.ne.jp`

こんな感じで長いのが出てくるのでコピー

そしてDiscordの公開鍵に貼り付け


## githubに公開鍵を登録

さらに公開鍵をgithubに登録します。
1 Githubの右上メニューからSettingを選択

![スクリーンショット 2020-10-21 175013](https://user-images.githubusercontent.com/15999897/96696772-1fa08d00-13c6-11eb-83d2-9fb6f5624e96.png)

2 左の SSH and GPG keys を選択

![スクリーンショット 2020-10-21 175040](https://user-images.githubusercontent.com/15999897/96696777-20392380-13c6-11eb-844e-5388faa9c79f.png)

3 New SSH Keyを押す

![スクリーンショット 2020-10-21 175100](https://user-images.githubusercontent.com/15999897/96696783-216a5080-13c6-11eb-9194-3b4e535ed572.png)

4 Title 分かりやすい名前、Key さっきコピーしたキーを貼り付けて Add SSH keyを押す

![スクリーンショット 2020-10-21 175144](https://user-images.githubusercontent.com/15999897/96696796-24fdd780-13c6-11eb-9a77-73f4ec77af55.png)

これで登録されます。

これで一通り設定は完了です。

# このリポジトリをクローンしよう

このリポジトリを自分のPCへダウンロード(複製します)

PCに何も無い状態でダウンロードすることをクローン(clone)と言います

リポジトリを起きたいディレクトリを作成して(MyDocumentにSchoolProjectみたいなディレクトリを作っておきましょう(なるべくパスに日本語を含まないように))

作成したディレクトリをエクスプローラーで開き、エクスプローラー上で右クリック。

デスクトップと同じようにGit Bash Here が出てくるのでクリック。

こうすることでカレントディレクトリをそのディレクトリとして開けます。

`git clone git@github.com:NekomimiMofuMofu/Tutorial.git`

と実行

もし鍵作成時にパスフレーズを登録していればこの段階で聞かれるので入力

`Are you sure you want to continue connecting (yes/no/[fingerprint])?`

と出てきたら`yes`と入力してEnter

そうするとクローンが始まります。

そしたらエクスプローラーにフォルダが作成されていて、このREADME.md ファイルがあればクローン成功です。

## リポジトリのpull
gitのリポジトリはcloneした時点で、githubサーバー(リモートリポジトリ)と、各自のPC内(ローカルリポジトリ)に別々に存在することになる。

リモートリポジトリが変更した際にその変更を自分のPCに持ってくることをpullコマンドで行える。

`git pull`

コマンドを実行することでpullが可能

# ファイルを追加しよう

まずリポジトリ内に自分のファイルを追加しよう。

リポジトリをクローンしたディレクトリ(`README.md`ファイルがあるディレクトリ)に自分の名前のディレクトリを作成しよう。

これよりリポジトリをクローンしたディレクトリを`@`としてパスに表記するよ

僕の環境では `E:\Users\Raiti\Document\School`にクローンしたので`@\Tutorial\Raiti\test.txt`は`E:\Users\Raiti\Document\School\Project\Tutorial\Raiti\test\txt`を指すことになるよ

その中に`test.txt`というテキストファイルでも作って中身も適当に書き込もう。`@\Tutorial\各自名前\test.txt`

特に内容思いつかなきゃ`hogehoge`とでも書いておいて

そしたら`@\Tutorial\`をエクスプローラーで開いて右クリックでいつもの黒いGitBashを開いて

`git add ./各自名前/test.txt` 

を実行

これでさっき作成したファイルがリポジトリ管理に追加されたよ。

ちなみに、

`git add *`

と実行するとリポジトリ内のフォルダにある全てのファイル

`git add ./各自名前/*`

と実行すると指定されたディレクトリ以下にあるすべてのファイル

がリポジトリ管理に追加されるよ。(ただし`git add` は管理に追加以外に機能があるからおすすめはしない

# コミットしよう

`git commit -m "コミットメッセージ"`

でコミットができるよ

コミットメッセージを

> (自分の名前)の初めてのコミット

としてコミットしてみよう。

コミットメッセージは日本語でもOK

こうすることでファイルを変更した履歴を残せる

逆に、過去のコミットに戻すこともできるので、変更してバグが生まれた!!

となっても戻せるから安心!

# プッシュしよう

さっきコミットしたけど、これはあくまでも、ローカル(自分のPC内)にしか記録されていない

リモート(サーバー側)の方には記録されてないから、その記録を送信してあげる必要がある

`git clone` PC内に何もない状態で新しくリポジトリをサーバーから取ってくる

`git pull` PC内にブランチがある状態でサーバー側の最新の状態に更新する

がサーバーとのやり取りであったけどもう一つ

`git push` ローカルでの変更をサーバー側にアップロードする。

コマンドがある

`git push origin master`

と実行してみよう。

これでコミットした内容がサーバーにアップロードされた。
