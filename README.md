# PSmine (PowerShell for Redmine )
PowershellでRedmineを操作するためのスクリプトです。以下の作業をPowershellプロンプトから実施できるようになります。  
- チケット一覧の表示  
- チケットの詳細表示  
- チケットの登録  
- チケットの更新（履歴更新）  
- チケットの更新（ステータス変更）     

##使い方
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
	STATUS  : 終了
	TITLE   : 嫁のお使い
	
	
	
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

###チケットのステータスを更新する。
psmine.ps1 change id {number} {open|start|close}　をコマンドを使います。
	> .\psmine.ps1 change id 45 close
	更新が成功しました

## 事前準備
1. config.xml.sampleを参にして、config.xmlを作成します。ユーザIDは、Redmineの画面右上に表示されているアカウント名のリンク先URLの末尾に記載されている数字です。rmIdは次のステップで確認します。  
2. psmine.ps1 showを実行してお使いのRedmineにおけるステータスIDを確認します。表示結果から、お使いの環境でopen/start/closeにマッチするID（数字）をconfig.xmlに入力してください。  
