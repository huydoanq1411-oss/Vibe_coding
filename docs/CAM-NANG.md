# Cẩm nang Vibe Code Web cho Full Stack AI Engineer

HTML → CSS → JavaScript → SQL → Java Core → Spring Boot → React, cộng với Python/AI (Machine Learning, Hugging Face) và bảo mật.

## 1. Vibe code trong lộ trình của bạn

Vibe code là dùng ngôn ngữ tự nhiên để giao việc cho AI viết, sửa và kiểm tra phần mềm. Bạn là người xác định mục tiêu, quyết định nghiệp vụ và nghiệm thu. AI là cộng sự lập trình.

Vì bạn đang học để trở thành AI Engineer Full Stack, thêm một nguyên tắc riêng: **không giao hết mà không hiểu**. Với mỗi đoạn code quan trọng, làm đủ 3 lớp:

1. AI viết code theo đặc tả.
2. AI giải thích từng dòng (dùng prompt ở mục 5.7).
3. Bạn tự sửa hoặc viết lại ít nhất một phần, rồi chạy kiểm tra.

Quy trình tổng thể: ý tưởng → yêu cầu → thiết kế → xây từng lát chức năng → kiểm tra → triển khai → bảo trì. Phát hiện vấn đề thì quay lại bước liên quan và cập nhật đặc tả.

AI có thể hiểu sai yêu cầu hoặc báo “đã xong” khi chưa kiểm tra. Luôn đòi bằng chứng: lệnh đã chạy, kết quả thực tế, và tự thử các luồng quan trọng.

Thêm một điểm cần nhớ: vibe code ra một website trông ổn chỉ mất vài phút, nhưng đó mới là mức “web $1”. Khác biệt giữa web $1 và web $10.000 không nằm ở việc trông đẹp hay xấu, mà ở **bao nhiêu công sức tư duy và kỹ thuật nằm sau nó**: nghiên cứu, mục tiêu kinh doanh, nội dung, tốc độ, SEO, bảo mật, kiểm thử, bảo trì. Quy trình trong tài liệu này (đặc tả, nghiệm thu, checklist) chính là phần giúp bạn nâng sản phẩm lên mức đó. Bảng so sánh đầy đủ ở mục 11.

## 2. Bản đồ stack theo những gì bạn đang học

| Lớp | Lựa chọn mặc định | Khi nào đổi |
| --- | --- | --- |
| Frontend | React 18 + Vite (có thể thêm Tailwind, shadcn/ui) | Trang tĩnh nhỏ: HTML/CSS/JS thuần |
| Backend&#32; | Spring Boot (Java 17) + Spring Security + JWT | Chỉ có AI/ML nhẹ: dùng thẳng FastAPI |
| Database | MySQL hoặc PostgreSQL (JPA/Hibernate; SQLAlchemy nếu ở phía Python) | Dữ liệu nhỏ, một người dùng: SQLite |
| Dịch vụ AI | Python (FastAPI) + scikit-learn / PyTorch / Hugging Face transformers | Chỉ cần gọi API mô hình có sẵn |
| API | REST, mô tả bằng OpenAPI/Swagger | — |
| Đóng gói, chạy | Docker (khi cần chạy giống nhau trên nhiều máy) | Chạy local khi mới học |

Kiến trúc điển hình có AI: React → Spring Boot (đăng nhập, nghiệp vụ, DB) → FastAPI (mô hình). Bản tối giản: React → FastAPI.

Đừng thêm thành phần chỉ vì AI đề xuất. Một backend đủ dùng thì không tách microservice.

Phân biệt bản mẫu với sản phẩm thật. Dữ liệu giả, nút chưa xử lý, đăng nhập mô phỏng, dữ liệu chỉ lưu trong trình duyệt phải được ghi rõ. Với phần AI, ghi rõ mô hình nào, dữ liệu nào, độ chính xác đo trên tập test nào. Không kết luận “mô hình tốt” từ vài ví dụ thử tay.

## 3. Workflow 7 bước

| Bước | Bạn làm | AI làm | Sản phẩm đầu ra |
| --- | --- | --- | --- |
| 1. Ý tưởng | Điền biểu mẫu mục 4.1 | Hỏi lại 3–5 câu quan trọng | Bản mô tả sản phẩm |
| 2. Phạm vi | Chốt bắt buộc / làm sau / ngoài phạm vi | Đề xuất bản đầu | Danh sách chức năng + tiêu chí nghiệm thu |
| 3. Thiết kế | Duyệt | Vẽ ERD, ma trận quyền, luồng, mô tả API, wireframe | Bộ bản vẽ |
| 4. Khung dự án | Tạo repo Git | Dựng khung backend, frontend, README | Dự án chạy được “Hello” |
| 5. Xây từng lát | Giao từng chức năng, đọc giải thích code | Code từ giao diện đến DB, chạy kiểm thử | Mỗi lát một commit |
| 6. Nghiệm thu | Tự thử thành công, sai dữ liệu, trái quyền | Viết test, báo kết quả thật | Checklist đã tích |
| 7. Triển khai, bảo trì | Duyệt cấu hình, theo dõi | Chuẩn bị build, biến môi trường, hướng dẫn | URL chạy thật + tài liệu vận hành |

Trình tự xây hợp lý: khung dự án → dữ liệu → đăng nhập và quyền → chức năng chính → chức năng AI → chức năng phụ → hoàn thiện giao diện. Đừng nhờ làm hàng chục chức năng trong một lượt rồi mới kiểm tra.

## 4. Biến ý tưởng thành yêu cầu

### 4.1. Biểu mẫu mô tả sản phẩm

Sao chép biểu mẫu này trước mỗi dự án. Ghi “chưa biết” nếu chưa rõ, AI sẽ hỏi lại.

