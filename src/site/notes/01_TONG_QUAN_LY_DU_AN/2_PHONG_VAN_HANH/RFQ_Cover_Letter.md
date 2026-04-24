---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/2-phong-van-hanh/rfq-cover-letter/","title":"RFQ — Thư Mời Báo Giá Dự Án DSS CLUB","dg-note-properties":{"title":"RFQ — Thư Mời Báo Giá Dự Án DSS CLUB"}}
---

# THƯ MỜI BÁO GIÁ (REQUEST FOR QUOTATION)
## Dự án: Hệ sinh thái Chăm Sóc Khách Hàng DSS CLUB

**Mã RFQ:** RFQ-DSSCLUB-2026-001
**Ngày phát hành:** 23/04/2026
**Hạn nộp báo giá:** 15/05/2026 (23:59 giờ VN)
**Phương thức nộp:** Email về `aihomevietnam@gmail.com` với tiêu đề `[RFQ-DSSCLUB] — Tên Công Ty`
**Trạng thái:** Chính thức phát hành

---

## 1. Giới Thiệu Bên Mời Thầu

**DSS CLUB** là cộng đồng các kỹ thuật viên (KTV), thợ thi công và đại lý trong ngành camera an ninh / thiết bị DSS tại Việt Nam. DSS CLUB đang trong giai đoạn xây dựng nền tảng số để:

- Quản lý cộng đồng thành viên phân theo cấp độ (Level 1 – Thợ cơ bản, Level 2 – Thợ tích xanh, Level 3 – Đại lý VIP tích vàng).
- Số hóa điểm thưởng (Loyalty Point) từ hành vi quét mã Serial Number sản phẩm, đổi quà, mini-game.
- Tổ chức các sự kiện offline (hội thảo, đào tạo, tri ân) với check-in thông minh.
- Tạo sân chơi nội dung (feed cộng đồng, bản đồ anh em quanh đây) để gắn kết thành viên.

Hệ thống đang có sẵn một **App CSKH (mobile)** và **website loyalty** ở giai đoạn khởi đầu. Dự án này là bước mở rộng lớn tiếp theo — chuyển từ công cụ đơn lẻ sang một **hệ sinh thái hoàn chỉnh** với 5 nhóm tính năng chính.

---

## 2. Mục Tiêu Của Dự Án

Bên mời thầu mong muốn lựa chọn **một (hoặc nhiều) nhà thầu** có năng lực để triển khai hệ thống theo 5 đặc tả tính năng đính kèm. Mục tiêu chiến lược:

1. **Đóng gói trải nghiệm thành viên** — để một người thợ từ lúc bước chân vào cộng đồng đến lúc trở thành Đại lý VIP đều có hành trình số rõ ràng, công bằng, minh bạch.
2. **Chống gian lận triệt để** — vì hệ thống có dính tới tiền thật (quà tặng, voucher), phải có cơ chế phòng thủ nhiều lớp.
3. **Offline-first cho sự kiện** — các sự kiện DSS có thể tổ chức ở nơi mạng yếu, hệ thống check-in phải chạy được kể cả khi mất Internet.
4. **Tích hợp sâu với App CSKH hiện có** — không dựng thêm app riêng, tận dụng tối đa kênh App đã có (WebView + SSO).
5. **Bảo mật dữ liệu cá nhân** — tuân thủ Nghị định 13/2023/NĐ-CP về bảo vệ dữ liệu cá nhân.

---

## 3. Phạm Vi Công Việc (Scope of Work)

Phạm vi chia thành **5 Hạng mục tính năng** (tương ứng 5 tài liệu Spec đính kèm). Nhà thầu có thể báo giá **toàn bộ** hoặc **chọn từng hạng mục** mà mình có thế mạnh. Trong trường hợp chỉ báo giá một phần, vui lòng ghi rõ.

### 3.1 Bảng Tóm Tắt Các Hạng Mục

