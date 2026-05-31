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
#### Bài B2 (20đ) — Box Model Lab

Dựa trên kết quả đo đạc từ trình duyệt DevTools (tab Computed) với các thông số width: 300px, padding: 20px, border: 5px:

* Hộp 1 (content-box): chiều rộng thực tế = 350 px (đo từ DevTools)
* Hộp 2 (border-box): chiều rộng thực tế = 300 px (đo từ DevTools)

**Giải thích sự khác biệt:**
* **Hộp 1 (content-box):** Đây là cơ chế mặc định của CSS. Chiều rộng thực tế hiển thị trên trình duyệt sẽ bằng thuộc tính `width` cộng thêm `padding` và `border` của cả 2 bên trái/phải ($300 + 20 \times 2 + 5 \times 2 = 350\text{px}$). Do đó, chiếc hộp bị phình to ra hơn so với kích thước ban đầu.
* **Hộp 2 (border-box):** Khi sử dụng cơ chế này, trình duyệt tự động tính toán để co phần không gian của vùng nội dung (content) lại, đảm bảo tổng chiều rộng hiển thị bên ngoài bao gồm cả `padding` và `border` luôn cố định đúng bằng giá trị `width` đã khai báo ($300\text{px}$). Điều này giúp việc thiết kế layout chính xác và dễ quản lý hơn nhiều.
**Phần 2 — Layout 3 cột:**
* Tính toán lý thuyết khi KHÔNG dùng `border-box`:
  Tổng chiều rộng thực tế = (250px + 15px*2) + (500px + 20px*2) + (250px + 15px*2) = 280px + 540px + 280px = 1100px.
* Vì $1100\text{px} > 1000\text{px}$ (vượt quá chiều rộng tối đa của container), các phần tử không thể xếp cùng một hàng mà cột bên phải (ads) bắt buộc phải bị đẩy vỡ xuống dòng bên dưới.
* Giải pháp: Khi kích hoạt `box-sizing: border-box`, kích thước thực tế của các cột được giữ nguyên đúng bằng tỉ lệ thiết kế (250px - 500px - 250px), giúp tổng chiều rộng vừa khít 1000px và layout hiển thị hoàn hảo trên một hàng dọc duy nhất.
#### Bài B3 (15đ) — Specificity Battle

1. Liệt kê 10 rules + specificity score:
   * `p` -> (0, 0, 1)
   * `.text` -> (0, 1, 0)
   * `p.text` -> (0, 1, 1)
   * `.text.highlight` -> (0, 2, 0)
   * `p.text.highlight` -> (0, 2, 1)
   * `#demo` -> (1, 0, 0)
   * `p#demo` -> (1, 0, 1)
   * `#demo.text` -> (1, 1, 0)
   * `p#demo.text` -> (1, 1, 1)
   * `p#demo.text.highlight` -> (1, 2, 1)

2. Element cuối cùng hiển thị màu gì? Tại sao?
   * Màu hiển thị: Màu xanh hải quân (navy).
   * Tại sao: Rule `p#demo.text.highlight` có điểm Specificity score cao nhất (1, 2, 1) nên nó sẽ thắng tất cả các rules còn lại.

4. Thay đổi thứ tự rules trong CSS file. Kết quả có đổi không? Giải thích.
   * Kết quả: KHÔNG ĐỔI.
   * Giải thích: Khi các selector có điểm Specificity khác nhau, trình duyệt luôn ưu tiên áp dụng selector có điểm cao hơn bất kể vị trí đứng trước hay đứng sau trong file CSS. Thứ tự viết chỉ có tác dụng khi hai selector có điểm Specificity hoàn toàn bằng nhau.
   #### Câu C1 (10đ) — Debug CSS Layout

Dựa trên yêu cầu từ hình image_89f1a1.png, dưới đây là phần phân tích và giải quyết:

1. **Tính chiều rộng thực tế của sidebar và content (content-box!):**
   * **Sidebar:** 300px (width) + 20px*2 (padding) + 1px*2 (border) = **342px**
   * **Content:** 660px (width) + 30px*2 (padding) + 1px*2 (border) = **722px**

2. **Giải thích tại sao layout bị vỡ:**
   * Tổng chiều rộng thực tế của hai khối là: $342\text{px} + 722\text{px} = 1064\text{px}$.
   * Vì $1064\text{px} > 960\text{px}$ (vượt quá độ rộng tối đa của `.container`), không gian không đủ để xếp hai khối nằm cạnh nhau, dẫn đến khối `.content` bị đẩy rơi xuống dòng mới.

3. **Đưa ra 2 cách sửa khác nhau:**
   * **Cách 1 (Dùng border-box):** Thêm thuộc tính `box-sizing: border-box;` cho cả `.sidebar` và `.content` để chiều rộng thực tế giữ nguyên cố định đúng bằng 300px và 660px (Tổng $300 + 660 = 960\text{px}$).
   * **Cách 2 (Không dùng border-box):** Tính toán lại thuộc tính `width` thủ công:
     * Kích thước width mới cho `.sidebar` = 300px - 20px*2 - 1px*2 = **258px**
     * Kích thước width mới cho `.content` = 660px - 30px*2 - 1px*2 = **598px**
     #### Câu C2 (10đ) — Cascade Puzzle

1. **"Sản phẩm A" (h2) có font-size = 20px và color = green**
   * *Giải thích:* * `font-size`: Thẻ h2 này khớp với selector `.card .title` nên nhận giá trị 20px.
     * `color`: Selector `.highlight` chứa thuộc tính `!important` nên ghi đè hoàn toàn tất cả các rules khác (kể cả ID `#featured .title`), làm cho chữ có màu xanh lá (green).

2. **"Mô tả sản phẩm" (p trong card featured) có color = blue**
   * *Giải thích:* Thẻ p này khớp với selector `.card p { color: inherit; }`. Thuộc tính `inherit` bắt buộc nó phải thừa kế màu từ phần tử cha trực tiếp là `.card` (thẻ div `#featured`). Mà `.card` có màu là `blue`, do đó thẻ p này nhận màu xanh dương (blue).

3. **"Sản phẩm B" (h2) có font-size = 20px và color = #333 (hoặc màu mặc định của trình duyệt cho h2 nếu không tính kế thừa body)**
   * *Giải thích:* * `font-size`: Thẻ h2 này khớp với selector `.card .title` nên nhận giá trị 20px.
     * `color`: Thẻ h2 này chỉ khớp với các selector chỉnh font-size, không có selector nào chỉ định trực tiếp thuộc tính `color` cho nó. Thuộc tính `color` không tự động kế thừa từ `.card` sang thẻ tiêu đề `h2` theo mặc định của trình duyệt, nên nó giữ màu nguyên bản đen/xám đậm ban đầu.

4. **"Mô tả sản phẩm B" (p.highlight) có color = green**
   * *Giải thích:* Thẻ p này khớp trực tiếp với selector `.highlight { color: green !important; }`. Sức mạnh của `!important` lập tức ghi đè quy tắc kế thừa `inherit` của selector `.card p`, ép chữ hiển thị màu xanh lá (green).