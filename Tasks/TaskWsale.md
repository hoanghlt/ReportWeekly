
# WSale - Task Backlog

---

## 1. Chính sách & API

- **Xử lý lấy thông tin chính sách**  
  _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
  - Xử lý lấy thông tin đơn hàng _Assignee: QuyenLB_
  - Xử lý lấy chính sách theo master data từ thông tin đơn hàng _Assignee: QuyenLB_

- **Phát triển API cung cấp cho Omnisell**
  - API nhận data checklist từ Omnisell đẩy về  
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Phân tích prototype input output _Assignee: Hoangvt_
    - Viết API nhận thông tin khách hàng từ Omnisell _Assignee: Hoangvt_

  - API Kiểm tra checklist đã được tiếp nhận hay chưa 
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Phân tích prototype input output _Assignee: Hoangvt_ 
    - Viết API kiểm tra checklist theo portalobjid truyền vào _Assignee: Hoangvt_

  - API cập nhật lại thông tin khi phân công lại  
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Phân tích prototype input output _Assignee: Hoangvt_
    - Viết API ghi nhận nhân viên được phân công _Assignee: Hoangvt_
    - Call API gửi notification lên SOP kèm link redirect sau khi ghi nhận được nhân viên được phân công _Assignee: HaiTN16_

## 2. Tích hợp & Consumer Data

- **Consumer data phiếu thi công các PTC lên từ DKOL**  
  _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Xin thông tin PTC từ anh Tài hoặc anh NamTH  _Assignee: HaiTN_

## 3. Giao diện WSale

- **Xử lý phần giao diện WSale**
  - Xử lý load dịch vụ bán, load kế hoạch (nghiên cứu đẩy vào dịch vụ nào)  
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Điều chỉnh API load kế hoạch từ Omnisell bổ sung thêm data Inbound _Assignee: LinhVQ_
    - Điều chỉnh API tìm kiếm checklist theo kế hoạch _Assignee: Hoangvt_

  - Tìm kiếm, gắn thêm điều kiện gọi về API Omnisell unicast  
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    - Bổ sung luồng Call API tiếp nhận checklist vào API GetInfo _Assignee: LinhVQ_

  - Hiển thị load chính sách mới
    _Timeline: 04/08 - 08/08 - 12/08_ **(Done)** 
    _Assignee: QuyenLB_

  - Xử lý logic cho phần hiển thị đơn hàng từ DKOL
    _Timeline: 04/08 - 08/08 - 15/08_ **(Done)** 
    _Assignee: QuyenLB, LinhVQ_
    - Recheck lại thông tin đơn hàng DKOL và Đơn hàng luồng trước đó làm để hiển thị theo đúng luồng

  - Bổ sung lấy thông tin SupID từ thông tin đơn hàng DKOL để tick hẹn triển khai  
    _Timeline: 04/08 - 08/08_  **(Done)**
    _Assignee: HaiTN_

  - Bổ sung tình trạng tư vấn mới cho nhu cầu của dự án 
    _Timeline: 04/08 - 08/08 - 12/08_ **(Done)** 
    - Chờ PO Chốt thông tin request 

  - WSale cập nhật kết quả tư vấn về Omnisell
    _Timeline: 04/08 - 08/08 - 12/08_  **(Done)**
    _Assignee: HaiTN_

  - Recheck phần tick hẹn triển khai PTC
    _Timeline: 04/08 - 08/08 - 12/08_ **(Done)** 
    - Kiểm tra luồng client WSale _Assignee: LinhVQ_

  - Kiểm tra luồng đã có đơn hàng thì hiển thị hết các tab để qua tick hẹn triển khai được
    _Timeline: 04/08 - 08/08 - 12/08_ **(Done)** 
    - Kiểm tra luồng đã có đơn hàng checklist trên WSale _Assignee: LinhVQ_

  - Tracking đơn hàng
    _Timeline: 04/08 - 08/08 - 15/08_ **(Done)** 
    - Kiểm tra luồng nhận tracking đơn hàng từ SC, thông tin đơn hàng được tạo từ SC _Assignee: Hoangvt_

## 4. Test round 1 (Done)

- **Check và xử lý bug**
    _Timeline: 12/08 - 15/08_