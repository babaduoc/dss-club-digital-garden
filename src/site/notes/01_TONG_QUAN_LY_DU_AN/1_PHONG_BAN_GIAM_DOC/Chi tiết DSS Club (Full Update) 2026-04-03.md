---
{"dg-publish":true,"permalink":"/01-tong-quan-ly-du-an/1-phong-ban-giam-doc/chi-tiet-dss-club-full-update-2026-04-03/","title":"TÀI LIỆU MÔ TẢ CHI TIẾT ỨNG DỤNG DSS CLUB (FULL UPDATE)","dg-note-properties":{"title":"TÀI LIỆU MÔ TẢ CHI TIẾT ỨNG DỤNG DSS CLUB (FULL UPDATE)","loai":"Detail_Requirement","ngay_cap_nhat":"2026-04-03","nguon":"Chi tiết DSS Club 10_03_2026.md"}}
---


# **TÀI LIỆU MÔ TẢ CHI TIẾT ỨNG DỤNG DSS CLUB**

*(Bản cập nhật ngày 2026-04-03 - Tích hợp đầy đủ tính năng)*

---

# **1. Giới thiệu ứng dụng**

**DSS Club** là ứng dụng chăm sóc khách hàng (Customer Loyalty App) do **DSS Việt Nam** phát triển, hướng đến kỹ thuật viên lắp đặt sản phẩm thiết bị **camera an ninh – thiết bị an toàn – giải pháp công nghệ** mà DSS Việt Nam phân phối.

Mục tiêu chính của ứng dụng:
● Tích điểm thông qua **quét mã sản phẩm** (số SN chính hãng).
● Theo dõi tổng lượng quét và tích lũy điểm đổi quà.
● Tham gia các chương trình khuyến mãi, vòng quay may mắn, minigame.
● Nhận thông báo cập nhật sản phẩm và chương trình từ DSS Việt Nam.

Ứng dụng hỗ trợ:
● **iOS** (App Store) – DSS Club V3  
● **Android** (Google Play)

---

# **2. Kiến trúc hoạt động tổng quan**

Ứng dụng DSS Club hoạt động theo quy trình:
1. **Đăng ký – xác thực tài khoản:** Xác thực qua ZNS của Zalo.
2. **Người dùng mua sản phẩm DSS:** Sản phẩm có mã QR hoặc Serial (SN) chính hãng.
3. **Người dùng quét mã trong ứng dụng:** Hệ thống kiểm tra tính hợp lệ qua API bảo hành và danh mục sản phẩm (giới hạn trong 2 năm gần nhất).
4. **Tích lũy điểm:** Tăng theo giá trị sản phẩm và các chương trình nhân điểm (x2, x3).
5. **Sử dụng điểm:** Đổi quà, đổi Voucher, quyên góp quỹ từ thiện, tham gia trò chơi.

---

# **3. Đối tượng sử dụng**

| Nhóm người dùng | Mục đích sử dụng | Lợi ích |
| ----- | ----- | ----- |
| **Đại lý – kỹ thuật viên** | Quét mã sản phẩm định kỳ | Tích lũy quà tặng và ưu đãi chuyên biệt |

---

# **4. Chi tiết tính năng và cách vận hành**

## **4.1. Đăng ký & Đăng nhập**
● Đăng ký bằng số điện thoại dùng Zalo.
● Nhận mã OTP xác thực qua ZNS Zalo.
● Tài khoản gắn chặt với: Số điện thoại + Device ID.

---

## **4.2. Cài đặt hệ thống (Admin Settings)**

### **4.2.1. Hạng thành viên (Membership Tiers)**
| Tên hạng | Điểm tối thiểu | Quà tối đa (Điểm/tuần) | Giới hạn quà/tuần | Điểm sinh nhật | Lượt quay/ngày |
|---|---|---|---|---|---|
| **Thành viên** | 0 | 100,000 | 5 | 100 | 0 |
| **Đồng** | 20,000 | 100,000 | 10 | 200 | 0 |
| **Bạc** | 50,000 | 100,000 | 20 | 300 | 0 |
| **Vàng** | 100,000 | 100,000 | 30 | 500 | 1 |
| **Bạch kim** | 500,000 | 1,000,000 | 100 | 1,000 | 1 |

