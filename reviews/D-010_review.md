<!-- owner: gemini -->
# Review D-010 — Đánh giá Quy trình Chuyển máy và Danh mục dự án `_shared/projects.md`

| Thông tin | Nội dung |
|---|---|
| Việc | Review D-010: Kiểm tra commit `21657de` (thêm `_shared/projects.md`, Mục 4.2 `CLAUDE.md`, quy trình "Cài đặt worktree cho máy mới") |
| Vai trò | Reviewer (Gemini) |
| Căn cứ xác nhận BA | Quyết định D-010 trong `_shared/decision-log.md` (BA yêu cầu quy trình chuyển máy an toàn, Claude liệt kê và hỏi xác nhận) |
| Tài liệu đối chiếu | `_shared/projects.md`, `CLAUDE.md`, `GEMINI.md`, `README.md`, `_shared/decision-log.md` |
| Đầu ra | `reviews/D-010_review.md` (nhánh `feature/review-gemini`) |
| Kết luận chung | **ĐẠT CHUẨN (Xuất sắc về quản trị & đúng nguyên tắc N1)** — Bổ sung 3 điểm góp ý tăng cường an toàn dữ liệu và kỹ thuật môi trường |

---

## 1. Kết quả kiểm tra chi tiết theo 5 yêu cầu Dispatch D-010

### 1.1 Kiểm tra file `_shared/projects.md`

- **Tính đầy đủ và chính xác của danh mục dự án**:
  + Dự án `ba-skill`: Ghi rõ là bộ quy tắc gốc, repo `vietcuong91hn/ba-skill`, public, đang dùng, khởi tạo 17/11/2026.
  + Dự án `G-Safe` (mã `G`): Ghi rõ repo `vietcuong91hn/g-safe` (private), loại dự án `C — sản phẩm nội bộ`, quy tắc gắn submodule `v1.0 (135cad9)`, trạng thái đang chạy, khởi tạo 17/11/2026.
- **Danh mục 4 worktree**:
  + Worktree quy tắc gốc: `coord-claude` (nhánh `feature/coord-claude`, agent `claude`) và `review-gemini` (nhánh `feature/review-gemini`, agent `antigravity`, lời nhắn: `Đọc GEMINI.md`).
  + Worktree dự án G-Safe: `g-coord` (nhánh `feature/coord-claude`, agent `claude`, lời nhắn đọc tóm tắt trạng thái và không tự ý bắt đầu việc) và `g-review` (nhánh `feature/review-gemini`, agent `antigravity`, lời nhắn chuẩn xác: `Đọc GEMINI.md của dự án và toàn bộ _skill/GEMINI.md; xác nhận vai trò; chờ dispatch.`).
- **Tính khả chuyển giữa các máy (Portability)**:
  + Không chứa bất kỳ đường dẫn thư mục tuyệt đối nào của máy cá nhân. Mọi đường dẫn đều được trừu tượng hóa và sẽ được xác định thông qua câu hỏi xác nhận của Claude khi cài đặt trên máy mới.

### 1.2 Kiểm tra quy trình tại `CLAUDE.md` Mục 4.2 ("Cài đặt worktree cho máy mới")

- **Tuyệt đối tuân thủ Nguyên tắc N1**:
  + Bước 3 quy định rõ: Claude bắt buộc phải **hỏi BA xác nhận và dừng chờ trả lời** (chọn cài dự án nào, đặt ở thư mục nào ngoài OneDrive, có chạy agent ngay không) trước khi thực hiện clone hay tạo worktree.
- **Nguyên tắc an toàn và không trùng lặp**:
  + Bước 2 và Bước 5 nêu rõ: Kiểm tra các repo/worktree đã có trên máy; repo đã có sẵn thì **không cài lại**, chỉ fetch và báo trạng thái.
  + Kiểm tra repo trên GitHub (`gh repo list`) đối chiếu với danh mục; không tự ý thêm repo lạ ngoài danh mục vào máy.
- **Bộ lệnh Git và Orca chuẩn hóa**:
  + Lệnh clone kèm submodule: `git clone --recurse-submodules https://github.com/<repo>`.
  + Đăng ký với Orca: `orca repo add --path <thư mục repo>`.
  + Tạo worktree: `orca worktree create --repo path:<thư mục repo> --name <worktree> --branch <nhánh> --base-branch origin/<nhánh> --no-parent`.
  + Gắn upstream và init submodule: `git branch -u origin/<nhánh>` và `git submodule update --init`.
  + Khởi chạy agent tự động theo đúng prompt định sẵn: `orca agent launch ...`.
