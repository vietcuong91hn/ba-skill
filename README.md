# ba-skill

Bộ file nhiệm vụ cho hai agent AI cùng thực hiện toàn trình công việc của một Senior BA, chạy trong [Orca](https://github.com/stablyai/orca).

| File | Agent | Vai trò |
|---|---|---|
| `CLAUDE.md` | Claude Code | Senior BA điều phối: chia việc, soạn đặc tả, giữ nhất quán `_shared/` |
| `GEMINI.md` | Gemini (chạy bằng Antigravity CLI) | Senior BA nghiên cứu & review: tra cứu, đọc tài liệu đa phương tiện, phản biện |

## Nguyên tắc chung

1. Luôn hỏi BA xác nhận trước khi làm bất kỳ việc nào (Phiếu đề xuất).
2. Mỗi việc luôn có 1 bên làm và 1 bên review.
3. Claude điều phối; bất đồng quá 1 vòng thì chuyển BA quyết.
4. Mỗi tài liệu nạp vào đều có phiếu xác nhận tiếp nhận và đầu ra cụ thể.

## Cách dùng

1. Copy `CLAUDE.md` và `GEMINI.md` vào thư mục gốc kho tài liệu dự án.
2. Mở kho trong Orca, bật orchestration. Claude Code chạy ở worktree điều phối (nhánh `feature/coord-claude`). Gemini chạy bằng Antigravity ở worktree riêng (nhánh `feature/review-gemini`), tạo bằng:
   `orca worktree create --name review-gemini --branch feature/review-gemini --base-branch feature/coord-claude --agent antigravity`
   Lời nhắn đầu tiên yêu cầu agent đọc `GEMINI.md`.
3. Chạy **Bước 0** (đồng bộ danh mục công việc) trước khi bắt đầu dự án.

Danh mục công việc G-01 … G-70 theo SDLC nằm ở Mục 6 của mỗi file, đã thống nhất ở Bước 0 ngày 17/11/2026 (Claude làm 49 việc, Gemini làm 21 việc).
