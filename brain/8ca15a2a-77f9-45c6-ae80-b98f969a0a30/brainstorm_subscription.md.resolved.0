## 🧠 Brainstorm: Xây dựng Hệ Thống Đăng Ký (Subscription) 2 Gói với RevenueCat

### Context
Mục tiêu là tích hợp hệ thống Subscription bằng **RevenueCat** cho ứng dụng học tiếng Anh dành cho đối tượng trẻ nhỏ, phát hành trên quy mô toàn cầu (sau khi tích hợp đa ngôn ngữ). 

Bạn đang đề xuất 2 Gói:
1. **Gói Pro** ($2/tháng, $10/năm): Vô cực năng lượng, Không quảng cáo.
2. **Gói Pro Max** ($3/tháng, $20/năm): Quyền lợi của Pro + Mở khóa toàn bộ Topic không cần học tuần tự + X2 số Sao khi học.
Điểm kích hoạt (Entry-point) nạp tiền nằm trong màn hình **Hồ Sơ (Profile)**.

**Đánh giá mức giá $2 - $3/tháng và $10 - $20/năm cho thị trường Toàn Cầu:**
- Mức giá này (giao động 50k - 75k VNĐ/tháng) là một **mức giá rất cạnh tranh và hợp lý** đối với các thị trường đang phát triển (Đông Nam Á, Nam Mỹ), ngang với một ly cà phê cá nhân nhưng mang lại giá trị học tập cao cho phụ huynh mua cho con cái. 
- Tại các quốc gia Tier 1 (Mỹ, Châu Âu, Úc), mức giá này siêu rẻ, dễ dàng tạo ra hành vi mua bốc đồng (impulse buy) của phụ huynh. Tuy nhiên, nếu rẻ quá có thể khiến họ đánh giá thấp chất lượng (bạn có thể ứng dụng PPP - sức mua tương đương - để điều chỉnh giá).

Dưới đây là 3 giải pháp (Options) để cấu trúc tính năng Subscription & Paywall này:

---

### Option A: Phân tầng Gói Tiêu chuẩn (Standard Tiering) bằng RevenueCat Offerings
Giữ nguyên ý tưởng hiện tại của bạn: Tạo 2 Offerings độc lập trong RevenueCat: `pro_offering` và `pro_max_offering` (Hoặc 1 Offering có 2 Packages là Pro và Pro Max). Khi ấn vào "Nâng cấp" ở Hồ Sơ, một Paywall xổ lên chứa cả loại Month và Year của cả 2 gói. Phụ huynh đọc mô tả (checklist) và tự quyết định.

✅ **Pros:**
- Khách hàng có quyền lựa chọn linh hoạt theo nhu cầu (chỉ muốn con hết quảng cáo vs muốn con tha hồ cày sao). 
- Doanh thu hàng năm tối đa ($20/học sinh).

❌ **Cons:**
- Nhiều tuỳ chọn (4 nút mua: Pro tháng/năm, Pro Max tháng/năm) có thể dẫn tới sự "Mệt mỏi phân định" (Paradox of Choice), làm giảm tỉ lệ chốt đơn của người mua vội.
- Lập trình phân tách logic khá tẻ nhạt. VD: Gói Pro vẫn bị khóa bài học, Gói Pro Max thì thả xích.

📊 **Effort:** Trung Bình 

---

### Option B: Khóa Tính Năng & Nâng Cấp Ngữ Cảnh (Contextual Upsell) thay vì chỉ bán trong "Hồ Sơ"
Bố trí Paywall không chỉ giới hạn trong bảng điều khiển "Hồ Sơ". Mỗi một Pain Point (Điểm thèm muốn) của người dùng sẽ kích hoạt quảng cáo gói phù hợp: 
1. **Ở Màn hình Bài Học**: Khi bài học đang khoá hình ổ khoá, phụ huynh click vào -> Hiện Paywall Gói **Pro Max**.
2. **Lúc hết Năng Lượng**: Popup Hết Năng Lượng có nút mua -> Hiện Paywall Gói **Pro** hoặc **Pro Max**.

✅ **Pros:**
- Tỉ lệ mua (Conversion Rate) cao gấp 3-4 lần do đánh trúng vào "Cơn khát" hiện tại của người chơi (con đang hăng hái học nhưng bài tới bị khóa/hết sức).
- Tận dụng tối đa cảm xúc tại thời điểm xảy ra hạn chế.

❌ **Cons:**
- Cần lập trình UI cho các màn hình khác ngoài "Hồ Sơ".
- Phải thiết kế Paywall (Màn hình Mua) sao cho bắt mắt nhưng an toàn với trẻ nhỏ (Chính sách Cổng Thanh Toán Của Phụ Huynh).

📊 **Effort:** Trung Bình - Cao (Tốn thời gian tối ưu luồng UI/UX).

---

### Option C: Hợp Nhất Gói (The "Simplicity" Freemium)
Xóa bỏ 2 gói phức tạp, gộp chúng lại làm 1 gói **Super Maxy** duy nhất với giá **$2.99/tháng** và **$19.99/năm**. Nó bao gồm TOÀN BỘ tính năng xịn: (Vô cực năng lượng, Không quảng cáo, Mở khóa All topic, x2 Ngôi Sao).

✅ **Pros:**
- Dễ tiếp thị, giảm sốc cấu trúc giá. Phụ huynh chỉ cần trả lời câu hỏi: MUA hay KHÔNG MUA?
- Lập trình RevenueCat siêu dễ (Chỉ kiểm tra quyền `entitlements.isActive` đúng 1 biến bool duy nhất).
- Lợi nhuận trung bình trên người dùng (ARPU) đạt tối đa (ai cũng buộc mua gói cao nhất).

❌ **Cons:**
- Mất đi những người dùng "hà tiện" chỉ muốn nạp rẻ để xóa quảng cáo với giá $2.

📊 **Effort:** Rất Thấp (Code đơn giản, ít lỗi sinh ra, RevenueCat cực mượt).

---

## 💡 Recommendation

**Option B (Bán theo Ngữ Cảnh) kết hợp cùng Option C (Hợp nhất 1 gói duy nhất)** là chiến thuật tốt nhất cho game/ứng dụng trẻ nhỏ. 

**Lý do:**
1. Phụ huynh hiếm khi vào tận mục "Hồ Sơ" để tìm mua gói. Con cái họ mới là người tương tác nhiều nhất. Khi con chơi tới màn bị Khóa, ứng dụng bật Popup hiện Toán giải đố (Parental Gate) và cho Phụ huynh mua ngay lúc đó thì tỉ lệ chốt đơn rất cao. 
2. Việc chẻ thành 2 gói Pro và Pro Max thu 2 đô / 3 đô tạo ra quá nhiều code rườm rà (kiểm tra Pro thì không xem quảng cáo, kiểm tra Pro Max thì nhân đôi sao). Một app giáo dục dành cho trẻ em toàn cầu cần **1 Gói Premium Đơn Giản** dễ hiểu nhất - "$2.99 để con có môi trường trải nghiệm hoàn hảo không giới hạn". 

Bạn muốn phát triển 2 Gói theo **Option A** gốc của bạn (Chấp nhận code dài một chút), hay muốn thu gọn cấu trúc Premium lại thành 1 gói VIP **Option C** để tối ưu Conversion Rate?
