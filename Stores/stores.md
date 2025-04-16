# Store Hierarchy trong Magento 2

## Tên
Website, Store, Store View

## Tác dụng
Magento sử dụng cấu trúc phân cấp để hỗ trợ xây dựng hệ thống bán hàng đa kênh, đa ngôn ngữ, hoặc đa thương hiệu. Bạn có thể quản lý nhiều cửa hàng chỉ trong một hệ thống Magento.

---

## 1. Website

### Tác dụng
Là cấp cao nhất trong Magento. Một website đại diện cho một công ty hoặc thương hiệu lớn. Có thể có **nhiều store** bên trong và cấu hình riêng cho:
- Khách hàng
- Giỏ hàng
- Phương thức thanh toán
- Đơn vị tiền tệ

### Ví dụ minh họa
Website `Fashion Corp` có 2 store: `Men Store` và `Women Store`.

### Đường dẫn
`Admin Panel → Stores → All Stores → Create Website`

### Cách sử dụng
Tạo Website mới khi bạn muốn tách riêng giỏ hàng, khách hàng hoặc phương thức thanh toán.

### Lưu ý
- Mỗi website có thể dùng theme khác nhau.
- Dữ liệu khách hàng và đơn hàng tách biệt giữa các website.

---

## 2. Store (Store Group)

### Tác dụng
Một Website có thể có nhiều Store. Mỗi Store đại diện cho một danh mục sản phẩm chính và có thể có nhiều **Store View**.

### Ví dụ minh họa
Store `Men Store` bán sản phẩm thời trang nam. Store `Women Store` bán sản phẩm nữ. Cả hai cùng nằm trong website `Fashion Corp`.

### Đường dẫn
`Admin Panel → Stores → All Stores → Create Store`

### Cách sử dụng
Tạo Store khi bạn muốn chia danh mục sản phẩm theo nhóm lớn.

### Lưu ý
- Một Store chỉ có **1 Root Category**.
- Nhiều Store có thể dùng chung hoặc khác theme, cấu hình.

---

## 3. Store View

### Tác dụng
Cấp độ thấp nhất, chủ yếu dùng để thay đổi **ngôn ngữ hiển thị**, **đơn vị tiền tệ**, hoặc **giao diện frontend**.

### Ví dụ minh họa
Một Store có thể có 2 Store View: `English` và `Vietnamese`.

### Đường dẫn
`Admin Panel → Stores → All Stores → Create Store View`

### Cách sử dụng
Tạo Store View khi bạn muốn hiển thị nội dung bằng nhiều ngôn ngữ hoặc phục vụ cho nhiều khu vực khác nhau.

### Lưu ý
- Nội dung CMS (Page, Block) và sản phẩm có thể được dịch riêng theo từng Store View.
- URL sẽ có dạng như:  
  `yourdomain.com/en/` hoặc `yourdomain.com/vi/` tùy cấu hình.

---

## Tổng kết

| Thành phần   | Vai trò                     | Dùng khi nào                             | Giao diện riêng | Khách hàng riêng | Nội dung riêng |
|--------------|------------------------------|------------------------------------------|------------------|-------------------|----------------|
| Website      | Hệ thống chính               | Khi cần tách toàn bộ chức năng           | ✅                | ✅                 | ✅              |
| Store        | Nhóm sản phẩm                | Khi muốn chia danh mục lớn               | ✅                | ❌                 | ✅              |
| Store View   | Ngôn ngữ / giao diện hiển thị | Khi cần đa ngôn ngữ / đa khu vực         | ✅                | ❌                 | ✅              |

---

## Cách hoạt động

- Khi người dùng truy cập trang web, Magento xác định `Store View` trước, rồi mới ngược lên `Store`, rồi `Website`.
- Cấu hình (`Configuration`) có thể được set theo từng cấp độ:  
  **Global → Website → Store View**

Ví dụ:

- Giá sản phẩm thường đặt ở cấp **Website**
- Mô tả sản phẩm đặt theo **Store View**
- Cấu hình thanh toán đặt theo **Website**

---

## Lưu ý chung

- Không thể xoá Website/Store/Store View mặc định, nên hãy cẩn trọng khi cấu hình ban đầu.
- Khi tạo mới các cấp này, nhớ gán `Root Category` và `Theme` phù hợp để tránh lỗi hiển thị.

# Magento 2 – Store Hierarchy

## Tên
Website, Store, Store View

