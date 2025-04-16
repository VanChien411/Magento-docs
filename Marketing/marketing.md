# 📣 Magento 2 - Marketing

Quản lý khuyến mãi và giao tiếp với khách hàng, bao gồm các quy tắc giá, chiến dịch email và bản tin newsletter.

---

## 🎁 Promotions

---

### 📘 Catalog Price Rule

### ✅ Tác dụng  
Tạo chương trình khuyến mãi **tự động áp dụng trong catalog** mà không cần mã coupon, ví dụ giảm giá theo danh mục, theo thuộc tính sản phẩm.

### 🔧 Ví dụ minh họa  
Giảm 20% cho tất cả sản phẩm thuộc danh mục "Áo thun" từ ngày 01/05 đến 07/05.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Promotions > Catalog Price Rule`  
- Tạo rule, điều kiện áp dụng và hành động giảm giá.  
- Chạy `bin/magento indexer:reindex` nếu không thấy thay đổi.

### ⚙️ Cách hoạt động  
- Tác động **trực tiếp đến giá hiển thị trong catalog**.  
- Không hiển thị dạng “giảm giá từ … còn …” nếu không dùng `special_price`.  
- Áp dụng cho tất cả người dùng (không có coupon).

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính         | Giải thích |
|--------------------|------------|
| `Conditions`       | Xác định sản phẩm nào được áp dụng |
| `Action`           | Giảm giá bao nhiêu % hoặc số tiền |
| `From/To Date`     | Thời gian hiệu lực |
| `Customer Group`   | Áp dụng theo nhóm |
| `Priority`         | Độ ưu tiên nếu có nhiều rule |

### ⚠️ Lưu ý  
- Không dùng được coupon.  
- Bắt buộc reindex và refresh cache để áp dụng.  
- Rule có thể không hiệu lực nếu xung đột với `special_price`.

---

### 📘 Cart Price Rules

### ✅ Tác dụng  
Tạo chương trình khuyến mãi khi khách **thêm sản phẩm vào giỏ**, có thể dùng mã giảm giá (coupon), điều kiện theo tổng đơn, sản phẩm...

### 🔧 Ví dụ minh họa  
Giảm 10% cho đơn hàng trên 1.000.000đ nếu nhập mã `SALE10`.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Promotions > Cart Price Rules`  
- Tạo rule, điều kiện (đơn hàng hoặc sản phẩm), hành động, mã coupon nếu có.

### ⚙️ Cách hoạt động  
- Áp dụng khi checkout.  
- Có thể áp dụng theo số lần dùng, cho từng khách, theo code hoặc tự động.  
- Hỗ trợ free shipping, tặng quà.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính              | Giải thích |
|-------------------------|------------|
| `Coupon Code`           | Mã khuyến mãi (có thể bỏ trống) |
| `Conditions`, `Actions` | Điều kiện áp dụng (sản phẩm, đơn hàng) |
| `Uses Per Customer`     | Giới hạn mỗi khách |
| `Free Shipping`         | Có áp dụng miễn phí ship không |
| `Discount Qty Step`     | Giảm theo bước số lượng |
| `Labels`                | Gắn nhãn hiển thị ngoài frontend |

### ⚠️ Lưu ý  
- Nếu khách nhập mã nhưng không thấy áp dụng, cần kiểm tra nhóm khách, điều kiện và trạng thái rule.  
- Có thể xếp chồng rule theo `Stop further rules processing`.

---

## 💌 Communications

---

### 📘 Email Templates

### ✅ Tác dụng  
Tạo và chỉnh sửa mẫu email tự động gửi như: xác nhận đơn hàng, đặt lại mật khẩu, thông báo…

