# Content Elements trong Magento 2

## Tên
Content Elements - Pages, Blocks, Widgets, Templates

## Tác dụng
Các phần tử nội dung (Content Elements) trong Magento 2 cho phép bạn tạo, quản lý và hiển thị nội dung tĩnh hoặc động trên trang web một cách linh hoạt. Chúng hỗ trợ người dùng không chuyên kỹ thuật tùy biến giao diện web dễ dàng qua admin panel.

## Các thành phần chính

### 1. Pages
- **Tác dụng**: Tạo các trang tĩnh như Giới thiệu, Chính sách bảo mật, Liên hệ,...
- **Ví dụ minh họa**: Trang "About Us" hiển thị ở menu chính của website.
- **Đường dẫn quản lý**:  
  `Admin Panel → Content → Pages`
- **Cách sử dụng**: Tạo trang mới, thêm nội dung HTML hoặc sử dụng các widget/block có sẵn.
- **Cách hoạt động**: Magento lưu thông tin trang trong bảng `cms_page`, nội dung HTML nằm trong `content` hoặc file `.phtml`.
- **Thuộc tính cần chú ý**:
  - `URL Key`: đường dẫn hiển thị trên trình duyệt.
  - `Layout`: định dạng 1 cột, 2 cột, full-width,...
  - `Content`: nội dung chính của trang.
- **Lưu ý**:
  - Có thể chèn widget hoặc block vào nội dung HTML bằng cú pháp `{{widget ...}}` hoặc `{{block ...}}`.

---

### 2. Blocks
- **Tác dụng**: Tạo các khối nội dung có thể tái sử dụng trên nhiều trang khác nhau như banner, thông điệp quảng cáo, footer,...
- **Ví dụ minh họa**: Block “Free shipping for orders over $50” hiển thị ở tất cả các trang.
- **Đường dẫn quản lý**:  
  `Admin Panel → Content → Blocks`
- **Cách sử dụng**: Tạo block, chèn vào CMS Page, Layout XML hoặc thêm vào template `.phtml`.
- **Cách hoạt động**: Lưu trong bảng `cms_block`, sử dụng các khu vực layout để hiển thị.
- **Thuộc tính cần chú ý**:
  - `Identifier`: mã định danh để chèn block.
  - `Content`: nội dung HTML, có thể chèn thêm widget/block khác.
- **Lưu ý**:
  - Có thể hiển thị qua XML layout với đoạn mã:
    ```xml
    <referenceContainer name="content">
        <block class="Magento\Cms\Block\Block" name="custom_block">
            <arguments>
                <argument name="block_id" xsi:type="string">your_block_identifier</argument>
            </arguments>
        </block>
    </referenceContainer>
    ```

---

### 3. Widgets
- **Tác dụng**: Cho phép chèn các nội dung động (sản phẩm, khuyến mãi, liên kết,...) vào trang CMS hoặc block mà không cần code.
- **Ví dụ minh họa**: Widget hiển thị danh sách sản phẩm khuyến mãi.
- **Đường dẫn quản lý**:  
  `Admin Panel → Content → Widgets`
- **Cách sử dụng**: Tạo widget → chọn loại nội dung → cấu hình điều kiện hiển thị.
- **Cách hoạt động**: Magento dựng widget dựa trên class widget tương ứng và inject vào layout XML.
- **Thuộc tính cần chú ý**:
  - `Widget Type`: loại widget (Catalog Products List, CMS Static Block,...)
  - `Display On`: nơi hiển thị.
  - `Conditions`: quy định hiển thị widget ở trang nào.
- **Lưu ý**:
  - Widget được thể hiện trong nội dung CMS bằng cú pháp như:  
    `{{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" ... }}`

---

### 4. Templates
- **Tác dụng**: Các file `.phtml` để hiển thị nội dung động trên giao diện frontend.
- **Ví dụ minh họa**: File template hiển thị form đăng ký, danh sách sản phẩm,...
- **Đường dẫn**:  
  `app/design/frontend/<Vendor>/<theme>/Magento_Cms/templates/`
- **Cách sử dụng**: Tạo file `.phtml`, định nghĩa block XML hoặc PHP gọi đến file này.
- **Cách hoạt động**: Magento load file `.phtml` thông qua layout XML hoặc PHP block.
- **Thuộc tính cần chú ý**:
  - Tên file: cần đúng cấu trúc và đặt đúng vị trí trong module/theme.
- **Lưu ý**:
  - Có thể gọi template từ CMS Page bằng `{{block class="..." template="..."}}`

---

## Tổng kết

| Thành phần | Quản lý qua Admin | Tái sử dụng | Có thể dùng code | Mục đích |
|------------|-------------------|-------------|------------------|----------|
| Page       | ✅                 | ❌           | ✅                | Tạo trang tĩnh |
| Block      | ✅                 | ✅           | ✅                | Tạo nội dung reuse |
| Widget     | ✅                 | ✅           | ✅                | Nội dung động |
| Template   | ❌ (bằng code)     | ✅           | ✅                | Hiển thị nội dung động bằng code |

