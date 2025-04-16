# Data Transfer – Truyền dữ liệu

## Tác dụng
Quản lý quá trình nhập và xuất dữ liệu sản phẩm, khách hàng, đơn hàng,... giữa Magento và hệ thống bên ngoài.

## Đường dẫn
Admin Panel → System → Data Transfer

## Các phần nhỏ
- Import
- Export
- Import/Export Tax Rates
- Import History

# Import

## Tác dụng
Cho phép nhập dữ liệu vào hệ thống từ file CSV (product, customer, stock...).

## Đường dẫn
System → Data Transfer → Import

## Cách sử dụng
1. Chọn Entity Type (Product, Customer,...)
2. Upload file CSV
3. Kiểm tra lỗi → Import

## Ví dụ minh họa
- Import danh sách sản phẩm mới từ file Excel đã convert thành CSV

## Lưu ý
- File phải đúng định dạng mẫu của Magento
- Cần chọn đúng "Import Behavior": Add, Replace, Delete

# Export

## Tác dụng
Xuất dữ liệu từ Magento ra file CSV để sao lưu, chỉnh sửa, hoặc chuyển sang hệ thống khác.

## Đường dẫn
System → Data Transfer → Export

## Cách sử dụng
1. Chọn Entity Type
2. Chọn các cột cần xuất
3. Bấm Export

## Ví dụ minh họa
- Xuất toàn bộ thông tin khách hàng ra file CSV

## Lưu ý
- Có thể dùng để chỉnh sửa hàng loạt và import lại

# Import/Export Tax Rates

## Tác dụng
Dễ dàng quản lý và cập nhật thuế theo vùng thông qua file CSV.

## Đường dẫn
System → Data Transfer → Import/Export Tax Rates

## Cách sử dụng
- Tải mẫu file CSV có sẵn → chỉnh sửa → import lại

## Ví dụ
- Import thuế mới theo từng tỉnh/thành phố

## Lưu ý
- Nên backup trước khi import

# Import History

## Tác dụng
Theo dõi lịch sử các file đã import vào hệ thống, trạng thái, lỗi...

## Đường dẫn
System → Data Transfer → Import History

## Cách sử dụng
- Xem chi tiết các lần import gần nhất
- Tải lại file đã import

## Lưu ý
- Giúp debug lỗi import nhanh chóng

# Extensions

## Tác dụng
Quản lý và cài đặt các extension của Magento Marketplace hoặc custom.

## Đường dẫn
System → Extensions → Integrations

## Lưu ý
- Một số extension yêu cầu cấu hình sau khi cài

# Integrations

## Tác dụng
Tạo và quản lý các kết nối API giữa Magento và hệ thống bên ngoài (ERP, CRM,...).

## Đường dẫn
System → Extensions → Integrations

## Ví dụ
- Kết nối với phần mềm quản lý kho hoặc phần mềm kế toán

## Lưu ý
- Có thể giới hạn quyền API khi cấp token

# Tools

## Tác dụng
Chứa các công cụ hỗ trợ quản trị như cache, index, backup,...

## Các mục con:
- Cache Management
- Index Management

# Cache Management

## Tác dụng
Xoá hoặc refresh các loại cache như config, layout, block, full page,...

## Đường dẫn
System → Tools → Cache Management

## Cách sử dụng
- Chọn cache cần xoá → Actions → Refresh / Flush

## Lưu ý
- Sau khi thay đổi cấu hình, nên "Flush Cache"

# Index Management

## Tác dụng
Tối ưu hiệu suất bằng cách tái lập chỉ mục (index) các loại dữ liệu như sản phẩm, giá, danh mục.

## Đường dẫn
System → Tools → Index Management

## Lưu ý
- Nếu Indexer ở chế độ "Update on Schedule", cần chạy cron

# Permissions – Quản lý người dùng và quyền

## Các phần nhỏ:
- All Users
- Locked Users
- User Roles
- Action Logs

# All Users

## Tác dụng
Quản lý danh sách tài khoản admin

## Đường dẫn
System → Permissions → All Users

## Lưu ý
- Chỉ Super Admin mới có thể chỉnh sửa user khác

# Locked Users

## Tác dụng
Hiển thị các user bị khóa do đăng nhập sai nhiều lần

## Lưu ý
- Có thể unlock để người dùng truy cập lại

# User Roles

## Tác dụng
Tạo các nhóm quyền (Admin, Content Editor, Sales...) để gán cho user.

## Cách sử dụng
- Tạo role mới → Chọn quyền → Gán user vào

## Lưu ý
- Magento phân quyền rất chi tiết theo từng menu

# Action Logs

## Tác dụng
Theo dõi các hành động của admin: sửa sản phẩm, xoá đơn hàng,...

## Lưu ý
- Hữu ích khi kiểm tra lỗi do thao tác người dùng

# Bulk Actions

## Tác dụng
Cho phép thực hiện thao tác hàng loạt: xoá nhiều sản phẩm, cập nhật giá,...

## Lưu ý
- Một số thao tác hàng loạt có thể ảnh hưởng hiệu suất

# Other Settings

## Tác dụng
Tùy chỉnh các cài đặt hệ thống nâng cao (như encryption, biến custom...)

## Bao gồm:
- Notifications
- Custom Variables
- Manage Encryption Key

# Notifications

## Tác dụng
Hiển thị các thông báo từ Magento như bản vá lỗi, cập nhật mới...

## Lưu ý
- Nên thường xuyên kiểm tra để cập nhật kịp thời

# Custom Variables

## Tác dụng
Tạo biến để dùng trong các email, block tĩnh hoặc template

## Ví dụ
- {{customVar code="promotion_banner"}}

## Lưu ý
- Hữu ích cho team marketing

# Manage Encryption Key

## Tác dụng
Quản lý khóa mã hóa các thông tin nhạy cảm như password, API key,...

## Lưu ý
- Nên backup kỹ trước khi thay đổi
- Magento cung cấp 2 lựa chọn: auto generate hoặc custom