```text
Tên website:
Giải quyết vấn đề gì:
Website này cần đem lại gì (thu lead, bán hàng, uy tín, portfolio, học tập...) và đo bằng gì:
Người dùng chính:
3 việc quan trọng nhất họ cần làm:
Vai trò và quyền (ví dụ: khách, người dùng, admin):
Các trang cần có:
Nội dung (chữ, ảnh, video) đã có hay cần viết/chụp:
Yêu cầu về tốc độ, SEO, bảo mật (nếu có):
Dữ liệu cần lưu:
Quy tắc nghiệp vụ bắt buộc:
Chức năng AI (nếu có): đầu vào / đầu ra / mô hình / cách đo chất lượng:
Phong cách giao diện, màu, font, ngôn ngữ (Việt / Nhật / Anh):
Mẫu tham khảo và điểm tôi thích ở từng mẫu:
Thiết bị ưu tiên:
Stack tôi muốn dùng hoặc mã nguồn hiện có:
Ngân sách vận hành và thời hạn:
Chưa cần trong bản đầu:
Điều kiện để tôi chấp nhận sản phẩm:
```

Ví dụ điền nhanh cho một sản phẩm thuộc phạm vi bạn đã làm — web đánh giá độ mạnh mật khẩu:

```text
Tên website: PassCheck
Giải quyết vấn đề: người dùng không biết mật khẩu của mình yếu hay mạnh
Người dùng chính: sinh viên, người dùng phổ thông
3 việc chính: nhập mật khẩu và xem điểm; xem giải thích vì sao yếu; sinh mật khẩu mạnh
Vai trò: khách (không cần đăng nhập)
Quy tắc bắt buộc: không gửi mật khẩu thô lên máy chủ khi không cần; không ghi mật khẩu vào log
Thang điểm: 0–40 Yếu, 41–70 Trung bình, 71–100 Mạnh
Chưa cần: lưu lịch sử, tài khoản người dùng
```

### 4.2. Quy tắc hỏi lại

AI cần hỏi khi câu trả lời ảnh hưởng lớn đến mục tiêu, dữ liệu, quyền, chi phí, tích hợp hoặc kiến trúc. Hỏi theo nhóm 3–5 câu, giải thích ngắn vì sao cần biết và đưa lựa chọn dễ hiểu. Chi tiết nhỏ thì dùng mặc định hợp lý và ghi rõ giả định. Không để AI tự đoán quy tắc tính tiền, quyền quản trị hay cách dùng dữ liệu nhạy cảm.

### 4.3. Chốt phạm vi bản đầu

Chia chức năng thành ba nhóm: **bắt buộc**, **làm sau**, **ngoài phạm vi**. Mỗi chức năng bắt buộc cần: ai dùng, điều kiện trước, đầu vào, luồng thành công, trường hợp lỗi, dữ liệu thay đổi, tiêu chí nghiệm thu.

Ví dụ tiêu chí nghiệm thu: “Người dùng đã đăng nhập đặt hàng thì tạo đúng một đơn. Bấm gửi hai lần không tạo đơn thứ hai. Người chưa đăng nhập gọi trực tiếp API bị từ chối với mã 401.”

Ví dụ tiêu chí cho chức năng AI: “Mô hình phân loại cảm xúc đạt tối thiểu X% accuracy trên tập test cố định; có xử lý văn bản rỗng và quá dài; thời gian phản hồi dưới Y giây trên máy chạy thật.”

### 4.4. Bản vẽ trước khi viết nhiều code

| Tài liệu | Nội dung cần chốt |
| --- | --- |
| Nghiên cứu người dùng, đối thủ và nội dung | Khách hàng là ai, đối thủ làm gì, hành trình người dùng, thông điệp chính, ảnh và video cần có |
| Danh sách trang và điều hướng | Có trang nào, đi từ đâu sang đâu |
| Ma trận quyền | Vai trò nào được làm gì với dữ liệu nào |
| Wireframe | Bố cục và nội dung từng màn hình |
| Luồng nghiệp vụ | Các bước, nhánh lỗi, điều kiện |
| ERD | Bảng, quan hệ, khóa ngoại, ràng buộc |
| Mô tả API | Đường dẫn, phương thức, đầu vào, đầu ra, mã lỗi, quyền |
| Mô tả mô hình AI | Dữ liệu, tiền xử lý, mô hình, chỉ số đánh giá, giới hạn |

Kết thúc bước này phải có một bản đặc tả làm nguồn thống nhất. Mọi thay đổi yêu cầu cập nhật vào đó trước khi sửa code.

## 5. Bộ prompt

### 5.1. Prompt tổng để bắt đầu dự án

```text
Bạn là cộng sự xây website cùng tôi: phân tích, thiết kế, lập trình,
kiểm tra, triển khai. Tôi là sinh viên CNTT đang học Full Stack
(Java Core, Spring Boot, React) và AI (Python, ML, Hugging Face).

Yêu cầu của tôi:
[DÁN BẢN MÔ TẢ SẢN PHẨM]

Quy tắc làm việc:
1. Đọc yêu cầu, tài liệu và mã nguồn hiện có trước khi hành động.
2. Chưa rõ điều ảnh hưởng lớn thì hỏi lại theo nhóm nhỏ, đề xuất lựa chọn.
   Chi tiết nhỏ thì dùng mặc định hợp lý và ghi rõ giả định.
3. Trước khi code rộng: lập đặc tả, danh sách trang, ma trận quyền,
   ERD, mô tả API và bản xem trước giao diện chính.
4. Chia việc thành các lát nhỏ, mỗi lát chạy và nghiệm thu độc lập.
5. Kiểm tra quyền ở backend. Giữ bí mật (khóa, mật khẩu DB, JWT secret)
   ngoài mã nguồn, dùng biến môi trường và file .env.example.
6. Ghi rõ phần nào đang dùng dữ liệu giả hoặc chưa làm.
7. Sau mỗi bước xong, tóm tắt chi tiết bước vừa làm: việc đã làm, file đổi
   và mục đích, lệnh và kết quả thật, quyết định và lý do, điều chưa làm.
   Sau mỗi lát báo: đã làm gì, cách kiểm tra, kết quả thực tế,
   giới hạn còn lại, bước tiếp theo.
8. Giữ README, đặc tả và lịch sử Git luôn cập nhật.
9. Với code quan trọng, giải thích từng dòng để tôi học được.
10. Việc đã rõ thì cứ làm tiếp; chỉ dừng hỏi khi thiếu quyết định
    thực sự cần thiết.

Hãy bắt đầu bằng việc nêu yêu cầu còn thiếu và đề xuất phạm vi bản đầu.
Chưa triển khai toàn bộ khi nghiệp vụ chính còn mơ hồ.
```

