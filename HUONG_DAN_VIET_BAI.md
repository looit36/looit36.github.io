# HƯỚNG DẪN VIẾT BÀI VÀ QUẢN LÝ BLOG HUGO

Tài liệu này lưu lại các lệnh và cú pháp cơ bản để bạn viết bài mới một cách nhanh chóng.

## 1. Cách Tạo Một Bài Viết Mới

Mở Terminal (hoặc PowerShell) tại thư mục gốc của blog (`c:\Users\Admin\blog`) và chạy lệnh:

```bash
hugo new posts/ten-bai-viet-viet-khong-dau.md
```
*(Ví dụ: `hugo new posts/chuyen-di-da-lat-2026.md`)*

File bài viết sẽ tự động được tạo ra tại thư mục: `content/posts/`.

---

## 2. Định Dạng Của Một Bài Viết (Front Matter)

Khi mở file bài viết vừa tạo, bạn sẽ thấy phần đầu tiên nằm giữa hai dấu `+++` như thế này (đây là định dạng TOML):

```toml
+++
title = "Tiêu đề bài viết hiển thị trên web"
date = 2026-07-07T11:37:44+07:00
draft = false

# Phân loại bài viết (Thẻ tags & Chuyên mục)
tags = ["Micromouse", "STM32"]
categories = ["Kỹ thuật"]

# Ảnh bìa của bài đăng (để trong thư mục static/img/)
thumbnail = "img/anh-bia-demo.png"

# Dòng mô tả ngắn gọn hiển thị dưới tiêu đề bài viết
lead = "Dòng mô tả ngắn gọn hiển thị dưới tiêu đề bài viết"
+++
```

**Lưu ý khi viết bằng TOML (`+++`):**
* Sử dụng dấu bằng `=` thay vì dấu hai chấm `:` để gán giá trị (ví dụ: `draft = false`).
* Các chữ viết phải nằm trong dấu ngoặc kép hoặc ngoặc đơn (ví dụ: `title = "Tiêu đề"`).
* **`draft = false`**: Bạn PHẢI đổi thành `false` thì bài viết mới được hiển thị trên trang web thực tế.
  * *Lưu ý:* Khi chạy thử ở máy cục bộ bằng lệnh `hugo server -D`, cờ `-D` (Draft) sẽ ép hệ thống hiển thị cả các bài viết đang để `draft = true`. Do đó bạn sẽ thấy chúng giống nhau ở máy cá nhân, nhưng khi đẩy lên GitHub (web thật), bài viết có `draft = true` sẽ **bị ẩn đi**.
* **`tags` & `categories`**: Các giá trị được bọc trong cặp ngoặc vuông `[]` và ngăn cách bởi dấu phẩy `,` (ví dụ: `tags = ["tag1", "tag2"]`).
* **`thumbnail`**: Chỉ ra đường dẫn tương đối của ảnh bìa tính từ thư mục `static/` (ví dụ: ảnh để ở `static/img/cover.jpg` thì khai báo là `"img/cover.jpg"`).

---

## 3. Định Dạng Ảnh Phù Hợp

Để trang web của bạn tải nhanh và mượt mà, hãy chọn định dạng ảnh phù hợp:
1. **WebP (`.webp`)**: **Khuyến nghị nhất**. Ảnh siêu nhẹ giúp web load cực nhanh mà chất lượng vẫn rất nét.
2. **PNG (`.png`)**: Thích hợp cho ảnh chụp màn hình code, sơ đồ mạch điện, hình vẽ có chữ để chữ không bị nhòe.
3. **JPEG/JPG (`.jpg`)**: Thích hợp cho ảnh chụp máy ảnh thông thường, phong cảnh (dung lượng nén tối ưu hơn PNG cho ảnh chụp thực tế).
4. **SVG (`.svg`)**: Tốt nhất cho các icon, logo (phóng to không bao giờ bị vỡ).

*Mẹo: Bạn có thể lưu ảnh vào thư mục `static/img/` rồi gọi ra bằng cú pháp Markdown: `![chú thích ảnh](/img/ten-anh.png)`.*

---

## 4. Viết Nội Dung (Markdown)

Bạn viết nội dung bài ngay dưới dấu `+++` cuối cùng.

* **Tạo đoạn trích dẫn (Read more / Summary):**
  * **Mặc định (Tự động):** Nếu không cấu hình gì thêm, Hugo sẽ tự động lấy khoảng **70 từ đầu tiên** của bài viết, bỏ qua các heading và hình ảnh để hiển thị làm tóm tắt ngoài trang chủ.
  * **Chủ động ngắt đoạn bằng thẻ `<!--more-->` (Khuyên dùng):** Bạn chèn thẻ này vào bất kỳ vị trí nào trong bài viết. Toàn bộ nội dung phía TRÊN thẻ này sẽ làm tóm tắt ngoài trang chủ, nội dung phía DƯỚI sẽ bị ẩn và chỉ hiện khi người đọc click vào bài viết.
  
  *Ví dụ:*
  ```markdown
  Đây là phần mở đầu muốn hiển thị ở trang chủ.
  
  <!--more-->
  
  ## Đây là tiêu đề thân bài
  Phần này và các phần tiếp theo sẽ bị ẩn ở trang chủ, người đọc phải bấm vào xem chi tiết mới đọc được.
  ```

* **Chèn ảnh mặc định:**
  Copy file ảnh của bạn vào thư mục `static/img/` (ví dụ: `static/img/hinh-anh.jpg`).
  Gọi ảnh ra trong bài viết bằng cú pháp Markdown:
  ```markdown
  ![Chú thích cho ảnh](/img/hinh-anh.jpg)
  ```

* **Chỉnh kích thước và căn giữa ảnh (Khuyên dùng):**
  Vì trang web của bạn đã được bật tính năng biên dịch HTML trực tiếp, bạn hãy sử dụng thẻ `<img>` của HTML thay vì cú pháp Markdown để chỉnh kích thước:
  
  * **Chỉnh theo Pixel (Ví dụ rộng 500px):**
    ```html
    <img src="/img/hinh-anh.jpg" alt="Chú thích ảnh" width="500">
    ```
  * **Chỉnh theo phần trăm & Căn giữa màn hình:**
    ```html
    <img src="/img/hinh-anh.jpg" alt="Chú thích ảnh" style="width: 60%; display: block; margin: 0 auto;">
    ```

---

## 4. Xem Thử Ở Máy Cá Nhân (Local)

Trước khi up lên mạng, bạn có thể xem thử bằng lệnh:

```bash
hugo server -D
```
*(Chữ `-D` viết tắt của Draft, nó sẽ hiển thị luôn cả các bài nháp đang để `draft: true`)*

Mở trình duyệt và vào đường dẫn: **http://localhost:1313**
Xem xong thì nhấn `Ctrl + C` ở terminal để tắt.

---

## 5. Xuất Bản Lên Web (Đẩy Lên GitHub)

Khi đã ưng ý, chạy lần lượt 3 lệnh sau để đưa bài viết lên mạng:

```bash
git add .
git commit -m "Thêm bài viết mới: Tiêu đề bài"
git push origin main
```

Chờ khoảng 30 giây đến 1 phút, GitHub sẽ tự động build lại trang web. Bạn truy cập **https://looit36.github.io** là sẽ thấy bài viết mới của mình!
