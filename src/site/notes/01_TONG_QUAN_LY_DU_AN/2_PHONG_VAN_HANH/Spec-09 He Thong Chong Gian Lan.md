---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/2-phong-van-hanh/spec-09-he-thong-chong-gian-lan/","title":"HỆ THỐNG CHỐNG GIAN LẬN QUÉT MÁ (ANTI-FRAUD)","dg-note-properties":{"title":"HỆ THỐNG CHỐNG GIAN LẬN QUÉT MÁ (ANTI-FRAUD)"}}
---

# ĐẶC TẢ TÍNH NĂNG
## HỆ THỐNG CHỐNG GIAN LẬN QUÉT MÃ (ANTI-FRAUD SYSTEM)
**Ứng dụng Chăm Sóc Khách Hàng — Mobile/Web/App/CMS**

**Tên tính năng:** Hệ thống Kiểm soát rủi ro & Chống gian lận (Anti-Fraud)
**Mã tính năng:** FEAT-RISK-001
**Phiên bản tài liệu:** v1.0
**Ngày tạo:** 22/04/2026
**Người viết:** Lập trình viên AI / Data Analyst
**Đội nhận tài liệu:** Dev Team, QC Team
**Trạng thái:** Draft

---

## 1. Tổng Quan
### 1.1 Mô tả tính năng
Tính năng này xây dựng một hệ thống phòng thủ nhiều lớp nhằm ngăn chặn các hành vi gian lận điểm thưởng trong quá trình người dùng quét mã Serial Number (SN). Thông qua việc sử dụng công nghệ MLKit trên nền tảng di động, thuật toán nhận diện hành vi quét trên server và quy tắc đối soát hàng hóa trực tuyến, hệ thống sẽ tự động phát hiện, cảnh báo và chặn lại các cá nhân/tổ chức cày điểm ảo. 

### 1.2 Mục tiêu (Goals)
- Chặn đứng hành vi chụp ảnh mã vạch lại từ màn hình máy tính/thiết bị khác (chụp lén mã từ kho) thông qua AI.
- Giải quyết triệt để vấn đề đoán mã/tạo mã giả liên tiếp nhằm cày điểm trục lợi quỹ quà tặng.
- Kiểm soát được dòng điểm thưởng của Đại lý Level 3 để tránh việc họ "vét" kho điểm từ hàng chưa đưa ra thị trường tiêu thụ.

### 1.3 Ngoài phạm vi (Non-goals)
⚠️ Tính năng này KHÔNG bao gồm:
- Khóa hoàn toàn hoặc xóa tài khoản tự động vĩnh viễn (Việc khóa/ban account sẽ hiển thị Cờ đỏ để Admin con người quyết định).
- Hệ thống nhận diện khuôn mặt (FaceID) mỗi lần quét mã (tránh làm phiền người dùng chân chính).

## 2. Đối Tượng Người Dùng
### 2.1 Vai trò liên quan

| Vai trò | Mô tả | Quyền thực hiện |
|---------|-------|-----------------|
| Thợ / KTV (Level 1, 2) | Nhóm người dùng đi thi công | Phải vượt qua Thử thách chụp ảnh bổ sung nếu bị hệ thống nghi ngờ gian lận. |
| Đại lý VIP (Level 3) | Doanh nghiệp mua hàng | Bị áp dụng quy tắc "Điểm tạm giữ" khi quét lượng hàng cực lớn. |
| Admin / QC | Người xét duyệt | Nhận cảnh báo Notification, đối chiếu hình ảnh chụp lén, ban/phạt tài khoản rác. |

### 2.2 User Stories
- [US-02] Là hệ thống tự động, khi phát hiện 1 user quét tay mà tốc độ quá nhanh hoặc quét 1 dải mã Serial liên tiếp quá dễ đoán, tôi muốn bật cơ chế "Thử thách (Challenge)", bắt user chụp đúng cái vỏ nhựa thiết bị của 1 mã ngẫu nhiên vừa quét để chứng minh họ đang cầm vật lý thiết bị đó.
- [US-03] Là kế toán / quản trị DSS, tôi muốn số lượng điểm khổng lồ mà Level 3 quét được phải nằm ở "Ví tạm giữ", sau [X] ngày mới được vào ví "Khả dụng" để chúng tôi có đủ thời gian kiểm toán luồng hàng.

## 3. Yêu Cầu Chức Năng

