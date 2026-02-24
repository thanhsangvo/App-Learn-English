# Kế hoạch thêm hiển thị năng lượng vào màn hình học tập

Người dùng muốn thấy năng lượng của mình ngay trong lúc học để biết khi nào sắp hết. Tôi sẽ thêm widget hiển thị năng lượng vào header của các màn hình học tập chính.

## Các màn hình thay đổi

### 1. Learning Screen (Học từ vựng)
- **File**: `lib/presentation/screens/learning_screen.dart`
- **Vị trí**: Header, nằm cạnh ô hiển thị Ngôi sao (Score).

### 2. Listen & Find Screen (Nghe và chọn hình)
- **File**: `lib/presentation/screens/listen_find_screen.dart`
- **Vị trí**: Header, nằm cạnh ô hiển thị Ngôi sao.

### 3. Memory Match Screen (Trò chơi lật hình)
- **File**: `lib/presentation/screens/memory_match_screen.dart`
- **Vị trí**: Header, nằm cạnh ô hiển thị Ngôi sao.

### 4. Speech Practice Screen (Tập nói)
- **File**: `lib/presentation/screens/speech_practice_screen.dart`
- **Vị trí**: Header, nằm cạnh ô hiển thị Tiến độ.

## Giải pháp kỹ thuật
- Sử dụng widget `EnergyBadge` đã có sẵn (hoặc một phiên bản thu nhỏ nếu cần) để đảm bảo tính nhất quán.
- Thêm `ProgressService` vào các controller nếu chưa có để lấy dữ liệu năng lượng (hầu hết đã có thông qua `LearningController` hoặc các dịch vụ liên quan).

## Kế hoạch xác minh
### Kiểm tra thủ công
1. Vào học một chủ đề bất kỳ -> Kiểm tra header có hiện ⚡ và số năng lượng không.
2. Chơi game "Nghe & chọn", "Lật hình", "Tập nói" -> Kiểm tra header.
3. Chạm vào ⚡ để đảm bảo popup giải thích năng lượng vẫn hoạt động tốt.
