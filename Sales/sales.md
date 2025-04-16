# 🛒 Magento 2 - Sales Overview

Quản lý quá trình bán hàng trong Magento 2, bao gồm Đơn hàng, Hóa đơn, Giao hàng, Hoàn tiền và Giao dịch thanh toán.

---

## 📘 Orders

### ✅ Tác dụng  
Đơn hàng là trung tâm toàn bộ hoạt động bán hàng: từ lúc khách đặt hàng đến khi hoàn tất giao dịch.

### 🔧 Ví dụ minh họa  
Khách đặt hàng 2 sản phẩm, chọn giao hàng chuẩn, thanh toán qua Braintree → Tạo đơn hàng trạng thái "Pending".

### ▶️ Cách sử dụng  
- Admin > **Sales > Orders**  
- Có thể tạo mới đơn từ backend, cập nhật trạng thái, in đơn hàng, tạo invoice/shipment/credit memo.

### ⚙️ Cách hoạt động  
- Khi khách đặt hàng, hệ thống tạo bản ghi trong `sales_order` và các bảng con.  
- Trạng thái đơn hàng thay đổi theo từng bước xử lý.

### 🏷 Các thuộc tính cần chú ý  
- `increment_id`: mã đơn hàng hiển thị (khác ID trong DB)  
- `status`, `state`: tình trạng xử lý của đơn hàng (ví dụ: processing, complete, holded)  
- `customer_id`: ID khách hàng (0 nếu là khách vãng lai)  
- `total_due`, `grand_total`: tổng tiền đơn hàng còn lại chưa thanh toán  
- `created_at`, `updated_at`: mốc thời gian quan trọng

### 📁 Đường dẫn  
- Admin: `Sales > Orders`  
- Code: `sales_order`, `sales_order_item`, `sales_order_address`

### ⚠️ Lưu ý  
- Một đơn hàng có thể tạo nhiều invoice/shipment.  
- Trạng thái `canceled` không thể khôi phục.

---

## 📘 Invoices

### ✅ Tác dụng  
Xác nhận việc **đã thanh toán**.

### 🔧 Ví dụ minh họa  
Admin tạo invoice khi xác nhận đơn hàng đã được thanh toán thành công.

### ▶️ Cách sử dụng  
- Vào đơn hàng > nhấn "Invoice", chọn sản phẩm cần tạo hóa đơn.

### ⚙️ Cách hoạt động  
- Một invoice tương ứng với phần tiền đã thanh toán.  
- Có thể gắn với transaction nếu thanh toán qua online gateway.

### 🏷 Các thuộc tính cần chú ý  
- `invoice_id`, `increment_id`: mã hóa đơn  
- `base_grand_total`, `base_total_paid`: tổng tiền invoice  
- `state`: trạng thái (có thể là paid, open...)  
- `email_sent`: xác định đã gửi thông báo cho khách chưa

### 📁 Đường dẫn  
- Admin: `Sales > Invoices`  
- Code: `sales_invoice`, `sales_invoice_item`

### ⚠️ Lưu ý  
- Phải tạo invoice trước khi hoàn tiền.  
- Không thể xóa hoặc sửa invoice sau khi đã tạo.

---

## 📘 Shipments

### ✅ Tác dụng  
Xác nhận việc giao hàng thành công.

### 🔧 Ví dụ minh họa  
Admin tạo shipment cho đơn hàng, nhập mã vận đơn.

### ▶️ Cách sử dụng  
- Tạo shipment từ đơn hàng.  
- Có thể thêm mã vận đơn và gửi email cho khách.

### ⚙️ Cách hoạt động  
- Khi shipment được tạo, số lượng trong kho giảm.  
- Lưu log giao hàng và tracking nếu có.

### 🏷 Các thuộc tính cần chú ý  
- `increment_id`: mã shipment  
- `total_qty`: tổng số lượng sản phẩm  
- `shipment_status`: trạng thái vận chuyển (custom hoặc dùng trong extensions)  
- `track_number`: mã vận đơn (trong bảng `sales_shipment_track`)

### 📁 Đường dẫn  
- Admin: `Sales > Shipments`  
- Code: `sales_shipment`, `sales_shipment_item`, `sales_shipment_track`

### ⚠️ Lưu ý  
- Shipment không đồng nghĩa với đã thanh toán.  
- Không thể xóa shipment.

---

## 📘 Credit Memos

### ✅ Tác dụng  
Hoàn tiền toàn phần hoặc từng phần.

### 🔧 Ví dụ minh họa  
Khách trả lại 1 sản phẩm, admin hoàn tiền phần đó.

