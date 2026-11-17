<!-- owner: gemini -->
# Review D-009 — Đánh giá kiến trúc Git Submodule và Bộ template dự án

| Thông tin | Nội dung |
|---|---|
| Việc | Review D-009: Đánh giá commit `b9e9c91` (kiến trúc submodule, `templates/project/`, Mục 4.1 quản lý nhiều dự án) |
| Vai trò | Reviewer (Gemini) |
| Căn cứ xác nhận BA | Quyết định D-009 trong `_shared/decision-log.md` (BA duyệt hướng submodule, mã dự án G, mã việc = mã dự án + số thứ tự) |
| Tài liệu đối chiếu | `CLAUDE.md`, `GEMINI.md`, `README.md`, `templates/project/`, `_shared/decision-log.md` |
| Đầu ra | `reviews/D-009_review.md` (nhánh `feature/review-gemini`) |
| Kết luận chung | **ĐẠT (Khớp kiến trúc & chuẩn BABOK)** — Đề xuất 2 điểm góp ý tối ưu trải nghiệm và quản trị rủi ro submodule |

---

## 1. Kết quả kiểm tra chi tiết theo 4 nội dung Dispatch D-009

### 1.1 Tính nhất quán Mục 4.1 và quy tắc đặt mã dự án / mã việc

- **So sánh Mục 4.1 giữa CLAUDE.md và GEMINI.md**:
  + Cả hai file đều định nghĩa thống nhất kiến trúc: `ba-skill` là repo quy tắc gốc; mỗi dự án là một repo riêng gắn `ba-skill` làm git submodule tại thư mục `_skill/`, chốt phiên bản theo tag (`vX.Y`).
  + Nguyên tắc bất biến: **Không sửa `_skill/` trong repo dự án**. Mọi thay đổi quy tắc chỉ thực hiện tại `ba-skill` và nâng phiên bản dự án phải qua Phiếu đề xuất được BA đồng ý.
  + Hướng dẫn đọc file cho Gemini (dòng 66 `GEMINI.md`): Khi khởi chạy trong repo dự án, agent đọc `GEMINI.md` ở root (lấy thông tin dự án), sau đó đọc toàn bộ `_skill/GEMINI.md` (lấy toàn bộ vai trò, quy tắc, bảng phân công).
- **Quy tắc mã hóa công việc**:
  + Mã dự án do BA đặt (ví dụ `G` cho G-Safe).
  + Mã công việc dự án = `<Mã dự án>-<Số thứ tự>` (dự án `G` dùng `G-01 … G-70`; dự án `H` dùng `H-01 … H-70`, ví dụ `H-13` là việc số 13 của bảng).
  + Mã `IN-xxx` và `D-xxx` đánh số độc lập trong từng dự án; khi trao đổi liên dự án phải gắn tiền tố (ví dụ `H/IN-003`).
  + Tin nhắn từ BA bắt buộc mở đầu bằng `[<MÃ>]` (ví dụ `[G] ...`). Nếu thiếu hoặc sai mã, trợ lý phải hỏi lại BA, không tự suy đoán.
- **Đánh giá**: Quy tắc rõ ràng, triệt tiêu nguy cơ nhầm lẫn ngữ cảnh và dữ liệu giữa các dự án khác nhau.

### 1.2 Kiểm tra bộ template dự án `templates/project/`

- **CLAUDE.md & GEMINI.md mẫu**:
  + Dòng 1 trỏ chính xác về submodule: `@_skill/CLAUDE.md` và `@_skill/GEMINI.md`.
  + Đầy đủ các trường thông tin quản trị dự án: Mã dự án, Tên dự án, Loại dự án (A/B/C/Chưa rõ), Nguồn vốn, Đội UX riêng, Phiên bản quy tắc, Repo/Worktree, Ngày khởi tạo.
  + Nhắc lại các nguyên tắc cốt lõi: Không sửa `_skill/`, chỉ nhận tin nhắn `[<MÃ>]`, hỏi BA khi có thông tin "Chưa rõ", không mang ngữ cảnh sang dự án khác và không dán dữ liệu dự án ra ngoài.
- **_shared/task-board.md mẫu**:
  + Đủ **70 việc** (G-01 đến G-70), khớp 100% với bảng Mục 6 đã được BA duyệt tại D-002: Claude làm 49 việc, Gemini làm 21 việc; mức độ (B/Đk/TC), Bên làm, Bên review và mô tả Đầu ra chính đều chuẩn xác.
  + Toàn bộ trạng thái công việc được đặt mặc định là "Chưa bắt đầu".
