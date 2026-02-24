# Task: Migrate Shop Items to Firebase

- [x] Update `ShopItemModel`
  - [x] Add `dx`, `dy`, `scale` fields.
  - [x] Add `isOnline` field (default `false`).
  - [x] Update `fromJson` and `toJson`.
- [x] Prepare Firestore Data
  - [x] Create a JSON array of current `shop_data.dart` items (hats, glasses, neck) with their respective offsets.
  - [x] Added button in the app (Profile screen) to automate uploading `shop_items_data.json` to Firestore.
- [x] Update `ShopData`
  - [x] Remove hardcoded hats, glasses, and neck items from `shop_data.dart` (except for the `remove_` items and `energy` items).
- [x] Implement Fetching and Caching
  - [x] Update `ShopController` (or create a dedicated `ShopService`) to fetch from Firestore `shop_items`.
  - [x] Implement local caching (e.g., using `SharedPreferences` or `hive`) to store fetched items.
  - [x] Merge fetched online items with local static items (`energy`, `remove_` items) in `itemsByType`.
