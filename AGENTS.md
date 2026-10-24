# AGENTS.md: Quy tắc vibe code web

Quy tắc bắt buộc cho AI khi làm việc trên mọi dự án web. Cẩm nang đầy đủ (prompt mẫu, công cụ, checklist, thước đo web $1 và web $10.000) nằm ở `docs/CAM-NANG.md`; đọc phần liên quan khi cần.
Chỉ điền mục 12 và 13 cho từng dự án.

## 1. Vai trò và nguyên tắc
- Tôi là sinh viên CNTT đang học Full Stack (HTML, CSS, JavaScript, SQL, Java Core, Spring Boot, React) và AI (Python, ML, Hugging Face). Tôi quyết định mục tiêu và nghiệm thu; bạn là cộng sự lập trình.
- Không giao hết mà không hiểu: với code quan trọng, giải thích từng dòng (vấn đề giải quyết, lý thuyết nền, vì sao viết vậy, lỗi thường gặp) để tôi học được.
- Không báo "đã xong" khi chưa kiểm tra. Luôn nêu lệnh đã chạy và kết quả thật. Phân biệt rõ điều đã kiểm tra với điều chỉ suy đoán.
- Việc đã rõ thì cứ làm tiếp; chỉ dừng hỏi khi thiếu quyết định thực sự cần thiết.
- Không thêm thành phần chỉ vì tiện (microservice, thư viện, dịch vụ trả phí). Một backend đủ dùng thì không tách.

## 2. Quy trình làm việc
Ý tưởng → yêu cầu → thiết kế → xây từng lát → kiểm tra → triển khai → bảo trì. Phát hiện vấn đề thì quay lại bước liên quan và cập nhật đặc tả.
1. Đọc yêu cầu, docs/SPEC.md và mã nguồn hiện có trước khi hành động.
2. Chưa có đặc tả thì lập trước khi code rộng: đặc tả, danh sách trang, ma trận quyền, ERD, mô tả API, wireframe.
3. Chia việc thành lát nhỏ; mỗi lát chạy và nghiệm thu độc lập, mỗi lát một commit.
4. Trình tự xây: khung dự án → dữ liệu → đăng nhập và quyền → chức năng chính → chức năng AI → chức năng phụ → hoàn thiện giao diện.
5. Không làm hàng chục chức năng trong một lượt rồi mới kiểm tra.
6. Mọi thay đổi yêu cầu cập nhật vào docs/SPEC.md trước khi sửa code.

## 3. Khi nào hỏi lại
- Hỏi khi câu trả lời ảnh hưởng lớn đến mục tiêu, dữ liệu, quyền, chi phí, tích hợp hoặc kiến trúc. Hỏi theo nhóm 3-5 câu, nêu lý do và đề xuất lựa chọn dễ hiểu.
- Chi tiết nhỏ: dùng mặc định hợp lý và ghi rõ giả định.
- Không tự đoán quy tắc tính tiền, quyền quản trị hay cách dùng dữ liệu nhạy cảm.

## 4. Chốt phạm vi
- Chia chức năng thành: bắt buộc, làm sau, ngoài phạm vi.
- Mỗi chức năng bắt buộc cần: ai dùng, điều kiện trước, đầu vào, luồng thành công, trường hợp lỗi, dữ liệu thay đổi, tiêu chí nghiệm thu đo được.
- Chức năng AI: ghi rõ đầu vào/đầu ra, mô hình, dữ liệu, chỉ số đánh giá và ngưỡng chấp nhận.

## 5. Stack mặc định (đổi khi dự án ghi khác)
- Frontend: React 18 + Vite (thêm Tailwind, shadcn/ui khi cần); trang tĩnh nhỏ dùng HTML/CSS/JS thuần.
- Backend: Spring Boot (Java 17) + Spring Security + JWT; chỉ có AI/ML nhẹ thì dùng FastAPI.
- Database: MySQL hoặc PostgreSQL (JPA/Hibernate); dữ liệu nhỏ một người dùng thì SQLite.
- Dịch vụ AI: Python (FastAPI) + scikit-learn / PyTorch / Hugging Face.
- API: REST, mô tả bằng OpenAPI/Swagger. Docker khi cần chạy giống nhau trên nhiều máy.
- Tuân theo cấu trúc hiện có (controller → service → repository → entity/DTO) và phong cách code sẵn có.

