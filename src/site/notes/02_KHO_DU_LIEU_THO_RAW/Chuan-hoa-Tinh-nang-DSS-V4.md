---
{"dg-publish":true,"permalink":"/02-kho-du-lieu-tho-raw/chuan-hoa-tinh-nang-dss-v4/","title":"TỔNG HỢP VÀ CHUẨN HÓA YÊU CẦU NÂNG CẤP DSS CUB V4","dg-note-properties":{"title":"TỔNG HỢP VÀ CHUẨN HÓA YÊU CẦU NÂNG CẤP DSS CUB V4"}}
---

# BẢNG TỔNG HỢP VÀ CHUẨN HÓA YÊU CẦU NÂNG CẤP DSS V4 (2026)
*(Được tổng hợp và biên soạn lại từ file Excel Ghi chú của Quản trị viên)*

Tài liệu này đã sắp xếp lại các hạng mục nâng cấp theo **nhóm tính năng (Module)** và sử dụng từ ngữ chuẩn hóa để Team Dev / Product có thể đọc hiểu dễ dàng nhất. Các tính năng lớn lõi (Core Features) đã được bóc tách và loại bỏ trùng lặp để dẫn hướng tới các tài liệu Đặc Tả Chi tiết.

---

## 1. QUẢN LÝ TÀI KHOẢN & XÁC THỰC NGƯỜI DÙNG (KYC)
> 🔗 **Tài liệu đặc tả liên kết:** [[01_TONG_QUAN_LY_DU_AN/2_PHONG_VAN_HANH/Spec-01 Verification Levels\|Spec-01 Verification Levels]]

**1.1 Đăng ký & Bảo mật:**
- **Đăng nhập Sinh trắc học (Biometrics):** Hỗ trợ FaceID / Vân tay để đăng nhập nhanh.
- **Xác thực Email:** Bổ sung bước xác thực qua địa chỉ email.
- **Cập nhật dữ liệu hành chính:** Cập nhật lại danh sách Tỉnh/Thành/Phường/Xã theo chuẩn mới nhất của Nhà nước.
*(Toàn bộ các nội dung về yêu cầu tên thật, upload giấy tờ và duyệt hồ sơ Level 2, Level 3 đã được hệ thống hóa và gom hoàn toàn vào tài liệu Spec-01)*.

**1.2 Tính năng Xác thực:**
- Khóa tính năng (bật Popup cảnh báo chuyển hướng tới trang KYC) và Cấu hình bảng ngưỡng thiết lập Điểm đã được chuẩn hóa tại Spec-01.

**1.3 Quản lý từ phía Admin:**
- **Ghi chú vĩnh viễn:** Admin có thể thêm Log (ghi chú) vào tài khoản (dạng danh sách thời gian). Các ghi chú này sẽ lưu vết vĩnh viễn, kể cả khi User đó khóa và mở lại tài khoản.

---

## 2. HỆ TRUNG TÂM THÔNG BÁO (NOTIFICATION)
**2.1 Trải nghiệm người dùng:**
- **Nút "Đã đọc tất cả" (Mark all as read):** Thêm tiện ích dọn sạch số Noti chưa đọc bằng 1 chạm.
- **Phân loại Tab Thông báo:** Tách Thông báo thành các nhóm (Tabs): *Tất cả*, *Biến động Điểm*, *Đơn hàng*, *Tin tức*, *Hệ thống*.
- **Thông báo đa liên kết (Deep-link Noti):** Khi nhấn vào thông báo, hệ thống điều hướng thẳng đến 1 bài viết, 1 web bên ngoài hoặc trực tiếp mở module game.

**2.2 Nội dung tự động (Auto-trigger):**
- Push thông báo khi có thay đổi trạng thái Duyệt Tài Khoản, Trạng thái Luân chuyển đơn hàng vận chuyển.
- Khi bắn Noti biến động Điểm, BẮT BUỘC phải in kèm Text **"Số điểm hiện tại"** để khách hàng theo dõi. *(Đồng bộ in thêm cột "Số điểm hiện tại" vào phần Lịch sử thay đổi điểm).*

---

## 3. QUẢN LÝ QUÉT MÃ (SCANNING) & ĐIỂM SỐ
**3.1 Quy trình quét mã:**
- Đưa tính năng **"Check Bảo hành ngẫu nhiên"** hiển thị nổi lên để thực hiện trước bước quét nhập Serial Number (SN).
- **Thời hạn vòng đời SN:** Admin được phép cấu hình chặn (VD: Sản phẩm xuất kho quá 3 năm thì khóa quét).
- **Kích hoạt tài khoản bằng mã:** Ràng buộc bắt quét thành công tối thiểu `[1]` mã để mở Active toàn bộ hệ thống.
- **Tra cứu Serial (CMS):** Tra cứu nhanh vòng đời 1 số SN: *Đại lý xuất -> Lịch sử user quét -> Đã bảo hành -> Khởi tạo khiếu nại.*
- Quy tắc thiết lập hạn mức tài khoản mới hạn chế đổi quà to.

**3.2 Quản trị rủi ro & Gian lận quét mã (Anti-Fraud):**
> 🔗 **Tài liệu đặc tả liên kết:** [[01_TONG_QUAN_LY_DU_AN/2_PHONG_VAN_HANH/Spec-09 He Thong Chong Gian Lan\|Spec-09 He Thong Chong Gian Lan]]

