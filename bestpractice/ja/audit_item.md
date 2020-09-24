# ディスプレイ操作履歴項目
1. [操作履歴フィールド](#anchor1)
2. [有効エンティティ名](#anchor2)
3. [有効イベントタイプ](#anchor3)
4. [各エンティティの出力項目名](#anchor4)
5. [カラム](#anchor5)

## 項目
操作履歴の項目は下記の通りです。 ※2020年08月28日時点のデータです。

#### 1.操作履歴フィールド
<a id="anchor1"></a>

|日本語名|
|---|
|更新日時|
|更新日時|
|更新ソース|
|アカウント名|
|アカウントID|
|キャンペーン名|
|キャンペーンID|
|広告グループ名|
|広告グループID|
|広告名|
|広告ID|
|広告タイプ|
|メディア名|
|メディアID|
|リスト名|
|リストID|
|ターゲットリスト種別|
|コンバージョン名|
|コンバージョンID|
|ラベル名|
|ラベルID|
|商品リスト名|
|商品リストID|
|商品セット名|
|商品セットID|
|エンティティ|
|イベントタイプ|
|項目名|
|更新前|
|更新後|


#### 2.有効エンティティ名
<a id="anchor2"></a>

| エンティティ名  |日本語名|
|---|---|
| CAMPAIGN|キャンペーン|
| AD_GROUP|広告グループ|
| TARGET|ターゲット|
| AD_GROUP_TARGET|ターゲット|
| AD|広告|
| MEDIA|画像|
| VIDEO|動画|
| IO|アカウント|
| TARGET_LIST|ターゲットリスト|
| SEARCH_KEYWORD_LIST|サーチキーワードリスト|
| PLACEMENT_URL_LIST|プレイスメントリスト|
| CONVERSION_TRACKER|コンバージョン測定|
| LABEL|ラベル|
| CAMPAIGN_LABEL|キャンペーン|
| AD_GROUP_LABEL|広告グループ|
| AD_LABEL|広告|
| FEED_ITEM_LIST|商品リスト|
| FEED_ITEM_SET|商品セット|

#### 3.有効イベントタイプ
<table id= 'anchor3'> 
<tr>
  <th>エンティティ名</th>
  <th>日本語名</th>
 </tr>

<tr>
  <td rowspan="4">CAMPAIGN</td>
  <td>追加</td>
</tr>
<tr>
  <td>キャンペーン設定情報変更</td>
</tr>
<tr>
  <td>キャンペーン削除</td>
</tr>
<tr>
  <td>キャンペーン予算変更</td>
</tr>

 
<tr>
  <td rowspan="4">AD_GROUP</td>
  <td>追加</td>
 </tr>
 <tr>
  <td>広告グループ設定情報変更</td>
 </tr>
 <tr>
  <td>広告グループ削除</td>
 </tr>
  <tr>
  <td>広告グループ入札価格設定</td>
 </tr>
 
 <tr>
  <td rowspan="2">TARGET</td>
  <td>ターゲティング設定</td>
 </tr>
  <tr>
  <td>ターゲティング削除</td>
 </tr>
 
 <tr>
  <td rowspan="3">AD_GROUP_TARGET</td>
  <td>追加</td>
 </tr>
  <tr>
  <td>入札価格調整率変更</td>
 </tr>
 <tr>
 <td>削除</td>
</tr>

<tr>
 <td rowspan="5">AD</td>
  <td>追加</td>
 </tr>
 <tr>
  <td>広告設定変更</td>
 </tr>
 <tr>
  <td>広告削除</td>
 </tr>
 <tr>
  <td>広告審査</td>
 </tr>
 <tr>
  <td>広告入札価格設定</td>
 </tr>
 
 <tr>
  <td rowspan="4">MEDIA</td>
  <td>追加</td>
 </tr>
 <tr>
  <td>画像設定変更</td>
 </tr>
 <tr>
  <td>画像削除</td>
 </tr>
 <tr>
  <td>画像審査</td>
 </tr>
 
 <tr>
  <td rowspan="4">VIDEO</td>
  <td>追加</td>
 </tr>
 <tr>
  <td>動画設定変更</td>
 </tr>
 <tr>
  <td>動画削除</td>
 </tr>
 <tr>
  <td>動画審査</td>
 </tr>

<tr>
 <td rowspan="3">IO</td>
 <td>追加</td>
</tr>
<tr>
 <td>アカウント設定情報変更</td>
</tr>
<tr>
 <td>アカウント予算設定</td>
</tr>

<tr>
 <td rowspan="3">TARGET_LIST</td>
 <td>追加</td>
</tr>
<tr>
 <td>ターゲットリスト設定変更</td>
</tr>
<tr>
 <td>ターゲットリスト削除</td>
</tr>

<tr>
 <td rowspan="4">SEARCH_KEYWORD_LIST</td>
 <td>追加</td>
</tr>
<tr>
 <td>サーチキーワードリスト設定変更</td>
</tr>
<tr>
 <td>サーチキーワードリスト削除</td>
</tr>
<tr>
 <td>サーチキーワード設定変更</td>
</tr>


<tr>
 <td rowspan="3">PLACEMENT_URL_LIST</td>
 <td>追加</td>
</tr>
<tr>
 <td>プレイスメントリスト設定変更</td>
</tr>
<tr>
 <td>プレイスメントリスト削除</td>
</tr>

<tr>
 <td rowspan="2">CONVERSION_TRACKER</td>
 <td>追加</td>
</tr>
<tr>
 <td>コンバージョン測定設定変更</td>
</tr>

<tr>
 <td rowspan="3">LABEL</td>
 <td>追加</td>
</tr>
<tr>
 <td>ラベル設定変更</td>
</tr>
<tr>
 <td>ラベル削除</td>
</tr>

<tr>
 <td rowspan="2">CAMPAIGN_LABEL</td>
 <td>ラベル設定</td>
</tr>
<tr>
 <td>ラベル設定削除</td>
</tr>

<tr>
 <td rowspan="2">AD_GROUP_LABEL</td>
 <td>ラベル設定</td>
</tr>
<tr>
 <td>ラベル設定削除</td>
</tr>

<tr>
 <td rowspan="2">AD_LABEL</td>
 <td>ラベル設定</td>
</tr>
<tr>
 <td>ラベル設定削除</td>
</tr>

<tr>
 <td rowspan="3">FEED_ITEM_LIST</td>
 <td>追加</td>
</tr>
<tr>
 <td>商品リスト設定変更</td>
</tr>
<tr>
 <td>商品リスト削除</td>
</tr>

<tr>
 <td rowspan="3">FEED_ITEM_SET</td>
 <td>追加</td>
</tr>
<tr>
 <td>商品セット削除</td>
</tr>
</table>

#### 4.各エンティティの出力項目名
<table id="anchor4">
<tr>
  <th>エンティティ名</th>
  <th>日本語名</th>
 </tr>
 
<tr>
 <td rowspan="29">CAMPAIGN</td>
 <td>キャンペーン名</td>
</tr>
<tr>
 <td>配信設定</td>
</tr>
<tr>
 <td>広告掲載方式</td>
</tr>
<tr>
 <td>1日の予算</td>
</tr>
<tr>
 <td>掲載開始日</td>
</tr>
<tr>
 <td>掲載終了日</td>
</tr>
<tr>
 <td>フリークエンシーキャップ (旧)（回数）</td>
</tr>
<tr>
 <td>フリークエンシーキャップ (旧)（階層）</td>
</tr>
<tr>
 <td>フリークエンシーキャップ (旧)（期間）</td>
</tr>
<tr>
 <td>コンバージョン単価の目標値</td>
</tr>
<tr>
 <td>キャンペーンタイプ</td>
</tr>
<tr>
 <td>アプリID/パッケージ名</td>
</tr>
<tr>
 <td>アプリ名</td>
</tr>
<tr>
 <td>アプリOS</td>
</tr>
<tr>
 <td>商品リストID</td>
</tr>
<tr>
 <td>入札方法</td>
</tr>
<tr>
 <td>キャンペーン購入タイプ</td>
</tr>
<tr>
 <td>キャンペーン目的</td>
</tr>
<tr>
 <td>キャンペーン入札戦略</td>
</tr>
<tr>
 <td>入札価格（vCPM）</td>
</tr>
<tr>
 <td>入札価格（CPC）</td>
</tr>
<tr>
 <td>入札価格（CPV）</td>
</tr>
<tr>
 <td>コンバージョン単価の目標値（tCPA）</td>
</tr>
<tr>
 <td>フリークエンシーキャップ（回数）</td>
</tr>
<tr>
 <td>フリークエンシーキャップ（階層）</td>
</tr>
<tr>
 <td>フリークエンシーキャップ（期間）</td>
</tr>
<tr>
 <td>ステータス変更通知先</td>
</tr>
<tr>
 <td>通期予算</td>
</tr>
<tr>
 <td>予約キャンセル日時</td>
</tr>

<tr>
 <td rowspan="18">AD_GROUP</td>
 <td>広告グループ名</td>
</tr>
<tr>
 <td>配信設定</td>
</tr>
<tr>
 <td>入札方法</td>
</tr>
<tr>
 <td>広告グループ入札価格</td>
</tr>
<tr>
 <td>コンバージョン単価の目標値</td>
</tr>
<tr>
 <td>デバイス</td>
</tr>
<tr>
 <td> ウェブページ/アプリ</td>
</tr>
<tr>
 <td> OS</td>
</tr>
<tr>
 <td>OSバージョン（下限）</td>
</tr>
<tr>
 <td>キャリア</td>
</tr>
<tr>
 <td>画像自動付与</td>
</tr>
<tr>
 <td>配信先OSバージョン下限</td>
</tr>
<tr>
 <td>配信先OSバージョン上限</td>
</tr>
<tr>
 <td>商品セットID</td>
</tr>
<tr>
 <td>入札価格（vCPM）</td>
</tr>
<tr>
 <td>入札価格（CPC）</td>
</tr>
<tr>
 <td>入札価格（CPV）</td>
</tr>
<tr>
 <td>コンバージョン単価の目標値（tCPA）</td>
</tr>

<tr>
 <td rowspan="9">TARGET</td>
 <td>曜日・時間帯</td>
</tr>
<tr>
 <td>年齢</td>
</tr>
<tr>
 <td>性別</td>
</tr>
<tr>
 <td>地域</td>
</tr>
<tr>
 <td>インタレストカテゴリー</td>
</tr>
<tr>
 <td>サイトカテゴリー</td>
</tr>
<tr>
 <td>サイトリターゲティング</td>
</tr>
<tr>
 <td>サーチキーワード</td>
</tr>
<tr>
 <td>プレイスメント</td>
</tr>

<tr>
 <td rowspan="15">AD_GROUP_TARGET</td>
 <td>曜日・時間帯</td>
</tr>
<tr>
 <td>年齢</td>
</tr>
<tr>
 <td>性別</td>
</tr>
<tr>
 <td>地域</td>
</tr>
<tr>
 <td>インタレストカテゴリー</td>
</tr>
<tr>
 <td>サイトカテゴリー</td>
</tr>
<tr>
 <td>サイトリターゲティング</td>
</tr>
<tr>
 <td>サーチキーワード</td>
</tr>
<tr>
 <td>プレイスメント</td>
</tr>
<tr>
 <td>デバイス</td>
</tr>
<tr>
 <td>キャリア</td>
</tr>
<tr>
 <td>ウェブページ／アプリ</td>
</tr>
<tr>
 <td>OS</td>
</tr>
<tr>
 <td>OSバージョン（下限）</td>
</tr>
<tr>
 <td>オーディエンスカテゴリー</td>
</tr>

<tr>
 <td rowspan="47">AD</td>
 <td>広告名</td>
</tr>
<tr>
 <td>配信設定</td>
</tr>
<tr>
 <td>広告入札価格</td>
</tr>
<tr>
 <td>広告タイプ</td>
</tr>
<tr>
 <td>広告タイトル</td>
</tr>
<tr>
 <td>広告説明文1</td>
</tr>
<tr>
 <td>広告説明文2</td>
</tr>
<tr>
 <td>キャリア（モバイル）</td>
</tr>
<tr>
 <td>アプリ名</td>
</tr>
<tr>
 <td>App ID/パッケージ名</td>
</tr>
<tr>
 <td>ボタン</td>
</tr>
<tr>
 <td>URLスキーム</td>
</tr>
<tr>
 <td>メディアID（ロゴ）</td>
</tr>
<tr>
 <td>メディアID（ロゴ2）</td>
</tr>
<tr>
 <td>メディアID（ロゴ3）</td>
</tr>
<tr>
 <td>主体者表記</td>
</tr>
<tr>
 <td>カラーテーマ名</td>
</tr>
<tr>
 <td>免責条項</td>
</tr>
<tr>
 <td>価格のプレフィックス</td>
</tr>
<tr>
 <td>価格のサフィックス</td>
</tr>
<tr>
 <td>広告のベースカラー</td>
</tr>
<tr>
 <td>メディアID</td>
</tr>
<tr>
 <td>表示URL</td>
</tr>
<tr>
 <td>リンク先URL</td>
</tr>
<tr>
 <td>インプレッションビーコンURL</td>
</tr>
<tr>
 <td>視聴ビーコンURL（再生開始）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（3秒視聴）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（10秒視聴）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（再生完了）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（25%再生）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（50%再生）</td>
</tr>
<tr>
 <td>視聴ビーコンURL（75%再生）</td>
</tr>
<tr>
 <td>入稿日</td>
</tr>
<tr>
 <td>メディアID（動画サムネイル）</td>
</tr>
<tr>
 <td>第三者測定スクリプトタグsrc属性URL</td>
</tr>
<tr>
 <td>リンク先更新/公開予定日時</td>
</tr>
<tr>
 <td>リンク先の状態</td>
</tr>
<tr>
 <td>メディアID（縮小メイン画像）</td>
</tr>
<tr>
 <td>メディアID（左サイド画像）</td>
</tr>
<tr>
 <td>メディアID（右サイド画像）</td>
</tr>
<tr>
 <td>メディアID（センター画像）</td>
</tr>
<tr>
 <td>事前承認ID</td>
</tr>
<tr>
 <td>メディアID（キャンペーンバナー）</td>
</tr>
<tr>
 <td>メディアID（キャンペーンバナー2）</td>
</tr>
<tr>
 <td>メディアID（キャンペーンバナー3）</td>
</tr>
<tr>
 <td>メディアID（キャンペーンバナー4）</td>
</tr>
<tr>
 <td>リンク先URL（キャンペーンバナー）</td>
</tr>

<tr>
 <td rowspan="3">MEDIA</td>
 <td>配信設定</td>
</tr>
<tr>
 <td>メディア名</td>
</tr>
<tr>
 <td>入稿日</td>
</tr>
<tr>
 <td rowspan="3">VIDEO</td>
 <td>配信設定</td>
</tr>
<tr>
 <td>メディア名</td>
</tr>
<tr>
 <td>入稿日</td>
</tr>
<tr>
 <td rowspan="20">IO</td>
 <td>アカウント名</td>
</tr>
<tr>
 <td>アカウント予算</td>
</tr>
<tr>
 <td>代理店担当者名</td>
</tr>
<tr>
 <td>代理店の所在地域</td>
</tr>
<tr>
 <td>広告主の所在地域</td>
</tr>
<tr>
 <td>アカウント作成日</td>
</tr>
<tr>
 <td>掲載終了日</td>
</tr>
<tr>
 <td>担当者名（広告主）</td>
</tr>
<tr>
 <td>自動入金額</td>
</tr>
<tr>
 <td>自動入金設定</td>
</tr>
<tr>
 <td>自動入金用クレジットカード登録者のYahoo! JAPANビジネスID</td>
</tr>
<tr>
 <td>配信設定</td>
</tr>
<tr>
 <td>連絡先利用者のYahoo! JAPANビジネスID</td>
</tr>
<tr>
 <td>入金割合</td>
</tr>
<tr>
 <td>インタレストマッチ配信</td>
</tr>
<tr>
 <td>規約同意日（注文確定日）</td>
</tr>
<tr>
 <td>連絡先メールアドレス</td>
</tr>
<tr>
 <td>お知らせメール設定</td>
</tr>
<tr>
 <td>自動タグ設定</td>
</tr>
<tr>
 <td>ターゲットリストの共有設定</td>
</tr>

<tr>
 <td rowspan="11">TARGET_LIST</td>
 <td>ターゲットリスト名</td>
</tr>
<tr>
 <td>ターゲットリストの説明</td>
</tr>
<tr>
 <td>ターゲットリスト種別</td>
</tr>
<tr>
 <td>訪問履歴の蓄積</td>
</tr>
<tr>
 <td>過去の訪問者の設定</td>
</tr>
<tr>
 <td>訪問履歴の有効期間</td>
</tr>
<tr>
 <td>DMP連携データの有効期間</td>
</tr>
<tr>
 <td>ターゲットリストの条件</td>
</tr>
<tr>
 <td>基にするターゲットリスト名</td>
</tr>
<tr>
 <td>ターゲットリストのサイズ</td>
</tr>
<tr>
 <td>ターゲットリストの共有状況</td>
</tr>

<tr>
 <td rowspan="5">SEARCH_KEYWORD_LIST</td>
 <td>ターゲットリスト名</td>
</tr>
<tr>
 <td>サーチキーワードリストの説明</td>
</tr>
<tr>
 <td>有効期間</td>
</tr>
<tr>
 <td>検索回数</td>
</tr>
<tr>
 <td>サーチキーワード</td>
</tr>

<tr>
 <td rowspan="3">PLACEMENT_URL_LIST</td>
 <td>プレイスメントリスト名</td>
</tr>
<tr>
 <td>プレイスメントリストの説明</td>
</tr>
<tr>
 <td>プレイスメントリストのURL</td>
</tr>

<tr>
 <td rowspan="11">CONVERSION_TRACKER</td>
 <td>コンバージョン種別</td>
</tr>
<tr>
 <td>コンバージョン名</td>
</tr>
<tr>
 <td>コンバージョン測定の目的</td>
</tr>
<tr>
 <td>計測期間</td>
</tr>
<tr>
 <td>計測期間（動画視聴）</td>
</tr>
<tr>
 <td>計測方法</td>
</tr>
<tr>
 <td>コンバージョン列に含める</td>
</tr>
<tr>
 <td>1コンバージョンあたりの価値</td>
</tr>
<tr>
 <td>アプリOS</td>
</tr>
<tr>
 <td>アプリID/パッケージ名</td>
</tr>
<tr>
 <td>ステータス</td>
</tr>

<tr>
 <td rowspan="4">LABEL</td>
 <td>ラベル名</td>
</tr>
<tr>
 <td>ラベル色</td>
</tr>
<tr>
 <td>ラベル説明文</td>
</tr>
<tr>
 <td>ラベル</td>
</tr>

<tr>
 <td rowspan="1">CAMPAIGN_LABEL</td>
 <td>ラベル</td>
</tr>

<tr>
 <td rowspan="1">AD_GROUP_LABEL</td>
 <td>ラベル</td>
</tr>

<tr>
 <td rowspan="1">AD_LABEL</td>
 <td>ラベル</td>
</tr>

<tr>
 <td rowspan="8">FEED_ITEM_LIST</td>
 <td>商品リスト名</td>
</tr>
<tr>
 <td>定期アップロードフィードURL</td>
</tr>
<tr>
 <td>定期アップロードユーザ名</td>
</tr>
<tr>
 <td>定期アップロードスケジュール時間</td>
</tr>
<tr>
 <td>定期アップロードスケジュール曜日</td>
</tr>
<tr>
 <td>定期アップロードスケジュール間隔</td>
</tr>
<tr>
 <td>定期アップロード取り込み種別</td>
</tr>
<tr>
 <td>定期アップロードステータス</td>
</tr>

<tr>
 <td rowspan="2">FEED_ITEM_SET</td>
 <td>商品セット名</td>
</tr>
<tr>
 <td>商品セット設定条件</td>
</tr>
</table>

#### 5.カラム
<table id="anchor5">
<tr>
  <th>項目</th>
  <th>日本語名</th>
 </tr>

<tr>
 <td rowspan="2">配信設定</td>
 <td>オフ</td>
</tr>
<tr>
 <td>オン</td>
</tr>

<tr>
 <td rowspan="1">1日の予算</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="1">広告入札価格</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="1">掲載終了日</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="1">フリークエンシーキャップ (旧)（回数）</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="4">フリークエンシーキャップ (旧)（階層）</td>
 <td>設定なし</td>
</tr>
<tr>
 <td>キャンペーン</td>
</tr>
<tr>
 <td>広告グループ</td>
</tr>
<tr>
 <td>広告</td>
</tr>

<tr>
 <td rowspan="6">フリークエンシーキャップ (旧)（期間）</td>
 <td>設定なし</td>
</tr>
<tr>
 <td>分</td>
</tr>
<tr>
 <td>時</td>
</tr>
<tr>
 <td>日</td>
</tr>
<tr>
 <td>週</td>
</tr>
<tr>
 <td>月</td>
</tr>

<tr>
 <td rowspan="3">入札方法</td>
 <td>キャンペーンの入札方法を適用</td>
</tr>
<tr>
 <td>手動入札</td>
</tr>
<tr>
 <td>自動入札（コンバージョン最適化）</td>
</tr>

<tr>
 <td rowspan="1">コンバージョン単価の目標値</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="1">コンバージョン単価の目標値</td>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="2">キャンペーンタイプ</td>
 <td>標準キャンペーン</td>
</tr>
<tr>
 <td>アプリキャンペーン</td>
</tr>

<tr>
 <td rowspan="2">アプリOS</td>
 <td>Android</td>
</tr>
<tr>
 <td>iOS</td>
</tr>


<tr>
 <td rowspan="5">デバイス</td>
 <td>PC</td>
</tr>
<tr>
 <td>モバイル</td>
</tr>
<tr>
 <td>スマートフォン</td>
</tr>
<tr>
 <td>タブレット</td>
</tr>
<tr>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="3">OS</td>
 <td>Android</td>
</tr>
<tr>
 <td>iOS</td>
</tr>
<tr>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="3">ウェブページ/アプリ</td>
 <td>アプリ</td>
</tr>
<tr>
 <td>ウェブ</td>
</tr>
<tr>
 <td>設定なし</td>
</tr>

<tr>
 <td rowspan="2">画像自動付与</td>
 <td>オン</td>
</tr>
<tr>
 <td>オフ</td>
</tr>

<tr>
 <td rowspan="24">広告タイプ</td>
 <td>テキスト（説明文19-19）</td>
</tr>
<tr>
 <td>テキスト（説明文33）</td>
</tr>
<tr>
 <td>ショートテキスト（14・19）</td>
</tr>
<tr>
 <td>ショートテキスト（12・12）</td>
</tr>
<tr>
 <td>掲載位置指定テキスト</td>
</tr>
<tr>
 <td>テキスト（15・90）</td>
</tr>
<tr>
 <td>レスポンシブ（画像）</td>
</tr>
<tr>
 <td>広告枠サイズ固定（300x250）-スクエアバナー（トップ）</td>
</tr>
<tr>
 <td>広告枠サイズ固定（300x250）-ワイドバナー（トップ）</td>
</tr>
<tr>
 <td>広告枠サイズ固定（300x250）-ワイドバナー（ミドル）</td>
</tr>
<tr>
 <td>動的ディスプレイ</td>
</tr>
<tr>
 <td>レスポンシブ（動画）</td>
</tr>
<tr>
 <td>バナー（動画）</td>
</tr>
<tr>
 <td>ブランドパネル クインティ</td>
</tr>
<tr>
 <td> ブランドパネル クインティ 動画</td>
</tr>
<tr>
 <td> ブランドパネル パノラマ</td>
</tr>
<tr>
 <td> ブランドパネル パノラマ 動画</td>
</tr>
<tr>
 <td> トップインパクト スクエア</td>
</tr>
<tr>
 <td> トップインパクト スクエア 動画</td>
</tr>
<tr>
 <td> トップインパクト クインティ</td>
</tr>
<tr>
 <td> トップインパクト クインティ 動画</td>
</tr>
<tr>
 <td> トップインパクト パノラマ</td>
</tr>
<tr>
 <td> トップインパクト パノラマ 動画</td>
</tr>
<tr>
 <td> バナー（画像）</td>
</tr>

<tr>
 <td rowspan="6">キャリア</td>
 <td>docomo</td>
</tr>
<tr>
 <td>KDDI</td>
</tr>
<tr>
 <td>SoftBank</td>
</tr>
<tr>
 <td>ワイモバイル</td>
</tr>
<tr>
 <td>その他</td>
</tr>
<tr>
 <td>すべてのキャリア</td>
</tr>

<tr>
 <td rowspan="3">お知らせメール設定</td>
 <td>受信しない</td>
</tr>
<tr>
 <td>重要なもののみ受信</td>
</tr>
<tr>
 <td>受信する</td>
</tr>

<tr>
 <td rowspan="49">代理店の所在地域</td>
 <td>北海道</td>
</tr>
<tr>
 <td>青森</td>
</tr>
<tr>
 <td>岩手</td>
</tr>
<tr>
 <td>宮城</td>
</tr>
<tr>
 <td>秋田</td>
</tr>
<tr>
 <td>山形</td>
</tr>
<tr>
 <td>福島</td>
</tr>
<tr>
 <td>茨城</td>
</tr>
<tr>
 <td>栃木</td>
</tr>
<tr>
 <td>群馬</td>
</tr>
<tr>
 <td>埼玉</td>
</tr>
<tr>
 <td>千葉</td>
</tr>
<tr>
 <td>東京</td>
</tr>
<tr>
 <td>神奈川</td>
</tr>
<tr>
 <td>新潟</td>
</tr>
<tr>
 <td>富山</td>
</tr>
<tr>
 <td>石川</td>
</tr>
<tr>
 <td>福井</td>
</tr>
<tr>
 <td>山梨</td>
</tr>
<tr>
 <td>長野</td>
</tr>
<tr>
 <td>岐阜</td>
</tr>
<tr>
 <td>静岡</td>
</tr>
<tr>
 <td>愛知</td>
</tr>
<tr>
 <td>三重</td>
</tr>
<tr>
 <td>滋賀</td>
</tr>
<tr>
 <td>京都</td>
</tr>
<tr>
 <td>大阪</td>
</tr>
<tr>
 <td>兵庫</td>
</tr>
<tr>
 <td>奈良</td>
</tr>
<tr>
 <td>和歌山</td>
</tr>
<tr>
 <td>鳥取</td>
</tr>
<tr>
 <td>島根</td>
</tr>
<tr>
 <td>岡山</td>
</tr>
<tr>
 <td>広島</td>
</tr>
<tr>
 <td>山口</td>
</tr>
<tr>
 <td>徳島</td>
</tr>
<tr>
 <td>香川</td>
</tr>
<tr>
 <td>愛媛</td>
</tr>
<tr>
 <td>高知</td>
</tr>
<tr>
 <td>福岡</td>
</tr>
<tr>
 <td>佐賀</td>
</tr>
<tr>
 <td>長崎</td>
</tr>
<tr>
 <td>熊本</td>
</tr>
<tr>
 <td>大分</td>
</tr>
<tr>
 <td>宮崎</td>
</tr>
<tr>
 <td>鹿児島</td>
</tr>
<tr>
 <td>沖縄</td>
</tr>
<tr>
 <td>海外</td>
</tr>
<tr>
 <td>未設定</td>
</tr>

<tr>
 <td rowspan="49">広告主の所在地域</td>
 <td>北海道</td>
</tr>
<tr>
 <td>青森</td>
</tr>
<tr>
 <td>岩手</td>
</tr>
<tr>
 <td>宮城</td>
</tr>
<tr>
 <td>秋田</td>
</tr>
<tr>
 <td>山形</td>
</tr>
<tr>
 <td>福島</td>
</tr>
<tr>
 <td>茨城</td>
</tr>
<tr>
 <td>栃木</td>
</tr>
<tr>
 <td>群馬</td>
</tr>
<tr>
 <td>埼玉</td>
</tr>
<tr>
 <td>千葉</td>
</tr>
<tr>
 <td>東京</td>
</tr>
<tr>
 <td>神奈川</td>
</tr>
<tr>
 <td>新潟</td>
</tr>
<tr>
 <td>富山</td>
</tr>
<tr>
 <td>石川</td>
</tr>
<tr>
 <td>福井</td>
</tr>
<tr>
 <td>山梨</td>
</tr>
<tr>
 <td>長野</td>
</tr>
<tr>
 <td>岐阜</td>
</tr>
<tr>
 <td>静岡</td>
</tr>
<tr>
 <td>愛知</td>
</tr>
<tr>
 <td>三重</td>
</tr>
<tr>
 <td>滋賀</td>
</tr>
<tr>
 <td>京都</td>
</tr>
<tr>
 <td>大阪</td>
</tr>
<tr>
 <td>兵庫</td>
</tr>
<tr>
 <td>奈良</td>
</tr>
<tr>
 <td>和歌山</td>
</tr>
<tr>
 <td>鳥取</td>
</tr>
<tr>
 <td>島根</td>
</tr>
<tr>
 <td>岡山</td>
</tr>
<tr>
 <td>広島</td>
</tr>
<tr>
 <td>山口</td>
</tr>
<tr>
 <td>徳島</td>
</tr>
<tr>
 <td>香川</td>
</tr>
<tr>
 <td>愛媛</td>
</tr>
<tr>
 <td>高知</td>
</tr>
<tr>
 <td>福岡</td>
</tr>
<tr>
 <td>佐賀</td>
</tr>
<tr>
 <td>長崎</td>
</tr>
<tr>
 <td>熊本</td>
</tr>
<tr>
 <td>大分</td>
</tr>
<tr>
 <td>宮崎</td>
</tr>
<tr>
 <td>鹿児島</td>
</tr>
<tr>
 <td>沖縄</td>
</tr>
<tr>
 <td>海外</td>
</tr>
<tr>
 <td>未設定</td>
</tr>

<tr>
 <td rowspan="2">自動入金設定</td>
 <td>オフ</td>
</tr>
<tr>
 <td>オン</td>
</tr>

<tr>
 <td rowspan="2">ヤフーによる配信設定</td>
 <td>オフ</td>
</tr>
<tr>
 <td>オン</td>
</tr>

<tr>
 <td rowspan="2">インタレストマッチ配信</td>
 <td>配信する</td>
</tr>
<tr>
 <td>配信しない</td>
</tr>

<tr>
 <td rowspan="1">訪問履歴の有効期間</td>
 <td>未設定</td>
</tr>

<tr>
 <td rowspan="5">ターゲットリスト種別</td>
 <td>デフォルト</td>
</tr>
<tr>
 <td>条件</td>
</tr>
<tr>
 <td>組み合わせ</td>
</tr>
<tr>
 <td>類似</td>
</tr>
<tr>
 <td>カスタム</td>
</tr>

<tr>
 <td rowspan="10">ターゲットリストのサイズ</td>
 <td>1</td>
</tr>
<tr>
 <td>2</td>
</tr>
<tr>
 <td>3</td>
</tr>
<tr>
 <td>4</td>
</tr>
<tr>
 <td>5</td>
</tr>
<tr>
 <td>6</td>
</tr>
<tr>
 <td>7</td>
</tr>
<tr>
 <td>8</td>
</tr>
<tr>
 <td>9</td>
</tr>
<tr>
 <td>10</td>
</tr>

<tr>
 <td rowspan="3">訪問履歴の蓄積</td>
 <td>オフ</td>
</tr>
<tr>
 <td>オン</td>
</tr>
<tr>
 <td>""</td>
</tr>

<tr>
 <td rowspan="3">過去の訪問者の設定</td>
 <td>オフ</td>
</tr>
<tr>
 <td>オン</td>
</tr>
<tr>
 <td>""</td>
</tr>

<tr>
 <td rowspan="2">コンバージョン種別</td>
 <td>ウェブ</td>
</tr>
<tr>
 <td>アプリ</td>
</tr>

<tr>
 <td rowspan="2">計測方法</td>
 <td>毎回</td>
</tr>
<tr>
 <td>初回のみ</td>
</tr>

<tr>
 <td rowspan="7">コンバージョン測定の目的</td>
 <td>未設定</td>
</tr>
<tr>
 <td>その他</td>
</tr>
<tr>
 <td>主要なページの閲覧</td>
</tr>
<tr>
 <td>購入/販売</td>
</tr>
<tr>
 <td>お申し込み</td>
</tr>
<tr>
 <td>販売促進</td>
</tr>
<tr>
 <td>その他</td>
</tr>
<tr>
 <td rowspan="2">コンバージョン列に含める</td>
 <td>含めない</td>
</tr>
<tr>
 <td>含める</td>
</tr>
<tr>
 <td rowspan="2">ステータス</td>
 <td>オン</td>
</tr>
<tr>
 <td>オフ</td>
</tr>
<tr>
 <td rowspan="3">自動タグ設定</td>
 <td>設定する</td>
</tr>
<tr>
 <td>設定しない</td>
</tr>
<tr>
 <td>オフ（継続）</td>
</tr>
<tr>
 <td rowspan="2">ターゲットリストの共有状況</td>
 <td>共有中</td>
</tr>
<tr>
 <td>無効</td>
</tr>
<tr>
 <td rowspan="2">ターゲットリストの共有設定</td>
 <td>有効</td>
</tr>
<tr>
 <td>無効</td>
</tr>

<tr>
 <td rowspan="7">定期アップロードスケジュール曜日</td>
 <td>日曜日</td>
</tr>
<tr>
 <td>月曜日</td>
</tr>
<tr>
 <td>火曜日</td>
</tr>
<tr>
 <td>水曜日</td>
</tr>
<tr>
 <td>木曜日</td>
</tr>
<tr>
 <td>金曜日</td>
</tr>
<tr>
 <td>土曜日</td>
</tr>

<tr>
 <td rowspan="2">定期アップロード取り込み種別</td>
 <td>部分更新</td>
</tr>
<tr>
 <td>全件更新</td>
</tr>
<tr>
 <td rowspan="2">定期アップロードステータス</td>
 <td>無効</td>
</tr>
<tr>
 <td>有効</td>
</tr>

<tr>
 <td rowspan="7">キャンペーン目的</td>
 <td>ブランド認知</td>
</tr>
<tr>
 <td>動画再生</td>
</tr>
<tr>
 <td>サイト誘導</td>
</tr>
<tr>
 <td>アプリ訴求</td>
</tr>
<tr>
 <td>コンバージョン</td>
</tr>
<tr>
 <td>商品リスト訴求</td>
</tr>
<tr>
 <td>目的設定なし（既存在庫）</td>
</tr>
<tr>
 <td rowspan="2">キャンペーン購入タイプ</td>
 <td>運用型</td>
</tr>
<tr>
 <td>予約型</td>
</tr>

<tr>
 <td rowspan="6">キャンペーン入札戦略</td>
 <td>自動入札</td>
</tr>
<tr>
 <td>手動入札（vCPM）</td>
</tr>
<tr>
 <td>手動入札（CPC）</td>
</tr>
<tr>
 <td>手動入札（CPV）</td>
</tr>
<tr>
 <td>自動入札（tCPA）</td>
</tr>
<tr>
 <td>入札戦略指定なし</td>
</tr>
<tr>
 <td rowspan="4">フリークエンシーキャップ（階層）</td>
 <td>設定なし</td>
</tr>
<tr>
 <td>キャンペーン</td>
</tr>
<tr>
 <td>広告グループ</td>
</tr>
<tr>
 <td>広告</td>
</tr>
<tr>
 <td rowspan="7">フリークエンシーキャップ（期間）</td>
 <td>設定なし</td>
</tr>
<tr>
 <td>分</td>
</tr>
<tr>
 <td>時</td>
</tr>
<tr>
 <td>日</td>
</tr>
<tr>
 <td>週</td>
</tr>
<tr>
 <td>月</td>
</tr>
<tr>
 <td>掲載期間</td>
</tr>
<tr>
 <td rowspan="2">リンク先の状態</td>
 <td>完成/公開済み</td>
</tr>
<tr>
 <td>後日更新/公開予定</td>
</tr>
</table>
