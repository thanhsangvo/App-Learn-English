# Tích hợp Firestore + FireCMS vào App Learn English

## Mô tả
Chuyển data vocabulary/topics từ hardcode sang **Firestore**, cho phép quản lý nội dung qua **FireCMS** mà không cần build lại app.

## User Review Required

> [!IMPORTANT]  
> **Cần có Firebase Project**: Bạn cần tạo Firebase project và thêm `google-services.json` (Android) + `GoogleService-Info.plist` (iOS). Hiện chưa có file nào trong project.



---

## Proposed Changes

### 1. Firebase Core Setup

#### [MODIFY] [pubspec.yaml](file:///Users/devsang/Developer/App Learn English/pubspec.yaml)
- Thêm `firebase_core`, `cloud_firestore`

#### [NEW] [firebase_options.dart](file:///Users/devsang/Developer/App Learn English/lib/firebase_options.dart)
- Tạo bằng `flutterfire configure` — config tự động cho Android/iOS

#### [MODIFY] [main.dart](file:///Users/devsang/Developer/App Learn English/lib/main.dart)
- Thêm `Firebase.initializeApp()` trong `main()`

---

### 2. Firestore Schema

```
📁 Firestore Collections:

topics/ (collection)
  ├── animals (document)
  │   ├── name: "Animals"
  │   ├── nameVi: "Động vật"
  │   ├── emoji: "🦁"
  │   ├── emoji: "🦁"
  │   ├── totalWords: 6
  │   ├── order: 0
  │   └── vocabularies/ (subcollection)
  │       ├── cat { word, meaning, emoji }
  │       ├── dog { ... }
  │       └── ...
  ├── colors (document)
  └── ...
```

---

### 3. Data Layer Changes

#### [NEW] [firestore_vocabulary_repository.dart](file:///Users/devsang/Developer/App Learn English/lib/data/repositories/firestore_vocabulary_repository.dart)
- Implement `VocabularyRepository` đọc từ Firestore
- Cache local để hoạt động offline
- Fallback về data hardcode nếu offline lần đầu

#### [MODIFY] [topic_model.dart](file:///Users/devsang/Developer/App Learn English/lib/data/models/topic_model.dart)
- Thêm `fromFirestore()` factory constructor
- Thêm `toFirestore()` method

#### [NEW] [firestore_seed_service.dart](file:///Users/devsang/Developer/App Learn English/lib/core/services/firestore_seed_service.dart)
- Script upload data hiện tại lên Firestore (chạy 1 lần)

---

### 4. Dependency Injection

#### [MODIFY] [home_controller.dart](file:///Users/devsang/Developer/App Learn English/lib/presentation/controllers/home_controller.dart)
- Inject `FirestoreVocabularyRepository` thay vì tạo trực tiếp

#### Các controllers khác dùng `VocabularyRepository`:
- `speech_practice_controller.dart`
- `memory_match_controller.dart`  
- `listen_find_controller.dart`

---

## Verification Plan

### Automated
- `flutter analyze` — zero errors
- Chạy app, kiểm tra topics load từ Firestore
- Test offline mode — vẫn hiển thị data cached

### Manual
- Sửa 1 từ vựng trên Firebase Console → verify app hiển thị đúng
- Hướng dẫn setup FireCMS để quản lý nội dung qua giao diện web