### ▶️ Cách sử dụng  
- Tạo từ đơn hàng > "Credit Memo".  
- Chọn sản phẩm cần hoàn, nhập ghi chú.

### ⚙️ Cách hoạt động  
- Gắn với invoice đã thanh toán.  
- Gọi API refund nếu thanh toán online.

### 🏷 Các thuộc tính cần chú ý  
- `adjustment_positive`, `adjustment_negative`: phụ phí điều chỉnh khi refund  
- `base_shipping_amount`, `refund_shipping_amount`: hoàn tiền phần phí ship  
- `do_offline`: hoàn tiền offline hoặc gọi qua gateway  
- `grand_total`: tổng hoàn lại

### 📁 Đường dẫn  
- Admin: `Sales > Credit Memos`  
- Code: `sales_creditmemo`, `sales_creditmemo_item`

### ⚠️ Lưu ý  
- Không hoàn được nếu chưa có invoice.  
- Không hoàn quá số tiền đã thanh toán.

---

## 📘 Billing Agreements

### ✅ Tác dụng  
Lưu token phương thức thanh toán để dùng lại.

### 🔧 Ví dụ minh họa  
Khách chọn lưu thông tin thẻ → tạo billing agreement.

### ▶️ Cách sử dụng  
- Admin > Sales > Billing Agreements  
- Dùng khi tạo đơn hàng mới từ admin.

### ⚙️ Cách hoạt động  
- Magento lưu token/payment ref từ cổng thanh toán.  
- Gắn với khách hàng.

### 🏷 Các thuộc tính cần chú ý  
- `agreement_id`, `reference_id`: mã liên kết với cổng thanh toán  
- `status`: active/disabled  
- `customer_id`: chủ sở hữu  
- `method_code`: loại payment (braintree, paypal...)

### 📁 Đường dẫn  
- Admin: `Sales > Billing Agreements`  
- Code: `sales_billing_agreement`

### ⚠️ Lưu ý  
- Bắt buộc cổng thanh toán phải hỗ trợ.  
- Không lưu thông tin thẻ rõ ràng trong DB.

---

## 📘 Transactions

### ✅ Tác dụng  
Lưu vết các giao dịch (thanh toán, hoàn tiền...).

### 🔧 Ví dụ minh họa  
Khách thanh toán thành công → Magento tạo transaction với trạng thái `paid`.

### ▶️ Cách sử dụng  
- Admin > Sales > Transactions  
- Dùng để tra cứu mã giao dịch, xác minh lỗi thanh toán.

### ⚙️ Cách hoạt động  
- Tạo khi Magento gọi và nhận phản hồi từ gateway.  
- Gắn với order/invoice/credit memo.

### 🏷 Các thuộc tính cần chú ý  
- `txn_id`: mã giao dịch trả về từ cổng thanh toán  
- `txn_type`: loại giao dịch (authorize, capture, refund)  
- `is_closed`: xác định đã kết thúc chưa  
- `additional_information`: chứa chi tiết XML/JSON response

### 📁 Đường dẫn  
- Admin: `Sales > Transactions`  
- Code: `sales_payment_transaction`

### ⚠️ Lưu ý  
- Transaction lỗi thường nằm ở đây.  
- Đọc `additional_information` để debug.

---

## 📘 Braintree Virtual Terminal

### ✅ Tác dụng  
Cho phép admin nhập thông tin thẻ và thanh toán trực tiếp.

### 🔧 Ví dụ minh họa  
Admin đặt hàng qua điện thoại → nhập thẻ khách → thanh toán qua Virtual Terminal.

### ▶️ Cách sử dụng  
- Admin > Sales > Braintree Virtual Terminal  
- Nhập số thẻ, ngày hết hạn, CVV → thanh toán.

### ⚙️ Cách hoạt động  
- Magento gửi API trực tiếp đến Braintree → nếu thành công, tạo transaction + invoice.

### 🏷 Các thuộc tính cần chú ý  
- Không lưu trực tiếp trong DB, chỉ log transaction.  
- Sử dụng Braintree SDK/API key.  
- Cấu hình trong `Stores > Configuration > Payment Methods > Braintree`.

### 📁 Đường dẫn  
- Admin: `Sales > Braintree Virtual Terminal`  
- Code: `Magento_Braintree` module

### ⚠️ Lưu ý  
- Không nên sử dụng trên môi trường production mà không có SSL.  
- Hạn chế lưu trữ bất kỳ thông tin thẻ nếu không cần thiết.

---