| Mã | Mô tả yêu cầu | Độ ưu tiên | Ghi chú |
|----|---------------|------------|---------|
| FR-01 | **Nhận diện gian lận Màn hình ảo (MLKit):** Trong quá trình camera client quét mã QR/Barcode thành công, App ngầm (silently) chụp lại 1 frame cảnh bao quát kích thước nhỏ. Ứng dụng tích hợp cấu hình học máy (như MLKit Object/Image Detection) phân tích xem nền ảnh có vân moiré của màn hình LCD kính hay viền máy tính ảo không. | Cao | Chụp không phát âm thanh màn trập |
| FR-02 | **Gửi Flag Cảnh báo Hình ảnh:** Nếu mô hình đánh giá Tỷ lệ là Ảnh Chụp Màn Hình (Screen Captured) > 85%, app tự động nén ảnh ném bản log về CMS Cảnh báo kèm Cờ Đỏ "Quay quét qua màn hình thiết bị khác". | Cao | Báo cáo Admin review |
| FR-03 | **Thuật toán quét dải Mã liên tiếp:** Khi Server API nhận request, tính toán List Code trong ngày. Nếu phát hiện > `[N]` Serial Numbers liên tiếp nhau theo thuật toán chuỗi số học. Gửi Cảnh báo tới CMS. | Cao | Cần Admin UI cấu hình biến `[N]` |
| FR-04 | **Ngăn chặn Spam Code Lỗi:** Nếu 1 user cố tình nhập/quét liên tục các mã lỗi hoặc mã trùng lặp (Duplicate Error) đạt giới hạn Admin quy định (Vd: 10 lần liên tiếp), khoá luồng quét của user trong 2 giờ. Cảnh báo Admin. | Cao | Từ file Raw Excel (Line 69) |
| FR-05 | **Thử thách Xác thực Ngẫu nhiên (Random Challenge):** Bị kích hoạt khi dính điều kiện FR-03 (Quét chuỗi) hoặc có cờ nghi vấn FR-02. Hệ thống Block Pop-up: Yêu cầu User chụp thẳng mã Barcode của số Serial ngẫu nhiên nằm trong List họ vừa quét xong. App ép mở Camera trực tiếp để chụp. | Cao | Không vượt qua = Khoá điểm tạm |
| FR-06 | **Cơ chế Điểm Tạm Giữ cho Level 3 (Pending Points):** Mọi điểm sinh ra do Level 3 quét đều cộng vào "Điểm tạm giữ" (Pending Wallet). Người dùng nhìn thấy số nhưng không Tiêu được. Cần chờ hết thời lượng `[Z]` ngày mới chuyển sang Điểm khả dụng. Tài khoản Level 1, 2 không bị áp dụng trừ khi dính Flag. | Cao | |
| FR-07 | **Rule Khiếu nại Chống Spam:** Một mã Serial Number chỉ được phép bị thực hiện mở "Khiếu nại" duy nhất 1 lần cho 1 user để tránh làm loãng công đoạn xử lý CSKH. | Trung bình | File Raw (Line 85) |
| FR-08 | **Phạt Trừ Uy Tín (Bị quét trùng):** Điểm uy tín tự động bị trừ -1 điểm nếu chạm ngưỡng số lần vi phạm: Số Serial đang thuộc quyền của User này nhưng lại liên tục bị User khác quét đè mạo nhận. | Cao | Tuân theo thang điểm 0-4 |
| FR-09 | **Phạt Trừ Uy Tín (Quét mã ngẫu nhiên ráp nối):** Điểm uy tín tự động bị trừ -1 điểm nếu User vượt ngưỡng cố tình đi quét các Serial của người khác đã kích hoạt, mã lỗi, hoặc tự chế mã. | Cao | Liên kết FR-04 |
| FR-10 | **Phạt Trừ Uy Tín (Thua Khiếu nại):** Vượt ngưỡng thao tác mở vụ Khiếu nại rác, sau khi Admin xem xét và xử Thua kiện, hệ thống đánh cờ và lập tức trừ -1 điểm uy tín. | Cao | Bắn Popup về App |

## 4. Yêu Cầu Phi Chức Năng
### 4.1 Hiệu năng
- Quá trình chạy model MLKit phân tích ảnh diễn ra trên Client Device (Edge computing) để tránh tốn băng thông và CPU của Server. App chỉ gửi về server một cờ `True/False` kèm chuỗi byte Ảnh nếu là False. Trọng lượng file ảnh gửi đi cực nhỏ (< 150KB).

### 4.2 Khả dụng
- Màn hình Challenge (Thử thách xác minh hộp) phải có thiết kế UI thân thiện, hướng dẫn rõ khách hàng nên để ánh sáng chiếu vào đâu, tránh việc khách hàng bực bội vì nghĩ app bị lỗi.

## 5. Luồng Xử Lý (Happy Path)

### 5.1 Luồng Trigger Thử thách Xác thực

| # | Tác nhân | Hành động | Kết quả / Điều kiện |
|---|----------|-----------|---------------------|
| 1 | Thợ L2 gian lận | Cắm USB barcode scanner hoặc dùng Camera app quét một loạt 15 số Serial liên tiếp (SN: 10001 -> 10015). | Hệ thống API phân tích phát hiện chuỗi nhảy dãy liên tục (Vi phạm FR-03). |
| 2 | Hệ thống | Trả về Status HTTP 403, bung màn hình "Bảo mật tài khoản: Thử thách ngẫu nhiên". | Nội dung: "Vui lòng chụp lại hình ảnh thực tế của vỏ hộp có chứa Serial: 10006". |
| 3 | Thợ L2 gian lận | Không có cái hộp 10006 vật lý trên tay vì vừa đoán mò (Gen code). Không thể chụp máy tính (Bị chặn bởi MLKit FR-01). Sau 5 phút bỏ qua thử thách. | Toàn bộ số điểm từ 10001->10015 bị Thu hồi. Đẩy cờ Vàng cảnh cáo về CMS Admin. |