---

## Lưu ý chung
- Một block có thể chứa nhiều widget nhưng 1 widget chỉ chứa 1 block.
- Nên phân biệt rõ `CMS Content` (Page/Block) với `Template` khi làm việc với theme.
- Luôn clear cache sau khi tạo mới hoặc chỉnh sửa nội dung:  
  `php bin/magento cache:flush`


# Media & Design trong Magento 2

## Tên
Media, Media Gallery, Design, Configuration, Themes, Schedule

## Tác dụng
Nhóm chức năng này hỗ trợ việc quản lý tài nguyên hình ảnh, thiết lập giao diện, cấu hình chủ đề (theme), và lên lịch thiết kế theo mùa hoặc chiến dịch marketing.

---

## 1. Media

### Tác dụng
Lưu trữ toàn bộ tài nguyên tĩnh như ảnh sản phẩm, banner, logo,... được upload từ admin hoặc qua code.

### Ví dụ minh họa
Ảnh sản phẩm hiển thị trong chi tiết sản phẩm được lưu trong thư mục `pub/media/catalog/product/`.

### Đường dẫn
- Trên hệ thống: `pub/media/`
- Từ admin: không quản lý trực tiếp, nhưng được dùng qua các block/widget hoặc CMS.

### Cách sử dụng
- Upload ảnh thông qua admin khi tạo sản phẩm, block, hoặc widget.
- Trong code, ảnh có thể được truy cập bằng `$block->getViewFileUrl()` hoặc gọi trực tiếp bằng URL tương đối từ `pub/media`.

### Lưu ý
- Nên tối ưu ảnh trước khi upload.
- Hệ thống có thể tạo ảnh thumbnail tự động khi load ảnh sản phẩm.

---

## 2. Media Gallery

### Tác dụng
Quản lý thư viện ảnh chung được sử dụng trong toàn site.

### Ví dụ minh họa
Chèn ảnh từ thư viện vào CMS Page bằng giao diện WYSIWYG editor.

### Đường dẫn
`Admin Panel → Content → Media Gallery`

### Cách sử dụng
- Upload ảnh mới hoặc chọn ảnh có sẵn khi tạo block hoặc page.
- Tìm kiếm ảnh theo tag hoặc đường dẫn thư mục.

### Cách hoạt động
Magento lưu ảnh ở `pub/media`, metadata được lưu trong DB (`media_gallery_asset`, `media_gallery_content`...)

### Thuộc tính cần chú ý
- Tên file, mô tả, tag ảnh, thư mục chứa ảnh

### Lưu ý
- Không xóa ảnh đang được dùng trong sản phẩm hoặc block.

---

## 3. Design

### Tác dụng
Quản lý theme và giao diện tổng thể của website.

### Ví dụ minh họa
Thay đổi theme thành "Luma" cho cửa hàng chính.

### Đường dẫn
`Admin Panel → Content → Design → Configuration`

### Cách sử dụng
- Chọn theme cho từng store view.
- Thiết lập logo, favicon, màu nền,...

### Cách hoạt động
Magento đọc cấu hình trong bảng `core_config_data` để xác định theme đang sử dụng.

### Thuộc tính cần chú ý
- `Default Theme`, `Header`, `Footer`, `Product Image Sizes`

### Lưu ý
- Sau khi thay đổi theme, cần deploy lại static content và flush cache.

---

## 4. Configuration (Theme)

### Tác dụng
Cấu hình theme và giao diện hiển thị theo từng store view.

### Ví dụ minh họa
Store `Vietnam` dùng theme A, store `US` dùng theme B.

### Đường dẫn
`Admin Panel → Content → Design → Configuration → [Edit]`

### Cách sử dụng
- Nhấp "Edit" trên store view → chọn theme phù hợp → Save.
- Có thể upload logo riêng cho từng store view.

### Cách hoạt động
Cấu hình được áp dụng tùy theo scope: Default / Website / Store view.

### Lưu ý
- Theme phải được enable trước khi áp dụng.
- Nếu có lỗi thì hãy thiết lập theme cho cấp cao hơn.
---

## 5. Themes

### Tác dụng
Là bộ giao diện điều khiển cách hiển thị của toàn bộ trang web.

### Ví dụ minh họa
Theme “Luma” với layout 2 cột, màu cam – trắng.

### Đường dẫn (trong mã nguồn)
`app/design/frontend/<Vendor>/<theme>`

### Cách sử dụng
- Cài theme qua Composer hoặc thủ công.
- Enable theme qua admin hoặc dòng lệnh:
  ```bash
  php bin/magento theme:enable <theme-name>
  php bin/magento setup:upgrade
  php bin/magento setup:static-content:deploy
