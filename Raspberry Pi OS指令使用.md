## 事先警告:本文是個人善意提供，若遇任何風險還請自行負責


# APT運用
-----------------------------------------
## 更新
```
sudo apt update  (需要時再改成apt-get)
```
## 升級
```
sudo apt upgrade (需要時再改成apt-get)
```
## 完整升級
```
sudo apt full-upgrade (apt-get為另一條指令，無法套用)
```
## 新增 PPA 個人套件庫
```
sudo add-apt-repository ppa:
```
## 移除 PPA 個人套件庫
```
sudo add-apt-repository --remove ppa:
```
## 安裝套件
```
sudo apt install (套件名稱) (需要時再改成apt-get)
```
## 移除套件
```
sudo apt purge (套件名稱) (需要時再改成apt-get)
```
或
```
sudo apt remove --purge '(套件名稱)' (需要時再改成apt-get)
```
## 自動移除套件(相依套件)
```
sudo apt autoremove (需要時再改成apt-get)
```
## 清除之前安裝(install)的安裝檔
```
sudo apt clean (需要時再改成apt-get)
```
## 清除之前下載的安裝檔，但不刪除已安裝軟體的安裝檔
```
sudo apt autoclean (需要時再改成apt-get)
```

# 已知套件
-----------------------------------------
"apt"有問題的話再改成"apt-get"看看<br>

## 注音輸入法
安裝完需重新啟動才能使用
```
sudo apt install fcitx-chewing
```
## NTP手動校準時間
使用方式請查看已知操作中的第4項
```
sudo apt install ntpdate
```
## 支援exFAT(FAT64)
```
sudo apt install exfat-utils
sudo apt install exfat-fuse
```
省略的
```
sudo apt install 'exfat-*'
```
舊版(無法更新)
```
sudo apt-add-repository ppa:relan/exfat
sudo apt-get update
sudo apt-get install 'exfat-utils'
sudo apt-get install 'exfat-fuse'
```
## 支援NTFS
```
sudo apt install ntfs-3g-dev
```
## 印表機
```
sudo apt install libcups2-dev
sudo apt install cups
sudo apt install system-config-printer
```
## 光碟燒錄
K3b(比較推薦)
```
sudo apt install k3b
```
Xfburn(方便操作)
```
sudo apt install xfburn
```
## 防火牆
GUFW(圖形介面，容易使用)
```
sudo apt install gufw
```
UFW(指令輸入，不佔空間)
```
sudo apt install ufw
```
## GNOME磁碟(可執行快速、完整格式化＆關閉磁碟機動作等)
建議！完整格式化請在電源充足的情況(不能出現閃電降壓符號)並且搭配主動式散熱器(風扇+散熱片)使用
```
sudo apt install gnome-disk-utility
```
## GParted(硬碟分割區軟體)
```
sudo apt install gparted
```
## Nautilus檔案瀏覽器(GNOME檔案瀏覽器)
```
sudo apt install nautilus
```
## Audacity(錄音與音訊編輯器)
須搭配USB聲卡使用
```
sudo apt install audacity
```
## Kdenlive(影片編輯器)
```
sudo apt install kdenlive
```
## GIMP(圖像編輯器)
```
sudo apt install gimp
```
## GNOME影像檢視器(可順利跑GIF檔，BCM2835無法)
```
sudo apt install eog
```
## calibre(電子書軟體)
```
sudo apt install calibre
```
## Firefox瀏覽器(Firefox ESR)
```
sudo apt install firefox-esr
```
## Chromium瀏覽器
```
sudo apt install chromium-browser
```
## Back in Time GNOME桌面版(備份還原工具)
```
sudo apt install backintime-gnome
```
## Arduino(Arduino IDE)
ARMv7架構以上才能使用，也就是至少要第二代的樹莓派才能用，Pi Zero系列也是不能使用
```
sudo apt install arduino
```

