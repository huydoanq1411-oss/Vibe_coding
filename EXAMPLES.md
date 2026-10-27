# Ví dụ: cách ra lệnh tốt và lỗi thường gặp

## 1. Yêu cầu giao diện
Mơ hồ: "Làm đẹp và chuyên nghiệp hơn."
Cụ thể: "Thẻ sản phẩm 4 cột trên máy tính, 1 cột trên điện thoại, giữ màu hiện tại, tăng khoảng cách giữa tiêu đề và danh sách lên 24px, font tiêu đề đổi sang font display đã chọn."

## 2. Tiêu chí nghiệm thu
Mơ hồ: "Đặt hàng phải hoạt động."
Đo được: "Người dùng đã đăng nhập đặt hàng thì tạo đúng một đơn. Bấm gửi hai lần không tạo đơn thứ hai. Người chưa đăng nhập gọi trực tiếp API bị từ chối với mã 401."

Tiêu chí cho chức năng AI: "Mô hình đạt tối thiểu X% accuracy trên tập test cố định; xử lý văn bản rỗng và quá dài; phản hồi dưới Y giây trên máy chạy thật."

## 3. Báo cáo kết quả
Không chấp nhận: "Đã sửa xong, mọi thứ chạy tốt."
Chấp nhận: "Đã sửa lỗi lọc theo ngày (nguyên nhân: so sánh chuỗi thay vì ngày). Đã chạy `npm test`: 24 đạt, 0 lỗi. Đã thử tay ba ca: ngày hợp lệ, ngày rỗng, ngày sai định dạng. Chưa kiểm tra trên Safari."

Tóm tắt chi tiết sau mỗi bước, ví dụ: "Bước vừa làm: tạo bộ file mẫu. Việc đã làm: (1) tạo ba file mẫu MD, DOCX, PDF; (2) kiểm tra metadata và gỡ tên tác giả. File: fixtures/sample.md (nguồn văn bản mẫu), fixtures/sample.docx (mẫu Word, đã gỡ metadata). Lệnh: `npm test` 34 đạt, 0 lỗi. Quyết định: dùng chuẩn hóa NFC vì dấu rời bị trích xuất sai (giả định, chờ bạn duyệt). Chưa làm: chưa thử trên Safari. Bước tiếp theo: chạy lại bộ ký tự mẫu."

## 4. Sửa lỗi bằng bằng chứng
Thiếu: "App bị lỗi, sửa giúp."
Đủ: thao tác gây lỗi, kết quả mong muốn, kết quả thực tế, stack trace đã xóa bí mật, môi trường (phiên bản Java, Node, trình duyệt). Yêu cầu AI sửa nguyên nhân gốc, không chỉ che thông báo lỗi.

## 5. Giao việc theo lát
Quá rộng: "Làm cho tôi toàn bộ hệ thống đặt hàng."
Đúng cỡ: "Làm chức năng thêm vào giỏ hàng: endpoint, quyền, test, giao diện nút và trạng thái. Chạy test rồi báo kết quả; chưa làm thanh toán."

## 6. Lỗi giao diện hay gặp
| Dấu hiệu | Cách sửa |
| --- | --- |
| Font mặc định, nhiều màu không theo hệ | Chọn cặp font và 3-5 màu, khai báo thành biến |
| Mọi section đều fade-up | Dành chuyển động cho một khoảnh khắc chính |
| Mobile chỉ là desktop thu nhỏ | Thiết kế bố cục riêng, thử trên máy thật |
| Ảnh stock, chữ chung chung | Dùng ảnh và nội dung riêng của dự án |
| Trang nặng, tải chậm | Tối ưu ảnh, lazy loading, nạp phần nặng sau |
