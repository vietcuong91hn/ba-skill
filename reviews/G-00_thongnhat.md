<!-- owner: claude -->
# G-00 — Bản thống nhất rà soát danh mục công việc (trình BA duyệt)

| Thông tin | Nội dung |
|---|---|
| Việc | G-00 — Bước 0 |
| Bên làm / review | Claude (`reviews/G-00_claude.md`, nhánh `feature/coord-claude`) / Gemini (`reviews/G-00_gemini.md`, nhánh `feature/review-gemini`, commit `9fc2e70`) |
| Xác nhận của BA | Phiếu đề xuất G-00 ngày 17/11/2026 — "Đồng ý", chọn 1a và 2 |
| Orchestration | Run `run_6f339f7bfb70`, task `task_48875208d4df`, dispatch `ctx_66488e5addbc` — Gemini `worker_done` (succeeded) lúc 04:12 UTC |
| Trạng thái | **Chờ BA duyệt.** Chưa thay đổi `CLAUDE.md`, `GEMINI.md`, `_shared/`. |

---

## Phần 1 — Hai bên đồng ý

Gemini rà soát độc lập trước khi đọc bản của Claude, và 6/8 đề xuất độc lập của Gemini (M-xx) trùng với đề xuất của Claude (C-xx). Gemini đồng ý hoàn toàn 12/14 đề xuất của Claude, đồng ý một phần 2/14, không phản đối đề xuất nào.

| # | Nội dung thống nhất | Nguồn | Mức |
|---|---|---|---|
| T-01 | **G-58 tách**: Gemini làm Biên bản họp (`minutes/`); decision-log do Claude ghi vào `_shared/decision-log.md` sau khi BA xác nhận. Gỡ mâu thuẫn quyền ghi `_shared/`. | C-01 = M-01 | Nghiêm trọng |
| T-02 | **G-42 Test case UAT, G-44 Dữ liệu kiểm thử** → Làm Gemini, Review Claude (kiểm thử độc lập với người viết đặc tả). G-44 ghi rõ yêu cầu **che giấu / ẩn danh dữ liệu cá nhân** *(bổ sung của Gemini)*. | C-02 = M-04 | Nên sửa |
| T-03 | **G-19 Yêu cầu pháp lý chi tiết** → Làm Gemini, Review Claude (nối tiếp G-03). | C-03 = M-02 | Nên sửa |
| T-04 | **G-61 Báo cáo tiến độ BA** → Làm Claude, Review Gemini (Claude giữ dữ liệu nguồn). | C-04 = M-06 | Góp ý |
| T-05 | **G-59** đổi thành **Quản lý RAID** (Rủi ro, Giả định, Vấn đề, Phụ thuộc). | C-05 | Nên sửa |
| T-06 | Thêm **G-69 🆕** Soạn yêu cầu kỹ thuật cho hồ sơ mời thầu / RFP (phía chủ đầu tư) — Đk, Claude / Gemini. | C-06 | Nên sửa |
| T-07 | Thêm **G-70 🆕** Phạm vi hợp đồng / SOW và tiêu chí nghiệm thu cấp hợp đồng — Đk, Claude / Gemini. | C-07 | Nên sửa |
| T-08 | **Không** tạo G-71. Điều kiện kích hoạt việc Đk, lịch phụ thuộc và cách quản trị yêu cầu (ai duyệt, ngưỡng lập CR) **gộp vào đầu ra G-13 BA Plan**. *Claude đã đồng ý với Gemini — xem Phần 2, M-08 / C-08.* | C-08, C-09, M-08 | Góp ý |
| T-09 | **G-09** thêm Kế hoạch hiện thực hóa lợi ích (nối G-09 → G-17 → G-53); dự án vốn ngân sách nhà nước dùng biến thể hồ sơ theo NĐ 73/2019 sửa bởi NĐ 82/2024. | C-10 = M-08 | Nên sửa |
| T-10 | Ranh giới **G-25** (tạo backlog ban đầu + baseline URD) và **G-38** (duy trì, tinh chỉnh, sắp ưu tiên backlog). | C-11 | Góp ý |
| T-11 | **G-28** thêm từ điển dữ liệu (kèm phân loại độ nhạy cảm); **G-32** thêm quy tắc đối soát dữ liệu sau chuyển đổi; **G-47** thêm yêu cầu chuyển tiếp. | C-12 = M-05 | Nên sửa |
| T-12 | **G-29 Wireframe** B → Đk (khi không có đội UX riêng, hoặc cần hình ảnh để chốt yêu cầu màn hình phức tạp). G-03 giữ Đk. G-66 DPIA: điều kiện "bắt buộc khi hệ thống xử lý dữ liệu cá nhân". | C-13 = M-07 | Góp ý |
| T-13 | **G-66 DPIA** → Làm Gemini, Review Claude, **với điều kiện** đầu vào bắt buộc là G-20 (TO-BE) và G-28 (từ điển dữ liệu); Claude review phần luồng xử lý dữ liệu. *Claude đã đồng ý với Gemini — xem Phần 2, M-03.* | M-03, C-13 | Nên sửa |
| T-14 | **G-55** thêm tự đánh giá hiệu quả công việc BA (tỷ lệ yêu cầu đổi sau baseline, lỗi do yêu cầu, thời gian phản hồi Q&A). | C-14 | Góp ý |