### 🔧 Ví dụ minh họa  
Chỉnh sửa mẫu email xác nhận đơn hàng để thêm logo công ty và hotline.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Communications > Email Templates`  
- Chọn “Add New Template” → Load from default → Chỉnh sửa.

### ⚙️ Cách hoạt động  
- Dùng biến như `{{var order.increment_id}}`, `{{trans "%name" name=$customer.name}}`  
- Áp dụng trong: `Stores > Configuration > Sales > Sales Email`

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính        | Giải thích |
|-------------------|------------|
| `Template Subject`| Tiêu đề email |
| `Template Content`| Nội dung HTML có thể dùng biến |
| `Template Type`   | HTML hoặc Text |
| `Template Styles` | CSS nội bộ |

### ⚠️ Lưu ý  
- Nếu dùng custom template, cần gán lại ở phần config (`Stores > Configuration`).  
- Không nên chỉnh template gốc – hãy clone và sửa riêng.

---

### 📘 Newsletter Templates

### ✅ Tác dụng  
Tạo nội dung email bản tin (newsletter) gửi định kỳ cho khách hàng đăng ký.

### 🔧 Ví dụ minh họa  
Gửi email tiêu đề “Khuyến mãi hè 2025 - Mua 1 tặng 1” cho toàn bộ subscriber.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Communications > Newsletter Templates`

### ⚙️ Cách hoạt động  
- Tạo mẫu → Cho vào Queue → Gửi tới subscribers.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính            | Giải thích |
|------------------------|------------|
| `Subject`             | Tiêu đề email |
| `Sender Name/Email`   | Người gửi |
| `Template Content`    | Nội dung HTML |

### ⚠️ Lưu ý  
- Không gửi email hàng loạt nếu chưa thử trước (test trước bằng tài khoản cá nhân).  
- Nên dùng hình ảnh nhẹ, tránh email bị vào spam.

---

### 📘 Newsletter Queue