### **4.2.2. Thông tin liên lạc (Hệ thống Chat)**
Phân chia luồng hỗ trợ Zalo: Hỗ trợ Kỹ thuật/IT và Kinh doanh theo hai miền Bắc/Nam.

### **4.2.3. Cơ chế mở khóa tính năng (Điểm uy tín)**
Số "Tim" đại diện cho mức độ uy tín để mở khóa chức năng:
- **0 Tim:** Khóa toàn bộ tính năng.
- **1 Tim:** Anh em quanh đây, Quyên góp quỹ từ thiện.
- **2 Tim:** Quét mã tích điểm.
- **3 Tim:** Tham gia trò chơi - thử thách.
- **4 Tim:** Đổi quà (Full quyền).

### **4.2.4. Cài đặt chung (Ngưỡng an ninh)**
- **Giới hạn quét mã:** 100 mã/ngày, 800 mã/tháng.
- **Ngưỡng quét lỗi:** 500 lần (Quá ngưỡng bị trừ Tim).
- **Phục hồi uy tín:** Tự động hồi phục vào ngày 20 hàng tháng.

### **4.2.5. Quản lý Voucher**
Admin thiết lập hình ảnh, khu vực áp dụng, loại % hoặc số tiền, và điều kiện nhận Voucher.

### **4.2.6. Thiết lập ưu đãi (Promotion Setup)**
Cấu hình hệ số nhân điểm (Coefficient) cho từng dòng sản phẩm theo thời gian khuyến mãi.

---

## **4.3. QUÀ TẶNG (Warehouse & Rewards)**

### **4.3.1. Phân loại kho quà tặng**
- **Gian hàng trải nghiệm:** Dùng thử sản phẩm mới. Giới hạn đổi theo hạng thành viên.
- **Quà tặng đổi điểm:** Kho vật phẩm chính dùng "Điểm đổi quà".
- **Quà vòng quay may mắn:** Kho quà dành riêng cho các chương trình Gamification.

### **4.3.2. Đối tượng đổi quà**
- Voucher giảm giá.
- Vật phẩm vật lý (Camera, thiết bị IT, quà lưu niệm).
- Vé sự kiện, Phiếu mua hàng / hoàn tiền.

### **4.3.3. Quy trình đổi & Giao nhận**
1. User chọn quà đủ điểm → Xác nhận đổi điểm.
2. Hệ thống trừ điểm & tạo mã nhận quà.
3. Admin đóng gói theo thông số (Cân nặng, Kích thước) và gửi qua **Viettel Post**.

---

## **4.4. Từ thiện**
● **Mục đích:** Tính năng này được tạo ra để cho người dùng có thể quyên góp số điểm mình có được trong quá trình sử dụng ứng dụng.
● **Sử dụng:** Số điểm quyên góp sẽ được dùng để quy đổi ra tiền mặt hoặc hiện vật giúp đỡ cho những người gặp khó khăn.
● **Điều kiện:** Mở khóa ở mức 1 Tim trở lên.
● **Thực tế vận hành:** Theo thống kê, từ lúc triển khai tính năng đến giờ chưa có một lần nào số điểm này được quy đổi ra để sử dụng thực tế.

---

## **4.5. Sản phẩm & Quản lý Mã quét**
Quản lý danh sách các sản phẩm hợp lệ để tích điểm và quy trình quét mã của User. Danh mục này được hiển thị trên App để người dùng tìm kiếm thông tin (nhưng ẩn giá vốn và số điểm).

### **4.5.1. Công thức tính điểm & Đổi quà**
- **Quy tắc:** Điểm sản phẩm = `Giá vốn / 10.000`
- **Tỷ giá quy đổi:** 1 Điểm tương đương `100 VNĐ`.
- **Ví dụ vận hành:** 
  - Sản phẩm giá vốn 500.000 VNĐ → Tích lũy được 50 điểm.
  - 900 điểm có giá trị tương đương 90.000 VNĐ (tương đương trị giá một cái áo thun).