# 其他指令
-----------------------------------------
## 刪除
```
檔案
(先用"cd"調整該檔資料夾的位置)rm XX.xxx  假如你要刪除/ZZZ/XXX的XX.xxx檔案,用cd定位到/ZZZ/XXX的位置後在用rm刪除該檔案   或是直接指定路徑也可 例如:rm /ZZZ/XXX/XX.xxx
資料夾
(先用"cd"調整該資料夾的位置)rm -r XXX  假如你要刪除/ZZZ/XXX的XXX資料夾，那要用cd定位到/ZZZ的位置在用rm -r把XXX資料夾刪除 或是直接指定路徑也可 例如:rm -r /ZZZ/XXX
```
## 安裝.deb檔
```
(先用"cd"調整該檔資料夾的位置)sudo dpkg -i *.deb
```
## 溫度狀態
```
vcgencmd measure_temp
```
## 時鐘速度狀態
```
watch -n 0 vcgencmd measure_clock arm  ("0"為0.1秒刷新。若改為"1"為1秒刷新、"2"為2秒刷新，以此類推)
```
## 卸載USB
```
sudo eject /dev/sdXX(XX是移除該位置的裝置。可以用"fdisk -l"檢視該裝置的位置)
```
## vchiq影片播放問題
```
sudo chmod 447(最大權限777) /dev/vchiq
```
## 給予使用Bash權限
```
(先用"cd"調整該檔資料夾的位置)chmod u+x P.sh ("P"是檔案名稱，副檔名為".sh")
```
## CPU 10次壓力溫度測試(sh腳本)
```
(來自ExplainingComputers.com)
#! /bin/bash
clear

for x in {1..10}
do
  vcgencmd measure_temp
  sysbench --test=cpu --cpu-max-prime=20000 --num-threads=4 run >/dev/null 2>&1
done
 
vcgencmd measure_temp
```
# vi簡單用法
-----------------------------------------
## 操作模式
```
a 由游標之後進行寫入模式
```
```
i 由游標之前進行寫入模式
```
```
o 新增一行於該行之下進行寫入模式(如同Enter鍵後開始打字)
```
```
x 刪除游標該字
```

```
dd 刪除游標該行
```
```
yy 複製游標該行文字
```
```
p 在游標新增下一行並貼上複製的文字
```


```
:w 存檔
```
```
:q 退出
```
```
:x 存檔後離開(僅當檔案被修改時才寫入,並更新檔案修改時間,否則不會更新檔案修改時間)
```
```
:wq 存檔後離開(強制更新檔案的修改時間)
```
```
!為強制性，在字母後輸入。示範 :q! 就是強制退出 :w! 就是強制存檔
```

```
:new 開啟視窗(水平)
```
```
:vnew 開啟視窗(垂直)
```
```
[Ctrl]+[w]+[w] 切換視窗
```
```
:?a   a代表所有視窗的意思    範例>>   :qa為所有視窗關閉   :qa!為所有視窗強制關閉   :wa為所有視窗寫入   :wqa!為所有視窗強制寫入關閉   ...依此類推
```
## 寫入模式
```
[Esc] 退出寫入模式到操作模式
```

# 其他操作(Terminal終端機)
-----------------------------------------
##### > (建立檔案)
##### touch (建立檔案或修改檔案時間)
##### cat (瀏覽或編輯文字檔)
##### cat>文字檔 (新增文字檔或覆蓋原有的文字並編輯)
##### cat>>文字檔 (編輯加入文字而不覆蓋原有的文字)
## 鍵盤動作
##### [Ctrl]+[D] (存檔在cat編寫的文字)
##### [Ctrl]+[C] (中止目前的執行)
##### [Ctrl]+[Shift]+[C] (複製，相當於一般在用的[Ctrl]+[C])
##### [Ctrl]+[Shift]+[V] (貼上，相當於一般在用的[Ctrl]+[V])
