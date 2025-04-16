# 🗂 Magento 2 - Catalog: Products & Categories

Phần Catalog là cốt lõi của Magento, nơi bạn quản lý toàn bộ danh mục sản phẩm và cấu trúc phân loại của website.

---

## 📘 Products

### ✅ Tác dụng  
Quản lý thông tin chi tiết của từng sản phẩm, bao gồm: tên, giá, tồn kho, hình ảnh, tùy chọn tùy chỉnh, và phân loại.

### 🔧 Ví dụ minh họa  
Sản phẩm "Áo Thun Nam Cổ Tròn" giá 299.000đ, màu sắc có thể chọn, size S/M/L → là một **Configurable Product** gồm các sản phẩm con.

### ▶️ Cách sử dụng  
- Admin: `Catalog > Products`  
- Thêm mới / chỉnh sửa thông tin chi tiết từng sản phẩm.

### ⚙️ Cách hoạt động  
- Mỗi sản phẩm lưu trong bảng `catalog_product_entity` (dạng EAV).  
- Các giá trị như tên, mô tả, giá… lưu trong bảng phụ tương ứng: `catalog_product_entity_varchar`, `decimal`, `text`, `int`...  
- Các thuộc tính (attributes) được định nghĩa và nhóm theo `attribute sets`.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính            | Giải thích |
|-----------------------|------------|
| `type_id`             | Loại sản phẩm: simple, configurable, virtual, downloadable... |
| `sku`                 | Mã sản phẩm, phải duy nhất |
| `status`              | 1 = Enabled, 2 = Disabled |
| `visibility`          | 1 = Not visible, 2 = Catalog, 3 = Search, 4 = Both |
| `price`, `special_price`, `special_from_date`, `special_to_date` | Giá và khuyến mãi |
| `qty`, `is_in_stock`  | Quản lý tồn kho trong bảng `cataloginventory_stock_item` |
| `weight`              | Bắt buộc nếu có giao hàng |
| `custom_attributes`   | Các giá trị tùy chỉnh (ví dụ: color, size, material...) |

### 🧩 Các loại sản phẩm chính  
| Loại                | Mô tả |
|---------------------|-------|
| **Simple**          | Sản phẩm đơn, không tùy chọn |
| **Configurable**    | Có các option (color, size...) liên kết nhiều simple products |
| **Virtual**         | Dịch vụ, không vận chuyển |
| **Downloadable**    | File tải về |
| **Grouped**         | Gộp nhiều sản phẩm đơn |
| **Bundle**          | Bộ sản phẩm, khách chọn từng phần |

| **Bundle**   
| Loại giá	| Mô tả |
|------|----------------------|
| Dynamic Price	| Giá của sản phẩm được tính dựa trên tổng giá của các item con bên trong.
| Fixed Price	| Giá cố định được đặt tại bundle, không phụ thuộc giá item con.

### 📁 Đường dẫn  
- Admin: `Catalog > Products`  
- Code: `catalog_product_entity`, `cataloginventory_stock_item`, `eav_attribute`...

### ⚠️ Lưu ý  
- Mỗi sản phẩm nên thuộc ít nhất 1 category để hiển thị ngoài frontend.  
- Nếu không set `visibility`, sản phẩm con trong configurable sẽ không hiển thị tìm kiếm.  
- Đừng xóa sản phẩm nếu có order, hãy "disable".

---

## 📘 Categories

### ✅ Tác dụng  
Tổ chức sản phẩm theo dạng phân cấp, giúp điều hướng và lọc sản phẩm dễ dàng.

### 🔧 Ví dụ minh họa  
"Quần áo Nam" (cha) → "Áo", "Quần", "Phụ kiện" (con) → giúp khách duyệt theo nhóm.

### ▶️ Cách sử dụng  
- Admin: `Catalog > Categories`  
- Chọn Root Category và thêm các nhánh con.

### ⚙️ Cách hoạt động  
- Danh mục lưu trong `catalog_category_entity` (cũng là EAV).  
- Phân cấp bằng trường `path`, `parent_id`, `level`.  
- Mỗi store view gắn với một **Root Category** riêng biệt.

### 🏷 Các thuộc tính cần chú ý  

| Thuộc tính             | Giải thích |
|------------------------|------------|
| `is_active`            | 1 = hiển thị, 0 = ẩn |
| `include_in_menu`      | Có hiển thị trong menu điều hướng hay không |
| `path`, `level`        | Định vị vị trí trong cây danh mục |
| `available_sort_by`, `default_sort_by` | Cách sắp xếp sản phẩm |
| `url_key`, `url_path`  | Dùng để tạo URL thân thiện |
| `display_mode`         | PRODUCTS / STATIC BLOCK / BOTH |
| `anchor`               | TRUE nếu muốn dùng layered navigation (lọc sản phẩm) |
| `position`             | Vị trí khi hiển thị trong menu |
| `product_count`        | Magento sẽ tính toán số sản phẩm trong danh mục này |

### 🧠 Root Category là gì?  
- Là danh mục gốc (cha của tất cả danh mục con) cho mỗi website/store view.  
- Một Magento có thể có nhiều root category.

### 📁 Đường dẫn  
- Admin: `Catalog > Categories`  
- Code: `catalog_category_entity`, `catalog_category_product`, `catalog_category_entity_varchar`...

### ⚠️ Lưu ý  
- Sản phẩm không thuộc category nào sẽ **không hiển thị** ngoài frontend.  
- Nếu tắt `is_anchor`, sẽ không dùng được filter ở frontend.  
- Cẩn thận khi đổi `url_key`, vì dễ mất SEO hoặc lỗi 404.

---

## 🔄 Mối liên hệ giữa Product và Category

- Liên kết nằm trong bảng: `catalog_category_product` (category_id - product_id)  
- Một sản phẩm có thể thuộc nhiều danh mục.  
- Sắp xếp thứ tự sản phẩm trong từng danh mục có thể chỉnh ở tab "Category Products".

---

## 🛠 Một số thao tác hay dùng (Tips)

| Tác vụ | Gợi ý |
|--------|-------|
| Import sản phẩm hàng loạt | Admin > System > Import (type = Products) |
| Tạo sản phẩm từ code | Dùng object `\Magento\Catalog\Model\ProductFactory` |
| Thêm sản phẩm vào danh mục bằng code | Dùng `\Magento\Catalog\Model\CategoryLinkRepositoryInterface` |
| Đổi ảnh sản phẩm qua code | Dùng `\Magento\Catalog\Model\Product\Gallery\Processor` |
| Lấy tất cả danh mục theo cây | Dùng `\Magento\Catalog\Model\ResourceModel\Category\CollectionFactory` |

---

