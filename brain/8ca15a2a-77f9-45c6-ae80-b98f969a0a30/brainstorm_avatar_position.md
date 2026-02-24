## 🧠 Brainstorm: Điều chỉnh vị trí vật phẩm cho MaxyAvatar

### Context
Hiện tại, trong `MaxyAvatar` (`lib/presentation/widgets/maxy_avatar.dart`), các vật phẩm (mũ, kính, vòng cổ) được set cứng tỷ lệ `top` và `scale` dựa trên container size. Tuy nhiên, mèo Maxwell có hình dạng hơi bầu bĩnh và các món đồ có kích thước gốc khác nhau. Việc set cứng khiến một số món (như mũ top hat, vương miện) bị lệch khỏi đầu hoặc che khuất mắt nhân vật.

---

### Option A: Thêm thuộc tính `offset` và `scale` vào `ShopItemModel`
Mở rộng model dữ liệu của từng món đồ trong cửa hàng để quy định chính xác vị trí và độ thu phóng riêng biệt của món đó.

✅ **Pros:**
- Chuẩn xác tuyệt đối cho từng món đồ.
- Dễ dàng thêm món mới với hình dáng kỳ lạ (ví dụ: một chiếc mũ rất cao hoặc kính lệch) mà không cần sửa code UI.
- File UI `MaxyAvatar` sẽ rất gọn gàng.

❌ **Cons:**
- Phải cập nhật lại toàn bộ file dữ liệu (`shop_data.dart`).
- Cần tốn thời gian căn chỉnh thủ công từng thông số `dx`, `dy`, `scale` cho từng món đồ.

📊 **Effort:** Medium

---

### Option B: Tinh chỉnh lại Logic tính `top` và `scale` dựa theo Category trong `MaxyAvatar`
Sử dụng hằng số tĩnh hoặc map config ngay trong widget `MaxyAvatar` thay vì tính tỷ lệ chung chung. Nhóm các item có cùng form dáng lại với nhau.

✅ **Pros:**
- Sửa nhanh gọn, chỉ cần mông má lại hàm `_buildAccessoryLayer` trong `MaxyAvatar`.
- Không cần sửa cấu trúc model hay data.
- Đáp ứng tốt nhu cầu hiện tại vì số lượng item theo từng loại (mũ, kính) có lẽ tương đồng form.

❌ **Cons:**
- Nếu sau này có một cái mũ hình dáng cực dị (vd: mũ phù thủy lệch 1 bên), logic này có thể bị phá vỡ và phải vất vả sửa lại.
- Tăng độ dài và phức tạp của hàm build UI.

📊 **Effort:** Low

---

### Option C: Sử dụng `Transform` với `FractionalOffset` và căn chỉnh tỷ lệ theo khung xương (Skeleton/Pivot)
Thay vì dùng `Positioned` với giá trị pixel/ratio cố định, ta cố định một "điểm neo" (pivot) trên hình ảnh con mèo chứa tọa độ tương đối (vd: điểm neo trên đỉnh đầu là (0.5, 0.1)). Các hình ảnh vật phẩm cũng được thiết kế (hoặc crop padding) sao cho viền dưới của chúng chạm đúng điểm neo đó.

✅ **Pros:**
- Layout tự nhiên, responsive 100% không lo bể layout khi đổi kích thước thiết bị.
- Đây là cách chuẩn nhất trong làm game 2D thay đổi trang phục.

❌ **Cons:**
- Đòi hỏi phải có sự can thiệp từ khâu cắt ghép hình ảnh (Asset) để tạo khoảng không xung quanh (padding) hoặc phải code logic tính điểm neo phức tạp.
- Cực kỳ tốn công thiết lập ban đầu.

📊 **Effort:** High

---

## 💡 Recommendation

**Option B** là lựa chọn phù hợp nhất với tiến độ hiện tại.
Ta có thể sửa lại hàm `_buildAccessoryLayer` bằng cách tạo một Map nhỏ chứa thông số cho riêng 1 vài món cụ thể (vd: nón sinh nhật cần thấp hơn nón ảo thuật). Quá trình này sẽ tốn khoảng 5 phút tinh chỉnh. Nếu tương lai shop lặp lại quá nhiều đồ, ta mới cân nhắc Option A.

**Anh/Chị muốn em triển khai theo hướng nào ạ?** Nếu chọn Option B, em sẽ tinh chỉnh lại tọa độ và viết một vài hard-code điều chỉnh cho chiếc nón anh vừa gửi hình nhé!
