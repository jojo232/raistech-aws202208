# 第2回 バージョン管理システムについて

## 1. 種類
1. Git gitHub

2. SVN



## 2. 特色<br>
1. git<br>
●メリット<br>
リモートリポジトリとローカルリポジトリに分かれており、複数の履歴保持の場所を持つ点がチーム開発に向いております。<br>
●デメリット<br> 
分散型ではないため、バージョン管理するリポジトリ(データの貯蔵庫)は単一です、リポジトリが破損すると今までのデータが消えます。<br>
しかし、スナップショットでバックアップを容易に取得できる為、復元は容易です。<br>




2. SVN<br>
●メリット<br>
リモートリポジトリとローカルリポジトリに分かれており、複数の履歴保持の場所を持つ点がチーム開発に向いております。<br>
●デメリット<br> 
Gitと違って分散型ではなく、チーム開発に向いていない為、最近では使用されていない。<br>



## 3. Markdown<br>
●HTML(Webページを表示させる言語)が使用できなくても、簡単な記号の修飾で同じような見た目を実現できる。<br>

●書き方<br>
見出しは、#、番号リストが1、番号なしリストは*または-で書きます。<br>



## 4. コマンド内容<br>
●実行コマンド<br>
mkdir (ファイル名)　ファイルを作成<br>
git config --global user.name “名前”<br>
git config --global user.email "メールアドレス"<br>
git config --global -l<br>
git init (作成したファイル/以下にあるファイルはGitでバージョン管理できるようになります。)<br>
git add README.md (git addでステージ　ワークツリーからインデックスへ)<br>
git commit -m "first commit"　(インデックスからローカルリポジトリへ)<br>
git branch -M main　(ローカルリポジトリのブランチ名を変更する。)<br>
git push -u origin main　(登録したリモートリポジトリにプッシュする)<br>
git remote add origin https://github.com/ユーザ名/first-git.git<br>
※mainブランチを作成<br>

git branch lecture02<br>
git checkout lecture02<br>
git add lecture02.md<br>
git commit -m "lecture02.md追加"<br>
git remote add origin https://github.com/ユーザ名/first-git.git<br>
git branch -M lecture02<br>
git push -u origin lecture02<br>


## 5. 説明<br>
git init<br>

- 現在のフォルダー内にリポジトリを作成し、ワークツリーとインデックスを用意する

git add ファイル名 <br>

- 新規追加や変更されたファイルを選択し、ステージさせる。

git commit -m ◯◯　<br>

- ステージされた変更をコミットする。

git status<br>

- ワークツリーとインデックス状況をファイル単位で確認する。

git diff	<br>

- ワークツリーとインデックスを比較して、その差分を表示する。

git log<br>
- 過去のコミットを確認する。


git remote add origin リモートリポジトリURL<br>
- ローカルリポジトリにリモートリポジトリを登録する。<br>

git remote -v	<br>
- ローカルリポジトリに登録されたリモートリポジトリの一覧を表示する。<br>

git branch -M main	<br>
- ローカルリポジトリのブランチ名をmainに変更する<br>

git push origin main　<br>
- 登録したリモートリポジトリへプッシュする。<br>

git push -f origin main<br>
- git pushに-f オプションをつけると、強制的にリモートリポジトリをローカルリポジトリで上書きすることができます。<br>
- しかし、大変危険なコマンドだから、チーム開発では慎重に行いましょう。<br>

git clone<br>
- git clone リモートリポジトリ.git コピー先フォルダ名<br>

git log --grep first<br>
- --grepを使用して、firstという文字列がコミットメッセージに入っているコミットを検索します。<br>

git checkout(git checkout -- list.html)<br>
- ワークツリーの変更を取り消したい場合に使用するコマンド<br>

git reset HEAD list.html<br>
- インデックスからワークツリーに戻し方法<br>

git commit --amend -m "メッセージ書き直し"<br>
- コミットメッセージを書き直したくなった時は、--amendオプションを使用するとすぐに書き直せる。<br>

git add 追加し忘れたファイル<br>
git commit --amend -m "メッセージ"<br>
- 追加すべきファイルを忘れてコミットしてしまった場合、<br>
- この場合は、そのままもう一度git addで追加し忘れたファイルを追加し、git commit --amendを実行しれば、<br>
- 直前のコミットが書き換えられ、忘れたファイルが追加された形で再コミットされます。<br>


### 過去のコミットまで戻る<br>
git show リビジョン番号:ファイル名<br>
・過去のコミット時点でのファイル内容を取得する。<br>
git log --oneline<br>
・まずは、コミットの履歴を確認する。<br>
git reset リビジョン番号<br>
・過去のコミット7d97d52まで戻ります。つまり、9f943bcのコミットを破棄し、元に戻ります。<br>
git reflog<br>
・リセットを元に戻す、間違ってgit resetしてしまった場合に使用。<br>

## 6. 補足<br>
●originとは<br>
自分にローカルリポジトリと同じリモートリポジトリを、originと言う名前にするのが習慣となっています。<br>
理由は、git cloneコマンドでリモートリポジトリをローカルリポジトリへコピーしてくると自動的にリモートリポジトリの名前がoriginと付けられるからです。<br>
●--オプションをつける理由<br>
実は--オプションをつけなくても、git checkout ファイル名で多くの場合は正しく動作します。<br>
ただし、--オプションをつけた方がより誤操作を心配することなく実行できます。なぜなら本来であればそこにブランチ名を指定する形式になっているからです。<br>
※注意<br>
git checkout -- ファイル名コマンドは、危険なコマンドです。ファイルの変更は跡形もなくなります。もう変更していた状態に戻せませんので、くれぐれも注意しましょう。<br>
●git initを使用すると下記のように構成される<br>
ワークツリー → インデックス ローカルリポジトリ<br>
●git reset<br>
git resetは危険なコマンドになります。その場合は、--hardオプションをつけた場合です。<br>
--hardをつけると、完全に変更を削除します。--haedオプションを付けない場合にはインデックスからワークツリーへ変更が戻るだけです。<br>
●--シリーズ<br>
--soft<br>
・戻した分のコミット内容をインデックスに反映する<br>
--mixed<br>
・オプションなしと同じ動作で、戻したコミット内容をワークツリーに反映する。<br>
--hard<br>
・戻した分のコミット内容は完全に破棄される。<br>
