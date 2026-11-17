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

Repo này là **bộ quy tắc gốc**. Mỗi dự án là một repo riêng, gắn repo này làm submodule `_skill/` ở một phiên bản (tag), và chỉ lưu ngữ cảnh, tài liệu của dự án. Chi tiết ở Mục 4.1 của `CLAUDE.md`.

**Khởi tạo một dự án** (Claude làm khi BA nhắn "Khởi tạo dự án [MÃ] …"):
1. Tạo repo dự án từ `templates/project/`, điền thông tin vào `CLAUDE.md`, `GEMINI.md` của dự án.
2. `git submodule add https://github.com/vietcuong91hn/ba-skill _skill`, rồi checkout tag hiện hành.
3. Đăng ký repo với Orca và tạo worktree `<mã>-coord` (Claude) và `<mã>-review` (Gemini/Antigravity); mỗi worktree chạy `git submodule update --init`.
4. Khởi chạy Antigravity ở worktree `<mã>-review` với lời nhắn mở đầu **bắt buộc** yêu cầu đọc `GEMINI.md` của dự án **và** `_skill/GEMINI.md` (Antigravity không tự nạp file qua dòng `@_skill/GEMINI.md`).

**Làm việc trong repo này** (sửa bộ quy tắc):
1. Mở kho trong Orca, bật orchestration. Claude Code chạy ở worktree điều phối (nhánh `feature/coord-claude`). Gemini chạy bằng Antigravity ở worktree riêng (nhánh `feature/review-gemini`), tạo bằng:
   `orca worktree create --name review-gemini --branch feature/review-gemini --base-branch feature/coord-claude --agent antigravity`
   Lời nhắn đầu tiên yêu cầu agent đọc `GEMINI.md`.
2. Chạy **Bước 0** (đồng bộ danh mục công việc) trước khi bắt đầu dự án.

## Chuyển máy

Lịch sử chat và cấu hình Orca chỉ nằm trên máy cũ; tài liệu, quyết định, trạng thái công việc nằm trong các repo trên GitHub. **Cuối mỗi buổi làm việc, push mọi nhánh.** Danh sách dự án và worktree ở `_shared/projects.md`.

**Trên máy mới:**
1. Cài Git, GitHub CLI, Orca, Claude Code, Antigravity CLI. Đăng nhập: `gh auth login`, Claude, Antigravity (tài khoản Google).
2. Lấy bộ quy tắc về (đặt ngoài OneDrive) và mở trong Orca:
   ```
   git clone -b feature/coord-claude https://github.com/vietcuong91hn/ba-skill C:\Users\<tên>\repos\ba-skill
   orca repo add --path C:\Users\<tên>\repos\ba-skill
   ```
   (Sau khi merge PR vào `main` thì bỏ `-b feature/coord-claude`.)
3. Mở Claude Code trong repo `ba-skill` và nhắn: **`Cài đặt worktree cho máy mới`**. Claude kiểm tra công cụ, liệt kê dự án và worktree, **hỏi xác nhận** rồi mới clone, tạo worktree và khởi chạy agent (Mục 4.2 của `CLAUDE.md`).

Không mở cùng một repo trên hai máy cùng lúc; trao đổi giữa các máy qua GitHub, không qua OneDrive.

Danh mục công việc G-01 … G-70 theo SDLC nằm ở Mục 6 của mỗi file, đã thống nhất ở Bước 0 ngày 17/11/2026 (Claude làm 49 việc, Gemini làm 21 việc).