- **Các sổ theo dõi dùng chung theo chuẩn BABOK v3**:
  + `decision-log.md`: Đầy đủ các cột truy vết quyết định (`Mã`, `Ngày`, `Việc`, `Quyết định`, `Căn cứ`, `Ảnh hưởng`) và bảng theo dõi "Chưa quyết (chờ BA)".
  + `intake-log.md`: Đầy đủ các trường tiếp nhận tài liệu Elicitation (`Mã`, `Ngày nhận`, `File`, `Loại tài liệu`, `Đọc được`, `Phục vụ việc`, `Claude làm`, `Gemini làm`, `Trạng thái`, `Kết quả`).
  + `glossary.md`: Có cột `Không dùng (từ đồng nghĩa dễ lẫn)` — đây là thực tiễn xuất sắc của Senior BA giúp ngăn ngừa đa nghĩa và hiểu lầm thuật ngữ nghiệp vụ.
  + `rtm.md`: Đạt chuẩn Requirements Traceability Matrix (RTM) của BABOK v3 với khả năng truy vết 2 chiều: Backward (Mục tiêu KD, Nguồn khảo sát) và Forward (Ưu tiên MoSCoW, BRD, URD/User Story, SRS, Test Case, Trạng thái).
- **Khung thư mục giai đoạn**:
  + Đầy đủ 14 thư mục theo cấu trúc Mục 4: `00_input/`, `01_presale/`, `02_khoi-tao/`, `03_khao-sat/`, `04_dac-ta/`, `05_thiet-ke/`, `06_phat-trien/`, `07_kiem-thu/`, `08_trien-khai/`, `09_sau-trien-khai/`, `minutes/`, `research/`, `reviews/`, `_shared/`.
  + Mỗi thư mục đều có file `.gitkeep` để duy trì cấu trúc thư mục rỗng trong Git.

### 1.3 Kiểm tra hướng dẫn khởi tạo dự án trong README.md

- `README.md` đã phân định rõ ràng giữa hai ngữ cảnh làm việc:
  1. *Khởi tạo một dự án mới*: Hướng dẫn 3 bước chuẩn hóa (Tạo repo từ `templates/project/` → Thêm submodule `_skill/` ở tag chốt → Đăng ký Orca và tạo 2 worktree kèm `git submodule update --init`).
  2. *Làm việc trong repo quy tắc gốc `ba-skill`*: Mở trong Orca, tạo worktree `review-gemini` và chạy Bước 0 khi cần cập nhật quy tắc.
- **Phát hiện lỗi định dạng nhỏ (Góp ý)**: Tại phần "Làm việc trong repo này" (dòng 26-30), số thứ tự các bước bị nhảy từ bước 1 sang bước 3 (thiếu bước 2).

### 1.4 Phân tích rủi ro khi sử dụng Git Submodule và giải pháp giảm thiểu

Qua thực tiễn vận hành trên môi trường Orca và Antigravity, Gemini nhận diện 4 rủi ro kỹ thuật tiềm ẩn kèm biện pháp xử lý:

| # | Rủi ro | Phân tích tác động | Giải pháp giảm thiểu đề xuất |
|---|---|---|---|
| **R-1** | **Antigravity không tự động import cú pháp `@_skill/GEMINI.md`** | Cú pháp `@` ở đầu file là cơ chế context inclusion riêng của Claude Code. Antigravity CLI không tự động transclude nội dung file con vào system prompt nếu không có chỉ thị. Nếu chỉ mở `GEMINI.md` ở root, Gemini sẽ thiếu toàn bộ quy tắc 289 dòng ở `_skill/GEMINI.md`. | **Đã có & cần nhấn mạnh**: Dòng 5 `templates/project/GEMINI.md` đã có chỉ dẫn tường minh. Khi tạo worktree `<mã>-review`, prompt khởi tạo đầu tiên gửi cho Antigravity **bắt buộc** phải có câu: *"Đọc file GEMINI.md ở gốc và đọc toàn bộ file _skill/GEMINI.md trước khi nhận việc"*. |
| **R-2** | **Worktree mới quên chạy init submodule** | Khi tạo worktree Git mới (`orca worktree create`), thư mục `_skill/` mặc định sẽ trống rỗng cho đến khi chạy lệnh cập nhật. Agent sẽ không thể đọc được tài liệu quy tắc gốc. | Lệnh `git submodule update --init --recursive` đã được đưa vào hướng dẫn bắt buộc tại Bước 3 trong `README.md` và Mục 4.1. Điều phối viên Claude khi gửi dispatch đầu tiên cần kiểm tra xem Gemini đã đọc được `_skill/` chưa. |
| **R-3** | **Vô tình chỉnh sửa hoặc commit vào `_skill/` trong repo dự án** | Thao tác sửa file trong submodule sẽ đưa submodule vào trạng thái detached HEAD hoặc uncommitted changes, gây xung đột nghiêm trọng khi cập nhật quy tắc. | Đã cấm rõ ràng tại Mục 4 và Mục 9 (`Không được ghi: _skill/`). Khuyến nghị bổ sung file `.gitignore` hoặc pre-commit hook trong template dự án cảnh báo nếu có staged changes thuộc `_skill/`. |
| **R-4** | **Trôi phiên bản quy tắc (Submodule drift)** | Chạy lệnh submodule update không chỉ định tag có thể kéo về commit mới nhất trên `main` của `ba-skill`, mang theo các thay đổi chưa được BA phê duyệt cho dự án đó. | Duy trì nghiêm ngặt quy định tại D-009: `ba-skill` luôn chốt phiên bản bằng git tag (`v1.0`, `v1.1`...). Mọi hành động nâng tag quy tắc trong dự án bắt buộc phải qua Phiếu đề xuất và BA đồng ý. |

---

## 2. Bảng nhận xét theo tiêu chuẩn GEMINI.md Mục 7

| # | Vị trí | Mức | Nhận xét | Đề xuất | Trả lời bên làm |
|---|---|---|---|---|---|
| 1 | `CLAUDE.md` & `GEMINI.md` Mục 4.1 | Đạt | Quy định làm việc nhiều dự án qua submodule, mã hóa dự án và phân lập ngữ cảnh hoàn toàn nhất quán, chặt chẽ, đúng quyết định D-009. | Chấp nhận không điều chỉnh. | — |
| 2 | `templates/project/` | Đạt | Bộ template đầy đủ, chuẩn mực. Task board đủ 70 việc (Claude 49, Gemini 21); các sổ `decision-log`, `intake-log`, `glossary`, `rtm` bám sát BABOK v3. Đủ 14 thư mục giai đoạn kèm `.gitkeep`. | Chấp nhận không điều chỉnh. | — |
| 3 | `README.md` dòng 27–30 | Góp ý | Mục "Làm việc trong repo này" bị nhảy số thứ tự: có bước 1 rồi nhảy sang bước 3 (thiếu số 2). | Sửa lại số thứ tự các bước thành 1, 2, 3 liên tục. | — |
| 4 | Cơ chế vận hành Antigravity | Góp ý | Do Antigravity không tự nạp file qua dòng `@_skill/GEMINI.md`, cần đảm bảo quy trình tạo worktree luôn gửi prompt mở đầu yêu cầu agent đọc cả `GEMINI.md` và `_skill/GEMINI.md`. | Bổ sung nhắc nhở này vào mẫu lệnh tạo worktree trong `README.md` để BA hoặc Claude không quên khi khởi tạo. | — |

---

## 3. Kết luận và Thống kê Review

- **Thống kê nhận xét**:
  + Nghiêm trọng: **0**
  + Nên sửa: **0**
  + Góp ý: **2** (lỗi đánh số thứ tự trong README và lưu ý prompt mở đầu cho Antigravity)
  + Đánh giá chung: **ĐẠT CHUẨN**
- **Đánh giá kiến trúc**: Giải pháp Git Submodule cho phép tách biệt hoàn hảo giữa "Bộ quy tắc quản trị BA dùng chung" (`ba-skill`) và "Dữ liệu/nghiệp vụ dự án cụ thể", ngăn ngừa rò rỉ ngữ cảnh (context leak) và đảm bảo tính chuẩn hóa cao trên nhiều dự án song song.
- **Sẵn sàng gắn tag**: Sau khi Claude tiếp thu 2 điểm góp ý nhỏ trên, bộ quy tắc `ba-skill` hoàn toàn đủ điều kiện để đóng gói và gắn tag phiên bản chính thức **`v1.0`** theo quyết định D-009.
