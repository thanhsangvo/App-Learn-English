# Kế hoạch Mở rộng Cửa hàng Foxy (Foxy Shop Expansion)

Kế hoạch này kết hợp cả 3 Option: Bulk Expansion (A), Themed Categories (B), và Backgrounds/Furniture (C) để tạo ra một hệ thống phần thưởng đồ sộ và hấp dẫn.

## User Review Required
> [!IMPORTANT]  
> - **Chức năng Hỗ trợ Ảnh Nền (Backgrounds)**: Yêu cầu thiết kế lại `FoxyAvatar` hoặc `FoxyKitchenScreen` một chút để render được Background/Furniture ở phía sau con cáo thay vì chỉ gắn đồ lên người.
> - **Tiến độ**: Với độ lớn của task này, nên làm lần lượt A -> B -> C để có ngay kết quả hiển thị cho các bé sớm nhất.

---

## Proposed Changes

### 1. Nâng cấp Data Model
Sửa đổi `ShopItemModel` để hỗ trợ thêm các tính năng liên quan đến Chủ đề (B) và Nội thất (C).

#### [MODIFY] `shop_item_model.dart`
- Thêm thuộc tính `category` (Ví dụ: `normal`, `event_summer`, `event_halloween`) để phục vụ lọc Chủ đề.
- Tuỳ chỉnh thuộc tính `type`: Mở rộng từ `hat`, `glasses`, `neck` thành `background`, `furniture`.

### 2. Bổ sung Danh sách Mặt hàng Khổng lồ (Option A & B)
Lấp đầy cửa hàng bằng dữ liệu tĩnh (Emoji/Image paths).

#### [MODIFY] `shop_data.dart`
- Bổ sung ít nhất 20 item trang phục tĩnh mới (Khẩu trang, Nón Cap, Bịt mắt, Cà vạt).
- Nhóm các item event: Summer (Kính mát mùa hè, Mũ cối), Winter (Khăn len lớn, Mũ len).

### 3. Nâng cấp Giao diện Cửa hàng Cửa Hàng (Shop Screen)
Tái cấu trúc UI để chứa được nhiều đồ và phân loại tốt hơn.

#### [MODIFY] `shop_screen.dart`
- Bổ sung **Bộ lọc (TabBar/SegmentedControl)** ở trên cùng: `Tất cả` | `Trang Phục` | `Sự Kiện` | `Phòng Ốc`.
- Highlight các item "Event" bằng viền màu đặc biệt (Ví dụ: Glow vàng) để thúc đẩy bé theo cơ chế khan hiếm.

### 4. Tích hợp Đồ dùng Phòng ốc và Bối cảnh (Option C)
Render đồ đạc và hình nền lên màn hình Avatar thay vì gắn lên người con Cáo.

#### [MODIFY] `foxy_avatar.dart` or `foxy_kitchen_screen.dart`
- Cập nhật cơ chế render vẽ Layer thấp nhất là `background`.
- Layer tiếp theo là `furniture`.
- Lớp trên cùng mới là bộ phận Foxy.

## Verification Plan

### Automated Tests
- Kiểm tra tính hợp lệ của hàm Filter mới trong `ShopController` (Chắc chắn lọc đúng `type` hoặc `category`).
- Kiểm tra cơ chế giới hạn và hiển thị thông báo "Mua thành công" cho đồ nội thất.

### Manual Verification
- Truy cập vào Shop và lướt qua các Tab phân trang.
- Mua thử 1 món đồ `background` mới (Ví dụ: Bầu trời đêm 🌌) và quay về trang chủ xem Background của Foxy có chuyển sang màu đêm không.
