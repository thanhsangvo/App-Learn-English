# Task: Đóng Vai Chuyên Gia UI/UX làm lại Game Lật Thẻ (Memory Match)

- [x] Chuẩn bị: Thêm thuộc tính `totalTime` vào `MemoryMatchController` để tính % thanh Tiến trình.
- [x] Phần 1: Cấu trúc Header (Top Bar)
  - [x] Bỏ tiêu đề "Mức độ".
  - [x] Nút Back to, tròn, dễ bấm.
  - [x] Gom ⚡ và ⭐ thành cụm khép cuối, tránh Overflow.
- [x] Phần 2: Đồng Hồ (Timer HUD)
  - [x] Chuyển lên dưới Header.
  - [x] Làm thanh Progress Bar chạy ngược.
  - [x] Thêm logic màu chạy: Xanh -> Vàng -> Đỏ chớp.
- [x] Phần 3: Bàn Chơi (Play Area)
  - [x] Căn giữa (`Center`). Tối ưu `childAspectRatio`.
  - [x] Không gian bao quát (Background / mây).
- [x] Phần 4: Thiết kế Thẻ Bài (Card)
  - [x] Đổi sang phong cách 3D (Skeuomorphism nhẹ): Viền trắng dày, đổ bóng sâu phần đáy.
  - [x] Decor mặt úp: Hoạ tiết chìm hoặc logo con vật.
- [x] Đảm bảo tính Responsive (LayoutBuilder).
