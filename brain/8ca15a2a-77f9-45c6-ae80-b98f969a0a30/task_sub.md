# Nhiệm Vụ: Tích Hợp Subscription & Nâng Cấp Ngữ Cảnh

## 1. Thiết lập & Cấu Hình RevenueCat
- [x] Thêm thư viện `purchases_flutter` vào pubspec.yaml.
- [x] Xây dựng dịch vụ trung tâm `RevenueCatService`.
- [x] Inject `RevenueCatService` vào `main.dart`.

## 2. Kết Nối Trạng Thái Ứng Dụng (VIP Logic)
- [x] Không trừ Năng Lượng nếu `isSuperMaxy`.
- [x] Mở khóa toàn bộ Topic nếu `isSuperMaxy`.
- [x] Không hiện Quảng Cáo Interstitial nếu `isSuperMaxy`.
- [x] X2 Sao thưởng cuối game nếu `isSuperMaxy`.

## 3. UI/UX "Super Maxy" & Contextual Upsell
- [x] Tạo `paywall_dialog.dart` (Giao diện mua VIP).
- [x] Kết nối Paywall vào `out_of_energy_dialog.dart`.
- [x] Thêm nút Upgrade VIP vào `profile_achievements_screen.dart`.

## 4. Test & Verification
- [x] Dart analyze — No errors.
- [ ] Test Sandbox trên device thật (cần API Key thật từ RevenueCat Dashboard).
