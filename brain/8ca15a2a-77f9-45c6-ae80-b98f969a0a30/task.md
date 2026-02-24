# Task: Đổi tên Foxy → Maxy ✅

## Đổi tên file (4 file) ✅
- [x] `foxy_avatar.dart` → `maxy_avatar.dart`
- [x] `foxy_kitchen_screen.dart` → `maxy_kitchen_screen.dart`
- [x] `foxy_kitchen_controller.dart` → `maxy_kitchen_controller.dart`
- [x] `foxy_kitchen_binding.dart` → `maxy_kitchen_binding.dart`

## Cập nhật nội dung code (24 file) ✅
- [x] Class names (FoxyAvatar→MaxyAvatar, FoxyKitchenController→MaxyKitchenController...)
- [x] Variable names (foxySpeech→maxySpeech, foxyHunger→maxyHunger, foxyState→maxyState...)
- [x] Method names (feedFoxy→feedMaxy, getFoxyMessage→getMaxyMessage...)
- [x] Import paths (foxy_avatar→maxy_avatar, foxy_kitchen→maxy_kitchen)
- [x] Route names (/foxy-kitchen → /maxy-kitchen)
- [x] UI strings ("Foxy nói"→"Maxy nói", puzzle names...)
- [x] SharedPreferences keys (foxy_hunger→maxy_hunger)
- [x] Notification strings
- [x] Comments and docs

## Verify ✅
- [x] `grep -ri "foxy"` → 0 results
- [x] `dart analyze` → zero errors liên quan
