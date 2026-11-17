<!-- owner: claude -->
# Danh mục dự án và worktree

Nguồn cho lệnh **"Cài đặt worktree cho máy mới"** (`CLAUDE.md` Mục 4.2). Claude cập nhật file này mỗi khi khởi tạo dự án, thêm/bỏ worktree, hoặc nâng phiên bản quy tắc của dự án. Không ghi đường dẫn tuyệt đối của máy: thư mục gốc được hỏi khi cài đặt.

## Dự án

| Mã | Dự án | Repo GitHub | Hiển thị | Loại | Quy tắc (`_skill/`) | Trạng thái | Khởi tạo |
|---|---|---|---|---|---|---|---|
| — | ba-skill (bộ quy tắc gốc) | `vietcuong91hn/ba-skill` | public | — | — | Đang dùng | 17/11/2026 |
| G | G-Safe | `vietcuong91hn/g-safe` | private | C — sản phẩm nội bộ | v1.0 (135cad9) | Đang chạy | 17/11/2026 |

## Worktree

| Mã | Worktree | Nhánh | Agent (Orca id) | Vai trò | Lời nhắn khởi chạy |
|---|---|---|---|---|---|
| — | `coord-claude` | `feature/coord-claude` | `claude` | Claude điều phối, sửa bộ quy tắc | (không cần) |
| — | `review-gemini` | `feature/review-gemini` | `antigravity` | Gemini review bộ quy tắc | Đọc `GEMINI.md` |
| G | `g-coord` | `feature/coord-claude` | `claude` | Claude điều phối G-Safe | `[G] Đọc task-board, decision-log, intake-log và tóm tắt trạng thái dự án; không bắt đầu việc nào.` |
| G | `g-review` | `feature/review-gemini` | `antigravity` | Gemini review G-Safe | Đọc `GEMINI.md` của dự án và toàn bộ `_skill/GEMINI.md`; xác nhận vai trò; chờ dispatch. |

## Lịch sử thay đổi

| Ngày | Thay đổi |
|---|---|
| 17/11/2026 | Tạo danh mục: ba-skill, G-Safe. |
