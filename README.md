# redmine_cli
パワーシェルでRedmineを操作するためのスクリプトです。
  
# 準備
1. config.xml.sampleを参考にして、config.xmlを作成します。ユーザIDは、Redmineの画面右上に表示されているアカウント名のリンク先URLの末尾に記載されている数字です。rmIdは次のステップで確認します。  
2. rm_cli.ps1 showを実行してお使いのRedmineにおけるステータスIDを確認します。表示結果から、お使いの環境でopen/start/closeにマッチするID（数字）をconfig.xmlに入力してください。  