| STT | Mã Tính Năng | Tên | Tài Liệu Đính Kèm | Độ Ưu Tiên |
|-----|--------------|-----|-------------------|------------|
| 1 | FEAT-VERIF-LVL | **Hệ thống Cấp Độ Xác Thực** (Level 1/2/3 + KYC + Điểm Uy Tín) | `Spec-01 Verification Levels.md` | ⭐⭐⭐ Rất cao |
| 2 | FEAT-SOCIAL-GAMIFY | **Cộng Đồng Feed + Điểm Cống Hiến** | `Spec-02 Social Community.md` | ⭐⭐ Cao |
| 3 | FEAT-EVENT-CHECKIN | **Event Check-in Offline-first + Mini-game + Welcome Screen** | `Spec-03_v2 Event Checkin.md` | ⭐⭐⭐ Rất cao |
| 4 | FEAT-MAP-001 | **Bản Đồ "Anh Em Quanh Đây"** | `Spec-08 Ban Do Anh Em Quanh Day.md` | ⭐ Trung bình |
| 5 | FEAT-RISK-001 | **Anti-Fraud — Chống Gian Lận Quét Mã** | `Spec-09 He Thong Chong Gian Lan.md` | ⭐⭐⭐ Rất cao |

### 3.2 Tóm lược từng hạng mục

#### Hạng mục 1 — FEAT-VERIF-LVL (Spec-01)

Xây dựng hệ thống 3 cấp độ tài khoản với cơ chế xác thực (eKYC) leo cấp:
- **Level 1:** Số điện thoại + OTP. Giới hạn 100 mã/tháng, quà < 1.000đ.
- **Level 2:** CCCD + Selfie matching → tích xanh. Giới hạn 500 mã/tháng, quà < 10.000đ.
- **Level 3:** CCCD + Selfie + GPKD/MST doanh nghiệp → tích vàng. Không giới hạn.

Kèm theo: Identity Lock (khóa CCCD chống clone), Consent Flow theo NĐ 13, thang **Điểm Uy Tín -4 → 4**, cơ chế Demote (giáng cấp khi xuống 0 điểm), Cold storage dữ liệu khi người dùng yêu cầu xoá tài khoản. CMS Admin cấu hình được matrix KYC.

→ **Ghi chú quan trọng:** Đây là **trái tim của toàn hệ thống** — tất cả các hạng mục khác đều gọi API vào module này. Nhà thầu phải đảm bảo module này hoàn thành **đầu tiên** hoặc làm song song.

#### Hạng mục 2 — FEAT-SOCIAL-GAMIFY (Spec-02)

Feed cộng đồng theo kiến trúc **Web-first + WebView** trong App CSKH (SSO token):
- Cơ chế **Điểm Cống Hiến** với công thức `Total = (View × A) + (Like × B) + (Comment × C) + (Post × D)`, Admin cấu hình được hệ số.
- Chống spam: Max 500đ/bài, 200đ/ngày, Unique View 24h.
- Giới hạn media: Ảnh ≤ 5MB (tối đa 9 ảnh), Video ≤ 50MB/60 giây, tổng ≤ 100MB.
- Leaderboard Tuần / Tháng / Năm.
- Báo cáo bài viết: ngưỡng ≥ 5 user report → tự động ẩn, chờ Admin duyệt.
- Hạ tầng lưu trữ: Server nội bộ trước, đẩy lên CDN khi load time > 3 giây.

#### Hạng mục 3 — FEAT-EVENT-CHECKIN (Spec-03 v2.3)

Hệ thống check-in sự kiện **offline-first** với "local server đầu não" đặt ngay tại địa điểm tổ chức:
- Kiến trúc **Phương án A:** 4 PC (gộp PC quầy làm Welcome Screen), dự toán thiết bị ~32 triệu VND.
- QR check-in có chữ ký Ed25519/HMAC-SHA256, chống làm giả vé.
- **Identity Resolution theo SĐT** — gộp người dùng App + Zalo OA + walk-in về cùng 1 profile.
- **Mini-game** (vòng quay may mắn) với segmentation theo cấp độ + popup trúng giải toàn màn hình.
- Push notification hậu check-in (FCM/APNs + Zalo OA cho người chưa có app).
- Tích hợp vào **web nhúng (WebView)** trong App CSKH + SSO.

