# Terms and Conditions

## Tên
Terms and Conditions – Điều khoản và điều kiện mua hàng

## Tác dụng
Hiển thị điều khoản thanh toán hoặc chính sách bán hàng để khách hàng chấp nhận trước khi hoàn tất đơn hàng.

## Đường dẫn
Admin Panel → Stores → Terms and Conditions

## Cách sử dụng
1. Tạo một bản điều khoản mới
2. Nhập tiêu đề, nội dung, chọn vị trí hiển thị
3. Bật chế độ "Enabled"

## Ví dụ minh họa
- "Tôi đồng ý với chính sách bảo hành của cửa hàng"
- "Đơn hàng không thể hoàn trả nếu đã qua 7 ngày"

## Lưu ý
- Hiển thị ở bước cuối cùng trước khi đặt hàng
- Có thể tạo nhiều điều khoản khác nhau cho từng store view

## Thuộc tính cần chú ý
- **Checkbox Text**: Văn bản bên cạnh checkbox xác nhận
- **Content**: Nội dung điều khoản (hỗ trợ HTML)
- **Status**: Enabled/Disabled
# Order Status

## Tên
Order Status – Trạng thái đơn hàng

## Tác dụng
Quản lý và tạo các trạng thái đơn hàng tùy chỉnh để phản ánh tiến trình xử lý đơn hàng.

## Đường dẫn
Admin Panel → Stores → Order Status

## Cách sử dụng
- Có thể gán trạng thái mới cho một "Order State" sẵn có (Pending, Processing, Complete,...)
- Dùng để tùy biến trạng thái hiển thị cho khách hàng

## Ví dụ minh họa
- Trạng thái mới: “Đang chuẩn bị hàng” → thuộc nhóm “Processing”
- Trạng thái: “Chờ xác nhận thanh toán Momo”

## Lưu ý
- Không thể tạo Order State mới, chỉ có thể thêm **Status** vào state sẵn có
# Inventory

## Tên
Inventory – Quản lý tồn kho

## Tác dụng
Quản lý số lượng sản phẩm, cảnh báo hết hàng, và tự động cập nhật tồn kho khi có đơn hàng.

## Đường dẫn
Admin Panel → Stores → Configuration → Catalog → Inventory

## Cách sử dụng
- Cấu hình tồn kho toàn hệ thống: cho phép đặt hàng khi hết hàng, số lượng tối thiểu,...
- Áp dụng mặc định cho tất cả sản phẩm

## Lưu ý
- Có thể override ở từng sản phẩm
- Nếu dùng **MSI (Multi-Source Inventory)** thì nên thiết lập tồn kho ở phần Sources

## Thuộc tính quan trọng
- **Backorders**: Cho phép đặt hàng khi hết hàng
- **Notify for Quantity Below**: Gửi cảnh báo khi số lượng dưới mức cho phép
- **Manage Stock**: Bật/Tắt quản lý tồn kho
# Sources (MSI)

## Tên
Sources – Nguồn hàng

## Tác dụng
Lưu trữ thông tin địa điểm kho hàng thực tế (có thể có nhiều kho ở nhiều nơi).

## Đường dẫn
Admin Panel → Stores → Sources

## Cách sử dụng
- Thêm một nguồn mới: địa chỉ, múi giờ, mã kho
- Gán các sản phẩm và số lượng cho từng nguồn

## Ví dụ minh họa
- Kho TP.HCM – 100 áo
- Kho Hà Nội – 50 áo

## Lưu ý
- Phải kết hợp với **Stocks** để hoạt động đúng
- Chỉ dùng được khi bật **Multi-Source Inventory**
# Stocks

## Tên
Stocks – Nhóm kho

## Tác dụng
Nhóm nhiều nguồn hàng (Sources) lại thành một "Stock" để kết nối với một website cụ thể.

## Đường dẫn
Admin Panel → Stores → Stocks

## Cách sử dụng
- Tạo một stock → chọn các source → gán cho website
- Dùng để định nghĩa kho tổng cho từng website

## Ví dụ
- Website 1 (Bán hàng VN): gán kho TP.HCM và Hà Nội
- Website 2 (Bán hàng quốc tế): gán kho Singapore

## Lưu ý
- Nếu không dùng MSI, chỉ có 1 nguồn và 1 stock mặc định
# Taxes – Thuế

## Tên
Tax Zones, Tax Rules, Tax Rates

## Tác dụng
Cấu hình các loại thuế suất khác nhau dựa trên quốc gia, vùng, mã zip...

## Đường dẫn
Admin Panel → Stores → Tax Zones and Rates  
Admin Panel → Stores → Tax Rules

---

### 📍 Tax Zones and Rates

## Cách sử dụng
- Tạo từng dòng thuế riêng theo khu vực
- Xác định thuế theo khu vực, loại sản phẩm, loại khách hàng

## Ví dụ
- 10% VAT cho khách tại Việt Nam
- 0% cho khách hàng quốc tế

## Thuộc tính cần chú ý
- Country, State, Zip
- Rate (%)

---

### 📋 Tax Rules

## Cách sử dụng
- Gộp nhiều rate lại thành một rule
- Gán theo nhóm khách hàng (retail, wholesale), loại sản phẩm

## Ví dụ minh họa
- Rule: “Thuế Việt Nam” → áp dụng cho nhóm khách hàng lẻ, tất cả sản phẩm

## Lưu ý
- Tax chỉ hoạt động khi gán rule cho sản phẩm và khách hàng đúng

