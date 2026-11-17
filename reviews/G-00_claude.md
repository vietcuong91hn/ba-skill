<!-- owner: claude -->
# G-00 — Rà soát danh mục công việc Senior BA (phần của Claude)

| Thông tin | Nội dung |
|---|---|
| Việc | G-00 — Bước 0: rà soát bảng Mục 6 (G-01 … G-68) |
| Bên làm / review | Claude / Gemini |
| Xác nhận của BA | Phiếu đề xuất G-00 ngày 17/11/2026 — BA trả lời "Đồng ý" (kèm chọn 1a: chia sẻ file qua nhánh git; 2: giao việc qua Orca orchestration) |
| Đầu vào | `CLAUDE.md` Mục 3, Mục 6; `GEMINI.md` Mục 4, Mục 6 |
| Trạng thái | Bản nháp chờ Gemini nhận xét — **chưa có hiệu lực** cho đến khi BA duyệt `G-00_thongnhat.md` |

---

## 1. Cách rà soát

Đối chiếu bảng Mục 6 theo bốn góc:

1. **Độ phủ vòng đời SDLC**: từ presale đến sau triển khai, mỗi giai đoạn có đầu ra đủ để giai đoạn sau dùng được không.
2. **Độ phủ 6 nhóm kiến thức BABOK v3**: Lập kế hoạch & giám sát BA; Khai thác & cộng tác; Quản lý vòng đời yêu cầu; Phân tích chiến lược; Phân tích yêu cầu & định nghĩa thiết kế; Đánh giá giải pháp. *(Tên nhóm theo hiểu biết của Claude về BABOK v3 — đề nghị Gemini đối chiếu bản gốc.)*
3. **Nhất quán nội bộ**: giữa Mục 6 với quy tắc quyền ghi (Mục 4), nguyên tắc N1–N4, và giữa `CLAUDE.md` với `GEMINI.md`.
4. **Phân công hợp lý**: đúng thế mạnh từng agent, tránh nghẽn, giữ tính độc lập giữa người viết và người kiểm.

Kết quả tóm tắt: bảng có độ phủ tốt (khoảng 90% hoạt động BA thông thường). Claude đề xuất **14 điểm**: 1 mâu thuẫn cần sửa ngay, 3 việc mới, 3 đổi bên làm, 7 làm rõ phạm vi / mức. Không đề xuất bỏ việc nào.

---

## 2. Danh sách đề xuất

Loại: **Sửa** = sửa mâu thuẫn · **Thêm** · **Tách** · **Gộp** · **Đổi** = đổi bên làm–review hoặc mức · **Rõ** = làm rõ phạm vi / đầu ra.
Mức ưu tiên dùng thang Mục 7: Nghiêm trọng / Nên sửa / Góp ý.

