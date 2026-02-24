# Speed Run Daily Challenge

Thiết kế lại Daily Challenge từ 5 câu hỏi tĩnh thành chế độ **Speed Run** cuốn hút: trả lời nhanh nhất trong 60 giây, mỗi chuỗi đúng liên tiếp tăng combo nhân điểm, đến 3 combo kích hoạt **Fever Mode** x2 điểm.

---

## Proposed Changes

### Controller

#### [MODIFY] [daily_challenge_controller.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/presentation/controllers/daily_challenge_controller.dart)

- **Timer 60 giây**: `Timer.periodic` đếm ngược, khi về 0 kết thúc game
- **Combo system**: `combo.obs` đếm số câu đúng liên tiếp, reset khi sai
- **Score system**: `score.obs` = `basePoints × multiplier` (combo ≥ 3 → x2)
- **Fever Mode**: `isFeverMode.obs` = true khi combo ≥ 3
- **Câu hỏi động từ Firestore**: Thay mock data bằng câu hỏi lấy từ các topic đã học
- **Phần thưởng sao**: Tính theo score đạt được (500pts → 1⭐, 2000pts → 3⭐, 5000pts → 5⭐)

#### [MODIFY] [daily_challenge_screen.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/presentation/screens/daily_challenge_screen.dart)

- **Header**: Bỏ 5 ngôi sao tĩnh → hiện đồng hồ đếm ngược + Score + Combo badge
- **Fever Mode banner**: Xuất hiện animated banner đỏ/cam khi combo ≥ 3
- **Câu hỏi**: Thêm hiệu ứng slide-in nhanh khi chuyển câu
- **Feedback**: Thay snackbar → flash xanh/đỏ ngay trên màn hình (không block UI)
- **Màn hình kết quả**: Hiện Score, điểm đạt được, sao nhận được + nút Play Again

---

## Cơ chế Điểm

| Điều kiện | Điểm |
|-----------|------|
| Trả lời đúng | +100 pts |
| Combo 3+ (Fever) | x2 multiplier |
| Bonus tốc độ (< 3 giây) | +50 pts thêm |
| Trả lời sai | Combo reset về 0 |

| Score đạt được | Sao nhận |
|---------------|----------|
| ≥ 500 pts | ⭐ 1 sao |
| ≥ 2.000 pts | ⭐ 3 sao |
| ≥ 5.000 pts | ⭐ 5 sao |

---

## Verification Plan

### Manual Testing
- Kiểm tra đồng hồ đếm ngược và kết thúc **tự động** khi hết giờ
- Kiểm tra Combo counter reset khi trả lời sai
- Kiểm tra Fever Mode (combo ≥ 3) kích hoạt và điểm x2
- Kiểm tra số sao nhận về đúng với bảng điểm