---

## Phần 2 — Claude trả lời từng đề xuất độc lập của Gemini

| Mã | Đề xuất của Gemini | Trả lời của Claude |
|---|---|---|
| M-01 | Tách G-58 | **Đã sửa** — trùng C-01 → T-01. |
| M-02 | G-19 sang Gemini | **Đã sửa** — trùng C-03 → T-03. |
| M-03 | G-66 DPIA sang Gemini làm | **Đã sửa, kèm điều kiện.** Ban đầu Claude giữ DPIA vì phần lõi của DPIA là mô tả hoạt động xử lý dữ liệu, vốn đến từ G-20 và G-28 do Claude làm. Nhưng lý lẽ của Gemini thuyết phục hơn: hồ sơ DPIA theo Luật 91/2025/QH15 là hồ sơ pháp lý có mẫu, và G-03 → G-19 → G-66 nên cùng một chủ. Điều kiện để giữ chất lượng: G-20 và G-28 là đầu vào bắt buộc; Claude review đúng phần luồng dữ liệu → T-13. |
| M-04 | G-42, G-44 sang Gemini | **Đã sửa** — trùng C-02, thêm che giấu dữ liệu → T-02. |
| M-05 | G-28 thêm từ điển dữ liệu | **Đã sửa** — trùng C-12 → T-11. |
| M-06 | G-61 sang Claude | **Đã sửa** — trùng C-04 → T-04. |
| M-07 | G-29 sang Đk | **Đã sửa** — trùng C-13 → T-12. |
| M-08 | Gộp điều kiện kích hoạt vào G-13, không tạo G-71 | **Đã sửa.** Claude rút đề xuất G-71: một mã việc riêng cho nội dung vốn thuộc BA Plan theo BABOK là phân mảnh không cần thiết → T-08. |

---

## Phần 3 — Hai bên khác nhau / Claude review phần việc của Gemini

**Không còn bất đồng nào về danh mục công việc.**

Claude review phần (C) Xác minh pháp lý của Gemini. Claude đã tự tra lại bằng tìm kiếm web ngày 17/11/2026 (chỉ dùng từ khóa số hiệu văn bản công khai, không dùng nội dung nội bộ):

