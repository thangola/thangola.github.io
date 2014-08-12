---
layout: post
title: "single mode trong grub2 ubuntu 12.04 & 14.04"
date: 2014-08-12 12:07:45 +0700
comments: true
categories: linux boot, grub,sysadmin
---

Nếu bạn lâu ngày không vào server ubuntu mà quên mất password root, đừng lo, đã có single mode :))
Sau đây là các bước để vào single mode trong ubuntu 12.04 ( 14.04 cũng được nà )
<br>

Bước 1: Lúc bật máy lên bạn giữ phím shift  để vào màn hình grub2 load  <br />
Bước 2: Chọn phiên bản kernel  <br />
Bước 3: Nhấn e để edit các tham số trong grub2  <br />
Bước 4: Chuyển con trỏ xuống cuối dòng bắt đầu bằng **linux /boot/vmlinuz......**   <br />
Bước 5: Thay các từ như **['ro', 'quiet', 'spalsh']** bằng cụm sau **rw init=/bin/bash**  <br />
Bước 6: Nhấn Ctrl + x để boot với chế độ single mode  <br />
Bước 7: thích làm gì thì làm.hihi :-)  <br />
Bước 8: sync & reboot <br />


Note: **Đôi lúc 1 số service của bạn bị hang lúc boot và server không thể khởi động lên được ( eg: redis) bạn có thể dùng cách này để vào disable auto start của service đó đi**

-Rd
Nhan
