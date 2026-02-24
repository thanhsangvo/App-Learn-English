# Kế hoạch triển khai Script Import Dữ Liệu

## Mục tiêu
Tạo công cụ giúp nhập liệu hàng loạt (Bulk Import) Topic và Vocabulary từ file JSON vào Firestore, tiết kiệm thời gian so với nhập thủ công trên FireCMS.

## Cấu trúc dữ liệu JSON
File `assets/data_import.json` sẽ có cấu trúc như sau:
```json
[
  {
    "id": "topic_id",
    "name": "Topic Name",
    "nameVi": "Tên chủ đề",
    "emoji": "🦁",
    "imagePath": "url_anh",
    "order": 1,
    "vocabularies": [
      {
        "id": "vocab_id",
        "word": "Word",
        "meaning": "Nghĩa",
        "imagePath": "url_anh_vocab",
        "emoji": "🐱",
        "audioPath": "url_audio"
      }
    ]
  }
]
```

## Script `lib/scripts/import_data.dart`
Script này sẽ thực hiện các bước:
1.  Đọc nội dung file `assets/data_import.json`.
2.  Khởi tạo Firebase (sử dụng `firebase_core` và `cloud_firestore`).
3.  Duyệt qua từng Topic trong JSON:
    -   Tạo/Ghi đè document trong collection `topics`.
    -   Duyệt qua danh sách `vocabularies` của Topic đó.
    -   Tạo/Ghi đè document trong subcollection `topics/{topicId}/vocabularies`.
4.  In ra log tiến độ và kết quả.

## Cách chạy
Sử dụng lệnh `flutter run` với target file là script này (hoặc chạy như một ứng dụng console nếu cấu hình phù hợp, tuy nhiên trong môi trường Flutter, chạy qua `flutter run` trên máy ảo/thiết bị là dễ nhất để tận dụng `firebase_core` đã setup).

**Lưu ý:** Để chạy script độc lập (Dart CLI), cần setup `firebase_admin` hoặc service account, khá phức tạp.
**Giải pháp đơn giản:** Tạo một nút bấm "Import Data" tạm thời trong màn hình Settings hoặc một màn hình Admin ẩn của App để gọi hàm import này. Hoặc viết script dạng `test` để chạy trên máy tính.

**Quyết định:** Viết thành một **Service** trong App (`DataImportService`), và gọi nó từ một nút bấm ẩn trong `ProfileScreen` (hoặc Setting) để tận dụng kết nối Firebase có sẵn của App.