### ✅ Tác dụng  
Quản lý danh sách các bản tin đang chờ gửi hoặc đã gửi.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Communications > Newsletter Queue`

### ⚙️ Cách hoạt động  
- Khi tạo queue từ template, Magento sẽ gửi theo lịch, không gửi tất cả 1 lúc.  
- Có thể dừng hoặc chỉnh sửa trước khi gửi.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính         | Giải thích |
|--------------------|------------|
| `Start Date`       | Thời gian bắt đầu gửi |
| `Status`           | Not Sent / Sending / Sent |
| `Template`         | Mẫu được dùng |

---

### 📘 Newsletter Subscribers

### ✅ Tác dụng  
Xem danh sách và trạng thái những khách đã đăng ký nhận bản tin.

### ▶️ Cách sử dụng  
- Admin: `Marketing > Communications > Newsletter Subscribers`  
- Có thể lọc theo: đăng ký, hủy, chưa xác nhận...

### ⚙️ Cách hoạt động  
- Thông tin lưu trong bảng `newsletter_subscriber`.  
- Có thể đăng ký thủ công trong admin hoặc tự động qua frontend.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính           | Giải thích |
|----------------------|------------|
| `subscriber_status`  | 1 = Subscribed, 2 = Not Active, 3 = Unsubscribed, 4 = Unconfirmed |
| `customer_id`        | Gắn với khách hàng nếu có |
| `subscriber_email`   | Email người đăng ký |


Giá trị	Trạng thái	Ý nghĩa thực tế

1	Subscribed	Khách đã xác nhận đăng ký nhận bản tin và đang active để nhận email.

2	Not Active	Hệ thống không dùng nữa (giá trị cũ, gần như không được sử dụng trong M2).

3	Unsubscribed	Khách đã hủy đăng ký nhận bản tin. Hệ thống sẽ không gửi email nữa.

4	Unconfirmed	Khách vừa đăng ký nhưng chưa xác nhận email (nếu cấu hình yêu cầu xác nhận).

### ⚠️ Lưu ý  
- Một khách có thể đăng ký mà không cần tạo tài khoản.  
- Magento không có hệ thống gửi tự động – cần dùng cron hoặc extension ngoài (Mailchimp, Dotdigital...).

---

# 🔍 Magento 2 - Marketing (SEO & Search, User Content)

Các công cụ hỗ trợ tối ưu hóa tìm kiếm và hiển thị nội dung do người dùng tạo (review), giúp cải thiện SEO và trải nghiệm khách hàng.

---

## 🌐 SEO & Search

---

### 📘 URL Rewrites

### ✅ Tác dụng  
Cho phép thay đổi URL mặc định thành URL thân thiện hơn với người dùng và công cụ tìm kiếm, mà không ảnh hưởng đến dữ liệu gốc.

### 🔧 Ví dụ minh họa  
Chuyển từ:  
`/catalog/product/view/id/42`  
thành:  
`/ao-thun-nam-co-tron.html`

### ▶️ Cách sử dụng  
- Admin: `Marketing > SEO & Search > URL Rewrites`  
- Tạo rewrite mới (custom hoặc liên kết với product/category/CMS).  
- Có thể chỉnh sửa các URL sinh tự động nếu cần.

### ⚙️ Cách hoạt động  
- Magento lưu các rewrite vào bảng `url_rewrite`.  
- Khi khách truy cập, hệ thống dò trong bảng này để điều hướng đúng.  
- Rewrite không phá vỡ liên kết gốc (nội bộ vẫn hoạt động).

### 🏷 Các thuộc tính cần chú ý

| Thuộc tính          | Giải thích |
|---------------------|------------|
| `Request Path`      | URL mới hiển thị |
| `Target Path`       | URL gốc (thường là route mặc định) |
| `Redirect Type`     | 301 (mãi mãi), 302 (tạm thời), hoặc None |
| `Store View`        | Có thể tạo rewrite theo từng store |
| `Entity Type/ID`    | Gắn với product, category hoặc page |

### ⚠️ Lưu ý  
- Không nên xóa rewrite gốc sinh ra từ sản phẩm hoặc category.  
- Nếu có lỗi 404, kiểm tra rewrite trùng hoặc bị sai `Target Path`.  
- Có thể dùng command `bin/magento catalog:product:url` để regenerate URL sản phẩm.

---

### 📘 Search Terms

### ✅ Tác dụng  
Thống kê các cụm từ mà khách hàng đã tìm kiếm trong website → phục vụ cho việc tối ưu keyword và sản phẩm.

### 🔧 Ví dụ minh họa  
Từ khoá "áo hoodie" có 300 lượt tìm → Admin cân nhắc tạo landing page hoặc tăng hiển thị từ khoá đó.

### ▶️ Cách sử dụng  
- Admin: `Marketing > SEO & Search > Search Terms`  
- Có thể chỉnh sửa hoặc redirect từ khoá sang URL mong muốn.

### ⚙️ Cách hoạt động  
- Magento lưu lại tất cả keyword tìm kiếm frontend (nếu không bị tắt).  
- Từ khoá có thể dùng để tạo redirect, tăng hiệu suất chuyển đổi.

### 🏷 Các thuộc tính cần chú ý

| Thuộc tính         | Giải thích |
|--------------------|------------|
| `Search Query`     | Từ khoá đã tìm |
| `Number of Results`| Bao nhiêu kết quả tìm được |
| `Popularity`       | Tần suất từ khoá được tìm |
| `Redirect`         | Nếu có, chuyển hướng khi tìm từ này |
| `Display in Suggested Terms` | Hiển thị gợi ý khi khách tìm |

### ⚠️ Lưu ý  
- Nên thường xuyên theo dõi để thêm từ khoá phổ biến vào SEO.  
- Từ khoá không có kết quả nên được redirect hợp lý hoặc cải thiện nội dung.

---

### 📘 Search Synonyms

### ✅ Tác dụng  
Cho phép định nghĩa **các từ đồng nghĩa** để mở rộng khả năng tìm kiếm (ví dụ: “t-shirt” cũng hiểu là “áo thun”).

### 🔧 Ví dụ minh họa  
Định nghĩa: `áo thun, tshirt, áo phông` → tìm bất kỳ từ nào cũng ra kết quả.

### ▶️ Cách sử dụng  
- Admin: `Marketing > SEO & Search > Search Synonyms`  
- Tạo nhóm đồng nghĩa, phân biệt theo Store View nếu cần.

### ⚙️ Cách hoạt động  
- Magento tích hợp với Elasticsearch – từ đồng nghĩa được ánh xạ trong index tìm kiếm.  
- Sau khi tạo synonym, cần reindex để có hiệu lực.

### 🏷 Các thuộc tính cần chú ý

| Thuộc tính          | Giải thích |
|---------------------|------------|
| `Synonyms`          | Danh sách từ cách nhau bởi dấu phẩy |
| `Store View`        | Store áp dụng |
| `Website`           | Website áp dụng |

### ⚠️ Lưu ý  
- Synonym chỉ hoạt động nếu search engine là **Elasticsearch**.  
- Nhớ reindex và clear cache để cập nhật.  
- Tránh đặt synonym không liên quan gây nhi kết quả.

---

### 📘 Site Map

### ✅ Tác dụng  
Tạo sitemap.xml cho công cụ tìm kiếm như Google để crawl website dễ dàng hơn.

### 🔧 Ví dụ minh họa  
Sitemap tại: `https://yourdomain.com/sitemap.xml` chứa link tới tất cả sản phẩm, danh mục, CMS pages.

