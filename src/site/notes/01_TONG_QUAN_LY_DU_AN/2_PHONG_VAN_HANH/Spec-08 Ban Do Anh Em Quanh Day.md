---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/2-phong-van-hanh/spec-08-ban-do-anh-em-quanh-day/","title":"BẢN ĐỒ ANH EM QUANH ĐÂY","dg-note-properties":{"title":"BẢN ĐỒ ANH EM QUANH ĐÂY"}}
---

# ĐẶC TẢ TÍNH NĂNG
## BẢN ĐỒ "ANH EM QUANH ĐÂY"
**Ứng dụng Chăm Sóc Khách Hàng — Mobile/Web/App/CMS**

**Tên tính năng:** Bản đồ "Anh em quanh đây"
**Mã tính năng:** FEAT-MAP-001
**Phiên bản tài liệu:** v1.1
**Ngày tạo:** 21/04/2026
**Người viết:** Lập trình viên AI / Theo yêu cầu anh em DSS
**Đội nhận tài liệu:** Dev Team
**Trạng thái:** Draft

---

## 1. Tổng Quan
### 1.1 Mô tả tính năng
Tính năng này cung cấp một bản đồ trực quan trong ứng dụng DSS Club để người dùng xem được mạng lưới thợ và cửa hàng xung quanh mình. Khi truy cập, người dùng (Level 1, 2) có thể nhận biết đâu là thợ đang hoạt động cùng ngành và đâu là các Cửa hàng/Đại lý kinh doanh camera (Level 3). 
Mặc định, ngay khi tạo tài khoản và đồng ý chia sẻ tính năng, vị trí của người dùng sẽ được ghi nhận và hiển thị dựa trên địa chỉ đăng ký. Khi truy cập vào màn hình bản đồ thực tế thi công, người dùng có thể bấm nút chức năng định vị lại (GPS thời gian thực) để hệ thống hiển thị chính xác vị trí đang đứng và tìm kiếm "anh em quanh đây" chuẩn xác hơn.

### 1.2 Mục tiêu (Goals)
- Giúp người thợ (Level 1, 2) dễ dàng tìm kiếm các Đại lý (Level 3) nằm trong khu vực xung quanh để mua sắm vật tư.
- Tạo cảm giác cộng đồng đông đảo, vững mạnh khi quan sát trên bản đồ thấy nhiều anh em thợ quanh lưu vực.
- Cân bằng tính tiện dụng: Xóa bỏ rào cản "mở app mới báo vị trí". App sẽ ghi nhận tự động ban đầu bằng text địa chỉ, và chỉ update sang GPS thực tế khi user chủ động nhấn nút.

### 1.3 Ngoài phạm vi (Non-goals)
⚠️ Tính năng này KHÔNG bao gồm:
- Không ép buộc tracking lộ trình di chuyển liên tục chạy ngầm trong điện thoại.
- Không bao gồm hệ thống chat bộ nội tuyến trực tiếp trên bản đồ (nếu cần liên hệ Đại lý LV3, hệ thống sẽ đẩy thẳng qua gọi số Điện Thoại/Zalo).

## 2. Đối Tượng Người Dùng
### 2.1 Vai trò liên quan

| Vai trò              | Mô tả                                    | Quyền thực hiện                                                                                  |
| -------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------ |
| Thợ/KTV (Level 1, 2) | Khách hàng cuối, thợ thi công hoặc tự do | Xem được các thợ/cửa hàng xung quanh. Nhấn nút cập nhật vị trí GPS thời gian thực.               |
| Đại lý VIP (Level 3) | Cửa hàng kinh doanh thiết bị Camera      | Được ghim nổi bật lớn trên bản đồ với biểu tượng Cửa hàng (Store) kèm thông tin liên hệ Hotline. |
| Admin (CMS)          | Quản trị dự án từ phía DSS               | Xem mật độ phân bổ người dùng trên heatmap, hỗ trợ team Marketing.                               |