| # | Mã | Loại | Mức | Đề xuất | Lý do |
|---|---|---|---|---|---|
| C-01 | G-58 | Sửa + Tách | **Nghiêm trọng** | Tách G-58 thành: **G-58 Biên bản họp** (Làm Gemini, Review Claude, đầu ra `minutes/`), còn **decision-log** chuyển về Claude ghi (gộp vào G-57 hoặc ghi rõ là nghĩa vụ của điều phối viên). Gemini đề xuất mục quyết định trong biên bản, Claude chép sang `_shared/decision-log.md` sau khi BA xác nhận. | Mâu thuẫn trực tiếp: Mục 6 giao Gemini đầu ra "Minutes + decision-log", nhưng Mục 4 quy định `_shared/` **chỉ Claude ghi** và GEMINI.md Mục 9 cấm Gemini ghi `_shared/`. Để nguyên thì Gemini không thể hoàn thành G-58 mà không vi phạm quy tắc. |
| C-02 | G-42, G-44 | Đổi | Nên sửa | Đổi **G-42 Test case & kịch bản UAT** và **G-44 Dữ liệu kiểm thử** sang Làm = Gemini, Review = Claude. | Nguyên tắc độc lập kiểm thử: Claude soạn URD/SRS (G-25, G-26); nếu Claude viết luôn test case thì cách hiểu sai của Claude được "kiểm thử" bằng chính cách hiểu đó. Gemini viết test case từ URD/SRS đã duyệt sẽ lộ ra chỗ yêu cầu mơ hồ — đây cũng là một vòng kiểm định chất lượng yêu cầu miễn phí. Đồng thời giảm tải cho Claude (đang làm 50/68). |
| C-03 | G-19 | Đổi | Nên sửa | Đổi **G-19 Yêu cầu pháp lý và tuân thủ chi tiết** sang Làm = Gemini, Review = Claude. | Liên tục với G-03 (Gemini rà khung pháp lý sơ bộ). Việc chính của G-19 là tra văn bản hiện hành, số hiệu, ngày hiệu lực, điều khoản — đúng thế mạnh Gemini (GEMINI.md Mục 3). Claude review ở góc chuyển điều khoản thành yêu cầu kiểm thử được và truy vết vào BRD/SRS. |
| C-04 | G-61 | Đổi | Góp ý | Đổi **G-61 Báo cáo tiến độ BA** sang Làm = Claude, Review = Gemini. | Nguồn dữ liệu của báo cáo là `_shared/task-board.md`, `decision-log`, issue/risk log — đều do Claude làm chủ. Gemini làm báo cáo thì chỉ chép lại số liệu của Claude, thêm một bước dễ lệch. Gemini review sẽ phát hiện báo cáo "tô hồng" tốt hơn. *(Đề xuất này làm Claude tăng 1 việc; tổng thể C-02 + C-03 + C-04 vẫn giảm Claude từ 50 xuống 48.)* |
| C-05 | G-59 | Rõ | Nên sửa | Đổi tên G-59 thành **Quản lý RAID** (Rủi ro – Giả định – Vấn đề – Phụ thuộc); đầu ra `RAID log`. | Giả định và phụ thuộc hiện không có chỗ ghi tập trung, trong khi CLAUDE.md Mục 3 yêu cầu "ước lượng có căn cứ, nêu giả định" (G-07, G-09). Giả định không được theo dõi là nguồn tranh chấp phạm vi phổ biến nhất. |
| C-06 | (mới) G-69 🆕 | Thêm | Nên sửa | **G-69 Soạn yêu cầu kỹ thuật cho hồ sơ mời thầu / RFP (phía chủ đầu tư)** — Đk, Làm Claude, Review Gemini. Đầu ra: Chương yêu cầu kỹ thuật + tiêu chí đánh giá. | Bảng hiện chỉ có G-05 (làm rõ RFI/RFP — góc nhà cung cấp trả lời) và G-08 (chọn nhà cung cấp). Khi BA đứng phía chủ đầu tư, việc **viết** yêu cầu để mời thầu là một sản phẩm riêng, quyết định chất lượng toàn dự án. |
| C-07 | (mới) G-70 🆕 | Thêm | Nên sửa | **G-70 Xác định phạm vi hợp đồng / SOW và tiêu chí nghiệm thu cấp hợp đồng** — Đk, Làm Claude, Review Gemini. | Nối G-07 (ước lượng) với G-46 (nghiệm thu). Tiêu chí nghiệm thu không được chốt từ lúc ký hợp đồng là nguyên nhân gốc của tranh chấp UAT. Áp dụng khi BA ở phía nhà cung cấp hoặc khi có hợp đồng thuê ngoài. |
| C-08 | (mới) G-71 🆕 | Thêm | Góp ý | **G-71 Tiêu chí kích hoạt việc "Đk" và lịch phụ thuộc giữa các G-xx** — B, Làm Claude, Review Gemini, làm 1 lần sau Bước 0 và cập nhật khi đổi dự án. Đầu ra: phần "Điều kiện áp dụng" + cột "Phụ thuộc" trong `_shared/task-board.md`. | 18 việc mức Đk hiện không có điều kiện áp dụng → mỗi dự án lại phải tranh luận việc nào làm. Cột phụ thuộc giúp đề xuất "việc tiếp theo" (CLAUDE.md Mục 1.1) có căn cứ. *Có thể không tạo mã mới mà gộp vào G-13 BA Plan — xem C-09.* |
| C-09 | G-13 | Rõ | Góp ý | Nếu không chấp nhận G-71 riêng: mở rộng đầu ra G-13 BA Plan gồm (a) điều kiện áp dụng các việc Đk, (b) cách quản trị yêu cầu: ai duyệt, cách xử lý thay đổi, ngưỡng phải lập CR. | BABOK đặt "Lập kế hoạch quản trị yêu cầu" trong nhóm Lập kế hoạch BA; hiện G-13 chỉ ghi "BA Plan" chung chung. |
| C-10 | G-09 | Rõ | Nên sửa | Đầu ra G-09 thêm **Kế hoạch hiện thực hóa lợi ích** (chỉ số, baseline lấy từ G-17, mốc đo, người chịu trách nhiệm). Nếu là dự án đầu tư CNTT dùng vốn nhà nước, G-09 có biến thể theo hồ sơ quy định (báo cáo nghiên cứu khả thi / thuyết minh dự án). | Hiện chuỗi G-09 → G-17 → G-53 không có sợi dây nối: G-53 "đo lường lợi ích" nhưng không có cam kết lợi ích gốc để so. Về hồ sơ vốn nhà nước: Claude hiểu là Nghị định 73/2019/NĐ-CP và các văn bản sửa đổi — **chưa kiểm chứng hiệu lực, đề nghị Gemini xác minh**. |
| C-11 | G-25, G-38 | Rõ | Góp ý | Ghi rõ ranh giới: G-25 **tạo** backlog ban đầu và baseline URD; G-38 **duy trì** backlog trong giai đoạn phát triển (tinh chỉnh, chia nhỏ, sắp ưu tiên lại). | Hai việc cùng đầu ra "backlog", dễ trùng lặp hoặc bỏ sót khi chuyển giai đoạn. |
| C-12 | G-28, G-32, G-47 | Rõ | Góp ý | G-28 thêm **từ điển dữ liệu** vào đầu ra. G-32 thêm **quy tắc đối soát dữ liệu sau chuyển đổi**. G-47 thêm **yêu cầu chuyển tiếp** (transition requirements: dữ liệu, song song vận hành, quyền truy cập tạm). | ERD không có từ điển dữ liệu thì dev/QA vẫn phải hỏi lại nghĩa từng trường. Đối soát và yêu cầu chuyển tiếp là khái niệm BABOK, hiện chưa có chủ. |
| C-13 | G-29, G-66, G-03 | Đổi mức | Góp ý | G-29 Wireframe: **B → Đk** (khi dự án không có đội UX riêng, hoặc khi cần làm rõ yêu cầu bằng hình). G-66 DPIA: giữ Đk nhưng điều kiện ghi rõ **"bắt buộc khi hệ thống xử lý dữ liệu cá nhân"**. G-03: giữ Đk, điều kiện "bắt buộc khi có quy định chuyên ngành hoặc dữ liệu cá nhân". | Dự án có đội UX/thiết kế thì BA không nên làm wireframe chính thức (dễ xung đột chủ sở hữu). Hầu hết hệ thống nghiệp vụ tại Việt Nam có xử lý dữ liệu cá nhân, nên DPIA thực tế gần như luôn áp dụng. Căn cứ pháp lý (Nghị định 13/2023/NĐ-CP; Luật Bảo vệ dữ liệu cá nhân 2025 có hiệu lực từ 01/01/2026) — **chưa kiểm chứng, đề nghị Gemini xác minh số hiệu và hiệu lực**. |
| C-14 | G-55 | Rõ | Góp ý | G-55 thêm phần **tự đánh giá hiệu quả công việc BA** (tỷ lệ yêu cầu thay đổi sau baseline, số lỗi do yêu cầu, thời gian phản hồi Q&A). | BABOK có hoạt động "cải thiện hiệu quả BA"; hiện bảng chỉ có bài học dự án, không đo chính công việc BA. Liên kết với G-62 (chuẩn hóa template). |

