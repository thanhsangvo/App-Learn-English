# Walkthrough: Review Queue System

Tôi đã hoàn tất xây dựng **Review Queue System (Hệ thống Ôn Tập Đầu Xếp Hàng)** cho toàn bộ khóa học để cá nhân hoá năng lực tiếp thu của người học. Nếu làm sai, người học không bị kết thúc ván chơi ngay (với cái chết do hết mạng) mà thay vào đó sẽ liên tục quay vòng những câu bị liệt.

## 🚀 Các Thay Đổi Lớn Nhất

### 1. Hàng đợi câu hỏi kéo dài (Endless Review)
**Cho các màn hình có tuần tự (Nghe Hình, Tập Nói, Flashcards):**
- Khi người dùng chọn/phát âm sai, ngoài việc **-1 năng lượng**, thẻ bài đó sẽ bị đánh dấu `failed` và lập tức được **nhân bản ném xuống cuối danh sách**.
- Nhịp độ (momentum) vẫn tiếp tục không ngắt quãng cho phép học viên vượt lên câu tiếp theo và sẽ gặp lại câu sai ở phần cuối của chặng đường.
- Cột mốc hoàn thành Progress Bar đã được khoá lại theo **số lượng câu học ban đầu**. Ví dụ tổng có 5 câu thì Progress Bar hiển thị chuẩn `x/5` và thanh UI fill đúng tỷ lệ thay vì bị co rút lại.

### 2. Định hình lại hệ thống Chấm Sao (⭐)
Hệ thống sao không còn bị trói buộc với số `lives` hay trả lời bừa được nữa:
- Sao **chỉ được trao** nếu người dùng trả lời chính xác ngay tại **lần thử đầu tiên**.
- Nếu câu hỏi đó vòng lại (tức là đã sai ở đầu) thì người dùng bắt buộc phải làm lại để được đi qua phần sau, nhưng *không nhận được điểm bù đắp* cho câu đó.

### 3. Quy chuẩn Năng Lượng ⚡ áp dụng riêng cho Game Lật Bàn (Memory Match)
Vì mini-game Lật thẻ Memory Match diễn ra trên toàn mặt phẳng thay vì từng câu một nên hàng đợi kéo dài không áp dụng. Thay vào đó nó dùng hệ thống cấm trực tiếp:
- Mỗi lần lật hớ 2 lá không khớp sẽ bị trừ đi một lượng năng lượng.
- Sẽ có đánh điểm lật sai để trừ đi 1 hoặc 2 sao vào phần tổng kết để đảm bảo sự đồng đều với các màn hình học tập khác.

## 📁 Code được tác động:
- Khử logic `lives` và thêm Review Queue tại `listen_find_controller.dart`
- Thêm cơ chế Levanshtein fallback và add thẻ cuối hàng tại `speech_practice_controller.dart`
- Fix thẻ đẩy lùi và progress logic tại `learning_controller.dart`
- Fix lỗi tính thừa thẻ tại `memory_match_controller.dart`

> [!TIP]
> Bạn có thể bấm chọn kết quả sai trong phần `Nghe & Chỉ` hoặc `Tập Nói` để quan sát Hàng Đợi Ôn Tập hoạt động.
