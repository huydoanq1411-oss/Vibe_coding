---
name: vibe-code-web
description: Quy trình và quy tắc vibe code cho dự án web (React, Spring Boot, FastAPI, Python AI). Dùng khi lập đặc tả, xây chức năng từng lát, sửa lỗi, nâng cấp giao diện, kiểm tra hoặc triển khai website; khi người dùng nhắc vibe code, đặc tả, nghiệm thu, web chuyên nghiệp hoặc chuẩn web $10K.
---

# Vibe Code Web

Người dùng quyết định mục tiêu và nghiệm thu; bạn là cộng sự lập trình. Quy tắc đầy đủ ở `AGENTS.md`, cẩm nang ở `docs/CAM-NANG.md`.

## Quy trình
1. Đọc yêu cầu, docs/SPEC.md và mã nguồn hiện có. Chưa có đặc tả thì lập trước: danh sách trang, ma trận quyền, ERD, mô tả API, wireframe.
2. Hỏi lại theo nhóm 3-5 câu khi câu trả lời ảnh hưởng mục tiêu, dữ liệu, quyền, chi phí hoặc kiến trúc; chi tiết nhỏ thì dùng mặc định hợp lý và ghi giả định.
3. Chốt phạm vi: bắt buộc, làm sau, ngoài phạm vi. Mỗi chức năng bắt buộc có tiêu chí nghiệm thu đo được.
4. Xây từng lát: khung → dữ liệu → đăng nhập và quyền → chức năng chính → AI → phụ → hoàn thiện giao diện. Mỗi lát một commit.
5. Kiểm tra: thành công, sai dữ liệu, trái quyền, thao tác trùng. Chạy test và báo kết quả thật.
6. Báo cuối lát: đã làm gì, cách kiểm tra, kết quả, giới hạn còn lại, bước tiếp theo.

## Giao diện chuẩn web $10K (8 điểm)
Một hướng thiết kế; cặp font display + body (không Inter/Roboto); 3-5 màu; thứ bậc có khoảng trắng; hình ảnh có chủ đích; chuyển động tiết chế và hỗ trợ reduced motion; mobile thiết kế riêng; kỹ thuật vô hình (dưới 2 giây, WCAG AA, bàn phím, HTML ngữ nghĩa, meta tag).

## Giữ trung thực
Không báo "đã xong" khi chưa kiểm tra. Phân biệt điều đã kiểm tra với điều suy đoán. Giải thích từng dòng với code quan trọng để người dùng học được.

Chi tiết: prompt mẫu ở mục 5, checklist trước triển khai ở mục 7.1, lỗi thường gặp ở mục 8, thước đo chất lượng ở mục 11 và 12 của `docs/CAM-NANG.md`.
