# Kế hoạch Tích hợp AdMob & Remote Config

## Mục tiêu
Tích hợp quảng cáo AdMob (Interstitial và Rewarded) được điều khiển qua Firebase Remote Config. 
- Hiển thị quảng cáo Interstitial sau khi hoàn thành game/topic.
- Cho phép xem quảng cáo Rewarded để nhận +5 Năng lượng khi hết.

## User Review Required
> [!IMPORTANT]
> - Cần cấu hình **Remote Config** trên Firebase Console với các keys: `showAdsTopic` (boolean), `interstitialAdUnitId` (string), `rewardedAdUnitId` (string).
> - ID App AdMob Android/iOS đang sử dụng **Test ID** của Google. Khi release thật, cần đổi thành ID Production.

---

## Proposed Changes

### 1. Dependencies & Platform Setup

#### [MODIFY] pubspec.yaml
- Thêm `google_mobile_ads`
- Thêm `firebase_remote_config`

#### [MODIFY] android/app/src/main/AndroidManifest.xml
- Thêm `<meta-data android:name="com.google.android.gms.ads.APPLICATION_ID" android:value="..."/>` (Test ID)

#### [MODIFY] ios/Runner/Info.plist
- Thêm `GADApplicationIdentifier` (Test ID)

### 2. Core Services

#### [NEW] lib/core/services/remote_config_service.dart
- Quản lý Firebase Remote Config.
- Lấy các giá trị: `showAdsTopic`, ID quảng cáo.

#### [NEW] lib/core/services/ad_service.dart
- Khởi tạo `MobileAds.instance.initialize()`.
- Load và quản lý **Interstitial Ad**.
- Load và quản lý **Rewarded Ad**.

#### [MODIFY] lib/main.dart
- Khởi tạo `RemoteConfigService` và `AdService` sau khi init Firebase.

### 3. Cài cắm Quảng Cáo (Integration)

#### [MODIFY] lib/presentation/controllers/learning_controller.dart, memory_match_controller.dart, listen_find_controller.dart
- Tại hàm kết thúc game/topic (khi win), nếu Remote Config `showAdsTopic` == `true` -> gọi `AdService.showInterstitialAd()`.

#### [MODIFY] lib/presentation/widgets/out_of_energy_dialog.dart
- Thêm nút "Xem video nhận +5 ⚡".
- Gọi `AdService.showRewardedAd()`.
- Callback khi xem xong: gọi `ProgressService.addEnergy(5)` và thông báo thành công.

---

## Verification Plan
### Automated Tests
- Chạy `flutter analyze` đảm bảo không có lỗi cú pháp.
- Build thử cho Android & iOS để đảm bảo Manifest/Info.plist cấu hình đúng.

### Manual Verification
1. Mở App, cạn năng lượng -> nhấn "Xem quảng cáo" -> Đợi hết video test -> Xác nhận ⚡ tăng thêm 5.
2. Hoàn thành một màn chơi (Flashcard/Lật Thẻ/Nghe Tìm) -> Xác nhận xem có nhảy quảng cáo xen kẽ (Interstitial) không.
3. Thay đổi giá trị `showAdsTopic` trên Firebase Console thành `false` -> Chơi lại -> Xác nhận quảng cáo xen kẽ KHÔNG hiển thị.