### 5.2 Luồng Điểm Tạm Giữ Level 3

| # | Tác nhân | Hành động | Kết quả / Điều kiện |
|---|----------|-----------|---------------------|
| 1 | Đại lý VIP Level 3 | Thu mua sỉ 500 cái camera và cho nhân viên lôi ra Quét tem nhưng chưa cắm lắp đặt. | App báo quét thành công 500 mã. Cộng số điểm tương ứng vào "Điểm Tạm Giữ". |
| 2 | Hệ thống | Ghi nhận thời gian quét và lưu trữ điểm tại ví tạm giữ. | Điểm nằm chết ở Ví Tạm Giữ, ko thể mang đi Đổi Quà Voucher. |
| 3 | Hệ thống | Thời gian trôi qua đủ [Z] ngày theo quy định giãn cách của Admin. | Hệ thống tự động kích hoạt tiến trình chuyển dịch khóa Điểm từ "Tạm giữ" sang "Khả dụng". |
| 4 | Đại lý | Truy cập lại vào ví điểm sau Z ngày. | Điểm khả dụng đã hiển thị, Đại lý chính thức có quyền dùng điểm để đổi quà. |

## 6. Xử Lý Lỗi & Trường Hợp Ngoại Lệ

| Tình huống lỗi | Thông báo hiển thị | Hành động tiếp theo |
|----------------|--------------------|---------------------|
| Màn hình điện thoại quá mờ/MLKit phân tích sai | "Hình ảnh thẻ không rõ ràng, hệ thống có cảnh báo nhẹ." | Vẫn cho qua nếu không dính Rule Quét nhanh, nhưng ghim cờ mờ vào ảnh ở CMS Admin tự xem. |

## 7. Tiêu Chí Chấp Nhận (Acceptance Criteria)

✅ Tính năng đạt khi:
- [AC-01] Tính năng MLKit trên điện thoại có thể bắt được tối thiểu 80% trường hợp người dùng chĩa camera vào một chiếc màn hình LCD/Máy tính (nhận diện độ chói và viền màn hình) khi scan mã. Ảnh chụp phải tự động upload khi có nghi vấn.
- [AC-02] Admin có bảng quản trị thông số để thiết lập cụ thể: `[Số lượng quét liên tiếp bị phạt]`, `[Thời lượng lock account khi quét mã lỗi trùng vòng lặp]`.
- [AC-03] Thử Thách Ngẫu Nhiên: Nếu App popup bảo "Nộp ảnh SN 12345", người dùng chỉ được dùng Native Camera chụp. Hình chụp đẩy lên Admin Panel và trạng thái chuỗi điểm đó hiển thị `[Đang chờ soát sét]`.
- [AC-04] Bảng hiển thị giao diện ví của Level 3 phân tách rõ 2 số dư: "Số dư Khả dụng" và "Điểm Đang Tạm Giữ". Chỉ số khả dụng mới lọt vào logic thanh toán Giỏ quà. Tự động dịch chuyển điểm sau [Z] ngày theo cài đặt của CMS.
- [AC-05] Xử lý nghiệp vụ từ file Excel: Nếu 1 mã Code đã từng ở trạng thái Đang Khiếu nại hoặc Đã xử lý khiếu nại trước đó, chặn mọi màn hình Popup khiếu nại lần 2 từ bất kỳ user nào để tránh spam báo cáo.
- [AC-06] Kiểm thử trừ Uy Tín: Khi đạt ngưỡng vi phạm (Bị quét đè mã / Thua khiếu nại), hệ thống tự động trừ đúng 1 điểm Uy tín, đồng bộ thẳng về Spec-01. Bắn hiển thị Popup cảnh báo trên điện thoại người vi phạm.

## 8. Phụ Thuộc & Rủi Ro
### 8.1 Phụ thuộc
- Phụ thuộc chất lượng Camera của những máy điện thoại giá rất rẻ (Android cỏ). Nếu camera mờ sương, MLKit không thể detect được mảng moiré màn hình LCD.

### 8.2 Rủi ro
- Việc bắt máy điện thoại phải "chụp ngầm 1 bức ảnh và chạy mô hình MLKit Local" ở mỗi lần ấn nút Scan có thể gây nóng máy và tiêu hao pin thợ nhanh. 
=> **Giải pháp:** Có thể set rule tỷ lệ chạy MLKit Random 20% mỗi lần quét, hoặc chỉ bật MLKit ngầm nếu trước đó dính cảnh báo Quét Quá Nhanh (Threshold dựa trên Time).

## 9. Lịch Sử Thay Đổi

| Phiên bản | Ngày | Người thực hiện | Nội dung thay đổi |
|-----------|------|-----------------|-------------------|
| v1.0 | 22/04/2026 | Lập trình viên AI | Tạo đặc tả Anti-Fraud (MLKit detect giả, Challenge Capture, Check Online Status, Pending Points). |
