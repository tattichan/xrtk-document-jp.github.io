# IL2CPPでの開発
## Nativeコードの記述
ネイティブコードはVS上で編集する上で、インテリセンスが効きません。.Netでは、UWP C#プロジェクトを出力しその先でネイティブコードの記述を行っていました。IL2CPPでは、ProjectName.Playerという専用のアセンブリファイルが生成されているのに気がつくと思います。このアセンブリ内では、AssemblyC-Sharpと同じ階層構造をもったファイル群が生成されており、この中ではインテリセンスが有効な状態でコードの編集が行えます。

## ビルド速度
一般的にビルド速度は遅いです。そこで高速化のための4つのポイントを紹介します。  

1. インクリメントビルド  
１度ビルドしたら、それ以降は同じ出力先を選択してビルドするという方法です。これは恐らく自然にやっていることだとは思います。  

2. プロジェクトとビルドフォルダーをマルウェア対策のソフトウェアスキャンから除外  
Windows Defender-> ウィルスと驚異の防止 -> ウィルスと驚異の防止の設定の項の「設定の管理」-> 除外の項の「除外の追加または削除」から出力先を除外に追加します。これは大幅にビルド時間の短縮を狙えます。  

3. プロジェクトとビルドフォルダーを Solid State Drive (SSD) に格納  
SSDを使いましょう。  

4. Script Only Build  
ビルドの対象をスクリプトに絞り込みます。BuildSettingsでDevelopment モードを有効にした時のみに選択可能になります。一度ビルドしたTarget先を選択する必要になります。  

[HoloLensのIL2CPPでの開発](https://www.tattichan.work/entry/2018/09/22/HoloLensのIL2CPPでの開発)