# Currency – Cài đặt tiền tệ

## Tên
Currency – Quản lý tiền tệ trong Magento

## Tác dụng
Cho phép cấu hình loại tiền tệ hiển thị và thanh toán trên cửa hàng.

## Đường dẫn
Admin Panel → Stores → Configuration → General → Currency Setup

## Cách sử dụng
1. Chọn tiền tệ mặc định
2. Chọn các tiền tệ được cho phép
3. Cấu hình phạm vi hoạt động (website/store view)

## Ví dụ minh họa
- Website VN: VND (mặc định), USD (chấp nhận)
- Website quốc tế: USD (mặc định), EUR, GBP

## Lưu ý
- Phải cập nhật tỷ giá thường xuyên nếu dùng nhiều loại tiền
- Giá sản phẩm luôn lưu ở tiền tệ mặc định

## Thuộc tính cần chú ý
| Tên trường | Ý nghĩa |
|-----------|---------|
| Base Currency | Dùng để nhập và lưu giá sản phẩm |
| Display Currency | Hiển thị cho khách hàng |
| Allowed Currencies | Danh sách tiền tệ được chấp nhận |

# Currency Rates – Tỷ giá tiền tệ

## Tên
Currency Rates

## Tác dụng
Cập nhật tỷ giá giữa các loại tiền tệ để chuyển đổi khi khách thay đổi tiền hiển thị.

## Đường dẫn
Admin Panel → Stores → Currency Rates

## Cách sử dụng
- Tự động cập nhật tỷ giá (qua dịch vụ như Fixer.io)
- Hoặc nhập tay nếu cần cố định giá

## Ví dụ minh họa
- 1 USD = 24,000 VND

## Lưu ý
- Nên cập nhật tỷ giá hàng ngày nếu bạn cho phép chuyển đổi tiền
- Cần cron job nếu dùng auto update

# Currency Symbols – Ký hiệu hiển thị tiền tệ

## Tên
Currency Symbols

## Tác dụng
Tuỳ chỉnh ký hiệu hiển thị của từng loại tiền (ví dụ: ₫, $, €)

## Đường dẫn
Admin Panel → Stores → Currency Symbols

## Cách sử dụng
- Bật "Custom symbol" → nhập ký hiệu mong muốn

## Ví dụ minh họa
- VND → "₫" hoặc "VNĐ"
- USD → "$"
- EUR → "€"

## Lưu ý
- Ký hiệu chỉ ảnh hưởng đến giao diện hiển thị, không ảnh hưởng giá trị tính toán

# Product Attributes – Thuộc tính sản phẩm

## Tên
Attributes

## Tác dụng
Là các đặc điểm (màu, size, chất liệu, ...) để mô tả và phân loại sản phẩm.

## Đường dẫn
Admin Panel → Stores → Product → Attributes

## Cách sử dụng
- Tạo thuộc tính → gán vào **Attribute Set** → dùng trong sản phẩm

## Ví dụ minh họa
- Attribute: Color
  - Type: Dropdown
  - Values: Red, Blue, Black
- Attribute: Material
  - Type: Text

## Thuộc tính cần chú ý
| Tên | Ý nghĩa |
|-----|--------|
| Catalog Input Type | Kiểu dữ liệu: text, dropdown, multi-select |
| Use in Layered Navigation | Cho phép lọc ở sidebar |
| Comparable | Cho so sánh sản phẩm |
| Required | Bắt buộc nhập hay không |
| Visible on Product Page | Hiển thị cho khách xem |

## Lưu ý
- Nên đặt mã thuộc tính (attribute code) không dấu và không khoảng trắng

# Attribute Set – Nhóm thuộc tính sản phẩm

## Tên
Attribute Set

## Tác dụng
Tập hợp các thuộc tính để áp dụng cho một nhóm sản phẩm cụ thể (ví dụ: Áo, Điện thoại, Sách...).

## Đường dẫn
Admin Panel → Stores → Attribute Set

## Cách sử dụng
1. Tạo mới từ Default hoặc clone từ bộ khác
2. Kéo thả các thuộc tính vào nhóm bạn muốn
3. Gán cho sản phẩm khi tạo mới

## Ví dụ minh họa
- Attribute Set: "Điện thoại"
  - Attributes: RAM, Storage, Color, Brand
- Attribute Set: "Áo thun"
  - Attributes: Size, Color, Material

## Lưu ý
- Attribute Set không thể thay đổi sau khi sản phẩm đã được tạo
- Giao diện kéo thả trực quan

# Rating – Đánh giá sao

## Tên
Rating

## Tác dụng
Cấu hình hệ thống đánh giá sản phẩm bằng sao (1 đến 5) và các tiêu chí đánh giá.

## Đường dẫn
Admin Panel → Stores → Rating

## Cách sử dụng
- Tạo tiêu chí đánh giá (Quality, Price, Value...)
- Gán vào các store view phù hợp

## Ví dụ minh họa
- Đánh giá sản phẩm:  
  - Quality: ★★★★☆
  - Price: ★★★☆☆
  - Value: ★★★★☆

## Lưu ý
- Các tiêu chí rating phải được kích hoạt theo từng store view
- Sử dụng kết hợp với Review để hiển thị cho người dùng

## Thuộc tính cần chú ý
| Tên | Ý nghĩa |
|-----|--------|
| Rating Title | Tên tiêu chí (hiển thị ở frontend) |
| Visibility | Chọn store hiển thị |
| Position | Thứ tự hiển thị trên giao diện |

