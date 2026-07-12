+++
date = '2026-07-12T16:24:00+07:00'
draft = false
title = 'Micromouse log day2'
tags = ["Micromouse","Encoder"]
categories = ["Kỹ thuật"]
thumbnail = '/img/mlogd2/IMG_7701.jpg'
+++

Không hiểu sao led ir kẹt ở kho ship cả mấy ngày, encoder về trước nên hôm nay ta sẽ test tạm xem sao nhé.

<!--more-->

## Chính thức "có học"!!!

Sau vài hôm mail năn nỉ phòng đào tạo, thì cuối cùng cũng được thêm lại vào lớp. 

![SE](/img/mlogd2/image.png)

Thế là vài ngày cuối ở quê trước khi lên Hà Nội mình lại tranh thủ đi chơi tí, vì ít nhất nghĩ được là hè này không phế vật lắm hehe.

## Thay đổi motor và encoder

Con cũ của mình sử dụng motor n20 kèm với encoder, cơ mà nó nhỏ bé yếu quá, kèm theo bộ giảm tốc của khiến cho chiều dài tổng thể quá lớn, hơn nữa cũng chỉ có 7PPR, nên mình đang tìm cách thay thế bằng motor coreless và encoder từ.

Sau vài ngày tìm hiểu thì mình tìm được loại MT6701, nó có xuất ra SSI, trễ 5us đầu ra, max rotation 55k Rpm, và khi chuyển sang mode xung AB, có thể đạt 1024PPR!!! Ăn đứt AS5600 về mọi mặt, giá thì chỉ chênh nhau 10k. Đặt vội 2 cái thì hôm nay nó cũng về hàng.

Module bán sẵn này người ta đang mắc chân mode mức cao cho mode I2c, nên mình sẽ cấu hình cho nó thành ABZ trước đã. Lưu vào EEPROM con này phải cho VDD lên quanh 4.5 - 5.5V, loay hoay một hồi không biết kiểu gì cháy luôn cái đường nguồn từ USB của con STM32... May còn cái mạch ESP32 được ông anh tặng cho nghịch, câu tạm đường 5V từ USB ra rồi nạp từ ESP thôi:

![SE](/img/mlogd2/IMG_7708.jpg)

Sau đó thì phải cạo cái đường mạch nối chân mode lên VDD đi:

![SE](/img/mlogd2/IMG_7705.jpg)

Rồi câu dây nối xuống GND, bỏ 2 con trở pull-up là chuyển qua mode ABZ được rồi:

![SE](/img/mlogd2/IMG_7701.jpg)

Gắn nam chân lên motor, sau đó cho nó quay chậm tí rồi dí vào, đọc ngon ơ (thế mà mất cả buổi chiều)

![SE](/img/mlogd2/IMG_7710.jpg)

Đoạn này là ESP32 đọc được xung rồi, định cắm lại bên STM32 test thì cái que hàn lăn ra hỏng (-_-) nên không test được gì thêm nữa.

Xem ra có khi mình vẽ luôn pcb đi cho lành, phèn phèn tí cũng được rồi để xem có những bệnh gì mình lại sửa từ nó tiếp. Thì cũng là nâng cấp dần qua từng phiên bản hehe. Nên giờ ta sẽ tập trung vẽ 3d thử cái ngàm gắn bánh xe, rồi sau đó là pcb.

Đúng là vua trì hoãn!!!
