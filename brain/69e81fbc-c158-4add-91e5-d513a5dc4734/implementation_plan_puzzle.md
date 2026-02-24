# Ghép Tranh Foxy (Puzzle Album 3×3)

Hệ thống mảnh ghép hiện tại chỉ tăng số nguyên. Thiết kế lại thành **Album Tranh Foxy**: mỗi tuần 1 bức tranh 3×3 (9 mảnh). Chơi/học mỗi ngày → mở 1 mảnh ngẫu nhiên. Ghép đủ 9 → nhận phần thưởng (sao + item Shop).

---

## Proposed Changes

### Dữ liệu tranh

#### [NEW] [puzzle_data.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/data/data_sources/puzzle_data.dart)

Danh sách 10 bức tranh Foxy, mỗi bức gồm:
- `id`, `name`, `emoji` (lưới 9 icon emoji tạo thành 1 bức tranh)
- `rewardStars` (sao nhận khi hoàn thành)
- `weekIndex` (tuần nào dùng tranh nào, xoay vòng)

### Logic

#### [MODIFY] [progress_service.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/core/services/progress_service.dart)

- Thay `puzzlePieces` (int) → `puzzleRevealedIndexes` (List\<int\>) — lưu vị trí mảnh đã mở (0-8)
- Thêm `currentPuzzleId` (String) — tranh hiện tại
- Thêm `completedPuzzleIds` (List\<String\>) — danh sách tranh đã hoàn thành
- Sửa `addPuzzlePiece()` → `revealPuzzlePiece()`: chọn random 1 vị trí chưa mở, thêm vào list
- Thêm `isPuzzleComplete` → kiểm tra 9/9, trao thưởng + auto chuyển tranh mới
- Logic chọn tranh theo tuần: `weekIndex = weekOfYear % totalPuzzles`

#### [MODIFY] [practice_controller.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/presentation/controllers/practice_controller.dart)

- Cập nhật getter để expose dữ liệu puzzle mới (revealedIndexes, currentPuzzle)

### Giao diện

#### [MODIFY] [practice_screen.dart](file:///Users/devsang/Developer/App%20Learn%20English/lib/presentation/screens/practice_screen.dart)

- Thay `_buildPuzzleProgress()` (thanh bar cũ) → **Widget Grid 3×3** hiện mảnh đã lật
- Mỗi ô: chưa mở = `❓`, đã mở = emoji tương ứng
- Khi bấm vào widget → mở PuzzleDetailDialog full-screen xem tranh lớn

---

## Cấu trúc dữ liệu tranh (Emoji Art)

Mỗi bức tranh = List 9 emoji xếp thành lưới 3×3:

| Tranh | Tên | Emoji Grid |
|-------|-----|------------|
| 1 | Foxy Đi Biển | 🌊☀️🌊 / 🏖️🦊🐚 / 🌴🏄🌴 |
| 2 | Foxy Phi Hành Gia | ⭐🌙⭐ / 🚀🦊🛸 / 🌍☄️🪐 |
| 3 | Foxy Siêu Đầu Bếp | 🍳🧁🍰 / 🥘🦊🍕 / 🥗🍜🍦 |
| ... | (thêm 7 tranh nữa) | ... |

---

## Phần thưởng

| Hoàn thành | Nhận được |
|------------|-----------|
| Ghép đủ 9/9 mảnh | ⭐ 10 sao + hiệu ứng confetti |
| Mỗi 3 tranh hoàn thành | 🎁 Unlock 1 item hiếm trong Shop |

---

## Verification Plan

### Manual Testing
- Kiểm tra mảnh ghép mở đúng random (không trùng vị trí đã mở)
- Kiểm tra hoàn thành 9/9 → trao sao + tự chuyển tranh mới
- Kiểm tra UI grid 3×3 hiển thị đúng emoji đã mở / ❓ chưa mở