### **4.5.2. Chuẩn hóa tên sản phẩm (API Matching)**
- Tên sản phẩm trên App **bắt buộc phải khớp** với tên trong phần mềm quản lý kho để API nhận diện hàng chính hãng.
- **Cơ chế:** Hệ thống tự động lược bỏ các ký tự đặc biệt (`/`, `DHI`, `DH`...) để đối chiếu và tăng tỷ lệ khớp tối đa.

### **4.5.3. Quy trình quét mã & Điều kiện**
1. Mở camera trên App quét mã SN/QR trên vỏ hộp hoặc sản phẩm.
2. Kiểm tra qua API bảo hành DSS: Lọc điều kiện sản phẩm xuất kho **không vượt quá 2 năm**.
3. **Quy định ngặt nghèo:** Mỗi mã SN chỉ được quét để tích điểm đúng **một lần duy nhất**.

### **4.5.4. Xử lý lỗi quét mã & Truy lĩnh điểm**
Hệ thống tự động chạy rà soát và cộng bù điểm vào **02:00 sáng hàng ngày** (Daily Job) cho 2 lỗi phổ biến sau:
1. **Lỗi "Mã có số điểm = 0":**
   - *Nguyên nhân:* Sản phẩm hợp lệ nhưng chưa được Admin tạo tên/giá vốn trên App.
   - *Xử lý:* Sau khi Admin cập nhật giá, hệ thống sẽ tự động tìm và cộng điểm hồi tố cho các User đã quét lỗi.
   
2. **Lỗi "Seri không tồn tại":**
   - *Nguyên nhân:* Kho đã xuất hàng nhưng chưa làm phiếu xuất trên hệ thống máy tính, khiến API báo hàng lậu.
   - *Xử lý:* Khi Kho hoàn tất thủ tục xuất, hệ thống sẽ tự quét lại và trả điểm cho kỹ thuật viên.

---

## **4.6. Tích điểm**
● Điểm từ sản phẩm quét chính hãng.
● Điểm thưởng sự kiện hoặc cộng trực tiếp từ Admin.
● Chế độ nhân điểm (x2, x3) trong các chiến dịch đặc biệt.

---

## **4.7. Sự kiện – Vòng quay may mắn**
● Sử dụng lượt quay miễn phí (cho hạng Vàng/Bạch kim) hoặc đổi bằng điểm.
● Quà tặng: Tai nghe, Loa, Camera mini... quà trúng thưởng nằm trong mục "Quà của tôi".

---

## **4.8. Tin tức & Thông báo**
● Tin tức sản phẩm mới, bảo hành, khuyến mãi.
● Gửi qua *Push Notification* và Pop-up khi mở ứng dụng.

---

## **4.9. Kho câu hỏi (FAQ)**
● Hỗ trợ giải đáp thắc mắc về cài đặt App, cách quét mã, đổi quà.

---

## **4.10. Anh em quanh đây (Bản đồ)**
● Kết nối thợ lắp đặt/đại lý theo vị trí địa lý.
● Điều kiện: Mở khóa ở mức 1 Tim trở lên.

---

## **4.11. Bảng xếp hạng**
● Vinh danh đại lý/kỹ thuật viên có doanh số tích lũy hoặc lượt quét mã cao nhất.

---

## **4.12. Báo cáo**
● Thống kê chỉ số quét mã, đổi quà, và hiệu quả chương trình KM (Dữ liệu Power BI).

---
# **5. Khiếu nại**
- Tính năng cho phép kỹ thuật viên lắp đặt cuối cùng khiếu nại nếu mã SN đã bị quét trước đó.
- Hệ thống đánh giá khiếu nại: Thu hồi điểm người trước, trả điểm cho người sau, trừ điểm uy tín người vi phạm.

---

# **6. Quy định & hạn chế**
● Chỉ sản phẩm chính hãng DSS phân phối mới được tích điểm.
● Điểm không có giá trị quy đổi tiền mặt.
● Admin có quyền hủy điểm nếu phát hiện gian lận.

---

