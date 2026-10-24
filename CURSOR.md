# Dùng bộ quy tắc này trong Cursor

1. Sao chép thư mục `.cursor/rules/` và file `AGENTS.md` vào thư mục gốc dự án.
2. Rule `vibe-code.mdc` có `alwaysApply: true`, nên được nạp ở mọi cuộc trò chuyện của dự án. Cursor cũng đọc `AGENTS.md` ở thư mục gốc.
3. Với dự án lớn, tách rule theo phạm vi (ví dụ `frontend.mdc`, `backend.mdc`) và gắn `globs` thay vì để tất cả `alwaysApply`.
4. Rule không bảo đảm AI tuân thủ tuyệt đối. Khi AI lặp lại một lỗi, thêm một dòng cụ thể vào `AGENTS.md` thay vì viết chung chung.
5. Kiểm tra hiệu quả bằng một task thật: AI có đọc đặc tả, làm theo lát nhỏ và báo kết quả kiểm tra thật không.