- **Cảnh báo rủi ro kỹ thuật**:
  + Đã đưa vào cảnh báo phòng ngừa lỗi Orca tự sinh nhánh phụ có hậu tố số (`<nhánh>-2`), yêu cầu dừng lại báo BA, không được push nhánh lạ lên GitHub.
  + Cấm tuyệt đối việc đồng bộ repo qua OneDrive để tránh hỏng Git index.

### 1.3 Kiểm tra hướng dẫn "Chuyển máy" trong `README.md`

- **Khả năng tự thực hiện của người mới (Bootstrap readiness)**:
  + Cung cấp bức tranh tổng thể rõ ràng: chat/cấu hình nằm trên máy cũ, toàn bộ tài sản nghiệp vụ nằm trên GitHub, nguyên tắc chốt buổi làm việc phải push toàn bộ nhánh.
  + Hướng dẫn 3 bước cực kỳ mạch lạc cho máy trắng:
    1. Cài đặt và đăng nhập các công cụ nền tảng (`git`, `gh`, `orca`, Claude Code, Antigravity CLI).
    2. Clone repo quy tắc gốc `ba-skill` về thư mục ngoài OneDrive và đăng ký vào Orca.
    3. Mở Claude Code trong `ba-skill` và chỉ cần gửi một khẩu lệnh duy nhất: `Cài đặt worktree cho máy mới`.
  + Đảm bảo một kỹ sư hoặc BA mới có thể thiết lập lại toàn bộ môi trường làm việc chỉ trong vòng 5–10 phút mà không cần can thiệp thủ công phức tạp.

### 1.4 Kiểm tra tính nhất quán Mục 4.1 giữa CLAUDE.md và GEMINI.md

- Đã so sánh dòng mô tả quy trình khởi tạo dự án tại Mục 4.1 của cả 2 file:
  + `CLAUDE.md` (dòng 86): `... tạo worktree <mã>-coord (...) và <mã>-review (...) → mỗi worktree chạy git submodule update --init → ghi dự án và worktree vào _shared/projects.md của ba-skill.`
  + `GEMINI.md` (dòng 65): `... tạo worktree <mã>-coord (...) và <mã>-review (...) → mỗi worktree chạy git submodule update --init → ghi dự án và worktree vào _shared/projects.md của ba-skill.`
  + Hai file hoàn toàn khớp từng chữ, đảm bảo việc cập nhật `_shared/projects.md` là một bước bắt buộc trong vòng đời khởi tạo dự án.

### 1.5 Phân tích các rủi ro còn thiếu khi chuyển máy và giải pháp giảm thiểu

Dưới góc độ Senior BA phản biện độc lập, Gemini nhận diện thêm 4 rủi ro thực tế khi chuyển giao giữa các máy:

| # | Rủi ro tiềm ẩn | Phân tích tác động | Giải pháp giảm thiểu đề xuất |
|---|---|---|---|
| **R-1** | **Dữ liệu đầu vào nhạy cảm trong `00_input/` bị sót trên máy cũ** | Một số tài liệu khách hàng (scan dung lượng >100MB, file ghi âm/video hoặc dữ liệu cá nhân theo Luật BVDL cá nhân 2025) có thể bị `.gitignore` chặn push lên GitHub. Khi sang máy mới, các tài liệu này sẽ bị thiếu, làm đứt gãy căn cứ truy vết của BA. Đồng thời, dữ liệu sót lại trên máy cũ có nguy cơ rò rỉ an ninh thông tin. | - Bổ sung bước kiểm tra thư mục `00_input/` trên máy cũ trước khi chuyển.<br>- Lưu trữ tài liệu dung lượng lớn/nhạy cảm trên Cloud Drive nội bộ có mã hóa và ghi link trong `intake-log.md`.<br>- Thực hiện vệ sinh an toàn dữ liệu trên máy cũ sau khi chuyển máy. |
| **R-2** | **Lệch nhánh do quên Push trên máy cũ (Branch drift / Unpushed commits)** | Nếu BA hoặc agent commit nhưng chưa push trên máy cũ (đặc biệt là nhánh review `feature/review-gemini`), khi máy mới clone về sẽ là bản cũ. Nếu máy mới tiếp tục commit rồi sau đó máy cũ push lên sẽ gây xung đột phân nhánh (divergent branch) rất khó gỡ. | - Trên máy cũ, trước khi rời máy cần chạy lệnh tổng kiểm tra: `git push --all origin`.<br>- Bổ sung vào Mục 4.2 nguyên tắc: Khi đã bắt đầu làm việc trên máy mới, coi máy cũ là "Read-only" cho đến khi đã pull đồng bộ phiên bản mới nhất từ GitHub. |
| **R-3** | **Quota và phân quyền tài khoản Antigravity CLI trên máy mới** | Trên máy mới, tài khoản Google đăng nhập vào Antigravity (`agy`) có thể khác tài khoản cũ hoặc chưa được kích hoạt đúng hạn ngạch (Tier/Quota), dẫn đến lỗi từ chối dịch vụ hoặc bị giới hạn context window khi đọc tài liệu lớn. | Bổ sung vào bước 1 (kiểm tra công cụ): Yêu cầu kiểm tra tài khoản đăng nhập Antigravity (`agy status` hoặc lệnh tương đương) trùng khớp với tài khoản được cấp quyền dự án. |
| **R-4** | **Giới hạn độ dài đường dẫn Windows (MAX_PATH 260 ký tự)** | Do sử dụng worktree lồng git submodule (`<repo>/_skill/...`), đường dẫn file trên hệ điều hành Windows rất dễ vượt quá 260 ký tự, gây lỗi git clone hoặc checkout file âm thầm. | Đưa khuyến nghị kích hoạt cấu hình `git config --system core.longpaths true` vào mục 1 (chuẩn bị công cụ trên máy mới) trong `README.md`. |

---

## 2. Bảng nhận xét theo tiêu chuẩn GEMINI.md Mục 7

| # | Vị trí | Mức | Nhận xét | Đề xuất | Trả lời bên làm |
|---|---|---|---|---|---|
| 1 | `_shared/projects.md` | Đạt | Danh mục đầy đủ, chuẩn xác (ba-skill, G-Safe), đúng 4 worktree, không chứa đường dẫn tuyệt đối, lời nhắn khởi chạy cho Gemini rất rõ ràng. | Chấp nhận không điều chỉnh. | — |
| 2 | `CLAUDE.md` Mục 4.2 | Đạt | Quy trình tự động hóa xuất sắc, tuân thủ nghiêm ngặt nguyên tắc N1 (dừng chờ BA xác nhận trước khi clone/tạo worktree), kiểm soát chặt chẽ việc không cài lại repo đã có và cảnh báo rủi ro nhánh lạ. | Chấp nhận không điều chỉnh. | — |
| 3 | `README.md` Mục "Chuyển máy" | Đạt | Hướng dẫn bootstrap trên máy mới 3 bước cực kỳ rõ ràng, dễ hiểu, người mới đọc là làm theo được ngay. | Chấp nhận không điều chỉnh. | — |
| 4 | `CLAUDE.md` & `GEMINI.md` Mục 4.1 | Đạt | Nhất quán 100% dòng quy định ghi dự án và worktree vào `_shared/projects.md` khi khởi tạo dự án. | Chấp nhận không điều chỉnh. | — |
| 5 | Quản trị rủi ro chuyển máy | Góp ý | Cần lưu ý về: (1) Dữ liệu `00_input/` không nằm trên Git; (2) Lệnh kiểm tra push hết nhánh trên máy cũ; (3) Cấu hình `core.longpaths` cho Windows. | Đề xuất Claude xem xét bổ sung vào cẩm nang vận hành hoặc cập nhật nhẹ Mục 4.2 để tăng độ an toàn. | — |

---

## 3. Kết luận và Thống kê Review

- **Thống kê nhận xét**:
  + Nghiêm trọng: **0**
  + Nên sửa: **0**
  + Góp ý: **1** (bổ sung lưu ý rủi ro dữ liệu `00_input/`, `git push --all` và `longpaths` Windows)
  + Đánh giá chung: **ĐẠT XUẤT SẮC**
- **Đánh giá tổng thể**: Giải pháp quản lý chuyển máy qua `_shared/projects.md` kết hợp lệnh tự động hóa `Cài đặt worktree cho máy mới` tại commit `21657de` giải quyết triệt để bài toán đồng bộ môi trường làm việc phân tán giữa nhiều máy tính. Bộ tài liệu `ba-skill` hoàn toàn sẵn sàng để đóng gói và gắn tag phiên bản chính thức **`v1.1`** theo quyết định D-010.