---

## 3. Tác động nếu BA chấp nhận toàn bộ

| Chỉ số | Hiện tại | Sau đề xuất |
|---|---|---|
| Tổng số việc | 68 | 71 (thêm G-69, G-70, G-71; nếu gộp G-71 vào G-13 thì 70) |
| Claude làm | 50 | 51 (= 50 − G-19 − G-42 − G-44 + G-61 + G-69 + G-70 + G-71) |
| Gemini làm | 18 | 20 (= 18 + G-19 + G-42 + G-44 − G-61) |
| Việc có mâu thuẫn quyền ghi | 1 (G-58) | 0 |

Tài liệu cần cập nhật sau khi BA duyệt: `CLAUDE.md` Mục 6, `GEMINI.md` Mục 6 (qua Phiếu đề xuất riêng), `_shared/task-board.md`, `_shared/decision-log.md`.

---

## 4. Câu hỏi mở cho BA

1. **Vị trí của BA trong các dự án sắp tới**: phía chủ đầu tư, phía nhà cung cấp, hay cả hai? Câu trả lời quyết định G-69 / G-70 / G-05 / G-08 việc nào là mặc định.
2. **Có dự án dùng vốn nhà nước không?** Nếu có, G-09 và G-03 cần theo hồ sơ quy định, khối lượng lớn hơn đáng kể.
3. **Dự án có đội UX riêng không?** Ảnh hưởng mức của G-29.

---

## 5. Phần dành cho Gemini

Gemini ghi nhận xét về từng đề xuất C-01 … C-14 trong `reviews/G-00_gemini.md` (Đồng ý / Không đồng ý + lý do), sau khi đã rà soát độc lập. Claude sẽ trả lời từng nhận xét trong `reviews/G-00_thongnhat.md`.
