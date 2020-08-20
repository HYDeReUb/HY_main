## 事先警告:本文是個人善意提供，若遇任何風險還請自行負責
----------------------------------
# 硬件警告與散熱
## 降電壓
![image](https://github.com/HYDeReUb/HY_main/blob/master/Picture%20Saved/under_volt.png)
```
這代表著電力提供不足而導致終點端電壓過度下降(低於4.63V (+/-5%))，會調降CPU時鐘性能，需要更換符合指定的線材跟電源，若不需要太麻煩可以直接買他們的電源直接來用即可
```
```
造成的影響:會影響USB跟SD卡的運作，長期使用下會有損壞的可能性
```
## 溫度過高(80~85°C)
![image](https://github.com/HYDeReUb/HY_main/blob/master/Picture%20Saved/over_temperature_80_85.png)
```
這代表著溫度已經到達80~85°C，會調降CPU時鐘性能，需要更換或使用主動式散熱或被動式散熱
```
```
造成的影響:可能導致機器跟週邊的運行壽命縮短
```
## 溫度過高(85°C以上)
![image](https://github.com/HYDeReUb/HY_main/blob/master/Picture%20Saved/over_temperature_85.png)
```
這代表著溫度已經到達85°C以上，會調降CPU跟GPU時鐘性能，建議立即關機散熱，並更換或使用主動式散熱或被動式散熱
```
```
造成的影響:可能導致機器跟週邊的運行壽命縮短甚至損壞
```
## 主動式散熱
![image](https://i.ytimg.com/vi/5Ud-grj4Zl0/maxresdefault.jpg)
```
用風扇把熱氣帶走，需要時可以加散熱片一起使用
```
```
好處:可以維持一定溫度不再上升
適合:長時間運算操作、超頻玩家、保持低溫運作等
```
## 被動式散熱
![image](https://i.ytimg.com/vi/VJC6OpGpq0Y/maxresdefault.jpg)
```
純粹利用散熱片把熱導出來並慢慢消去而無使用風扇
```
```
好處:由於不需風扇，降低了耗電並增加了安靜感
適合:短時間運算操作、長時間待機、後續清理容易等
```
------------------------------------------------
# Raspberry Pi已知操作
## 1.初始使用Raspberry Pi
### 下載區
一開始不確定要用哪個系統和不會燒錄SD卡者，可以選NOOBS使用<br>
若確定要使用哪個系統但猶豫選擇或不太會操作燒錄軟體者，推薦他們自家的 Raspberry Pi Imager
```
https://www.raspberrypi.org/downloads/
```
### 保護您的Raspberry Pi(Raspberry Pi OS)
在基礎設定下完成之後，由於裡面設定還是預設狀態，而預設用戶pi跟Windows的Administrator權限相當，可能會有入侵風險(帶有防火牆的路由器雖安全，但也建議做)，下列操作是個人增加安全性的方法
```
1.用passwd更改pi的密碼

2.安裝"GUFW"或是"UFW"防火牆套件。"GUFW"請查看下面2-1說明，"UFW"請詳細參見第二個網址並設定
2-1.使用"sudo apt install gufw"來安裝"GUFW"後，去"開始(樹莓派LOGO)>偏好設定>防火牆設定"中把"狀態"啟動並確定"內送"為"拒絕"、"外送"為"允許"，這樣就算是完成了

3.開始新增使用者名稱(也就是之後主要的用戶)並給予權限(詳細參見第一個網址的3、4條指令)

4.要求pi用戶使用sudo時要用戶密碼(詳細參見第一個網址的9、10條指令，vi的用法在倒數第二個)

5.使用sudo passwd指令來設定UNIX密碼(就是超級使用者(root)的密碼，權限跟Administrator相當，之後若把Pi鎖住或刪除時剛好sudo權限突然無法使用時，這應該是唯一後路了)(之後要切入超級使用者模式時，輸入su指令後打UNIX密碼即可進入超級使用者(root)模式，符號會從＄變成＃，若非必要盡量別常用)(設定後可能會有鎖定目標暴力破解的問題，可以去看第三個網址來防止遠端SSH登入root的問題，雖然已經有UFW防護就是了...)

6.切換使用者後用sudo passwd --lock pi來鎖定pi(解鎖sudo passwd --unlock pi)，或刪除pi(詳細參見第一個網址的6~8條指令)，但我不建議對pi做刪除的動作，以防跟pi有關的問題發生
```
```
https://www.raspberrypi.org/documentation/configuration/security.md
```
```
https://www.taiwaniot.com.tw/%E6%8A%80%E8%A1%93%E6%96%87%E4%BB%B6/%E6%A8%B9%E8%8E%93%E6%B4%BE%E6%8A%80%E8%A1%93%E6%96%87%E4%BB%B6/%E6%A8%B9%E8%8E%93%E6%B4%BE%EF%BC%8Draspberry%EF%BC%8C%E5%85%A7%E7%BD%AE%E7%9A%84%E9%98%B2%E7%81%AB%E7%89%86ufw%E8%A8%AD%E7%BD%AE%E5%92%8C%E5%95%9F%E7%94%A8/
```
```
https://blog.gtwang.org/linux/howto-disable-ssh-root-login-in-linux/
```
若在新用戶裡無法使用sudo時，可查看下面網址
```
https://www.itread01.com/content/1532680819.html
```
## 2.把USB儲存裝置當主硬碟開機
### 注意:本篇針對Raspberry Pi 4 Model B做說明，其他Raspberry Pi需自行尋找操作方式
### 注意:這裡的操作只對Raspberry Pi OS有效而已，NOOBS跟其他OS可能無效
### 警告:本操作具有一定的風險性，若稍有錯誤可能會有開不了機的情況。請謹慎操作
```
網址提供:

https://www.raspberrypi.org/documentation/hardware/raspberrypi/bcm2711_bootloader_config.md#usbmassstorageboot

https://www.youtube.com/watch?v=2zrwjGcyM5s
```
```
說明:
在這兩個資訊中，我推薦先看第二個網址(影片中的Firmware Update)然後再看第一個網址(USB-MSD firmware setup instructions的部份)，下面會配合影片的部份說明

1.在打開"bootloader"資料夾後，要選擇"stable"資料夾而不是影片的"beta"資料夾，因為該影片發布時還沒有穩定版可用

2.輸入"vcgencmd bootloader_version"後，他指定的第一行是要確認eeprom中的最後套件升級時間，而要支援USB開機就是要手動更新eeprom套件(如果日期是2020-6月多可以從6-1開始試)

3-1.而他接下來做的事情，其實中間省略的一個步驟，這個在他的說明欄最後兩段話有說明，我個人也是遵循他的方法(詳見4-3)，如果想按照官方作法，請看3-2，否則跳過
3-2.使用"su"切換為root模式時，輸入"vi /etc/default/rpi-eeprom-update"並將"critical"改為"stable"，這個在第一個網址裡"Update the bootloder"裡的第二行"As root, edit"那一部分

4-1.輸入"sudo rpi-eeprom-update -d -f "後，把"stable"點開來後找"pieeprom"開頭後面日期比較新的，並把該檔案的路徑打上去，不懂可以看4-2範例修改
4-2.ex:"sudo rpi-eeprom-update -d -f /lib/firmware/raspberrypi/bootloader/stable/pieeprom-2020-07-16.bin"
4-3.在3-1提到會做不更動的動作是因為做"sudo rpi-eeprom-update -d -f "的"-d -f"強制動作時就會忽略rpi-eeprom-update的範圍設置，若選擇為"stable"未來的可能會接收到"stable"版的更新套件
而不是原始的"critical"版套件，相對選"critical"若更新eeprom套件時可能會有刷回去一開始無法使用USB開機的風險(不過就情況來看是很小的，通常偵測到更新的固件日期是不會有用舊換掉新的情況)，
穩定程度"critical">"stable">"beta"(關鍵>穩定>測試)

5-1.完成之後照影片方式重新啟動
5-2.再次輸入"vcgencmd bootloader_version"查看是否和"pieeprom"後寫的日期一致

6-1.在影片的15:12中，插入日後要當主硬碟USB裝置後，並注意SD Card Copier的Copy from跟Copy to(from是指來源，to是指定到)，一旦反了可能就變成SD卡的資料消失了
6-2.假如SD卡或USB裝置資料真的搞消失了日後也不需要在做4-1跟4-2的步驟，3-2若一開始有去改的話再去改一下就可以了

7.copy完成後先關機並切斷電源，然後把SD卡抽走後在通電開機，若能成功進入彩屏畫面就表示成功了
```
## 3.定期備份系統資料
### 建議:最好主系統硬碟是外接USB的SSD而非Micro SD卡
### 注意:這是我嘗試出來的結果，不確定是否真的有用
///這可以備份自己的檔案到其他地方，算是相當方便，不過這要自行發揮了///
```
1.使用"sudo apt install backintime-gnome"進行安裝

2.安裝好後，去"開始(樹莓派LOGO)">"系統工具">"Back In Time(root)"輸入root或pi的密碼

3.去"snapshot">"設定"

4.設好"快照存放位置"跟排程時間

5.點擊"包含"後並點"Modify for Full System Backup"確認有跑出一個"/"的資料夾

6.點擊"不包含"後點擊"新增資料夾"將路徑"/home"跟"/media"加入除外名單中

7.點擊"自動移除"後打勾"時間超過"並設定你要它自動刪除的天數，我幾乎每天都用所以是輸入5並選擇天，也就是5天後的檔案會自動刪除，下面的"剩餘空間少於"跟"If free inodes is less than"打勾並保持
默認值就好(或者這兩個可不勾?我是不太清楚)

8.確認設定的資料沒問題後點擊"OK"即可完成，只要到了或超過你指定的時間就會開始備份

9.若想還原的話，去"開始(樹莓派LOGO)">"系統工具">"Back In Time(root)"輸入root或pi的密碼後，點擊要還原快照的日期時間，按上方"還原">"還原"，跳出視窗後點擊Yes(勾的用途我不太確定，所以沒去勾)即可還原
```
---------------------------------------
# Raspberry Pi 4 Model B已知問題
## USB部份
``` 
1.若要提供SSD、HDD、光碟機這樣的高耗電外接裝置時，在足夠電力的情況下只能選一個來使用，若同時使用兩個多半會有不夠電的問題發生
2.若上述要使用2個以上時，只能接HUB並確保線材與電源提供電量充足
3.使用像Argon one有帶電源鍵的外殼，若在HUB有接電源的情況下可能會有開不了機的情況，重新插拔HUB的電源線即可解決
```
## 音訊部份
```
1.使用音效卡只能打開一個音訊程式，打開第二個會顯示忙碌或錯誤
2.若有用Argon one外殼，要注意音訊孔有些可能會插不夠深，導致只有單喇叭播放
3.連續對VLC播放器做跳轉動作可能會有短暫降音的情況
```
## 其他部份
```
1.建議在執行格式化或移動檔案這樣的操作時，別執行其他程式來多工操作，避免使用量過高強關或重起導致資料毀損
2.GPIO不要做熱插拔的動作，更不能短路3V3接腳，否則易造成損壞(Raspberry Pi 3 Model B+只要GND或5V去接觸3V3接腳，直接掛點!)
```
