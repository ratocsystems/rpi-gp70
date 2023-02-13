## **はじめにお読みください「RPi-GP70 について」**

本製品を正しく安全にお使いいただくための取り扱い方法、使用上の注意等について説明するものです。  
ご使用の前に必ずお読みください。  
___
### **機能概要**  
RPi-GP70 は、Raspberry Pi の GPIO 40Pin（I2C）に接続する絶縁型のRS485/RS422シリアル拡張ボードです。  
本製品には以下の機能があります。
- Raspberry Pi GPIO40Pinコネクタに装着する絶縁型RS485/RS422シリアルボード
- RS485/RS422シリアルポートは２ポート搭載
- RS485/422Aに対応
- シリアルポートコネクタは、5ピンネジ式脱着型端子台
- I2C-シリアル２ポートコントローラとしてSC16IS752を使用
- 送受信各64ByteのFIFOバッファ搭載
- シリアルポートの絶縁(絶縁耐圧2.5kV)は、コントローラとドライバ/レシーバ間。
　さらに、2ポート間（CN1とCN2間）も絶縁。
- Pythonモジュール「PyModbus」を使い、Modbus方式のシリアル通信を行うポートとして使用可能
 
***
### **ご使用の前に**
#### 内容物の確認  
パッケージの中に下記のものがすべて揃っているかをご確認ください。  
万一不足がありましたら、お手数ですが弊社サポートセンターまたは販売店までご連絡をお願いいたします。  

- RPi-GP70
- 5ピン電線側ネジ式端子台 x 2（基板へ装着済み）
- GPIO 40PIN ピンヘッダー x1  
- スペーサー（固定用 M2.6）x4
- ネジ（固定用 M2.6）x8
- 設定用ショートプラグ 4個(基板上のJP1,JP2,JP3,JP4に装着)
- ピン番号ラベル
- 保証書
 
---  
 
### **各項目については以下のリンクをご参照ください**  

## Content  

- [RPi-GP70の各部名称と説明](./constitution/README.md)  

- [Raspberry Pi OSの設定](./install/README.md)  

- [RPi-GP70の設定と装着](./setup/README.md)  

- [RPi-GP70の機能と説明](./interface/README.md)  

- [サンプルプログラムについて](./python/README.md)  

- [ハードウェア仕様](./specification/README.md)
