---
title: 駭遠傳給的 RTL6100W
description: 駭進去遠傳提供的神秘 Dynalink RTL6100W，一個奇怪的東西
---
# 駭進去遠傳提供的 Dynalink RTL6100W

## 連結：
- GitHub Repo: [hpware/hacking-RTL6100](https://github.com/hpware/hacking-RTL6100)
- GitHub Issues [Issues](https://github.com/hpware/hacking-RTL6100/issues)
- 畫的大慨圖： [drawings](/drawings.md)
- 資訊來源: [sources](/sources.md)

## 已知
1. 這是被改的 Dynalink RTL0100CT，移除 WAN 孔 (如果不想再繼續使用把Sim 卡當網路，他就會變成 ewaste)
2. 有一個多餘的 LAN 孔（在 RTL0100CT 也是）， 而且可以增加
3. LAN 孔可以變成「WAN」孔，如果你不要更改其他設置，這個適合
4. Dynalink RTL0100CT 和 Dynalink RTL6100 使用的 ROM 不一樣
5. 把後面的 LTE PCIE 的東西移除無法開機，就像電源會先到那邊去再送電到其他的東西，如果你想插你已經有的 WiFi卡 or 硬碟 有 99% 會壞掉。
6. 他用的膠，可以使用一個扁的Screwdriver (Flathead Screwdriver)，並把它斷開，就可以看到裡面。

## 神秘的 Micro-B 孔
這個感覺是一個給開發者刷程式/進入 ADB 的孔 (對這個跑 Android)，但是 `./adb devices` 沒有顯示，而且他在開機後2秒就消失了。

## 晶片
這個 RTL6100 主要使用這些晶片：
- Realtek RTL8367 (交換器的晶片)
- Realtek RTL8197 (提供 WiFi 2.4GHz 的訊號 支援 802.11b/g/n)
- ASIX AX88179 (把 Android 的熱點變成網路孔，啊難怪需要交換器的晶片)
- 