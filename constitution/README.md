# RPi-GP70 各部名称と説明  
___  
## 1. 基板構成  
製品基板の各部名称は以下のとおりです。  

![board](./img/GP70_board.png)  

| No | 名称 | 機能 |  
|:-----:|:-----|-----|  
|1|GPIO 40PINコネクタ|Raspberry Pi GPIO|  
|2|JP3/JP4 ジャンパピン|シリアルポート0,1 受信制御信号設定|
|3|JP1/JP2 ジャンパピン|シリアルポート0,1 終端抵抗設定|
|4|CN1/CN2 OMRON XW4A<br> 5ピンネジ式脱着型端子台|シリアルポート0,1 |

※CN1,CN2(電線側ソケット XW4B-05B1)の適合電線はAWG28～AWG16, ストリップ長は7mmです。  
___  
## 2. 各端子・コネクタについて  
### 2-1. GPIO 40PINコネクタ  
GPIO 40 PIN の配列および使用ピンは以下のとおりです。  
![GPIO40PIN](./img/gp70_gpio.png)  

40PIN GPIOのピン配列と説明  

| PIN# | 信号名 | 説明 | PIN# | 信号名 | 説明 |  
|:---:|:---|:---|:---:|:---|:---|  
|1|3.3V|3.3V電源|2|5V|5V電源|  
|3|I2C SDA1/GPIO 2|I2C SDA1|4|5V|5V電源|  
|5|I2C SCL1/GPIO 3|I2C SCL1|6|GND|GND|  
|7|GPIO 4|(未使用)|8|GPIO 14|(未使用)|  
|9|GND|GND|10|GPIO 15|(未使用)|  
|11|IRQ/GPIO 17|IRQ入力|12|GPIO 18|(未使用)|  
|13|GPIO 27|絶縁電源制御|14|GND|GND|  
|15|GPIO 22|(未使用)|16|GPIO 23|(未使用)|  
|17|3.3V|3.3V電源|18|GPIO 24|(未使用)|  
|19|SPI0 MOSI/GPIO 10|(未使用)|20|GND|GND|  
|21|SPI0 MISO/GPIO 9|(未使用)|22|GPIO 25|(未使用)|  
|23|SPI0 SCLK/GPIO 11|(未使用)|24|SPI CE0/GPIO 8|(未使用)|  
|25|GND|GND|26|SPI CE1/GPIO 7|(未使用)|  
|27|I2C SDA0/GPIO 0| HAT_ID読み込み用I2C |28|I2C SCL0/GPIO 1|HAT_ID読み込み用I2C|  
|29|GPIO 5|(未使用)|30|GND|GND|  
|31|GPIO 6|(未使用)|32|GPIO 12|(未使用)|  
|33|GPIO 13|(未使用)|34|GND|GND|  
|35|GPIO 19|(未使用)|36|GPIO 16|(未使用)|  
|37|GPIO 26|(未使用)|38|GPIO 20|(未使用)|  
|39|GND|GND|40|GPIO 21|(未使用)|  

### 2-2. シリアルポート0,1 [5ピン端子台]
シリアルポート0[CN1], ポート1[CN2]は、5ピン端子台を使用しています。  
![GP70_CN1](./img/GP70_CN1CN2_image.jpg) 
ボード上のジャンパ[JP1/JP2] で終端抵抗の有効無効を設定します。  
ボード上のジャンパ[JP3/JP4] で受信制御信号を設定します。  
5ピン端子台は、独自の端子配列となります。  
詳細については[RPi-GP70の設定と装着](../setup/README.md)を参照してください。  

___