### 5.2. Prompt giao một chức năng backend (Spring Boot)

```text
Triển khai chức năng: [TÊN] cho backend Spring Boot (Java 17).
Người dùng và quyền: [...].
Luồng sử dụng: [...].
Quy tắc nghiệp vụ: [...].
Endpoint cần có (phương thức, đường dẫn, request, response, mã lỗi): [...].
Bảng/entity liên quan: [...].
Tiêu chí nghiệm thu: [...].

Tuân theo cấu trúc hiện có (controller → service → repository → entity/DTO).
Kiểm tra dữ liệu đầu vào, trả lỗi có cấu trúc rõ ràng, kiểm tra quyền
bằng Spring Security. Không để lộ entity thô ra API nếu có thông tin nhạy cảm.
Viết test cho luồng thành công, sai dữ liệu, trái quyền, thao tác trùng.
Chạy test và báo kết quả thật. Phân biệt rõ đã kiểm tra và chưa kiểm tra được.
```

### 5.3. Prompt giao một chức năng frontend (React)

```text
Triển khai trang/component: [TÊN] bằng React 18 + Vite.
Luồng người dùng: [...].
API sẽ gọi: [mô tả endpoint].
Các trạng thái bắt buộc: đang tải, rỗng, lỗi, thành công, dữ liệu dài.
Kiểm tra biểu mẫu phía client (không thay thế kiểm tra ở backend).
Lưu token đăng nhập theo cách an toàn đã thống nhất, xử lý hết hạn đăng nhập.
Responsive cho điện thoại và dùng được bằng bàn phím.

Tuân theo phong cách và cấu trúc thư mục hiện có.
Kiểm tra lại trên máy tính và điện thoại, báo kết quả thực tế.
```

### 5.4. Prompt dịch vụ AI (Python / Hugging Face)

```text
Xây dịch vụ AI bằng Python (FastAPI) cho chức năng: [VÍ DỤ: phân loại cảm xúc].
Đầu vào/đầu ra: [...].
Mô hình: [mô hình Hugging Face có sẵn / fine-tune / scikit-learn].
Dữ liệu: [nguồn, kích thước, cách chia train/val/test].
Chỉ số đánh giá: [accuracy, F1, ...].

Yêu cầu:
- Tải mô hình một lần khi khởi động, không tải lại mỗi request.
- Kiểm tra đầu vào (rỗng, quá dài, sai kiểu), giới hạn kích thước.
- Endpoint /health và /predict, mô tả bằng OpenAPI.
- Tách tập test, không dùng dữ liệu test để chọn tham số.
- Báo chỉ số thật trên tập test và các trường hợp mô hình sai.
- Ghi rõ giới hạn của mô hình, không khẳng định vượt quá bằng chứng.
- Nếu gọi từ Spring Boot hoặc React, mô tả CORS/URL gọi và xử lý timeout.
```

### 5.5. Prompt chỉnh và nâng cấp giao diện

```text
Đọc mã nguồn và nâng cấp giao diện trang [TÊN TRANG].
Hiện tại: [...].
Tôi muốn: [...] (nêu thuộc tính quan sát được: số cột, khoảng cách, màu, cỡ chữ).
Mẫu tham khảo và điều tôi thích ở mẫu: [bố cục / màu / chuyển động].
Hướng thiết kế (một hướng duy nhất, ví dụ editorial, dark-luxury, brutalist): [...].
Cặp font (một font display + một font body, không dùng Inter/Roboto): [...].
Bảng màu 3-5 màu (mã hex), vai trò từng màu: [...].
Công nghệ hiện có: [React, Tailwind, ...].
Chức năng, route, API cần giữ nguyên: [...].

Đề xuất một hệ thiết kế thống nhất (màu, font, bo góc, khoảng cách),
chỉnh một trang đại diện để tôi xem trước rồi mới áp dụng rộng.
Chỉ thêm thư viện khi cần. Animation nhẹ, hỗ trợ reduced motion.
Kiểm tra mobile, bàn phím, nội dung dài, tràn ngang.
Thiết kế bố cục riêng cho điện thoại, không chỉ thu nhỏ bản máy tính.
```

Nói “làm đẹp, chuyên nghiệp” là quá mơ hồ. Hãy nêu cụ thể: “thẻ sản phẩm 4 cột trên máy tính, giữ màu hiện tại, tăng khoảng cách tiêu đề và danh sách”.

### 5.6. Prompt sửa lỗi bằng bằng chứng

```text
Thao tác gây lỗi: [...].
Kết quả mong muốn: [...].
Kết quả thực tế: [...].
Thông báo lỗi / stack trace / log (đã xóa bí mật): [...].
Môi trường: [Java 17, Spring Boot x.x, Node x, trình duyệt, hệ điều hành].

Tái hiện hoặc xác định nguyên nhân từ bằng chứng, sửa nguyên nhân gốc,
kiểm tra lại ca lỗi và các hành vi liên quan.
Không chỉ che thông báo lỗi để coi là đã sửa.
```

