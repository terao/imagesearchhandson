# ECSの構築
###### 15min

注意：アカウントをお持ちでない方は本Stepを省略してください。

## Elastic Compute Service(ECS)
Alibaba Cloud上の仮想的なサーバーです。CPU・メモリ・ディスク・通信速度等のスペックを自由に選択できます。スペックに比例した1時間ごとの従量課金と月額サブスクリプション料金体系があります。

## セキュリティグループ
ECSに設定できるファイアウォールサービスです。特定のIPやネットワークからの受信を許可・拒否することと特定のIPやネットワークへの送信を許可・拒否させることができます。
Webアプリのインフラ構成として、外部からの443ポートへの通信を許可するWebサーバーと、Webサーバーからの通信のみを許可するWebアプリサーバーと、Webアプリサーバーからの通信のみを許可するデータベースサーバーの構成が良く取られます。本ハンズオンではスムーズにImage Searchを使用してもらうために、外部からの22ポートと8888ポートを通信を許可するセキュリティグループをECSサーバーに設定します。

![ECS](img/ecs.png)

## セキュリティグループの作成
1. *仮想サーバー* メニューの *Elastic Compute Service* を選択します
1. 左上のリージョンから指定されたリージョンを選択します
1. 左のメニューから *セキュリティグループ* を選択します
1. 右上の *セキュリティグループの作成* をボタンを押下します
1. 次の通り入力します
    1. *テンプレート* : `カスタマイズ`
    1. *セキュリティグループ名* : `sg-imagesearchhandson`
    1. *セキュリティグループタイプ* : `ベーシックセキュリティグループ`
    1. *ネットワークタイプ* : `VPC`
    1. *VPC* : `vpc-imagesearchhandson`
1. *OK* ボタンを押下します
1. *ルールをすぐに設定* ボタンを押下します
1. **jupyter notebook用**
    1. 右上の *セキュリティグループルールを追加* ボタンを押下します
    1. 次の通り入力します
        1. *ルールの方向* : `受信`
        1. *権限付与ポリシー* : `許可`
        1. *プロトコルタイプ* : `Custom TCP`
        1. *ポート範囲* : `8888`
        1. *プライオリティ* : `1`
        1. *権限付与タイプ* : `IPv4 CIDR ブロック`
        1. *権限付与オブジェクト* : `0.0.0.0/0`
    1. *OK* ボタンを押下します
1. **SSH用**
    1. 右上の *セキュリティグループルールを追加* ボタンを押下します
    1. 次の通り入力します
        1. *ルールの方向* : `受信`
        1. *権限付与ポリシー* : `許可`
        1. *プロトコルタイプ* : `SSH(22)`
        1. *プライオリティ* : `1`
        1. *権限付与タイプ* : `IPv4 CIDR ブロック`
        1. *権限付与オブジェクト* : `0.0.0.0/0`
    1. *OK* ボタンを押下します

## ECSの構築
1. *仮想サーバー* メニューの *Elastic Compute Service* を選択します
1. 左上のリージョンから指定されたリージョンを選択します
1. 左のメニューから *インスタンス* を選択します
1. 右上の *インスタンスを作成* ボタンを押下します
1. 次の通り入力します
    1. *価格モデル* : `従量課金`
    1. *リージョン* : 指定されたリージョンごとに選択してください
        1. *中国（香港）* : `Hong Kong Zone B`
        1. *シンガポール* : `Singapore Zone A`
        1. *オーストラリア（シドニー）* : `Sydney Zone A`
        1. *日本（東京）* : `Tokyo Zone A`
    1. *インスタンスタイプ*
        1. *vCPU* : `1vCPU`
        1. *メモリ* : `1GiB`
        1. *1 vCPU 0.5 GiB* : `バースト可能タイプ t5`
        1. *インスタンス数* : `1`
    1. *イメージ*
        1. ECSイメージ配布にご同意した方はこちら
            1. *パブリックイメージ* : `CentOS` : `7.7 64ビット`
        1. ECSイメージ配布にご同意していない方はこちら
    1. *ストレージ*
        1. *Ultra ディスク* : `20GiB`
1. *次のステップ: ネットワーク* ボタンを押下します
1. 次の通り入力します
    1. *ネットワーク*
        1. *VPC* : `vpc-imagesearchhandson`
        1. *VSwitch* : `vswitch-imagesearchhandson`
    1. *ネットワーク課金タイプ*
        1. *パブリック IP の割り当て* : **チェックをつける**
        1. *帯域幅の料金* : `1Mbps`
    1. *セキュリティグループ*
        1. *セキュリティグループの再選択* を選択します
        1. `sg-imagesearchhandson` :  **選択する**
        1. *選択* ボタンを押下します
1. *次のステップ: システム構成* ボタンを押下します
1. 次の通り入力します
    1. *ログイン認証* : `パスワード`
    1. *パスワード* : `任意の文字列`
    1. *パスワードの確認* : `任意の文字`
    1. *インスタンス名* : `ecs-imagesearchhandson`
    1. *ホスト* : `imagesearchhandson`
1. *次のステップ: グループ化* ボタンを押下します
1. *次のステップ: プレビュー* ボタンを押下します
    1. 次の通り入力します
        1. *利用規約* : **チェックをつける**
1. *インスタンスの作成* ボタンを押下します
1. *コンソール* ボタンを押下します

## 参考
- [ECS公式ドキュメント](https://jp.alibabacloud.com/product/ecs)


[戻る](Step4.md) | [次へ](Step6.md)
