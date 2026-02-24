# Task: AdMob & Remote Config Integration

## 1. Setup & Config
- [x] Thêm dependencies (`google_mobile_ads`, `firebase_remote_config`)
- [x] Cấu hình Android (AndroidManifest.xml)
- [x] Cấu hình iOS (Info.plist)

## 2. Services
- [x] Tạo `RemoteConfigService` (fetch keys, expose values)
- [x] Tạo `AdService` (load/show Interstitial, load/show Rewarded)
- [x] Khởi tạo trong `main.dart`

## 3. Integration - Interstitial Ads
- [x] Cài cắm gọi `showInterstitialAd()` vào `learning_controller.dart` khi hoàn thành bài.
- [x] Cài cắm gọi `showInterstitialAd()` vào `memory_match_controller.dart` khi thắng.
- [x] Cài cắm gọi `showInterstitialAd()` vào `listen_find_controller.dart` khi kết thúc.

## 4. Integration - Rewarded Ads (Energy)
- [x] Sửa `out_of_energy_dialog.dart` thêm UI nút "Xem quảng cáo (+5 ⚡)"
- [x] Tích hợp xử lý gọi `showRewardedAd` và cộng năng lượng qua `ProgressService`.

## 5. Verify & Test
- [x] Đảm bảo Ads không gây crash khi chạy offline.
- [x] Kiểm tra remote config fallback default values.
