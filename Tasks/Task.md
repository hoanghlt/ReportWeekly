
# Weekly Report (18/08 - 22/08)

## 1. WSale

### 1.1. Đang thực hiện
- **Migration Website client** 
- **Migration api backend** 
- **Tích hợp bán các dịch vụ mới:** Internet, PayTV, Camera _(chưa bắt đầu)_
- **Chuẩn hóa API/SERVICE & CODE:** QuyenLB đang thực hiện
- **Dựng UI thông tin GTBB:** QuyenLB đang thực hiện
- **Phân tích database & tổ chức source cho phân quyền:** QuyenLB đang thực hiện
- **Tách dần source W-Sale sang microservice:** QuyenLB đang thực hiện
- **Dựng luồng tương tác thử nghiệm bằng GRPC giữa các service:** QuyenLB đang thực hiện

### 1.2. Đã thực hiện
- **Tích hợp đơn hàng DKOL cho ECOM tư vấn:**
  - API nhận data 
  - Tích hợp nhận master từ Omnisell _(chưa bắt đầu)_
- **Test CSOC:** Sửa lỗi CSOC _(Done Round 1)_
  - Bổ sung phân quyền theo token userlogin để check quyền truy cập data

### 1.3. Kế hoạch/Nghiên cứu
- Nghiên cứu hướng xử lý cho multiple version API service _(chưa bắt đầu)_
- Xử lý dữ liệu nhạy cảm trong response của API _(chưa bắt đầu)_
- Dựng service xử lý log _(chưa bắt đầu)_
- Phân tích & thực hiện chức năng ẩn giấu dữ liệu nhạy cảm trên UI _(chưa bắt đầu)_
- Hỗ trợ kiểm tra & fix lỗi đăng nhập IAM của source UI DBA _(pending)_
- Migration source API thành chuẩn chung _(pending)_

---

## 2. Telesales

### 2.1. Đã hoàn thành 
- **Tích hợp trả trước PayTV** (Staging)
  - Tích hợp API lấy ID dịch vụ PayTV và cước thuê bao tương ứng
  - Tích hợp API lấy ID câu lệnh khung theo ID dịch vụ Pay và cước
  - Bổ sung rule: Nếu cước PayTV tăng hoặc có phí swap → không cho miễn phí đồng thời cả 2
  - Tích hợp API đẩy khoản thu recare pay với VAT 8%
  - Call API đẩy tiền trả trước PayTV khi ra bill (HaiTN đang thực hiện)
- **Viết logic chặn thao tác hoàn tất trùng bằng cách chèn cờ kiểm soát vào bảng**
  - Nếu đã tồn tại record với ID đơn hàng, ghi log và dừng xử lý
- **Test CSOC:** Sửa lỗi CSOC _(Round 2)_
  - Bổ sung phân quyền theo token userlogin để check quyền truy cập data

### 2.2. Đang thực hiện
- **Lương Telesales**
  - Điều chỉnh màn hình lương telesales, tách các cột swap, làm rõ các cột Cam
  - Bổ sung nhận diện loại trừ HĐ GTBB