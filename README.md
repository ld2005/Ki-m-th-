KỊCH BẢN KIỂM THỬ HIỆU NĂNG (PERFORMANCE TEST SCENARIO)
1. Thông tin chung

Công cụ sử dụng: Apache JMeter 5.6.3

Mục tiêu kiểm thử: Đánh giá hiệu năng, thời gian phản hồi (Response Time) và thông lượng (Throughput) của hệ thống khi có lượng truy cập vào Trang chủ và các Trang con.

Cấu hình chung: Sử dụng HTTP Request Defaults để thiết lập các thông số mặc định (như Server Name/IP, Protocol, Port) cho tất cả các request trong Test Plan.

Thành phần báo cáo: Theo dõi kết quả thông qua View Results Tree và Summary Report.

2. Chi tiết các kịch bản (Thread Groups)

Dựa trên cấu trúc Test Plan, việc kiểm thử được chia làm 3 kịch bản chính (tương ứng với 3 Thread Group):

Kịch bản 1: test1 - Kiểm tra tải cơ bản trên Trang chủ
Mục đích: Đánh giá thời gian phản hồi khi người dùng truy cập vào "Trang chủ".

Số lượng (Samples): Tổng cộng 50 request được gửi đi.

Kết quả ghi nhận:

Request "Trang chủ" (20 samples): Tỉ lệ lỗi 0%, thời gian phản hồi trung bình (Average) là 4278 ms.

Lưu ý: Có 30 request không có tên (label trống) bị lỗi 100%. Đây có thể là một HTTP Request chưa được cấu hình URL hoặc bị thiếu tham số.

Kịch bản 2: test2 - Kiểm tra luồng truy cập Trang chủ và Trang con
Mục đích: Mô phỏng hành vi người dùng truy cập tuần tự vào "trang chủ", sau đó chuyển hướng sang "Trang Con".

Số lượng (Samples): 100 vòng lặp (hoặc 100 users).

Kết quả ghi nhận:

Request "trang chủ" (100 samples): Tỉ lệ lỗi 0%, thời gian phản hồi trung bình là 4541 ms.

Request "Trang Con" (100 samples): Tỉ lệ lỗi 0%, thời gian phản hồi trung bình là 3236 ms.

Lưu ý: Tương tự kịch bản 1, kịch bản này cũng có một request không tên (100 samples) đang bị lỗi 100%.

Kịch bản 3: test3 - Kiểm tra tải đồng thời trên nhiều Trang con
Mục đích: Đánh giá khả năng xử lý của hệ thống khi truy cập song song vào nhiều trang con khác nhau ("Trang Con 1" và "Trang Con 2").

Số lượng (Samples): Tổng cộng 337 request (có thể kịch bản này được cài đặt chạy theo thời gian - duration test, hoặc được người dùng dừng thủ công nên số lẻ).

Kết quả ghi nhận:

Request "Trang Con 1" (172 samples): Tỉ lệ lỗi 0%, thời gian phản hồi trung bình là 3378 ms.

Request "Trang Con 2" (165 samples): Tỉ lệ lỗi 0%, thời gian phản hồi trung bình là 3623 ms.
