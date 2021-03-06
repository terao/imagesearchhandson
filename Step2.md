# RAMユーザーの作成
###### 10min

注意：アカウントをお持ちでない方は本Stepを省略してください。

## Resource Access Management(RAM)
Alibaba Cloudリソースをアカウントに代わって他のユーザーやAlibaba Cloudサービスが使えるようにするサービスです。

![RAM](img/ram.png)

## RAMユーザー
アカウントは全てのAlibaba Cloudリソースの操作権限を持っています。アカウント情報を複数の人で使い回すことは、使用者に過剰な権限を与えることになり、誤操作をまねきます。また、誰がどの操作をしたのかがわからなくなります。そのため、必要な人に必要な権限のみを与えるRAMユーザーを使用します。

本ハンズオンでは2つのRAMユーザーを使用します。
- **環境構築をするユーザー**
  - `AdminUser`
- **画像検索を行うアプリ**
  - `ImageSearchHandsOnUser`

## `AdminUser` の作成
1. Alibaba Cloudコンソールにログインします
1. *マネジメント* メニューの *Resource Access Management* を選択します
1. 左のメニューから *ユーザー* を選択します
1. 右上の *新規ユーザー* ボタンを押下します
1. 次の通り入力します
    1. *ログイン名* : `AdminUser`
1. *OK* ボタンを押下します
1. ユーザー一覧から `AdminUser` を選択します
1. *Web コンソールログイン管理* の *コンソールへのログインの有効化* を選択します
1. 次の通り入力します
    1. *新しいパスワード* : `任意の文字列`
    1. *パスワードの確認* : `任意の文字列`
    1. *次回ログイン時にパスワードのリセットが必要* : **チェックを外す**
1. *OK* ボタンを押下します
1. 左のメニューから *権限付与ポリシー* を選択します
1. 右上の *権限付与ポリシの編集* ボタンを押下します
1. `AdministratorAccess` ポリシーを選択し、 `>` ボタンを押下します
1. *OK* ボタンを押下します

## `AdminUser` の使用
1. 左のメニューから `<` ボタンを押下します
1. 左のメニューから *設定* を選択します
1. *ユーザのエイリアスの設定* タブを選択し、 *RAM ユーザーログイン* をメモします
    1. *RAM ユーザーログイン* 例 : `http://signin-intl.aliyun.com/ <<アカウントID>>/login.htm`
1. 右上の絵文字アイコンを押下し、*サインアウト* を押下します
1. 3.でメモした *RAM ユーザーログイン* にアクセスします
1. 次の通り入力し、ログインします
    1. *ユーザー名* : `AdminUser@<<アカウントID>>`
    1. *パスワード* : `任意の文字列`

## `ImageSearchHandsOnUser` の作成
以降、全てのAlibaba Cloud上の操作を `AdminUser` にて行います
1. *マネジメント* メニューの *Resource Access Management* を選択します
1. 左のメニューから *ユーザー* を選択します
1. 右上の *新規ユーザー* ボタンを押下します
1. 次の通り入力します
    1. *ログイン名* : `ImageSearchHandsOnUser`
    1. *このユーザーの AccessKey を自動生成* : **チェックをつける**
1. *OK* ボタンを押下します
1. *AK 情報を保存* をボタンを押下します
1. アクセスキーとシークレットキーがCSVファイルでダウンロードされるので、保管します
1. 右上 `×` ボタンを押下し、モーダルを閉じます
1. 左のメニューから *権限付与ポリシー* を選択します
1. 右上の *権限付与ポリシの編集* ボタンを押下します
1. 次のポリシーを選択し、それぞれに対して `>` ボタンを押下します
    1. `AliyunImageSearchFullAccess`
    1. `AliyunOSSFullAccess`
1. *OK* ボタンを押下します

## 参考
- [RAM公式ドキュメント](https://jp.alibabacloud.com/product/ram)
- [プライマリアカウントのセキュリティのベストプラクティス](https://jp.alibabacloud.com/help/doc-detail/93245.htm)


[戻る](Step1.md) | [次へ](Step3.md)
