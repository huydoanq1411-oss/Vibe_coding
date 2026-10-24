# vibe-web-playbook

Bộ quy tắc và cẩm nang vibe code web cho Full Stack AI Engineer (React, Spring Boot, FastAPI, Python AI). Dùng với Claude, Cursor, GitHub Copilot, Gemini và ChatGPT/Codex, cho mọi dự án: đặc tả trước, xây từng lát, nghiệm thu bằng bằng chứng, giao diện chuẩn "web $10K".

## Cấu trúc

| Đường dẫn | Vai trò |
| --- | --- |
| `AGENTS.md` | Quy tắc bắt buộc cho AI, dùng chung cho mọi công cụ |
| `CLAUDE.md` | Một dòng `@AGENTS.md` để Claude Code đọc |
| `CURSOR.md`, `.cursor/rules/` | Hướng dẫn và rule cho Cursor |
| `.github/copilot-instructions.md` | Trỏ GitHub Copilot về `AGENTS.md` |
| `GEMINI.md` | Một dòng `@./AGENTS.md` để Gemini CLI đọc |
| `WEB-CHAT.md` | Bản ngắn để dán vào ChatGPT, Gemini (Gem), Claude Project |
| `skills/vibe-code-web/SKILL.md` | Skill cô đọng cho Claude Code |
| `.claude-plugin/` | Khai báo plugin và marketplace |
| `docs/CAM-NANG.md` | Cẩm nang đầy đủ: prompt mẫu, công cụ, checklist, thước đo |
| `EXAMPLES.md` | Ví dụ lệnh tốt và lỗi thường gặp |

## Cài đặt

**Claude Code (plugin).** Thay `TEN-GITHUB-CUA-BAN` bằng tên GitHub của bạn trong `.claude-plugin/*.json`, push repo, rồi chạy:

```text
/plugin marketplace add TEN-GITHUB-CUA-BAN/vibe-web-playbook
/plugin install vibe-web-playbook@vibe-web-playbook
```

**Mỗi dự án (mọi công cụ).** Sao chép `AGENTS.md`, `CLAUDE.md`, `.cursor/` và `.github/copilot-instructions.md` vào thư mục gốc dự án, hoặc đặt repo này làm template repository rồi bấm *Use this template*. Chỉ điền mục 12 và 13 của `AGENTS.md`.

**Cursor và Copilot.** Xem `CURSOR.md`; Copilot đọc `.github/copilot-instructions.md`.

**Gemini.** Gemini CLI đọc `GEMINI.md` ở thư mục gốc dự án; file này nhập `AGENTS.md` qua cú pháp `@./AGENTS.md`. Gemini trên web dùng bản ngắn trong `WEB-CHAT.md` dán vào Gem.

**ChatGPT và Codex.** Codex (CLI, tiện ích IDE, bản chạy trên đám mây) đọc `AGENTS.md` ở thư mục gốc repo, không cần cấu hình thêm. ChatGPT trên web không đọc repo: dán bản ngắn trong `WEB-CHAT.md` vào Custom Instructions hoặc Instructions của Project.

Cách các công cụ tìm và nạp file hướng dẫn thay đổi theo phiên bản; kiểm tra tài liệu chính thức của từng công cụ nếu file không được nhận.

## Nguyên tắc cập nhật repo
- Chỉ thêm kiến thức chung dùng được cho mọi dự án; không đưa nội dung của một dự án cụ thể vào.
- Khi AI lặp lại một lỗi, thêm một dòng cụ thể vào `AGENTS.md`; giữ file ngắn.
- Kiểm tra công cụ, giá và cú pháp cấu hình trên tài liệu chính thức trước khi dùng cho dự án thật.