→ Đã có sẵn file HTML trình bày cho lãnh đạo (`Spec-03_EventCheckin_Pitch.html`) — nhà thầu có thể dùng làm context visual.

#### Hạng mục 4 — FEAT-MAP-001 (Spec-08)

Bản đồ ghim các thợ & đại lý gần nhau:
- Ghi nhận tọa độ mặc định qua **Geocoding** (từ địa chỉ đăng ký — không bắt buộc mở GPS).
- Người dùng chủ động bấm nút "Định vị lại" để cập nhật GPS thực tế.
- Icon phân cấp: Level 1/2 chấm nhỏ, Level 3 hình cửa hàng nổi bật.
- **Marker Clustering** khi zoom-out để không lag thiết bị cỏ.
- Offset ngẫu nhiên 50–100m để bảo vệ địa chỉ nhà riêng của thợ.
- Đề xuất dùng **Goong API** hoặc **Mapbox** thay Google Maps để tiết kiệm chi phí.

#### Hạng mục 5 — FEAT-RISK-001 (Spec-09)

Hệ thống chống gian lận quét mã nhiều lớp:
- **MLKit on-device** phát hiện vân moiré khi người dùng chĩa camera vào màn hình LCD (chụp lén mã từ máy tính).
- Phát hiện chuỗi SN liên tiếp (số học) → trigger Challenge ngẫu nhiên.
- **Random Challenge:** App bắt người dùng chụp hộp vật lý của 1 mã random vừa quét.
- **Pending Wallet** cho Level 3: điểm quét số lượng lớn sẽ bị tạm giữ Z ngày trước khi khả dụng.
- Khóa spam mã lỗi / mã trùng (10 lần liên tiếp → block 2 giờ).
- Gắn tự động -1 điểm Uy Tín (kết nối Spec-01) khi vi phạm đủ ngưỡng.

---

## 4. Yêu Cầu Kỹ Thuật & Kiến Trúc Tổng Thể

### 4.1 Ràng buộc kiến trúc không thương lượng

| # | Yêu cầu | Lý do |
|---|---------|-------|
| KT-01 | **Web nhúng (WebView) trong App CSKH + SSO token** | Không dựng app riêng cho từng tính năng. Tận dụng channel App đã có. |
| KT-02 | **Identity Resolution theo số điện thoại** | SĐT là khóa chính duy nhất gộp user qua mọi kênh (App, Zalo OA, walk-in, web). |
| KT-03 | **Offline-first cho Event Check-in** | Event có thể tổ chức nơi mạng yếu — local server phải tự chạy và sync sau. |
| KT-04 | **Core + Plug-in architecture** | Face ID / eKYC / Payment phải là plug-in — có thể bật/tắt theo ngân sách từng phase. |
| KT-05 | **Tuân thủ NĐ 13/2023/NĐ-CP** | Consent Flow, quyền xoá dữ liệu, cold storage. Không negotiable. |
| KT-06 | **MLKit on-device** (không server-side AI) | Tiết kiệm băng thông, CPU server. Ảnh chỉ upload khi có flag nghi vấn (<150KB). |

### 4.2 Tích hợp với hệ thống hiện có

Nhà thầu phải tích hợp với các hệ thống hiện có của DSS:

- **App CSKH** (iOS/Android) — đã có. Nhà thầu cần viết các màn hình native bridge để WebView gọi Camera / Gallery / Push.
- **Website Loyalty** — đã có. Nhà thầu cần gọi API cộng/trừ điểm qua module Loyalty có sẵn (sẽ cung cấp tài liệu API khi ký NDA).
- **Zalo OA** — DSS đã có Official Account, nhà thầu cần tích hợp ZNS template + API.
- **Push Notification** — FCM (Android) + APNs (iOS).
- **eKYC provider** — DSS chưa chốt, nhà thầu có thể đề xuất (VNPT eKYC, FPT.AI, Trusting Social, v.v.).

### 4.3 Công nghệ gợi ý (không bắt buộc)