| # | Vị trí trong G-00_gemini.md | Mức | Nhận xét của Claude | Đề xuất |
|---|---|---|---|---|
| R-01 | (C) mục 1, 2 — "Nguồn xác thực" | Nên sửa | Link nguồn là **trang chủ** (chinhphu.vn, vcci.com.vn, bocongan.gov.vn), không trỏ tới văn bản cụ thể → không kiểm lại được, chưa đạt yêu cầu "link + ngày truy cập" của GEMINI.md N4. | Thay bằng link văn bản, ví dụ Công báo NĐ 82/2024: https://congbao.chinhphu.vn/van-ban/nghi-dinh-so-82-2024-nd-cp-42310.htm |
| R-02 | (C) mục 2 | **Nghiêm trọng** | Thiếu một điểm then chốt: **NĐ 356/2025/NĐ-CP thay thế NĐ 13/2023/NĐ-CP**. Gemini mô tả NĐ 13/2023 là "văn bản tiền đề" mà không nói đã hết hiệu lực. Nếu G-03 / G-19 sau này còn viện dẫn NĐ 13/2023 thì sai căn cứ pháp lý. *(Đề xuất C-13 ban đầu của Claude cũng viện dẫn NĐ 13/2023 — Claude ghi nhận sai sót của mình.)* | Ghi rõ NĐ 13/2023 hết hiệu lực từ 01/01/2026; căn cứ hiện hành là Luật 91/2025/QH15 + NĐ 356/2025/NĐ-CP. |
| R-03 | (C) mục 2 — ngày ban hành NĐ 356 | Góp ý | Gemini ghi 31/12/2025; một số cổng tỉnh ghi 30/12/2025. Ngày hiệu lực 01/01/2026 khớp ở các nguồn. | Đối chiếu bản gốc trên Công báo trước khi dùng trong tài liệu chính thức. |
| R-04 | (C) mục 1 — "Nội dung trọng yếu" NĐ 82/2024 | Nên sửa | Phần tóm tắt nội dung chung chung và không gắn nguồn. Theo các nguồn Claude tìm được, NĐ 82/2024 tập trung vào thuê dịch vụ CNTT và bãi bỏ một khoản Điều 28 cùng Mục 3 Chương II (Điều 46–50) của NĐ 73/2019 — khác với tóm tắt của Gemini. | Tóm tắt lại theo toàn văn, ghi điều khoản cụ thể; phần chưa đọc toàn văn ghi "chưa kiểm chứng". |
| R-05 | (C) mục 2 — DPIA gửi A05; "quy mô lớn hoặc dữ liệu nhạy cảm" | Nên sửa | Hai khẳng định này chưa có nguồn cụ thể và quyết định trực tiếp phạm vi G-66. | Ghi "chưa kiểm chứng" hoặc dẫn điều khoản. |
| R-06 | (D) mục 2 — "định mức hướng dẫn của Bộ TT&TT" | Góp ý | Bộ TT&TT đã hợp nhất vào Bộ KH&CN từ năm 2025 (NĐ 82/2024 hiện đăng trên mst.gov.vn). *Claude chưa tra văn bản hợp nhất — chưa kiểm chứng ngày cụ thể.* | Dùng tên cơ quan hiện hành. |

**Kết luận về phần pháp lý**: số hiệu và ngày hiệu lực chính đều **đúng** (Luật 91/2025/QH15 hiệu lực 01/01/2026; NĐ 356/2025/NĐ-CP hiệu lực 01/01/2026; NĐ 82/2024/NĐ-CP hiệu lực 10/07/2024). Các điểm R-01 … R-06 **không ảnh hưởng quyết định về danh mục công việc**, nên Claude đề xuất xử lý trong việc G-03 khi có dự án cụ thể, thay vì mở thêm một vòng G-00. Gemini sẽ trả lời từng dòng R-xx theo N3 khi được dispatch.

Nguồn Claude dùng để kiểm tra (truy cập 17/11/2026):
- Công báo — NĐ 82/2024/NĐ-CP: https://congbao.chinhphu.vn/van-ban/nghi-dinh-so-82-2024-nd-cp-42310.htm
- Bộ KH&CN — NĐ 82/2024/NĐ-CP: https://mst.gov.vn/van-ban-phap-luat/25016.htm
- Thư viện Pháp luật — NĐ 356/2025/NĐ-CP: https://thuvienphapluat.vn/phap-luat-nha-dat/toan-van-nghi-dinh-3562025ndcp-huong-dan-luat-bao-ve-du-lieu-ca-nhan-13670.html
- Cổng Hành chính công Nghệ An — NĐ 356/2025/NĐ-CP: https://hcc.nghean.gov.vn/laws/detail/Nghi-dinh-so-356-2025-ND-CP-cua-Chinh-phu-Quy-dinh-chi-tiet-mot-so-dieu-va-bien-phap-thi-hanh-Luat-Bao-ve-du-lieu-ca-nhan-2058/
- Frasers Law — nghị định hướng dẫn Luật BVDLCN: https://www.frasersvn.com/vi/legal-updates-and-publications/the-next-chapter-in-data-protection-new-decree-guiding-the-personal-data-protection-law

