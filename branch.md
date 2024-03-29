# ブランチ
ブランチとは、分岐することで複数の機能の同時並行で開発可能な仕組み。
ブランチはコミットを指すポインタであり、HEADとは現在作業中のブランチを指す。

## ブランチの作成

```
git branch ブランチ名
```

上記コマンドでブランチを作成できる。

```
git branch
```

上記コマンドで存在するブランチを確認できる
## コンフリクト
コンフリクトとは、同じ個所を異なる内容の編集をした場合に、どちらの変更内容を優先させるかを決めるマージ方法  

## コンフリクトの解決方法
1. コンフリクトしたファイルの内容を書き換える
2. << や == や >>の記述を削除する

## コンフリクトを防ぐ方法
* 複数人で同じファイルを変更しない
* pullやmergeする前に変更中の状態をなくしておく(commitやstashをしておく)
* pullするときは、pullするブランチに移動してからpullする


# ブランチを使った開発手法
masterブランチをリリース用ブランチに、開発はトピックブランチを作成して進めるのが基本  
開発した機能をmasterブランチにトピックブランチからマージする  

## プルリクエスト
自分の変更したコードをリポジトリに取り込んでもらえるよう依頼する機能

## プルリクエストの手順

## リベースとは
履歴をきれいにすることができる。
リベースでは、履歴が一直線か、マージして親コミットが複数あるかの違い

## リベースでやっていけないこと
GitHubのコミットをリベースしてはいけない

プッシュしていないローカルの変更にはリベースを行い、  
プッシュした後はマージを使う。

コンフリクトしそうならマージを使う。  