### 2.2 User Stories
- [US-01] Là thợ kỹ thuật, tôi muốn mở tính năng "Anh em quanh đây" để xem có những thợ nào (chấm xanh) đang hoạt động quanh khu vực tôi đứng.
- [US-02] Là thợ kỹ thuật, tôi muốn nhìn trên bản đồ để phát hiện các cửa hàng/đại lý Level 3 (ngôi nhà/ngôi sao) ở gần nhất để phi xe tới nhập vật tư.
- [US-03] Là thợ mới tạo tài khoản, tôi muốn vị trí mặc định của mình tự động xuất hiện trên "Bản đồ anh em" căn cứ theo Địa chỉ tôi đã gõ vào form đăng ký (để không cần bật GPS).
- [US-04] Dù nhà ở Quận 12 nhưng tôi đang đi công trình ở Quận 1, tôi muốn nhấn "Định vị lại" trên góc bản đồ để GPS kéo toạ độ ảo của tôi về đúng vị trí thực tế, xem xung quanh có đại lý nào dễ mua hàng.

## 3. Yêu Cầu Chức Năng

| Mã | Mô tả yêu cầu | Độ ưu tiên | Ghi chú |
|----|---------------|------------|---------|
| FR-01 | **Ghi nhận Toạ độ Mặc định (Geocoding):** Sau user hoàn tất tạo tài khoản và check ô "Đồng ý hiển thị Anh em quanh đây", Backend gọi Google Geocode chuyển text "Địa chỉ / Phường" của tài khoản thành toạ độ (Lat/Long) để ghim sẵn trên bản đồ. | Cao | Database luôn có lượng Marker đầy đủ. |
| FR-02 | **Nút định vị GPS thực tế:** Tại màn hình Map, hiển thị nút Icon "Tâm ngắm". Bấm nút, App mới popup xin quyền truy cập Location (nếu chưa có). Lấy xong, cập nhật marker về đúng vị trí hiện tại của thiết bị và lưu cập nhật vị trí mới trên DB. | Cao | Cơ chế xin quyền "1 lần khi bấm". |
| FR-03 | **Hiển thị Level 1, 2 (Thợ):** Icon hiển thị dạng điểm / Chấm nhỏ chuẩn. Nhấp vào popup giới thiệu Tên Nickname + Cấp độ (Level 1/2). | Trung bình | Yêu cầu Ẩn thông tin SDT để giữ Privacy. |
| FR-04 | **Hiển thị Level 3 (Cửa hàng):** Icon có thiết kế chuyên biệt (Cửa hàng, Ngôi nhà to). Nhấp vào popup hiển thị: Tên Đại lý, Ngành hàng Camera/An ninh, Nút 'Gọi điện/Chat Zalo' (Nhúng action link). | Cao | Hiển thị nổi bật so với các chấm Level 1, 2. |
| FR-05 | **Bật/Tắt Riêng tư (Privacy Option):** User có công tắc tắt hiển thị trong trang Tài Khoản, để xoá điểm ghim của mình ra khỏi bản đồ của người khác. | Cao | |

## 4. Yêu Cầu Phi Chức Năng
### 4.1 Hiệu năng
- Với logic FR-01, trong Phase 1 bản đồ sẽ có ngay hàng nghìn điểm marker rải rác. Đội ngũ Front-end App NÊN áp dụng thư viện Marker Clustering (Tụ nhóm lại số lượng +20, +50...) khi người dùng zoom-out Bản đồ để máy điện thoại không bị lag (tụt FPS).
- Nền tảng Map: Cân nhắc sử dụng Goong API hoặc Mapbox thay vì Google Maps nếu muốn tiết kiệm chi phí dịch vụ.

### 4.2 Bảo mật
- **Bảo mật vị trí:** Khi sử dụng Geocode để chuyển địa chỉ nhà của tài khoản (FR-01), thuật toán trên server nên tự động trượt (offset) một khoảnh dời ngẫu nhiên 50-100m. Để bảo vệ an toàn cho nhà riêng của Thợ KTV không bị ghim chuẩn đến từng centimet trên bản đồ công khai.

## 5. Luồng Xử Lý (Happy Path)

### 5.1 Luồng Tìm kiếm Anh em và Cửa hàng

