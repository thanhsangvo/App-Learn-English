# ⚡ Task Tracker: Hệ Thống Năng Lượng (Hearts) & Subscriptions

- [x] 1. Core Logic (`ProgressService`):
  - Khai báo state: `currentEnergy` (mặc định 10), `lastEnergyRefillTime`, `isUnlimitedEnergy`.
  - Hàm check / trừ năng lượng: `deductEnergy()`.
  - Logic phục hồi: Timer cộng 1 ⚡ mỗi 20-30 phút. Hoặc tính toán chênh lệch thời gian khi mở lại App.
- [x] 2. UI Hiển thị (`EnergyBadge`):
  - Hiển thị số Năng Lượng ⚡ hiện tại trên Header của `MainWrapper`.
  - Đỏ/Xám khi năng lượng = 0 và hiện Countdown Timer tới lúc hồi 1 ⚡.
- [x] 3. Màn hình Cứu Trợ (`OutOfEnergyDialog`):
  - Bật lên khi người dùng cố chơi hoặc đang chơi mà mất ⚡ cuối cùng.
  - Option 1: Dùng 100 ⭐️ mua 1 ⚡.
  - Option 2: Mua gói Plus (Unlimited ⚡).
- [x] 4. Logic Game Loop (Trừ năng lượng):
  - [x] Cài cắm hàm trừ ⚡ vào `learning_controller.dart` (Flashcard / Trắc nghiệm).
  - [x] Cài cắm vào `memory_match_controller.dart` (Lật sai thẻ).
  - [x] Cài cắm vào `listen_find_controller.dart` (Nghe tìm hình sai).
