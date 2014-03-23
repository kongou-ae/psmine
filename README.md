# redmine_cli
パワーシェルでRedmineを操作するためのスクリプトです。以下の作業をPowershellプロンプトから実施できるようになります。  
- チケット一覧の表示  
- チケットの詳細表示  
- チケットの登録  
- チケットの更新（履歴更新）  
- チケットの更新（ステータス変更）     



##使い方
###チケット一覧を確認する
	rm_cli.ps1 show

###特定のチケットの詳細を確認する。
	rm_cli.ps1 show id {number}  
###チケットの履歴を更新する
	rm_cli.ps1 update id {number} {note}

###チケットのステータスを更新する。
	rm_cli.ps1 update id {number} {open|start|close}



## 事前準備
1. config.xml.sampleを参にして、config.xmlを作成します。ユーザIDは、Redmineの画面右上に表示されているアカウント名のリンク先URLの末尾に記載されている数字です。rmIdは次のステップで確認します。  
2. rm_cli.ps1 showを実行してお使いのRedmineにおけるステータスIDを確認します。表示結果から、お使いの環境でopen/start/closeにマッチするID（数字）をconfig.xmlに入力してください。  