Nhà thầu tự do đề xuất stack, nhưng cần **giải trình lý do** nếu khác gợi ý sau:

- Backend: Node.js / Go / Java Spring (ưu tiên stack có sẵn đội ngũ Việt Nam đông).
- Database: PostgreSQL + Redis (cache).
- Mobile: Native (Swift/Kotlin) + WebView (React/Next.js).
- Map: Goong hoặc Mapbox.
- AI/ML: Google MLKit (on-device).
- QR Sign: Ed25519 hoặc HMAC-SHA256.

---

## 6. Yêu Cầu Đối Với Nhà Thầu

### 6.1 Năng lực tối thiểu

- Đã từng triển khai **tối thiểu 2 dự án tương đương** (app mobile + backend + WebView + hệ thống điểm thưởng). Cung cấp link sản phẩm / case study.
- Đội ngũ **tối thiểu 5 người** full-time (1 PM, 1 BA/QA, 1 Mobile, 1 Backend, 1 Frontend). Dưới mức này vui lòng nêu rõ cơ chế cộng tác.
- Có kinh nghiệm với **eKYC Việt Nam** (CCCD QR code, GPKD/MST). 
- Có năng lực về **offline-first architecture** (sync engine, conflict resolution). 
- Pháp lý: Công ty có tư cách pháp nhân Việt Nam, mã số thuế.

---

## 7. Định Dạng Báo Giá Yêu Cầu

Báo giá vui lòng trình bày theo **định dạng chuẩn** sau để bên mời thầu dễ so sánh giữa các nhà thầu:

### 7.1 Cấu trúc bảng báo giá

Cho mỗi hạng mục (5 hạng mục), cung cấp bảng chi tiết:

| Phần | Công việc | Số man-days | Vai trò (PM/BA/Dev/QA) | Đơn giá (VND/MD) | Thành tiền |
|------|-----------|-------------|------------------------|------------------|------------|
| A | Phân tích thiết kế | ... | PM + BA | ... | ... |
| B | Phát triển Backend | ... | Backend | ... | ... |
| C | Phát triển Mobile | ... | Mobile | ... | ... |
| D | Phát triển Frontend/WebView | ... | Frontend | ... | ... |
| E | QA / Testing | ... | QA | ... | ... |
| F | Triển khai + Bảo hành 6 tháng | ... | DevOps + Support | ... | ... |

### 7.2 Các khoản mục bắt buộc nêu rõ

- [ ] Chi phí **hạ tầng tháng** (server, CDN, SMS OTP, Zalo ZNS, Map API, FCM/APNs, eKYC provider) — ước tính cho Year 1 với giả định **5.000 user active tháng**.
- [ ] Chi phí **license** (nếu có) — bản quyền font, thư viện, SDK.
- [ ] **Thuế VAT 10%** — ghi rõ đã bao gồm / chưa bao gồm.
- [ ] **Điều kiện thanh toán** — đề xuất giai đoạn (VD: 30% ký HĐ, 30% UAT, 30% Go-live, 10% hết bảo hành).
- [ ] **Ngân sách Phase 1** vs **Phase 2** tách riêng.
- [ ] **Gói Maintenance** từ tháng thứ 7 trở đi — VND/tháng + scope SLA.


## 10. Điều Khoản Ràng Buộc

- **Tính bảo mật:** Tất cả tài liệu Spec đính kèm là **tài liệu nội bộ**. Nhà thầu không được chia sẻ cho bên thứ ba nếu không có sự đồng ý bằng văn bản. Nhà thầu trúng thầu sẽ ký NDA chính thức trước khi nhận tài liệu API nội bộ.
- **Quyền sở hữu:** Toàn bộ source code, database schema, tài liệu kỹ thuật thuộc sở hữu của DSS CLUB sau khi nghiệm thu.
- **Quyền từ chối:** Bên mời thầu có quyền từ chối toàn bộ báo giá mà không cần giải thích, hoặc huỷ RFQ bất kỳ lúc nào.
- **Chi phí tham gia:** Nhà thầu tự chịu chi phí liên quan đến việc chuẩn bị báo giá.

---