## 6. Quy tắc code và bảo mật
- Kiểm tra quyền ở backend, không chỉ ẩn nút ở giao diện. Kiểm tra dữ liệu đầu vào ở cả client và backend.
- Trả lỗi có cấu trúc rõ ràng. Không để lộ entity thô có thông tin nhạy cảm ra API.
- Mật khẩu băm bằng thuật toán chậm có salt (ví dụ bcrypt); không lưu mật khẩu thô, không ghi mật khẩu vào log.
- Bí mật (JWT secret, mật khẩu DB, khóa API) nằm trong biến môi trường; cập nhật .env.example; không commit .env.
- CORS chỉ cho phép đúng địa chỉ frontend.
- Chức năng tải file lên: kiểm tra loại file bằng nội dung, giới hạn dung lượng, xử lý trong môi trường cô lập, xóa file tạm.
- Frontend luôn có các trạng thái: đang tải, rỗng, lỗi, thành công, dữ liệu dài. Lưu token theo cách an toàn đã thống nhất và xử lý hết hạn đăng nhập.
- Chỉ lưu dữ liệu trong bộ nhớ hoặc trình duyệt khi đó là quyết định có chủ đích; ghi rõ dữ liệu giả, nút chưa xử lý, đăng nhập mô phỏng.
- Test cho nghiệp vụ quan trọng: luồng thành công, sai dữ liệu, trái quyền, thao tác trùng. Chạy test và báo kết quả thật.
- Sửa lỗi bằng bằng chứng: tái hiện, tìm nguyên nhân gốc, sửa, kiểm tra lại. Không chỉ che thông báo lỗi. Sửa ba lần không tiến triển thì dừng, tóm tắt bằng chứng, nêu giả thuyết, chọn một phép thử nhỏ.

## 7. Dịch vụ AI / Machine Learning
- Tải mô hình một lần lúc khởi động, không tải lại mỗi request.
- Kiểm tra đầu vào (rỗng, quá dài, sai kiểu) và giới hạn kích thước. Có /health và /predict, mô tả bằng OpenAPI.
- Tách tập test; không dùng tập test để chọn tham số.
- Báo chỉ số thật trên tập test và các ca mô hình sai. Ghi rõ giới hạn; không kết luận "mô hình tốt" từ vài ví dụ thử tay.
- Gọi từ backend hoặc frontend: mô tả URL, CORS và xử lý timeout.

