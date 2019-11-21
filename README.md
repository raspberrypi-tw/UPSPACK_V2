# UPSPack V2 產品軟硬體使用指南

![](https://github.com/rcdrones/UPSPACK_V2/wiki/images/ups.JPG)

## 產品介紹
樹莓派是一款單板電腦(SBC, Single Board Computer)，本身和 Linux 電腦的應用很相近。所有的系統都跑在 microSD 卡上。但是當外部突然斷電時，microSD 上的系統資訊(或者使用者資訊)面臨丟掉的可能，從而導致系統無法啟動的後果。此外樹莓派由於本身體積較小，在攜帶式的應用中，常需要一個合適的行動電源對樹莓派供電。基於以上的考慮，RPi Club 設計了這款 UPSPack V2 的產品，你可以把它當作行動電源來使用，亦可以當作樹莓派的不斷電電源來使用。除此以外，V2 版本提供了序列埠通訊，和 I/O 通訊的界面，可以和樹莓派進行資訊交換。讓跑在 Linux 系統上的體可以得知 UPS 上的硬體/電池資訊。從而決定關機的時間點，亦可向雲端回報外部供電異常等資訊。

## 電池的續航測試
UPSPack 上的電池界面是 PH2.0。產品提供了 3 種不同容量的電池。使用者也可以可自行接不同容量，標準電壓為 3.7V 的鋰聚合物軟性電池，或者是 3.7V 18650 電池組。注意：輸入 UPS 電池界面的電壓範圍必須是小於等於 4.2V。（言外之意：所有電池組必須是並聯關係，不能把電芯串聯）。我們測試了不同的應用組合，得到的續航資訊。供給使用者參考不同的電池容量：

|  容量  |   Pi4單機  |  Pi4搭載7吋DSI螢幕  |  Pi3B+搭載3.5吋GPIO螢幕  |  Pi3B+搭載5吋HDMI螢幕  |  Pi3B+搭載7吋HDMI螢幕  |  Pi3B+搭載官方7吋DSI螢幕  |
|--------|------------|-----------------------|------------------------|----------------------|----------------------|-------------------------|
|3800mAh |  4.2h     |      2.3h              |   4.4h                |     3.2h             |          2.0h         |        4.7h             |
|6500mAh |   7.5h     |  4.2h                 |   7.0h                 |     5.8h             |          3.3h       |        7.7h              |
|10000mAh |   11.6h      |  6.5h                |   11.6h                 |     9.0h              |          5.8h         |        13.0h             |
### 備註：
1. 以上所有資訊單位為小時(hours)。
2. 執行的系統為：Raspbian Buster with desktop and recommended software Version:July 2019 Release date:2019-07-10 ，系統不做任何設定修改。
3. 3 種容量的電池完全充滿電量，然後接上樹莓派，利用程式紀錄時間。放電截至點為 UPS 檢測到電池電壓低於 2.8V，電池保護板截至放電為止。
4. 下載、並執行 UPSPACK_V2/time_count/RPi_runtime_recoder.py 進行時間記錄。當樹莓派關機後，接上其他電源轉接器讀取目錄下的 log.txt 查看續航時間。


## 歷史介紹
UPSPack V2 是在 UPSPack V1 版本的基礎上，增加了 UPS 主板和樹莓派主板進行交互通訊的能力。可以觀測到當前 UPS 上的電池電量、外部是否停電、系統輸出電壓是否正常等資訊。作為執行在樹莓派系統上的軟體，通過得到的這些綜合性的資訊，實現軟體關機的功能(防止 microSD 卡上的文件丟掉）、亦可向指定 Email 發送關機或是停電等資訊，讓使用者在手機上得到重要提醒。為後續處理帶來方便。

### 硬體參數
1. Micro USB 輸入電壓：5.1V 2-3A。電源轉接器輸出電流。
2. 2 個 USB-A/5V GPIO 排針： 輸出電壓為 5.1V±0.1V ，所有界面輸出電流最大合計為：3.0A
3. 帶 1 個 UART 序列埠，Baudrate：9600 8N1
4. 帶 1 個 I/O 輸出，高電位：表示電池工作正常。 低電位：表示電池即將消耗完畢。
5. 電池輸出界面為： PH2.0
6. 4 顆電量 LED 燈，1 顆 PMU 工作狀態燈，1 顆外部輸出電源燈。
7. 1 個外部輸出開關，用於控制 PMU 對外輸出的電壓。
8. UPS 板設計有恢復保險絲，並且 3 款電池內部都有鋰電池保護板。防止過充和過放。

### 機械尺寸
UPSPack V2 和樹莓派 4 代/3 代的孔徑和位置是一致的。所以可以直接用 M2.5 銅柱安裝在Pi4（Pi3）主板上。

## 產品使用指南
![](https://github.com/rcdrones/UPSPACK_V2/wiki/images/wire.JPG)  
進入[Wiki](https://github.com/rcdrones/upspack_v2/wiki)進行學習


## 合作夥伴
* [Amazon](https://www.amazon.com/MakerFocus-Raspberry-Standard-Expansion-Cellphone/dp/B01LAEX7J0)
* [RICELEE](https://ricelee.com/product/raspberry-pi-ups-lithium-battery-expansion-board)
* [EBAY](https://www.ebay.com/itm/UPS-Raspberry-Pi-Lithium-Battery-Expansion-Board-with-3800mAh-Lithium-Battery-/173685870116?_trksid=p2385738.m4383.l4275.c10)
* [AliExpress](https://www.aliexpress.com/item/UPS-Lithium-Battery-Expansion-Board-with-3800mAh-Lithium-Battery-for-Raspberry-Pi-Durable/32990788550.html)
* If you will like be partnership with us , contact us via email: rcdrones#163.com (# -> @)

