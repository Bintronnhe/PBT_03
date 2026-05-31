#### Câu A1 (5đ) — 3 Cách nhúng CSS

Dựa trên nội dung Chương 08 và yêu cầu từ hình image_8a6dc1.png, dưới đây là chi tiết về 3 phương thức nhúng CSS vào HTML:

* **Inline CSS (CSS trực tiếp trong thẻ):**
    * **Ví dụ code:** `<h1 style="color: blue; font-size: 20px;">Chào Minh!</h1>`
    * **Ưu điểm:** Áp dụng nhanh cho một phần tử cụ thể mà không cần viết selector.
    * **Nhược điểm:** Khó bảo trì, làm code HTML bị rối và không thể tái sử dụng style.
    * **Khi nào nên dùng:** Khi cần định dạng nhanh cho duy nhất một phần tử hoặc debug gấp.

* **Internal CSS (CSS nội bộ):**
    * **Ví dụ code:**
```html
    <style>
      p { color: red; line-height: 1.5; }
    </style>
    ```
    * **Ưu điểm:** Quản lý toàn bộ style của một trang trong một file HTML duy nhất.
    * **Nhược điểm:** Làm file HTML nặng hơn và gây lặp code nếu website có nhiều trang.
    * **Khi nào nên dùng:** Phù hợp cho Landing Page đơn lẻ hoặc các bài tập nhỏ.

* **External CSS (CSS bên ngoài):**
    * **Ví dụ code:** `<link rel="stylesheet" href="style.css">`
    * **Ưu điểm:** Tách biệt nội dung và giao diện, dễ bảo trì, trình duyệt load nhanh hơn nhờ cache.
    * **Nhược điểm:** Tốn thêm yêu cầu HTTP để tải file, style bị mất nếu file CSS lỗi.
    * **Khi nào nên dùng:** Cách chuẩn nhất, dùng cho mọi dự án thực tế và chuyên nghiệp.

---

**Câu hỏi thêm: Nếu cùng 1 element có cả 3 cách CSS đồng thời áp dụng, cách nào "thắng"? Giải thích tại sao.**

* **Cách "thắng":** **Inline CSS** (CSS trực tiếp trong thẻ).
* **Giải thích:** Theo quy tắc **Cascading (Độ ưu tiên)**, CSS ưu tiên theo thứ tự từ gần đến xa. Inline CSS nằm ngay trong thẻ nên có trọng số ưu tiên cao nhất so với Internal và External.
#### Câu A2 (8đ) — CSS Selectors — Dự đoán kết quả

Dựa trên đoạn mã HTML đã cho và yêu cầu từ hình image_8a6277.png, kết quả dự đoán các selector chọn được là:

1. **h1** 
   → Chọn: `ShopTLU`

2. **.price** 
   → Chọn: `25.990.000đ` và `45.990.000đ`

3. **#app header** 
   → Chọn: Toàn bộ nội dung trong thẻ `<header>` (bao gồm h1 và nav)

4. **nav a:first-child** 
   → Chọn: `Home`

5. **.product.featured h2** 
   → Chọn: `MacBook Pro`

6. **article > p** 
   → Chọn: `25.990.000đ`, `Mô tả sản phẩm...`, `45.990.000đ`, `Mô tả sản phẩm...` (Tất cả các thẻ p là con trực tiếp của article)

7. **a[href="/"]** 
   → Chọn: `Home`

8. **.top-bar.dark h1** 
   → Chọn: `ShopTLU`
   #### Câu A3 (7đ) — Box Model — Tính toán kích thước

Dựa trên các thông số đã cho và kiến thức về Box Model tại Chương 11 (image_8a61fe.png), kết quả tính toán như sau:

/* Trường hợp 1: content-box (mặc định) */
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 450px 
  (Công thức: 400px (width) + 20px*2 (padding) + 5px*2 (border))
→ Không gian chiếm trên trang = 470px 
  (Công thức: 450px (chiều rộng hiển thị) + 10px*2 (margin))

/* Trường hợp 2: border-box */
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 400px 
  (Vì border-box bao gồm cả padding và border vào trong width đã khai báo)
→ Kích thước content thực tế = 350px 
  (Công thức: 400px - 20px*2 (padding) - 5px*2 (border))
→ Không gian chiếm trên trang = 420px 
  (Công thức: 400px (chiều rộng hiển thị) + 10px*2 (margin))

/* Trường hợp 3: Margin collapse */
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
→ Khoảng cách giữa box-a và box-b = 40px
→ Giải thích tại sao KHÔNG PHẢI 65px: 
  Đây là hiện tượng "Margin collapse" (Gộp lề) trong CSS. Khi hai lề dọc (top/bottom) của hai khối kề nhau tiếp xúc, chúng sẽ gộp lại thành một khoảng cách duy nhất bằng giá trị của lề lớn nhất (ở đây là 40px), thay vì cộng dồn lại với nhau.
  #### Câu A4 (5đ) — Specificity (Độ ưu tiên)

Dựa trên các CSS rules và element đã cho trong hình image_8a5ef6.png, dưới đây là phân tích chi tiết:

**1. Tính specificity score (a, b, c) cho mỗi rule:**
*   **Rule A (`p`):** Score = **(0, 0, 1)** (Chỉ có 1 Type selector).
*   **Rule B (`.price`):** Score = **(0, 1, 0)** (Chỉ có 1 Class selector).
*   **Rule C (`#main-price`):** Score = **(1, 0, 0)** (Chỉ có 1 ID selector).
*   **Rule D (`p.price`):** Score = **(0, 1, 1)** (Gồm 1 Type selector và 1 Class selector).

**2. Element sẽ có màu gì? Giải thích:**
*   **Kết quả:** Element sẽ có màu **Đỏ (red)**.
*   **Giải thích:** Rule C có Specificity score cao nhất (1, 0, 0) vì nó sử dụng ID selector. Trong CSS, ID luôn có ưu tiên cao hơn Class và Type selector bất kể số lượng.

**3. Nếu thêm style trực tiếp vào thẻ, element có màu gì?**
*   **Kết quả:** Element sẽ có màu **Cam (orange)**.
*   **Giải thích:** Inline style (viết trực tiếp trong thuộc tính style của thẻ HTML) có độ ưu tiên cao hơn tất cả các bộ chọn (selectors) nằm trong file CSS bên ngoài hoặc thẻ style nội bộ.

**4. Nếu Rule A thêm `!important`, element có màu gì? Tại sao?**
*   **Kết quả:** Element sẽ có màu **Đen (black)**.
*   **Giải thích:** Từ khóa `!important` là một công cụ mạnh nhất trong CSS, nó ghi đè lên tất cả các quy tắc về Specificity thông thường (kể cả ID hay Inline style). Khi Rule A có `!important`, nó sẽ trở thành quy tắc tối thượng và được áp dụng.