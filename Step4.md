# OSSバケットの構築
###### 5min

注意：アカウントをお持ちでない方は本Stepを省略してください。

## Object Storage Service(OSS)
Alibaba Cloud上の仮想的なストレージサービスです。バケットと呼ばれる領域に、オブジェクトと呼ばれる画像・動画・ファイル等をアップロード、ダウンロードすることができます。バケットのデフォルトの公開範囲は外部非公開で、権限を持ったRAMユーザーやRAMロールでしかオブジェクトにアクセスができません。オブジェクトごとに有効期限付きの署名付きURLを発行すると、権限を持たないユーザーもオブジェクトにアクセスができます。バケット名はAlibaba Cloud全てでユニークである必要があります。月額でオブジェクトのアップロード総量とOSS APIの呼び出し回数に応じて課金がされます。

![OSS](img/oss.png)

## OSSバケットの構築
1. *ストレージと CDN* メニューの *Object Storage Servicee* を選択します
1. 右の *Bucket 管理* から *バケットの作成* をボタンを押下します
1. 次の通り入力します
    1. *バケット名* : `imagesearchhandson-任意の文字列`
    1. *リージョン* : 指定されたリージョンごとに選択してください
        1. *中国（香港）* : `China (Hong Kong)`
        1. *シンガポール* : `Singapore`
        1. *オーストラリア（シドニー）* : `Australia (Sydney)`
        1. *日本（東京）* : `Japan (Tokyo)`
    1. *ストレージクラス* : `標準ストレージ`
    1. *ACL* : `非公開`
    1. *リアルタイムログ照会* : `Disable`
1. *OK* ボタンを押下します

## 参考
- [OSS公式ドキュメント](https://jp.alibabacloud.com/product/oss)
- [Alibaba Cloud OSSの画像編集機能を使ってみよう](https://www.sbcloud.co.jp/entry/2017/07/05/alibaba-cloud-oss-object-storage-service-useful-use/)


[戻る](Step3.md) | [次へ](Step5.md)