# **7. Lợi ích tổng quan**
● **Với User:** Nhận quà giá trị, hưởng đặc quyền theo hạng thành viên.
● **Với DSS:** Quản lý vòng đời sản phẩm, chống hàng giả, chăm sóc khách hàng hiệu quả.

---
---
# **8. Phụ lục Kỹ thuật (Developer Notes)**

Chương này dành cho đội ngũ phát triển (Developers) và vận hành hệ thống, liệt kê các đặc tả kỹ thuật và mô hình dữ liệu lõi trích xuất trực tiếp từ mã nguồn `DSSClub`.

## **8.1. Kiến trúc Hệ thống (Tech Stack)**
- **Framework:** .NET Core Web API (Backend) / ASP.NET MVC (Admin Site).
- **Dữ liệu:** Entity Framework Core (Code-First) / SQL Server.
- **Xác thực:** JWT Token & Zalo ZNS (giao thức `TrackingOTP`).
- **Xử lý song song:** `SerialQueue` (TaskQueue) được sử dụng để điều phối các tác vụ ghi danh mã serial, chống xung đột dữ liệu (Race condition).

## **8.2. Bản đồ Dữ liệu (Key Entities)**
Hệ thống quản lý dữ liệu thông qua các bảng lõi sau (trích xuất từ `DSSDbContext`):

| Module | Bảng Database quan trọng | Vai trò |
|---|---|---|
| **Thành viên** | `Users`, `Rankings`, `UserRankings` | Quản lý định danh, thứ hạng và điểm danh. |
| **Quét mã** | `UserQRCodes`, `Products`, `TrackingUserScore` | Lưu vết serial, thông tin sản phẩm và lịch sử biến động điểm. |
| **Vận hành** | `Orders`, `GiftStocks`, `Complains` | Đơn hàng đổi quà, kho vật phẩm và khiếu nại. |
| **Hệ thống** | `Settings`, `ChatSettings`, `PreferentialSettings` | Cấu hình ngưỡng bảo mật, luồng chat và nhân hệ số điểm. |
| **Game** | `LuckyWheelGames`, `LotteryGames` | Các chương trình vòng quay và xổ số tích điểm. |

## **8.3. Đặc tả API & Luồng Xử lý (Backend Logic)**

### **8.3.1. Các API Endpoints chính cho Mobile App**
- **Quản lý Serial:**
    - `POST /api/Scan/add-serial`: Đưa mã vào danh sách chờ.
    - `POST /api/Scan/register-serials`: Kích hoạt đồng thời danh sách mã (Batch Process).
- **Xác thực:**
    - `POST /api/Authentication/verify-register-phone`: Gửi mã xác thực về Zalo.

### **8.3.2. Quy tắc kiểm tra tính hợp lệ (Scan Validation)**
Khi người dùng kích hoạt mã, Backend thực hiện các bước:
1. **Security Check:** Chặn ký tự đặc biệt (`\n`, `\t`, `\r`) để tránh bypass API.
2. **Limit Check:** Đối soát với bảng `Settings` (ScanLimit/MonthLimit).
3. **Mirror Check:** Gọi API bảo hành DSS để lấy thông tin sản phẩm (`MaHangHoa`, `NgayXuat`).
4. **Year Check:** Nếu `NgayXuat` cũ hơn 2 năm so với hiện tại → Trả lỗi không hợp lệ.

### **8.3.3. Cơ chế Chạy ngầm (Scheduled Services)**
Hệ thống sử dụng `IHostedService` để thực thi các tác vụ định kỳ:
- **`CheckProductForSerialBackgroundService`**: Chạy hàng ngày lúc **02:00 AM**. Rà soát các mã lỗi `SystemError` (Điểm = 0) để cộng hồi tố khi Admin đã cập nhật danh mục.
- **`CheckSerialBackgroundService`**: Chạy vào **10:00 AM sáng Chủ nhật** hàng tuần. Kiểm tra các mã không tồn tại hoặc lỗi trong vòng 90 ngày.

---
*Bản tài liệu này đã được bổ sung chi tiết kỹ thuật dựa trên phân tích mã nguồn và cập nhật vào ngày 2026-04-09.*