## Tác dụng
Magento 2 sử dụng cấu trúc phân cấp gồm: **Website → Store → Store View** để giúp bạn dễ dàng xây dựng hệ thống bán hàng đa thương hiệu, đa ngành, đa ngôn ngữ chỉ trong một hệ thống duy nhất.

---

## Ví dụ minh họa – Mô hình Bách hóa

Giả sử bạn sở hữu hệ thống siêu thị tên là **MegaMart**. Bạn có thể cấu hình như sau:

Website (MegaMart Corp) └── Store 1: MegaMart Thực phẩm ├── Store View: Vietnamese └── Store View: English └── Store 2: MegaMart Điện máy ├── Store View: Vietnamese └── Store View: English


| Magento         | Thực tế ngoài đời                                  |
|-----------------|----------------------------------------------------|
| Website         | Tập đoàn bách hóa MegaMart                         |
| Store           | Các ngành hàng lớn: Thực phẩm, Điện máy,...        |
| Store View      | Giao diện theo ngôn ngữ: Vietnamese, English,...   |

---

## Chi tiết từng thành phần

### 1. Website

- Là cấp cao nhất trong hệ thống Magento.
- Có thể có nhiều store bên trong.
- Tách biệt dữ liệu khách hàng, giỏ hàng, phương thức thanh toán.

**Ví dụ:**  
Website 1: Bán hàng nội địa  
Website 2: Bán hàng quốc tế

**Đường dẫn tạo:**  
`Admin Panel → Stores → All Stores → Create Website`

**Lưu ý:**
- Mỗi website có thể có theme và cấu hình riêng.
- Các website không chia sẻ giỏ hàng hoặc khách hàng.

---

### 2. Store (Store Group)

- Là các chi nhánh/ngành hàng lớn trong website.
- Mỗi store chứa một danh mục chính (Root Category).
- Một website có thể có nhiều store.

**Ví dụ:**  
Store: MegaMart Thời trang – chứa các sản phẩm quần áo  
Store: MegaMart Thực phẩm – chứa các sản phẩm ăn uống

**Đường dẫn tạo:**  
`Admin Panel → Stores → All Stores → Create Store`

**Lưu ý:**
- Nhiều store có thể dùng chung theme, khách hàng, cấu hình.
- Một store chỉ có một Root Category.

---

### 3. Store View

- Là giao diện hiển thị cho người dùng cuối.
- Chủ yếu dùng để thay đổi ngôn ngữ, đơn vị tiền tệ hoặc theme frontend.

**Ví dụ:**  
Store View: Vietnamese – hiển thị sản phẩm bằng tiếng Việt  
Store View: English – hiển thị sản phẩm bằng tiếng Anh

**Đường dẫn tạo:**  
`Admin Panel → Stores → All Stores → Create Store View`

**Lưu ý:**
- Dùng để dịch nội dung CMS, sản phẩm.
- Có thể thay đổi logo, theme giao diện.
- URL có thể có dạng: `/en/`, `/vi/`, tùy cấu hình.

---

## Cách hoạt động

- Khi người dùng truy cập trang, Magento xác định `Store View`, rồi `Store`, rồi `Website`.
- Cấu hình có thể áp dụng ở nhiều cấp độ:
  - Global (tất cả)
  - Website (riêng theo website)
  - Store View (chi tiết theo từng giao diện)

**Ví dụ:**
- Giá sản phẩm → cấu hình theo **Website**
- Tên sản phẩm → dịch theo **Store View**
- Theme giao diện → set theo **Store View**

---

## Thuộc tính cần chú ý

| Thành phần | Có giỏ hàng riêng | Có khách hàng riêng | Theme riêng | Ngôn ngữ riêng |
|------------|------------------|---------------------|-------------|----------------|
| Website    | ✅               | ✅                  | ✅          | ✅             |
| Store      | ❌               | ❌                  | ✅          | ✅             |
| Store View | ❌               | ❌                  | ✅          | ✅             |

---

## Tổng kết

Magento giúp bạn quản lý một hệ thống phức tạp với nhiều cửa hàng, ngôn ngữ, và giao diện khác nhau — chỉ trong **một hệ thống duy nhất**.

> Ví dụ thực tế:
> - Tập đoàn bán lẻ lớn → Website
> - Các ngành hàng: Thời trang, điện máy → Store
> - Giao diện theo ngôn ngữ: Tiếng Việt, English → Store View

---