## 8. Giao diện: chuẩn "web $10K"
1. Quan điểm thiết kế: chọn MỘT hướng (editorial, dark-luxury, brutalist, retro-modern...) và giữ nhất quán; ghi trong docs/SPEC.md. Không dùng bố cục template chung chung; không chỉ đổi màu và logo.
2. Typography: một font display + một font body, không dùng Inter, Roboto, Arial làm font chính. Thứ bậc tạo bằng cỡ chữ và độ đậm, khai báo thành token một lần.
3. Hệ màu: 3-5 màu, khai báo thành biến CSS hoặc theme. Không thêm màu ngoài bảng.
4. Thứ bậc có không gian thở: mỗi trang có cấp chính, phụ, thứ ba; dùng khoảng trắng, kích thước và tương phản dẫn mắt; không nhồi nội dung thành mảng phẳng.
5. Hình ảnh có chủ đích: không dùng ảnh stock mặc định; mọi ảnh có alt, kích thước cố định, lazy loading, không bị vỡ hay kéo giãn.
6. Chuyển động tinh tế: có chủ đích, tập trung vào một khoảnh khắc chính; không gắn fade-up cho mọi section. Luôn hỗ trợ prefers-reduced-motion.
7. Mobile được thiết kế riêng, không chỉ thu nhỏ bản máy tính; kiểm tra ở 375px, bàn phím, nội dung dài, tràn ngang.
8. Phần kỹ thuật vô hình: tải dưới 2 giây, tương phản đạt WCAG AA, điều hướng được bằng bàn phím, HTML ngữ nghĩa, có title và meta description, SEO kỹ thuật cơ bản.
- Nâng cấp giao diện theo thứ tự: nội dung và điều hướng → font, màu, khoảng cách → component đồng nhất → mobile và bàn phím → chuyển động → hiệu năng và nghiệp vụ.
- Trước khi áp dụng rộng, chỉnh một trang đại diện để tôi xem trước. Chỉ thêm thư viện khi cần. Giữ nguyên chức năng, route và API khi chỉ đổi giao diện.
- Nội dung thật: không để Lorem ipsum hay chữ ai cũng viết được; dữ liệu giả phải ghi rõ.
- Hiệu năng cho phần nặng (3D, video, ảnh lớn): hiện bản tĩnh trước, nạp phần nặng sau, nén tài nguyên, có phương án dự phòng khi thiết bị không hỗ trợ.

## 9. Báo cáo cuối mỗi lát
Báo đủ năm mục: đã làm gì; cách kiểm tra; kết quả thực tế (lệnh và đầu ra); giới hạn còn lại; bước tiếp theo.
Với giao diện, thêm điểm Lighthouse thật và các mục chưa đạt.

## 10. Checklist trước khi triển khai
- [ ] Nội dung, giao diện, điều hướng đúng đặc tả; các luồng chính chạy từ đầu đến cuối.
- [ ] Dữ liệu lưu bền vững, tải lại vẫn đúng; đã thử dữ liệu sai, trống, trùng, yêu cầu thất bại.
- [ ] Quyền kiểm tra bằng gọi trực tiếp backend (Swagger/Postman).
- [ ] Mật khẩu băm đúng cách; không có bí mật trong Git; CORS đúng địa chỉ.
- [ ] Dùng được trên điện thoại và bằng bàn phím; thử nhiều thiết bị và trình duyệt.
- [ ] Đủ 8 điểm giao diện ở mục 8; không còn font hay màu mặc định.
- [ ] Tốc độ đo bằng Lighthouse; ảnh tối ưu; không có thư viện thừa.
- [ ] SEO cơ bản; có analytics hoặc cách đo mục tiêu của website.
- [ ] Phần AI có số đo trên tập test, xử lý đầu vào rỗng/quá dài, giới hạn thời gian phản hồi.
- [ ] Có test nghiệp vụ; README có hướng dẫn chạy, cấu hình và biến môi trường mẫu.
- [ ] Có sao lưu, giới hạn quyền truy cập, theo dõi lỗi và cách quay về bản trước.

## 11. Không được làm
- Không đổi công nghệ, xóa dữ liệu thật hoặc đăng ký dịch vụ trả phí khi chưa được tôi cho phép.
- Không sửa hoặc xóa code ngoài phạm vi yêu cầu; không sửa nhiều phần cùng lúc.
- Không dán code vào mà không giải thích; không chồng bản vá khi chưa hiểu nguyên nhân.
- Không chỉ kiểm tra trường hợp thành công; không tin giao diện đẹp là xong.
- Không đưa bí mật vào mã nguồn hay log.

## 12. Dự án (điền cho từng repo)
- Tên và mục tiêu một câu: [...]
- Người dùng chính và điều website cần đem lại (đo bằng gì): [...]
- Hướng thiết kế, cặp font, bảng màu: [...]
- Stack khác với mặc định (nếu có): [...]
- Lệnh chạy: backend [...] / frontend [...] / AI service [...] / test [...]

## 13. Trạng thái hiện tại
[Cập nhật cuối mỗi buổi: chức năng xong, lỗi còn lại, bước tiếp theo]
