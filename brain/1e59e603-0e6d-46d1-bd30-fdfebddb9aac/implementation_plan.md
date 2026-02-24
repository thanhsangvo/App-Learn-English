# Kế hoạch Cập nhật Hệ thống Shop Dynamic

Mục tiêu là làm cho hệ thống hiển thị vật phẩm (MaxyAvatar) có thể nhận diện được các vật phẩm mới được thêm từ Firebase mà không cần cập nhật code (file `shop_data.dart`).

## Thay đổi đề xuất

### 1. ShopController
- Thêm phương thức `getItemById(String id)` để tìm kiếm vật phẩm trong danh sách `items` đã được merge (Local + Firebase).
- Đảm bảo danh sách `items` được khởi tạo ngay khi controller được tạo.

### 2. MaxyAvatar
- Thay đổi logic tìm kiếm vật phẩm đang mặc.
- Thay vì gọi `ShopData.getItemById(id)`, widget sẽ gọi `ShopController.getItemById(id)`.
- Thêm xử lý an toàn nếu `ShopController` chưa được khởi tạo.

### 3. Tổ chức dữ liệu (Tương lai)
- Khi dữ liệu trên Firebase đã ổn định, có thể rút gọn `shop_data.dart` chỉ còn các item hệ thống (Tháo đồ, Energy).

## Kế hoạch xác minh

### Kiểm tra tự động
- Chạy ứng dụng và mở Cửa hàng.
- Kiểm tra log để đảm bảo dữ liệu Firebase được tải và merge thành công.

### Kiểm tra thủ công
- Trang bị một món đồ lấy từ Firebase.
- Quay lại màn hình chính và kiểm tra xem `MaxyAvatar` có hiển thị đúng món đồ đó không.
- Thử thêm một món đồ mới trên Firebase Console và kiểm tra xem app có hiển thị được không (sau khi reload).