### ▶️ Cách sử dụng  
- Admin: `Marketing > SEO & Search > Site Map`  
- Chọn path lưu sitemap, định kỳ regenerate bằng cron.

### ⚙️ Cách hoạt động  
- Magento sinh file `.xml` chứa đường dẫn cần index.  
- Có thể submit sitemap lên Google Search Console.

### 🏷 Các thuộc tính cần chú ý

| Thuộc tính       | Giải thích |
|------------------|------------|
| `Path`           | Đường dẫn lưu file sitemap |
| `Store View`     | Tạo sitemap theo từng store |
| `Last Generated` | Thời gian cập nhật gần nhất |

### ⚠️ Lưu ý  
- File sitemap nên có quyền đọc công khai (`644`).  
- Đường dẫn không nên chứa `/pub/`.  
- Kiểm tra lại nếu site không index lên Google.

---

## 🧑‍💬 User Content

---

### 📘 All Reviews

### ✅ Tác dụng  
Quản lý toàn bộ đánh giá sản phẩm do khách hàng gửi từ frontend.

### 🔧 Ví dụ minh họa  
Khách A đánh giá 4★ cho sản phẩm "Áo Polo X", admin có thể duyệt, chỉnh sửa hoặc ẩn.

### ▶️ Cách sử dụng  
- Admin: `Marketing > User Content > All Reviews`

### ⚙️ Cách hoạt động  
- Khi khách đánh giá, review sẽ ở trạng thái “Pending”.  
- Admin duyệt → review hiển thị ngoài frontend.

### 🏷 Các thuộc tính cần chú ý

| Thuộc tính        | Giải thích |
|-------------------|------------|
| `Title`           | Tiêu đề review |
| `Detail`          | Nội dung chi tiết |
| `Rating`          | Số sao (1-5) |
| `Nickname`        | Tên hiển thị |
| `Status`          | Pending / Approved / Not Approved |
| `Product`         | Sản phẩm được đánh giá |

### ⚠️ Lưu ý  
- Nếu review không hiển thị, hãy kiểm tra trạng thái hoặc cấu hình `Stores > Configuration > Catalog > Catalog > Product Reviews`.

---

### 📘 Pending Reviews

### ✅ Tác dụng  
Hiển thị các đánh giá đang chờ duyệt.

### ▶️ Cách sử dụng  
- Admin: `Marketing > User Content > Pending Reviews`  
- Tại đây admin có thể phê duyệt, chỉnh sửa hoặc xóa.

### ⚠️ Lưu ý  
- Nên kiểm duyệt thường xuyên để không làm khách thất vọng vì review không xuất hiện.  
- Có thể cấu hình để review được tự động duyệt nếu muốn.

---

