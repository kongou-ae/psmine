# PSmine (PowerShell for Redmine )
PowershellでRedmineを操作するためのスクリプトです。以下の作業をPowershellプロンプトから実施できるようになります。  
- チケット一覧の表示  
- チケットの詳細表示  
- チケットの登録  
- チケットの更新（履歴更新）  
- チケットの更新（ステータス変更）     

##使い方
psmine.ps1とconfig.xmlが格納されたディレクトリでコマンドを実行して下さい。

###チケット一覧を確認する
psmine.ps1 show コマンドを使います。  

	> .\psmine.ps1 show
	
	
	ID      : 50
	project : tech
	subject : kibana3 elasticseachをリバプロ経由にする。
	status  : 新規

	ID      : 49
	project : tech
	subject : kibana3 ダッシュボードに表示されるデータを機器ごとに限定する。
	status  : 新規

###特定のチケットの詳細を確認する。
psmine.ps1 show id {number}　をコマンドを使います。  

	> .\psmine.ps1 show id 44
	>> Ticket Summary

	ID      : 44
	PROJECT : home
	TITLE   : 嫁のお使い
	STATUS  : 終了	
	
	
	>> Ticket Detail
	
	
	created_on                                                       name                                                     notes                                                          
	----------                                                       ----                                                     -----                                                          
	2014-03-10T15:36:19Z                                             kongou-ae                                                たまごも買う                                                         
	2014-03-11T07:51:29Z                                             kongou-ae                                                くりーむっぽいごまドレッシングも買う                                             
	2014-03-11T07:59:28Z                                             kongou-ae                                                福神漬け                                                           
	2014-03-13T06:34:17Z                                             kongou-ae                                                             
###チケットの履歴を更新する
psmine.ps1 update id {number} {note}　をコマンドを使います。  

	> .\psmine.ps1 update id 45 ベンダーへの問い合わせを実施した。
	更新が成功しました
	（更新後のチケット詳細が表示される）

###チケットのステータスを更新する。
psmine.ps1 change id {number} {open|start|close}　をコマンドを使います。  

	> .\psmine.ps1 change id 45 close
	更新が成功しました
	（更新後のチケット詳細が表示される）

###チケットのステータスを新規作成する。
psmine.ps1 add {title} {description}　をコマンドを使います。 現在の実装では、チケットが作成できるプロジェクトは、config.xmlに記載するた1つのプロジェクトのみです。 

	> .\psmine.ps1 add title description
	チケットの追加が成功しました
	（追加したチケットの詳細が表示される）	

## 事前準備
###1．基本設定
config.xml.sampleを元に、config.xmlを作成します。  

入力項目|入力内容
:-----|:-----
apiKey|PSmineでアクセスするRedmineで発行されたAPI Key
rmUrl | PSmineでアクセスするRedmineのURL
rmAssign | PSmineで利用するユーザのID

RedmineのユーザIDは画面右上に表示されているアカウント名のリンク先URLの末尾に記載されている数字です。

###2．ステータスIDの入力
PSmineでは、チケットのステータスを以下の3つで管理します。これら3つにマッチするIDをconfig.xmlに入力してください。

ステータス名|PSmineが想定するステータス
:-----|:-----
rmID.open|チケットが起票された直後のステータス
rmID.start|担当者がチケットの対応に着手したステータス
rmID.close|チケットがクローズされた際のステータス

入力すべき値はpsmine.ps1 check　コマンドで確認可能です。以下の例だと、新規のステータスIDは7になります。

	>.\psmine.ps1 check
	>> Status ID is as below
	7        新規
	8        進行中
	14       リーダー承認待ち
	10       差戻し
	15       リーダー承認済
	13       解決
	16       室長承認済
	11       完了
	12       取下げ

###3．プロジェクトIDの入力
PSmineでは、1つのプロジェクトに対してのみチケットを作成することが出来ます。PSmineでチケットを作成したいプロジェクトのIDをconfig.xmlに入力してください。入力箇所はrmProjectです。
入力すべき値はpsmine.ps1 check　コマンドで確認可能です。testプロジェクトに対してチケットを作成したい場合は、39を入力します。

	> .\psmine.ps1 check
	>> Status ID is as below
	（中略）
	>> Project ID is as below
	39       test
	63       test2
	38       test