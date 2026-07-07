+++
date = '2026-07-07T11:37:44+07:00'
draft = false
title = 'Micromouse log day1'
tags = ["Micromouse","Phototransistor"]
categories = ["Kỹ thuật"]
thumbnail = '/img/mlogd1/mlogd1.jpg'
+++

Chả là hè mình vừa bị hủy môn học, nên sẽ có 1 tháng khá là... nhàn. Mình cũng muốn xin vào lab gì đó, cơ mà gpa chưa đủ trọng lượng lắm nên làm một project nhỏ nhỉ?

<!--more-->

## Dở dang micromouse...

Năm ngoái mình có tham gia một cuộc thi micromouse của trường. Đợt đó cũng lười phết, mà quá nhiều ý tưởng muốn làm cùng lúc cộng thêm cái môn OOP nữa (làm mãi không xong). Đâm ra làm cứ loay hoay mãi một phần mà còn bao nhiêu thứ phải tối ưu nữa (tận 1 tuần trước chung kết mình mới đặt pcb, xong lại còn bị báo lỗi hỏng mạch).

Nên là năm nay, chi ít phải phục thù một chút. Kỳ trước học được một tí SE, cũng ngộ ra vài cái ngu đần của mình khi năm ngoái thiết kế micromouse như nào:

![SE](/img/mlogd1/image%20(42).png)

Mình quá tập trung vào tối ưu từng hệ thống một với hy vọng đến chung kết thì mọi thứ sẽ đạt hoàn chỉnh của nó. Xong rồi mải tối ưu hệ thống lái quá (cộng nhận nó ngon thật) thì đến chung kết vội code dò map không kịp tinh chỉnh. Nên lần này sẽ cố làm hoàn chỉnh hẳn một con, rồi sẽ nâng cấp dần qua các phiên bản (dự là tốn kha khá hơn đây TT).

## Thay đổi cảm biến?

Trước mình dùng laser để đọc khoảng cách (vl53l0x), nhưng nó đọc mỗi lần nhanh nhất mất tận 20ms, cũng dùng được thôi nhưng hồi đó mình chưa biết đến RTOS nên để đọc thì phải chịu cái hàm block của nó, thì sẽ ảnh hướng đến vòng 1000hz tính toán các kiểu của mình. Nên lần này sẽ thay sang hồng ngoại để có thể đọc ADC tức thì.

<img src="/img/mlogd1/mlogd1_p.jpg" style="width: 30%; display: block; margin: 0 auto;">

Và cũng do mọi micromouse thiết kế đều dùng IR... Mình có đặt mua mấy con linh kiện 0603 để test luôn xem sao. Nó bé quá sức tưởng tượng, thổi cái là có thể thổi bay luôn rồi. Qua hàn được quả này cũng phải căng mắt nín thở mới dính vào được, xong thì test với cái điều khiển điều hòa thì đọc ADC ngon lành rồi.

Mục tiêu chiều nay hoàn thiện nốt schematic, và nếu có thể thì bố cục xong pcb. Mình vẫn đang nghĩ xem nên dùng pin 2cell cho fullsize hay 1cell để làm halfsize... Nhưng chắc là vẫn sẽ phải làm fullsize thôi, mặc dù muốn làm halfsize đẳng cấp flexin ngầu ngầu =)).