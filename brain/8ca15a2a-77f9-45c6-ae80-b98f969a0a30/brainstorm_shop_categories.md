## 🧠 Brainstorm: Tách danh mục Cửa hàng và Chức năng Tháo đồ

### Context
Hiện tại, mục "Trang Phục" đang gộp chung Kính, Mũ và Dây chuyền. Người dùng muốn tháo đồ đã mặc ra nhưng không có nút nào cho phép làm vậy. Cần tách danh mục cho rõ ràng hơn và thêm chức năng "Unequip" (Tháo đồ).

---

### Option A: Thêm ô "Không mặc" ngay đầu mỗi danh mục con
Tách "Trang Phục" thành 2-3 tab riêng biệt: "Mũ", "Kính", "Vòng Cổ". Tại vị trí đầu tiên của mỗi tab (hoặc trong lưới vật phẩm), thêm một thẻ "Item" đặc biệt (có icon dấu gạch chéo hoặc icon trống rỗng) với nhãn "Tháo ra".

✅ **Pros:**
- Rất dễ hiểu và thao tác, giống hệt cách chọn mua đồ.
- Nằm ngay trong luồng trải nghiệm vuốt chạm của người dùng.
- Tận dụng luôn UI của thẻ `_buildItemCard` hiện tại.

❌ **Cons:**
- Tốn một slot hiển thị trong lưới đồ.
- Cần sửa nhẹ logic `ShopController` để nhận diện Item ID đặc biệt này mang ý nghĩa "Unequip".

📊 **Effort:** Low

---

### Option B: Thêm nút "Tháo đồ" nổi (Floating Action Button) riêng biệt trên Cửa hàng
Tách "Trang Phục" thành "Mũ", "Kính". Gần vị trí `MaxyAvatar` hoặc ở góc dưới Cửa hàng, đặt một nút "Tháo đồ đang chọn". Khi người dùng ấn vào một category (VD: Mũ), nút này sẽ hiện ra và cho phép tháo Mũ.

✅ **Pros:**
- UI gọn gàng, không dính líu đến danh sách đồ.
- Tách biệt rõ ràng hành động Mua/Mặc và Tháo.

❌ **Cons:**
- Cần viết UI mới hoàn toàn cho nút nổi.
- Tốn không gian trên màn hình (đặc biệt khi Bottom Sheet kéo lên).
- Logic tháo đồ phải phụ thuộc vào việc "Tab nào đang được mở".

📊 **Effort:** Medium

---

### Option C: Tháo đồ trực tiếp từ Widget Avatar (Tương tác trên người bé mèo)
Tách "Trang Phục" thành "Mũ", "Kính". Cho phép người dùng nhấn thẳng vào cái Mũ trên đầu Maxy (ở màn hình Cửa hàng hoặc Profile) để tháo nó ra, kèm hiệu ứng "Poof" biến mất.

✅ **Pros:**
- Trải nghiệm tương tác cực kỳ thú vị và "Pro Max".
- Cảm giác chân thực như đang tương tác với thú cưng.

❌ **Cons:**
- Code rất phức tạp vì phải bao bọc từng thành phần phụ kiện bằng các nút bấm nhận diện tọa độ.
- Có thể vô tình chạm nhầm khi đang muốn kéo Bottom Sheet.

📊 **Effort:** High

---

## 💡 Recommendation

**Option A** là lựa chọn tối ưu, dễ hiểu và giống với các game phổ biến nhất.
Em đề xuất:
1. Đổi tên tab "Trang Phục" thành các tab riêng: "Mũ", "Kính".
2. Chèn một thẻ giả có ID vd `remove_hat` / `remove_glasses` làm vật phẩm đầu tiên trong mỗi danh sách. Nút này sẽ đại diện cho việc "Tháo đồ". Khi ấn vào, gọi hàm `progressService.equippedItems.remove(...)`.

Anh thấy Option A và hướng triển khai như vậy có mượt không ạ?
