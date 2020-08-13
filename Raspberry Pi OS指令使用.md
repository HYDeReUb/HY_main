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
## 支援exFAT(FAT64)
```
sudo apt install exfat-utils
sudo apt install exfat-fuse
```
#### 省略的
```
sudo apt install 'exfat-*'
```
#### 舊版(無法更新)
```
sudo apt-add-repository ppa:relan/exfat
sudo apt-get update
sudo apt-get install 'exfat-utils'
sudo apt-get install 'exfat-fuse'
```
<br>
## 支援NTFS
```
sudo apt install ntfs-3g-dev
```
<br>
## 印表機
```
sudo apt install libcups2-dev
sudo apt install cups
sudo apt install system-config-printer
```
<br>
## 光碟燒錄
注意!!請在足夠的電源下再使用光碟機!!!
### K3b(比較推薦)
```
sudo apt install k3b
```
### Xfburn(易於操作)
```
sudo apt install xfburn
```
<br>
## 防火牆
### GUFW(圖形介面，易於使用)
```
sudo apt install gufw
```
### UFW(需指令輸入，容量不佔空間)
```
sudo apt install ufw
```
<br>
## GNOME磁碟(可執行快速、完整格式化＆關閉磁碟機動作等)
建議！完整格式化請在電源充足的情況(不能出現閃電降壓符號)並且搭配主動式散熱器(風扇+散熱片)使用
```
sudo apt install gnome-disk-utility
```
<br>
## GParted(硬碟分割區軟體)
```
sudo apt install gparted
```
<br>
## Nautilus檔案瀏覽器(GNOME檔案瀏覽器)
```
sudo apt install nautilus
```
<br>
## Audacity(錄音與音訊編輯器，須搭配USB聲卡使用)
```
sudo apt install audacity
```
<br>
## Kdenlive(影片編輯器)
```
sudo apt install kdenlive
```
<br>
## GIMP(圖像編輯器)
```
sudo apt install gimp
```
<br>
## GNOME影像檢視器(可順利跑GIF檔，BCM2835無法)
```
sudo apt install eog
```
<br>
## calibre(電子書軟體)
```
sudo apt install calibre
```
<br>
## Firefox瀏覽器(Firefox ESR)
```
sudo apt install firefox-esr
```
<br>
## Chromium瀏覽器
```
sudo apt install chromium-browser
```
<br>
## Back in Time(備份還原工具)
```
sudo apt install backintime-gnome
```
<br>
# 其他指令
-----------------------------------------
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
