WSale
1. Version hiện tại: 1.5
2. Mục tiêu 
- Nâng cấp hạ tầng K8s cụm API TLS Inside
- LDP V.VIP MKT : Bổ sung thông tin nhận diện tập data từ FMI
- LDP V.VIP Map : Khách hàng tra cứu được khu vực nào đã có hạ tầng Wifi 7 Biết TTKD/VPGD nào đang cung cấp dịch vụ để chủ động liên hệ và đăng ký
- Autocall :Bổ sung thêm điều kiện check giỏ blacklist,check trùng tự động SDT chính chủ khi đẩy data KHG sang Dialo
- Nâng cấp Camera: Bổ sung LDP nâng cấp Camera chung luồng EPL
- WSale bản Mobile SOP
3. Thời gian release
- Staging - 1.5:  29/04/2026
4. Tiến độ
- Nâng cấp hạ tầng K8s cụm API TLS Inside (1/1-30/1): 95% [IN PROGRESS] - Infrastructure
- LDP V.VIP MKT (5/1-9/1): 100% [DONE] - Marketing
- LDP V.VIP Map (12/2, 13/2 → Tết → 17/3-24/3): 0% [PENDING] - Features
- Autocall (02/2-11/2): 70% [IN PROGRESS] - Automation
- Nâng cấp Camera (5/2-11/2): 15% [IN PROGRESS] - Features
- WSale bản Mobile SOP (25/3-29/4): 0% [IN PROGRESS] - Development
5. Việc đã hoàn thành 
- LDP V.VIP MKT (5/1-9/1): 100% [DONE] - Marketing
6. Công việc 2 tuần tiếp (1/2 - 14/2)
 - Tuần 1 (1/2 - 7/2):
   - Nâng cấp Camera: Triển khai LDP Nâng cấp Camera (4/2 - 9/2)
     - Điều chỉnh banner và luồng xử lý search hợp đồng (UI/UX)
     - Thiết kế và triển khai màn hình xác nhận cho Nâng cấp Camera
     - Tích hợp API nâng cấp camera lấy gói bán dịch vụ, lấy thông tin đơn hàng, thông tin thanh toán, ...
   - Nâng cấp K8s: Hoàn thành tuning cuối cùng
   - Autocall: Bổ sung thêm blacklist bằng số ĐT, điều chỉnh luồng check trùng SDT (02/2 - 11/2)
 - Tuần 2 (8/2 - 14/2):
   - Autocall: Tiếp tục phát triển check trùng SDT (02/2 - 11/2)
   - LDP V.VIP Map: Bắt đầu phân tích và thiết kế (trước kỳ Tết)
7. Vấn đề
- Resource dev chưa đáp ứng đủ với số lượng task hiện tại
- Chưa được hỗ trợ tích hợp Order Service từ SPF