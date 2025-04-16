# 👥 Magento 2 - Customers

Quản lý thông tin khách hàng, nhóm khách hàng, trạng thái đăng nhập và hoạt động trên website.

---

## 📘 All Customers

### ✅ Tác dụng  
Quản lý toàn bộ khách hàng đã đăng ký trên website, bao gồm thông tin cá nhân, địa chỉ, nhóm, đơn hàng đã đặt…

### 🔧 Ví dụ minh họa  
Khách hàng "Nguyễn Văn A", email `a@gmail.com`, thuộc nhóm "General", có 2 đơn hàng thành công và 1 đơn bị hủy.

### ▶️ Cách sử dụng  
- Admin: `Customers > All Customers`  
- Click vào khách để xem chi tiết hoặc chỉnh sửa.

### ⚙️ Cách hoạt động  
- Dữ liệu chính nằm trong bảng `customer_entity` (dạng EAV).  
- Thông tin như tên, email, ngày sinh nằm trong bảng phụ như `customer_entity_varchar`, `datetime`...  
- Địa chỉ nằm trong `customer_address_entity`.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính             | Giải thích |
|------------------------|------------|
| `email`                | Email đăng nhập, duy nhất |
| `firstname`, `lastname`| Tên khách |
| `group_id`             | Nhóm khách (liên quan đến giá, thuế) |
| `confirmation`         | Xác nhận email (nếu bật) |
| `disable_auto_group_change` | Tắt chuyển nhóm tự động |
| `created_at`, `updated_at` | Thời điểm tạo & cập nhật |
| `store_id`, `website_id`    | Thông tin store view đã đăng ký |

### 📁 Đường dẫn  
- Admin: `Customers > All Customers`  
- Code: `customer_entity`, `customer_address_entity`...

### ⚠️ Lưu ý  
- Tránh xóa khách hàng đã từng đặt hàng, sẽ mất liên kết đơn hàng.  
- Có thể disable khách thay vì xóa (`is_active = 0`).  
- Khách có thể thuộc các website/store khác nhau (multi website).

---

## 📘 Now Online

### ✅ Tác dụng  
Xem danh sách khách hàng hoặc khách vãng lai đang hoạt động trên website theo thời gian thực.

### 🔧 Ví dụ minh họa  
3 khách đang duyệt sản phẩm, 1 khách đã đăng nhập và đang ở trang thanh toán.

### ▶️ Cách sử dụng  
- Admin: `Customers > Now Online`

### ⚙️ Cách hoạt động  
- Dựa trên session và bảng `customer_visitor` & `customer_log`.  
- Hệ thống cập nhật dựa trên cấu hình thời gian timeout online.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính         | Giải thích |
|--------------------|------------|
| `last_visit_at`    | Lần cuối hoạt động |
| `remote_addr`      | IP của khách |
| `customer_id`      | Nếu đã đăng nhập |
| `last_url`         | Đường dẫn trang cuối cùng |

### ⚠️ Lưu ý  
- Nếu bật cache mạnh, có thể gây sai lệch thông tin thực tế.  
- Khách chưa login vẫn được theo dõi dưới dạng visitor.

---

## 📘 Login as Customer Log

### ✅ Tác dụng  
Ghi lại lịch sử các lần admin dùng chức năng "Login as Customer" (đăng nhập thay khách).

### 🔧 Ví dụ minh họa  
Admin `admin1` đăng nhập thay khách `b@gmail.com` lúc 10h sáng 15/04/2025.

### ▶️ Cách sử dụng  
- Admin: `Customers > Login as Customer Log`  
- Gồm lịch sử các thao tác, thời gian, admin thực hiện.

### ⚙️ Cách hoạt động  
- Ghi log trong bảng `login_as_customer_log`.  
- Kết hợp với quyền ACL `Magento_LoginAsCustomer`.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính        | Giải thích |
|-------------------|------------|
| `admin_user_id`   | Ai thực hiện login |
| `customer_id`     | Khách được đăng nhập thay |
| `created_at`      | Thời gian thực hiện |
| `store_id`        | Store đã đăng nhập vào |
| `ip_address`      | IP admin thực hiện |

### ⚠️ Lưu ý  
- Chức năng này cần được bật trong cấu hình: `Stores > Configuration > Customers > Login as Customer`.  
- Nên giới hạn quyền cho các vai trò admin.

---

## 📘 Customer Groups

### ✅ Tác dụng  
Phân loại khách hàng để áp dụng mức giá, thuế suất, chương trình khuyến mãi, hiển thị...

### 🔧 Ví dụ minh họa  
- "General" – khách thông thường  
- "Retailer" – đại lý, giá khác  
- "Not Logged In" – khách vãng lai

### ▶️ Cách sử dụng  
- Admin: `Customers > Customer Groups`  
- Dùng để liên kết trong: catalog price rules, cart price rules, tax rules...

### ⚙️ Cách hoạt động  