---

## Phần 4 — Đề xuất cuối (BA quyết)

### 4.1 Thay đổi bảng Mục 6 (gồm T-01 … T-14)

| Mã | Thay đổi | Làm | Review | Mức |
|---|---|---|---|---|
| G-09 | Đầu ra thêm Kế hoạch hiện thực hóa lợi ích; biến thể hồ sơ vốn nhà nước | Claude | Gemini | B |
| G-13 | Đầu ra thêm: điều kiện kích hoạt việc Đk, phụ thuộc, quản trị yêu cầu, **profile dự án** (xem 4.2) | Claude | Gemini | B |
| G-19 | Đổi bên làm | **Gemini** | **Claude** | Đk |
| G-25 / G-38 | Ghi rõ ranh giới tạo / duy trì backlog | Claude | Gemini | B |
| G-28 | Thêm từ điển dữ liệu + phân loại độ nhạy cảm | Claude | Gemini | B |
| G-29 | Đổi mức | Claude | Gemini | **Đk** |
| G-32 / G-47 | Thêm đối soát dữ liệu / yêu cầu chuyển tiếp | Claude | Gemini | Đk / B |
| G-42 | Đổi bên làm | **Gemini** | **Claude** | B |
| G-44 | Đổi bên làm; thêm che giấu dữ liệu | **Gemini** | **Claude** | B |
| G-55 | Thêm tự đánh giá hiệu quả BA | Claude | Gemini | B |
| G-58 | Chỉ còn Biên bản họp (`minutes/`) | Gemini | Claude | B |
| G-57 | Nhận thêm việc ghi decision-log | Claude | Gemini | B |
| G-59 | Đổi tên: Quản lý RAID | Claude | Gemini | B |
| G-61 | Đổi bên làm | **Claude** | **Gemini** | B |
| G-66 🆕 | Đổi bên làm; đầu vào bắt buộc G-20, G-28 | **Gemini** | **Claude** | Đk |
| G-69 🆕 | Mới: Yêu cầu kỹ thuật hồ sơ mời thầu / RFP | Claude | Gemini | Đk |
| G-70 🆕 | Mới: Phạm vi hợp đồng / SOW + tiêu chí nghiệm thu | Claude | Gemini | Đk |

**Tổng sau thay đổi: 70 việc. Claude làm 49, Gemini làm 21** (= Claude 50 − G-19 − G-42 − G-44 − G-66 + G-61 + G-69 + G-70; Gemini 18 + G-19 + G-42 + G-44 + G-66 − G-61). Mã G-71 không dùng.

### 4.2 Đề xuất thêm của Gemini — Claude ủng hộ, cần BA quyết

| # | Đề xuất | Ý kiến Claude |
|---|---|---|
| P-01 | **Profile dự án trong G-13**: A — phía chủ đầu tư (bật G-08, G-46, G-69; G-05, G-70 không áp dụng); B — phía nhà cung cấp (bật G-05, G-06, G-70; G-69 không áp dụng); C — sản phẩm nội bộ. | Ủng hộ. Trả lời gọn câu hỏi mở số 1 mà không phải cố định bảng cho một phía. |
| P-02 | **Bộ template riêng cho dự án vốn ngân sách nhà nước** (`templates/gov_it_investment/`), dùng khi BA xác nhận dự án thuộc diện này. | Ủng hộ, nhưng đề xuất làm trong G-62 khi có dự án thật, không làm ngay. |

### 4.3 Câu hỏi BA cần trả lời (từ Mục 4 bản của Claude)

1. Profile thường gặp nhất trong các dự án sắp tới: A, B hay C?
2. Có dự án dùng vốn ngân sách nhà nước sắp tới không?
3. Các dự án thường có đội UX riêng không?

### 4.4 Việc làm sau khi BA duyệt

1. Phiếu đề xuất sửa Mục 6 trong **`CLAUDE.md` và `GEMINI.md`** (BA là chủ hai file).
2. Tạo `_shared/task-board.md` (70 việc, trạng thái), `_shared/decision-log.md` (ghi quyết định G-00).
3. Ghi R-01 … R-06 vào việc G-03 để Gemini xử lý khi có dự án.