| # | Tác nhân | Hành động | Kết quả / Điều kiện |
|---|----------|-----------|---------------------|
| 1 | Thợ L1 | Điền form đăng ký account, Địa chỉ ghi: "Thủ Đức, HCM". Tick vào [x] Bật hiển thị bản đồ. | Backend quét địa chỉ "Thủ Đức" thành Marker tại toạ độ Thủ Đức lưu DB. |
| 2 | Thợ L1 | Vài hôm sau, đi làm thầu ở "Tân Bình". Mở tính năng "Bản đồ anh em". | View Map hiện ra toạ độ trung tâm là "Thủ Đức" kèm anh em khu vực đó. |
| 3 | Thợ L1 | Bấm vào nút "Định vị lại" (Icon Target). | App kích hoạt Modal xin quyền Định vị. |
| 4 | Thợ L1 | Nhấn "Cho phép một lần" | Hệ thống gọi GPS, lấy vị trí Tân Bình, API gửi lưu lên server cập nhật vị trí. Camera của Map cũng trượt trỏ về toạ độ "Tân Bình" của User. |
| 5 | Thợ L1 | Zoom in trên Map thấy xung quanh có 1 số chấm nhỏ (thợ khác) và 1 chấm bự (Đại lý Level 3). | |
| 6 | Thợ L1 | Nhấp vào Đại lý Level 3, bung popup "Cửa hàng CCTV Phúc Long". Bấm nút Gọi Ngay. | Mở Native Phone Dialer để gọi xin hàng vật tư. |

## 6. Xử Lý Lỗi & Trường Hợp Ngoại Lệ

| Tình huống lỗi                                        | Thông báo hiển thị                                              | Hành động tiếp theo                                                         |
| ----------------------------------------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Địa chỉ đăng ký quá mơ hồ không map ra được Toạ độ    | Không hiển thị Popup lỗi cản trở luồng user.                    | Hệ thống ghim tự động User về vùng toạ độ trọng điểm của Tỉnh Thành phố đó. |
| Nhấn Định vị GPS nhưng tắt service trong Hệ thống Máy | "Vui lòng bật Định vị toàn cầu (GPS) của thiết bị để tiếp tục!" | Nhấn nút điều hướng người dùng văng thẳng vô App Settings của iOS/Android.  |

## 7. Tiêu Chí Chấp Nhận (Acceptance Criteria)

✅ Tính năng đạt khi:
- [AC-01] User vừa đồng ý chia sẻ định vị từ lúc Sign up tài khoản, ngay lập tức Marker của User đó xuất hiện thành công trên màn hình app của mọi User khác theo căn cứ là "Địa chỉ đăng ký" (mà không cần user đó phải thực sự mở màn hình bản đồ lấy permission).
- [AC-02] Dấu ghim Marker của Level 3 (Cửa hàng) luôn phải có hình khối, màu sắc khác biệt hoàn toàn (đè chồng độ ưu tiên hiển thị cao hơn) so với đám điểm ghim của các thợ Level 1, 2.
- [AC-03] Trên thiết bị Thợ L2, nhấp vào cái Chấm của 1 Thợ L2 khác bên cạnh CHỈ thấy "Tên" và "Cấp độ", che giấu số điện thoại cá nhân.
- [AC-04] Khi zoom out ra xem toàn thành phố, các Marker điểm Level 1/2 đứng gần nhau tự động sáp nhập thành hình bong bóng báo số lượng tổng (Vd: +15, +30) để không làm đơ thiết bị di động (Clustering effect).

## 8. Lịch Sử Thay Đổi

| Phiên bản | Ngày | Người thực hiện | Nội dung thay đổi |
|-----------|------|-----------------|-------------------|
| v1.0 | 21/04/2026 | Lập trình viên AI | Tạo đặc tả bản đồ với SOS Cứu hộ và Offline Check-in. |
| v1.1 | 21/04/2026 | Lập trình viên AI | Cập nhật lại phạm vi đơn giản hóa: Hiển thị Thợ vs Cửa hàng, áp dụng cơ chế tự động ghi nhận theo Địa chỉ (Geocode) và định vị lại tự chọn. |
