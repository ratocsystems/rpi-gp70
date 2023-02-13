# RPi-GP70用Pythonサンプルファイル

RPi-GP70用Pythonサンプルファイルの使用方法について説明します。  
Raspberry Piは'Raspberry Pi4 ModelB'、OSは'Raspberry Pi OS Version 2022-09-22'で説明します。
サンプルファイルは`sampleGp70.py`です。  

  
***
## 準備  
### Raspberry PiにRPi-GP70を接続  
下記の準備をおこなってください。
- [`OS(Raspberry Pi OS)のインストール`](../install/README.md#raspberry-pi-osのインストール)  
- [GPIO40pinのI2C設定](../install/README.md#4-osの起動とi2cの有効設定)  
- ['Raspberry Pi'に'RPi-G70'を接続](../setup/README.md#rpi-gp70の設定と装着)  
- [シリアルドライバの設定](/setup/README.md#4-シリアルドライバ設定)  

### Pythonサンプルファイルを実行するディレクトリを作成  
1. 'mkdir'コマンドを使って'RPi-GP70'という名前のディレクトリを作成します。(ディレクトリ名や作成場所は自由です)  
    ```
    $ mkdir RPi-GP70  
    ```

1. 'ls'コマンドを実行して'RPi-GP70'ディレクトリが作成されていること確認します。  
    ```
    $ ls  
    ```

1. 'cd'コマンドで'RPi-GP70'ディレクトリに移動します。  
    ```
    $ cd RPi-GP70  
    ```  
    
### PythonサンプルファイルをGitHubからダウンロード    
GitHubからPythonサンプルファイルをダウンロードします。  
1. sampleGp70.pyをダウンロード  
    ```
    $ wget https://github.com/ratocsystems/rpi-gp70/raw/master/python/sampleGp70.py  
    ```  

1. `ls`コマンドを実行してPythonサンプルファイル`sampleGp70.py`がダウンロードされていることを確認します。  
    ```
    $ ls  
    sampleGp70.py  
    ```
  
***
## Pythonサンプルファイルについて  
  
`sampleGp70.py`  

RPi-GP70を使用してシリアルの送受信を行うPythonサンプルプログラムです。  
サンプルプログラムでは下記の処理を行っています。  

1. **RPi-GP70の初期設定 init_GP70()**  
    GPIOの初期設定を行います。  
    ※<u>ハードウェアに依存する設定ですので変更しないでください。</u>  
    - GPIOをGPIO番号で指定するように設定  
    - 絶縁回路用電源をONに設定   
        電源ON後、安定するまで待ちます。  

1. **シリアル設定情報変更 input_param( serial )**  
    [pyserialモジュール](https://pythonhosted.org/pyserial/pyserial_api.html#serial.Serial)のシリアル設定パラメータを入力値へ設定変更します。  
    以下のパラメータを指定可能です。変更しない場合はenterのみを入力してください。
    - ボーレート[bps]  
    - バイト長[bit]  
    - パリティ[なし,奇数,偶数,スペース,マーク] ※  
    - ストップビット長[bit]  
    - 受信タイムアウト時間[sec]  
    - フロー制御 XON/XOFF設定[False/True]  
    - フロー制御 RTS/CTS設定[False/True]  
    - フロー制御 DSR/DTR設定[False/True] ※  
    ※ Pyserial 3.5 では、パリティのスペース、マークとフロー制御のDTR/DSRの設定は、本製品には無効です。

1. **メニュー表示**  
    次のメニューを表示します。  
    `1:送受信テスト(RS422全二重) 2:1:送受信テスト(RS485半二重) 3:設定 0:終了 > `  

1. **送受信テスト**  
    メニューで1または2が入力された場合は、シリアル送受信テストを行います。  
    送信ポート番号と受信ポート番号(0,1)を入力します。enterのみでメニューに戻ります。  
    `送信ポート番号(0, 1) enter:戻る > `  
    `受信ポート番号(0, 1) enter:戻る > `  
    メニューで2が入力されていればRS485の半二重モード動作(差動ドライバの自動イネーブル制御)を有効にします。  
    `送信データ入力 enter:戻る > `  
    で、送信する文字列を入力します。送信後に受信文字列を表示します。  
    受信は設定されたタイムアウトが発生するまで継続されます。  
    タイムアウト後に、送信データ入力に戻ります。  
    送信データ入力時にenterのみでメニューに戻ります。  

1. **設定**  
    メニューで3が入力された場合は、シリアル設定を変更します。  
    ポート0とポート1についてシリアル設定情報変更 input_param() を行います。  
  
1. **終了**  
    メニューで0が入力された場合は、プログラムを終了します。  

***
## Pythonサンプルファイルの使い方  
サンプルファイル名の前に、`python3`をつけて実行します。  
- **シリアル送受信テスト**    
    `例) ボーレート115200bpsでポート0からポート1へ折り返し送受信テストをする場合`  
    ~~~  
    $ python3 sampleGp70.py  
    RPi-GP70 検査プログラム  
    1:送受信テスト(RS422全二重) 2:1:送受信テスト(RS485半二重) 3:設定 0:終了 > 3  
    [Port0 現在の設定]  
    Serial<id=0x76a49b90, open=False>(port='/dev/ttySC0', baudrate=9600, bytesize=8, parity='N', stopbits=1, timeout=0.5, xonxoff=False, rtscts=False, dsrdtr=False)  
    設定値を入力 enter:変更なし >  
     baudrate(300,1200,2400,4800,9600,14400,19200,38400,57600,115200,230400,460800,921600) = 115200  
     bytesize(5, 6, 7, 8) =  
     parity('N','E','O','S','M') =  
     stopbits(1, 1.5, 2) =  
     timeout =  
     xonxoff(False, True) =  
     rtscts(False, True) =  
     dsrdtr(False, True) =  
    [Port1 現在の設定]  
    Serial<id=0x76a49bb0, open=False>(port='/dev/ttySC1', baudrate=9600, bytesize=8, parity='N', stopbits=1, timeout=0.5, xonxoff=False, rtscts=False, dsrdtr=False)  
    設定値を入力 enter:変更なし >  
     baudrate(300,1200,2400,4800,9600,14400,19200,38400,57600,115200,230400,460800,921600) = 115200  
     bytesize(5, 6, 7, 8) =  
     parity('N','E','O','S','M') =  
     stopbits(1, 1.5, 2) =  
     timeout =  
     xonxoff(False, True) =  
     rtscts(False, True) =  
     dsrdtr(False, True) =  
    1:送受信テスト(RS422全二重) 2:1:送受信テスト(RS485半二重) 3:設定 0:終了 > 1  
    送信ポート番号(0, 1) enter:戻る > 0  
    受信ポート番号(0, 1) enter:戻る > 1  
    送信データ入力 enter:戻る > ABCD  
    受信データ：ABCD  
    
    送信データ入力 enter:戻る > EFGH  
    受信データ：EFGH  
    
    送信データ入力 enter:戻る > UUUU  
    受信データ：UUUU
    
    送信データ入力 enter:戻る >  
    1:送受信テスト(RS422全二重) 2:1:送受信テスト(RS485半二重) 3:設定 0:終了 > 0  
    ~~~