Nếu AI sửa nhiều lần vẫn không tiến triển: yêu cầu dừng sửa lan rộng, tóm tắt bằng chứng, nêu giả thuyết, chọn một phép thử nhỏ để phân biệt nguyên nhân. Không chồng thêm bản vá chưa hiểu.

### 5.7. Prompt học: giải thích từng dòng và ra đề ôn

```text
Giải thích đoạn code sau cho người đang học, theo trình tự:
1. Phân tích vấn đề: code này giải quyết việc gì.
2. Lý thuyết nền cần biết (khái niệm, annotation, hàm, thư viện).
3. Giải thích từng dòng, đánh số dòng, nói rõ vì sao viết như vậy.
4. Các lỗi thường gặp và cách nhận biết.
5. 5 câu hỏi ôn tập kèm đáp án.
Trình bày có tiêu đề rõ ràng để tôi chép vào vở.

[DÁN CODE]
```

### 5.8. AGENTS.md

`AGENTS.md` ở thư mục gốc repo là bản quy tắc hoàn chỉnh dùng cho mọi dự án. Tạo thêm `CLAUDE.md` (một dòng `@AGENTS.md`) cho Claude Code và `.github/copilot-instructions.md` cho GitHub Copilot. Với mỗi dự án chỉ điền mục 12 và 13 của `AGENTS.md`.

## 6. Công cụ hỗ trợ

Kiểm tra giá, hạn mức, giấy phép và khả năng xuất mã trên trang chính thức trước khi dùng cho dự án thật. Không cần dùng tất cả công cụ.

### 6.1. Công cụ lập trình và kiểm tra

| Công cụ | Vai trò | Cách áp dụng |
| --- | --- | --- |
| VS Code + GitHub Copilot (gói Student) | Soạn code, gợi ý, chat trong editor | Dùng cho sửa nhỏ, giải thích code, viết test |
| Trợ lý AI đọc được mã nguồn (Claude, Copilot Chat, ...) | Làm cộng sự theo prompt ở mục 5 | Giao từng lát chức năng, yêu cầu báo kết quả thật |
| Git + GitHub | Lịch sử, quay lại phiên bản, nộp đồ án | Mỗi lát chạy được là một commit |
| Swagger UI / Postman | Thử API trực tiếp, kiểm tra quyền không qua giao diện | Gọi thẳng backend với token đúng, sai, không có |
| MySQL Workbench / pgAdmin | Xem dữ liệu thật sau mỗi thao tác | Xác nhận bản ghi được lưu đúng, không bị trùng |
| Hugging Face (Hub, Datasets, Spaces) | Mô hình và dữ liệu có sẵn, demo mô hình | Chọn mô hình, đọc model card, thử nhanh trước khi tích hợp |
| Docker | Chạy giống nhau trên nhiều máy | Dùng khi cần đóng gói backend, DB, AI service |

### 6.2. Công cụ giao diện