*(Luồng cảnh báo người dùng quét các dải số SN liên tiếp, chống spam quét mã lỗi liên tục, và cơ chế chuyển đổi thành Điểm tạm giữ của VIP Level 3 đã được dời thẳng vào tài liệu phân tích kỹ thuật chống gian lận Spec-09).*

---

## 4. QUẢN LÝ KHIẾU NẠI (TICHKETS)
- Bố cục tìm kiếm: Cải tiến tách biệt thành 2 bộ lọc *Bên khởi kiện* vs *Bên bị kiện*. 
- **Preview ảnh nhanh:** Gắn Thumbnail hình chụp khiếu nại nhỏ ra giao diện lưới ở CMS để Admin nhìn dễ hiểu.
*(Luật cấm 1 SN khiếu nại nhiều lần đã được dời vào quy tắc hệ thống của Spec-09).*

---

## 5. ĐƠN HÀNG & LOGISTICS
- **Giao diện Lọc ngày:** Áp dụng bộ Date picker nhanh theo định dạng app vận chuyển.
- **Chia Tab Đơn Hàng:** Phân rã thành nhóm Tab (Chờ lấy, Đang giao, Thành công...).
- **Luồng Hủy đơn Admin:** Khi CMS hủy 1 đơn, BẮT BUỘC hiện Popup để nhập "Lý do hủy" và bắn Noti lý do đó về App khách.

---

## 6. SỰ KIỆN COIN & MINI GAMES
- **Tùy biến nhúng (Theme Customization):** Trò điểm danh hằng ngày cho phép Upload thay icon quà tặng và thay đổi linh hoạt hệ dải màu nền UI theo dịp lễ (Tết, Giáng sinh...).
- **Áp lực thời gian (Time-Attack):** Câu hỏi trắc nghiệm phải có tính năng đếm ngược. Admin cài đặt được Rule thời gian trên số lượng câu (Vd: 30 câu trong 90 phút).
- **Chỉ số năng lực & Bảng xếp hạng:** CMS thống kê tổng thời gian User tham gia thi đấu / làm đề. Mở thêm Tab Bảng Cảm Ứng (Leaderboard) sắp xếp vị trí High score. Xét điều kiện ưu tiên hoàn thành trong kỳ thời gian ngắn nhất khi nổ đồng hạng (bằng điểm).

---

## 7. TIỆN ÍCH CHO THỢ LẮP ĐẶT & CỘNG ĐỒNG
> 🔗 **Tài liệu đặc tả liên kết:** 
> - [[01_TONG_QUAN_LY_DU_AN/2_PHONG_VAN_HANH/Spec-02 Social Community\|Spec-02 Social Community]]
> - [[01_TONG_QUAN_LY_DU_AN/2_PHONG_VAN_HANH/Spec-08 Ban Do Anh Em Quanh Day\|Spec-08 Ban Do Anh Em Quanh Day]]

*(Toàn bộ các ý tưởng liên quan tới mạng xã hội chia sẻ Video kỹ năng nghề, trò chuyện bình luận hai chiều, cũng như bản đồ hiển thị thợ lân cận đã được lập Đặc Tả riêng ở Spec-02 và Spec-08).*

---

## 8. SỬA LỖI BUG NHANH (HOT FIXES)
- Quét khiếu nại thành công sau đó mang mã đi quét lại báo lỗi "Không tồn tại" thay vì status chuẩn là "Đã quét thành công".
- Khớp lại Item Product giữa list CMS và Product Mobile (Sai lệch vd với quà "miếng dán cảnh báo").
- Hủy khiếu nại mà không có tội vẫn bị App trừ Điểm Uy Tín cần kiểm tra.
- Đơn hàng đẩy sang Viettel Post vận chuyển mà lỡ dính Fail/Hủy -> Tự động bắn luồng cập nhật đồng bộ Cập nhật Status về lại kho CMS báo hủy.

---

## 9. DASHBOARD TRUNG TÂM CMS
- **Chuông quản trị Server:** Admin có cái chuông riêng phân chia Tab: *Cảnh báo Spam*, *Hệ thống nhận diện AI*, *Cập nhật phiên bản*.
- **Report Robot Live Feed:** Bảng Panel góc chạy Log nhảy text báo hiệu AI đang hoạt động ngầm. VD: *"Robot Đã xử lý 33 mã lỗi... Robot Vừa phát hiện 19 Tân thủ đăng ký..."*.
- **Bulk Action (Thao tác nhóm):** Mọi Danh sách trên CMS (Lịch sử điểm, Seri, Câu hỏi...) luôn phải thiết kế một checkbox ở tiêu đề để tick nháy Check-All và cho ra nút Menu 🔽 Xóa/Copy hàng loạt.
- Backend tự động Filter cấm lưu record khởi tạo 2 sản phẩm trùng Tên. Edit sản phẩm được phép tháo nhấc chuyển Danh Mục.

---
`*Tài tài liệu này đã được review và mapping chéo (cross-referenced) với các Đặc Tả Nhánh nhằm đảm bảo tính liền mạch trong khâu lập trình V4 năm 2026.`
