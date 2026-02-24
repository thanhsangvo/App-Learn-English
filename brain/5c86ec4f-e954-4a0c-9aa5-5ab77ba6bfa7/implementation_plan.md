# Sửa lỗi cú pháp JSON trong `shop_items_data.json`

Dữ liệu shop đang bị lỗi cú pháp tại dòng 39 và 45, khiến ứng dụng không thể load được danh sách vật phẩm.

## Thay đổi đề xuất

### Assets

#### [MODIFY] [shop_items_data.json](file:///Users/devsang/Developer/App%20Learn%20English/assets/shop_items_data.json)
- Sửa dòng 39 và 45 để tách các trường `price`, `type`, `category`, `dx`, `dy`, `scale` ra riêng biệt và đúng cú pháp JSON.
- Đảm bảo tất cả các cặp key-value đều có dấu ngoặc kép và được ngăn cách bởi dấu phẩy.

## Kế hoạch xác minh

### Kiểm tra thủ công
- Đọc lại file sau khi sửa bằng `view_file` để đảm bảo cấu trúc JSON đã chính xác.
- Nếu có thể, chạy `dart format assets/shop_items_data.json` để chuẩn hóa.

### Kiểm tra ứng dụng
- Quan sát log ứng dụng (nếu có) để xác nhận không còn lỗi "Colon expected".