| Công cụ | Vai trò | Cách áp dụng |
| --- | --- | --- |
| [v0](https://v0.app/) | Dựng và chỉnh giao diện bằng yêu cầu hoặc hình tham khảo | Thử 2–3 hướng, chọn một hướng rồi tích hợp |
| [shadcn/ui](https://ui.shadcn.com/) | Component nền tảng, tùy chỉnh được | Biểu mẫu, nút, bảng, dialog trong React |
| [21st.dev](https://21st.dev/) | Component React, template, prompt tích hợp | Tìm hero, card, navbar |
| [Magic UI](https://magicui.design/) | Component và hiệu ứng động | Điểm nhấn cho chữ, nền, section (React/Tailwind) |
| [Aceternity UI](https://ui.aceternity.com/components) | Hero, card, nền chuyển động | Khu vực cần nổi bật; thử hiệu năng trên điện thoại |
| [Uiverse](https://uiverse.io/) | UI nhỏ bằng HTML/CSS | Nút, input, loader cho trang HTML/CSS thuần |
| [Motion](https://motion.dev/) | Thư viện animation cho React, JS | Chuyển động menu, bố cục, cuộn |
| [Mobbin](https://mobbin.com/) | Tham khảo luồng màn hình của sản phẩm thật | Học cách tổ chức đăng nhập, điều hướng; không phải kho prompt |
| [MotionSites](https://motionsites.ai/) | Kho prompt thiết kế website và section | Chọn mẫu, lấy prompt, sửa theo nội dung dự án |
| [Framer Templates](https://www.framer.com/marketplace/templates/) | Mẫu website theo ngành | Tham khảo bố cục; không mặc định xuất được mã React |

Prompt từ kho mẫu chỉ định hướng giao diện. Backend, phân quyền, dữ liệu và triển khai vẫn cần đặc tả riêng. Nếu dự án dùng HTML/CSS thuần, yêu cầu AI chuyển ý tưởng sang stack hiện tại, đừng tự thêm React chỉ vì mẫu dùng React.

### 6.3. Cách lấy và chỉnh prompt có sẵn

1. Chọn mẫu phù hợp loại website và người dùng.
2. Xác định phần muốn học từ mẫu: bố cục, kiểu chữ, màu hay chuyển động.
3. Lấy prompt hoặc mã trong phạm vi tài khoản và giấy phép.
4. Thay tên thương hiệu, nội dung, màu, menu và nút kêu gọi hành động.
5. Thêm stack hiện có, yêu cầu mobile và chức năng cần giữ.
6. Tích hợp một section trước, kiểm tra rồi mới mở rộng.

Nếu AI không đọc được đường dẫn, gửi ảnh hoặc dán nội dung. Ảnh tĩnh không thể hiện animation, cần mô tả thêm chuyển động mong muốn.

### 6.4. Prompt biến mẫu tham khảo thành prompt của bạn

```text
Giúp tôi tạo prompt triển khai giao diện, chưa viết code ở lượt này.
Website của tôi: [mục tiêu, người dùng, trang cần có].
Stack hiện có: [React + Vite, Tailwind, ...].
Mẫu tham khảo: [link / ảnh / prompt gốc].
Tôi thích: [bố cục, màu, kiểu chữ, hiệu ứng cụ thể].
Tôi muốn thay đổi: [...].
Nội dung và nút kêu gọi thực tế: [...].
Chức năng cần giữ: [...].

Phân tích bố cục, phân cấp chữ, màu, khoảng cách, component, chuyển động
và cách hiển thị trên điện thoại. Phân biệt điều quan sát được với phần suy đoán.
Thiếu thông tin quan trọng thì hỏi lại trước khi chốt.
Viết prompt để AI lập trình tích hợp vào dự án, gồm responsive, bàn phím,
trạng thái lỗi/trống/đang tải, reduced motion và tiêu chí nghiệm thu.
```

### 6.5. Phối hợp theo nhu cầu

| Nhu cầu | Cách phối hợp đề xuất |
| --- | --- |
| Landing page, portfolio | MotionSites hoặc Framer Templates chọn hướng → AI chỉnh prompt → 21st.dev hoặc Magic UI cho section |
| Web có đăng nhập, quản trị, thương mại điện tử (React + Spring Boot) | Mobbin tham khảo luồng → shadcn/ui → Swagger để thử API → Motion cho tương tác nhẹ |
| Web có chức năng AI (React + FastAPI/Spring Boot) | Hugging Face chọn mô hình → AI viết dịch vụ → v0 hoặc shadcn/ui dựng giao diện kết quả |
| Trang HTML/CSS/JS thuần (tài liệu, khóa học) | Mẫu tham khảo → AI chuyển sang HTML/CSS thuần → Uiverse cho chi tiết nhỏ |
| Thử nhanh giao diện | AI viết 2–3 hướng → v0 dựng bản mẫu → chọn một hướng để tích hợp |

Thứ tự nâng cấp giao diện: nội dung và điều hướng → font, màu, khoảng cách → component đồng nhất → mobile và bàn phím → chuyển động → kiểm tra hiệu năng và nghiệp vụ. Khi ghép nhiều nguồn, giữ một hệ màu, kiểu chữ và bo góc chung. Nếu máy cấu hình vừa phải, thử hiệu ứng trên máy thật và giảm nền video, hạt hoặc 3D khi bị chậm.

### 6.6. Công cụ cho web 3D (khi dự án có phần 3D)

| Việc | Công cụ | Ghi chú |
| --- | --- | --- |
| Dựng 3D trên web | [Three.js](https://threejs.org/) | Nền tảng chuẩn, nên học trước |
| Dùng trong React | [React Three Fiber](https://r3f.docs.pmnd.rs/) + drei | Viết cảnh 3D như component |
| Vật lý | [Rapier](https://rapier.rs/) (`@react-three/rapier`), cannon-es | Bóng nảy, va chạm thật |
| Animation | [GSAP](https://gsap.com/), Motion | Timeline cho camera, UI, đối tượng |
| Mô hình 3D | Blender (xuất `.glb`), Sketchfab | Kiểm tra giấy phép trước khi dùng |
| Nén tài nguyên | Draco / meshopt (mô hình), KTX2 / WebP (texture) | Giữ trang tải nhanh |
| Dựng nhanh bản thử | [Spline](https://spline.design/) | Thử ý tưởng trước khi code |

Quy tắc hiệu năng cho 3D: hiện ảnh tĩnh của cảnh trước, nạp thư viện 3D và mô hình sau khi trang đã hiển thị; giới hạn `devicePixelRatio` tối đa 2; dừng vẽ khi tab bị ẩn; luôn có phương án dự phòng khi không có WebGL hoặc khi bật reduced motion.

## 7. Nghiệm thu và đưa lên mạng

### 7.1. Checklist trước khi triển khai

- [ ] Nội dung, giao diện và điều hướng đúng đặc tả.
- [ ] Các luồng chính chạy từ đầu đến cuối.
- [ ] Dữ liệu lưu bền vững, tải lại vẫn đúng.
- [ ] Đã thử dữ liệu sai, trống, trùng và yêu cầu thất bại.
- [ ] Kiểm tra quyền bằng gọi trực tiếp backend (Swagger/Postman), không chỉ nhìn nút ẩn hiện.
- [ ] Mật khẩu được băm bằng thuật toán chậm có salt (ví dụ bcrypt), không lưu mật khẩu thô, không ghi mật khẩu vào log.
- [ ] Khóa bí mật (JWT secret, mật khẩu DB, khóa API) nằm trong biến môi trường, không có trong Git.
- [ ] CORS chỉ cho phép đúng địa chỉ frontend.
- [ ] Giao diện dùng được trên điện thoại và bằng bàn phím.
- [ ] Đã thử trên nhiều thiết bị và trình duyệt, không vỡ layout.
- [ ] Nội dung thật, không còn Lorem ipsum hay chữ chung chung; ảnh không vỡ, không bị kéo giãn.
- [ ] Tốc độ: ảnh đã tối ưu, lazy loading, không có plugin/thư viện thừa; đo bằng Core Web Vitals (Lighthouse), cân nhắc CDN.
- [ ] SEO kỹ thuật cơ bản: title, meta description, cấu trúc URL rõ ràng, sitemap, schema khi phù hợp.
- [ ] Một hướng thiết kế, cặp font và bảng màu 3-5 màu được áp dụng nhất quán, không còn font hay màu mặc định.
- [ ] Trang tải dưới 2 giây trên mạng trung bình (đo Lighthouse ở chế độ điện thoại).
- [ ] Tương phản đạt WCAG AA, HTML ngữ nghĩa, điều hướng hoàn toàn bằng bàn phím được.
- [ ] Chuyển động có chủ đích, giảm hoặc tắt khi người dùng bật reduced motion.
- [ ] Bố cục điện thoại được thiết kế riêng, không chỉ thu nhỏ bản máy tính.
- [ ] Có analytics hoặc cách đo để biết website có đạt mục tiêu ở biểu mẫu 4.1 không.
- [ ] Có sao lưu định kỳ, giới hạn quyền truy cập, và có người/quy trình theo dõi sau khi chạy thật.
- [ ] Phần AI: có số đo trên tập test, xử lý đầu vào rỗng/quá dài, có giới hạn thời gian phản hồi.
- [ ] Có test cho nghiệp vụ quan trọng, không chỉ kiểm tra build.
- [ ] README có hướng dẫn chạy, cấu hình và biến môi trường mẫu.

### 7.2. Triển khai theo loại ứng dụng

Website tĩnh chỉ cần nơi phục vụ tệp. Ứng dụng có backend cần môi trường chạy tương thích Java hoặc Python. Database và tệp tải lên cần nơi lưu bền vững. Dịch vụ AI có thể cần nhiều bộ nhớ hơn, và thời gian khởi động lâu vì phải tải mô hình. Đừng chọn hosting chỉ vì hiển thị được trang chủ. Khi chọn dịch vụ cụ thể, yêu cầu AI kiểm tra tài liệu chính thức hiện hành.

Quy trình: chọn phiên bản mã nguồn → cấu hình môi trường → tạo database/lưu trữ → build → migration nếu có → khởi động → HTTPS/tên miền → kiểm tra trực tiếp trên địa chỉ triển khai.

```text
Chuẩn bị triển khai dự án hiện có.
Đọc cấu hình và xác định môi trường chạy phù hợp cho từng phần
(React, Spring Boot, FastAPI, database). Kiểm tra tài liệu chính thức hiện hành
khi chọn dịch vụ hoặc lệnh triển khai.

Chuẩn bị build, biến môi trường mẫu, migration, lệnh khởi động, HTTPS, log,
sao lưu và phương án quay về phiên bản trước.
Không đưa bí mật vào mã nguồn, không xóa dữ liệu thật để sửa lỗi,
không tự đăng ký dịch vụ trả phí ngoài phạm vi tôi cho phép.

Sau triển khai, kiểm tra trên địa chỉ thật với các luồng chính.
Báo rõ URL, phiên bản, kết quả đã kiểm tra và phần còn thiếu.
```

Sau khi chạy thật: theo dõi lỗi, thử khôi phục từ bản sao lưu, cập nhật phụ thuộc, xử lý phản hồi. Thêm chức năng thì quay lại quy trình yêu cầu → thiết kế → xây → kiểm tra → cập nhật.

## 8. Lỗi thường gặp khi vibe code

| Lỗi | Cách khắc phục |
| --- | --- |
| Chỉ nói “làm đẹp, chuyên nghiệp” | Đưa mẫu và yêu cầu quan sát được |
| Đổi yêu cầu liên tục mà không ghi lại | Cập nhật đặc tả trước khi sửa code |
| Tin giao diện đẹp là xong | Thử nghiệp vụ, quyền và dữ liệu thật |
| Để AI đoán quy tắc quan trọng | Hỏi lại, chốt bằng ví dụ cụ thể |
| Sửa nhiều phần cùng lúc | Chia nhỏ, kiểm tra, commit |
| Chỉ thử trường hợp thành công | Thử sai dữ liệu, trái quyền, thao tác trùng |
| Tin “đã chạy tốt” khi không có bằng chứng | Đòi lệnh đã chạy và kết quả thật |
| Dán code AI vào mà không đọc | Dùng prompt 5.7 và tự viết lại một phần |
| Lỗi Spring Security / JWT: filter sai thứ tự, import sai (ví dụ HttpMethod), quên cho phép đường dẫn công khai | Dán stack trace đầy đủ, hỏi nguyên nhân gốc, thử endpoint bằng Postman |
| Frontend gọi API bị chặn CORS | Cấu hình CORS ở backend đúng địa chỉ frontend, không mở toàn bộ |
| Chỉ lưu dữ liệu trong bộ nhớ hoặc trình duyệt | Chọn nơi lưu theo nhu cầu thật |
| Mô hình AI tốt trên vài ví dụ nhưng sai trên dữ liệu thật | Đánh giá trên tập test cố định, xem ca sai |
| Tải lại mô hình ở mỗi request | Tải một lần lúc khởi động dịch vụ |
| Đưa lên mạng rồi bỏ mặc | Theo dõi, sao lưu, cập nhật |
| Dùng nguyên template, chỉ đổi màu và logo | Xây hệ thiết kế riêng (màu, font, khoảng cách, bo góc) theo thương hiệu và mục tiêu |
| Để Lorem ipsum, ảnh stock chung chung, chữ ai cũng viết được | Viết nội dung có chiến lược, dùng ảnh/video đúng ngữ cảnh |
| Bỏ qua tốc độ và SEO vì “chạy được là được” | Đo Core Web Vitals, nén ảnh, lazy loading, làm SEO kỹ thuật cơ bản |
| Nghĩ đắt là tốt, rẻ là tệ (hoặc ngược lại) | Xét theo mục tiêu: web cần đem lại gì, rồi chọn mức đầu tư tương ứng |
| Dùng Inter/Roboto và nhiều màu không theo hệ | Chọn cặp font display + body riêng và bảng 3-5 màu, khai báo thành biến |
| Gắn hiệu ứng fade-up cho mọi section | Dành chuyển động cho một khoảnh khắc chính, còn lại tiết chế; hỗ trợ reduced motion |
| Mobile chỉ là desktop thu nhỏ | Thiết kế bố cục riêng cho điện thoại, thử trên máy thật |
| Phần 3D hoặc media nặng làm trang tải chậm | Hiện ảnh tĩnh trước, nạp phần nặng sau; nén mô hình, texture, video; có phương án dự phòng khi thiết bị không hỗ trợ |
| Chức năng tải file lên không kiểm tra | Kiểm tra loại file bằng nội dung, giới hạn dung lượng, chạy bộ chuyển đổi trong môi trường cô lập, tự xóa file tạm |

## 9. Lộ trình thực hành 4 tuần

Chọn một sản phẩm nhỏ có đủ đăng nhập, dữ liệu và một chức năng AI (ví dụ PassCheck mở rộng: lưu lịch sử đánh giá theo tài khoản, hoặc web phân loại cảm xúc bình luận). Mỗi tuần kết thúc bằng một bản chạy được và một commit.

| Tuần | Mục tiêu | Sản phẩm kiểm tra được |
| --- | --- | --- |
| 1 | Điền biểu mẫu 4.1, chốt phạm vi, vẽ ERD, ma trận quyền, mô tả API, viết AGENTS.md | Thư mục docs/ và repo có khung chạy |
| 2 | Backend Spring Boot: entity, đăng nhập JWT, băm mật khẩu, 2–3 endpoint chính, test | Gọi được API bằng Postman, test chạy đạt |
| 3 | Frontend React: trang đăng nhập, trang chính, gọi API, trạng thái lỗi/trống/đang tải | Dùng được từ đầu đến cuối trên máy tính và điện thoại |
| 4 | Dịch vụ AI (FastAPI + Hugging Face), nối vào backend, nghiệm thu, triển khai, README | URL chạy thật + bảng số đo mô hình + checklist 7.1 |

Mỗi tuần, chọn một đoạn code do AI viết, dùng prompt 5.7 để hiểu từng dòng, rồi tự sửa hoặc viết lại.

## 10. Câu hỏi ôn tập

1. Vì sao “giao diện đẹp và chạy được trên máy” chưa đủ để coi là hoàn thành?
2. Liệt kê ba nhóm khi chốt phạm vi bản đầu và cho một ví dụ cho mỗi nhóm.
3. Vì sao phải kiểm tra quyền ở backend thay vì chỉ ẩn nút trên giao diện?
4. Viết một tiêu chí nghiệm thu cho chức năng đăng nhập và một cho chức năng AI.
5. Khi nào nên tách dịch vụ AI riêng bằng FastAPI, khi nào dùng thẳng một backend?
6. AI sửa lỗi ba lần vẫn không được thì bạn làm gì tiếp theo?
7. Vì sao không dùng tập test để chọn tham số mô hình?
8. Prompt lấy từ kho mẫu giao diện giải quyết được phần nào của sản phẩm, và phần nào vẫn phải tự đặc tả?
9. Kể ít nhất năm điểm khác nhau giữa web $1 và web $10.000, và cho biết bạn đang trả tiền chủ yếu cho điều gì ở web $10.000.
10. Khi nào một website dùng template giá rẻ là lựa chọn hợp lý, khi nào cần đầu tư thiết kế riêng?
11. Kể tên 8 điểm của checklist $10K ở mục 12 và cho biết điểm nào AI không thể làm thay bạn.
12. Làm thế nào để một trang có nội dung nặng (3D, video) vẫn tải dưới 2 giây và dùng được khi thiết bị không hỗ trợ?

## 11. Thước đo chất lượng: web $1 và web $10.000

Web $1 thường là template dựng sẵn. Web $10.000 là sản phẩm được thiết kế riêng cho một mục tiêu kinh doanh cụ thể. Dùng bảng này để tự chấm sản phẩm của bạn trước khi nghiệm thu.

### 11.1. So sánh theo tiêu chí

| Tiêu chí | Web $1 | Web $10.000 |
| --- | --- | --- |
| Thiết kế | Template có sẵn, đổi màu và logo | Thiết kế riêng theo thương hiệu, có design system nhất quán |
| Mục tiêu | “Có web cho có” | Tạo ra doanh thu, thu lead, xây uy tín |
| Nghiên cứu | Không có | Nghiên cứu khách hàng, đối thủ, hành trình người dùng |
| Nội dung | Lorem ipsum, hoặc chữ chung chung | Copywriting có chiến lược, ảnh và video chuyên nghiệp |
| Tốc độ | Chậm, ảnh nặng, plugin thừa | Tối ưu Core Web Vitals, CDN, lazy loading |
| Responsive | Thường vỡ layout trên một số thiết bị | Test kỹ trên nhiều thiết bị và trình duyệt |
| SEO | Gần như không có | SEO kỹ thuật, cấu trúc URL, schema, sitemap |
| Bảo mật | Mặc định, dễ bị hack | HTTPS, backup, giới hạn quyền, giám sát |
| Code | Rối, khó mở rộng | Sạch, có cấu trúc, dễ bảo trì và mở rộng |
| Tính năng | Cơ bản | Tích hợp CRM, thanh toán, analytics, A/B test |
| Hỗ trợ | Không có | Bảo hành, bảo trì, đào tạo sử dụng |

### 11.2. Dấu hiệu nhận biết bằng mắt thường

Web rẻ tiền thường:

- Tải lâu, ảnh bị vỡ hoặc kéo giãn.
- Font và khoảng cách lộn xộn, nhiều kiểu chữ khác nhau.
- Nút bấm không rõ, không biết nên làm gì tiếp theo.
- Ảnh stock chung chung, nội dung nghe như ai cũng viết được.
- Giao diện mobile khó dùng.

Web đắt tiền thường:

- Có một “câu chuyện” rõ ràng ngay từ màn hình đầu tiên.
- Từng chi tiết nhỏ (hover, chuyển trang, khoảng trắng) đều có chủ đích.
- Luồng người dùng mượt: biết mình cần bấm gì, ở đâu.
- Mượt và nhanh ở mọi thiết bị.
- Nhìn là nhận ra thương hiệu nào.

### 11.3. Bạn đang trả tiền cho cái gì?

Giá $10.000 chủ yếu là **thời gian của nhiều người giỏi**: strategist, designer, developer, copywriter, QA, project manager. Phần code chỉ là một phần nhỏ trong đó.

Khi vibe code, AI đảm nhận phần lớn việc viết code, nhưng các vai trò còn lại vẫn cần có người làm. Bạn là người giữ các vai trò chiến lược, nội dung, kiểm thử và quản lý dự án:

| Vai trò trong agency | Tương ứng trong quy trình của bạn |
| --- | --- |
| Strategist | Biểu mẫu 4.1, chốt phạm vi (4.3), nghiên cứu người dùng và đối thủ |
| Designer | Hệ thiết kế thống nhất, mẫu tham khảo (mục 6), prompt 5.5 |
| Developer | AI viết code theo prompt 5.2–5.4, bạn đọc và tự sửa (5.7) |
| Copywriter | Tự viết hoặc duyệt kỹ nội dung do AI tạo, không để chữ chung chung |
| QA | Nghiệm thu (bước 6), checklist 7.1, tự thử sai dữ liệu và trái quyền |
| Project manager | Workflow 7 bước, AGENTS.md, đặc tả, commit từng lát |

### 11.4. Lưu ý quan trọng

- **Đắt không đồng nghĩa với tốt.** Có agency tính $10.000 nhưng giao một template đổi tên.
- **Rẻ cũng chưa chắc tệ.** Với một quán nhỏ hay portfolio cá nhân, template $1 kèm nội dung tốt có thể là đủ.
- Câu hỏi đúng là: **“Website này cần đem lại gì cho mình?”** Nếu một khách hàng mới đáng giá vài nghìn đô, thì web $10.000 hoàn vốn rất nhanh. Nếu chỉ cần trang giới thiệu, bỏ $10.000 là lãng phí.

### 11.5. Prompt tự chấm chất lượng sản phẩm

```text
Đọc mã nguồn và đặc tả của dự án, rồi chấm website theo 11 tiêu chí:
thiết kế, mục tiêu, nghiên cứu, nội dung, tốc độ, responsive, SEO,
bảo mật, chất lượng code, tính năng, hỗ trợ/bảo trì.

Với mỗi tiêu chí: nêu mức hiện tại (giống web template giá rẻ hay đã
chuyên nghiệp), bằng chứng cụ thể (tệp, trang, số đo Lighthouse nếu chạy
được), và việc nên làm tiếp theo theo thứ tự ưu tiên.
Mục tiêu của website: [điền từ biểu mẫu 4.1].
Phân biệt điều đã kiểm tra với điều chỉ suy đoán. Không sửa code ở lượt này.
```

## 12. Checklist 8 điểm của web $10K

Bổ sung cho bảng ở mục 11, tập trung vào những gì nhìn và cảm nhận được. Dùng khi tự chấm hoặc khi giao việc cho AI.

| # | Điểm | Việc cần làm | Áp dụng ở mục |
| --- | --- | --- | --- |
| 1 | Quan điểm thiết kế, không dùng template | Chọn một hướng (editorial, dark-luxury, brutalist...) và giữ nhất quán | 5.5, 5.8 |
| 2 | Typography có chức năng | Font display + font body, không dùng Inter/Roboto; cỡ và độ đậm tạo thứ bậc | 5.5, 5.8 |
| 3 | Hệ màu tiết chế | 3-5 màu, dùng nhất quán qua biến | 5.5, 5.8 |
| 4 | Thứ bậc có không gian thở | Cấp chính, phụ, thứ ba rõ; khoảng trắng và tương phản dẫn mắt | 7.1 |
| 5 | Hình ảnh có chủ đích | Ảnh riêng, tài nguyên tự tạo hoặc tuyển chọn kỹ, không dùng ảnh stock mặc định | 8, 11.2 |
| 6 | Chuyển động tinh tế | Một khoảnh khắc nổi bật, còn lại nhẹ; hỗ trợ reduced motion | 5.5, 7.1 |
| 7 | Mobile được thiết kế riêng | Bố cục điện thoại khác desktop, thử trên máy thật | 5.3, 7.1 |
| 8 | Phần vô hình | Tải dưới 2 giây, WCAG AA, bàn phím, HTML ngữ nghĩa, meta tag đầy đủ | 7.1, 11.1 |

Prompt chấm theo 8 điểm:

```text
Đọc mã nguồn, đặc tả và chạy Lighthouse nếu có thể, rồi chấm website theo 8 điểm:
quan điểm thiết kế, typography, hệ màu, thứ bậc, hình ảnh, chuyển động,
mobile, phần kỹ thuật vô hình.
Mỗi điểm: mức hiện tại, bằng chứng cụ thể (tệp, trang, số đo), việc nên làm tiếp.
Phân biệt điều đã kiểm tra với điều chỉ suy đoán. Không sửa code ở lượt này.
```

Tài liệu này là quy trình dùng lại. Khi bắt đầu website cụ thể, điền biểu mẫu 4.1 rồi dán vào prompt 5.1.
