<!-- owner: gemini -->
# G-00 — Rà soát danh mục công việc Senior BA (Phần độc lập & phản biện của Gemini)

| Thông tin | Nội dung |
|---|---|
| Việc | G-00 — Bước 0: Rà soát danh mục công việc Mục 6 (G-01 … G-68) |
| Vai trò | Review & Nghiên cứu độc lập (Gemini) |
| Dẫn chiếu xác nhận của BA | Phiếu đề xuất G-00 ngày 17/11/2026 — BA trả lời "Đồng ý" (kèm chọn 1a: chia sẻ file qua nhánh git; 2: giao việc qua Orca orchestration) |
| Đầu vào | `GEMINI.md` Mục 3, Mục 4, Mục 6; `CLAUDE.md` Mục 3, Mục 4, Mục 6; đề xuất của Claude tại nhánh `feature/coord-claude:reviews/G-00_claude.md` |
| Đầu ra | `reviews/G-00_gemini.md` (trên nhánh `feature/review-gemini`) |
| Trạng thái | Hoàn tất rà soát & phản biện — chờ Claude tổng hợp vào `reviews/G-00_thongnhat.md` trình BA duyệt |

---

## 1. Phương pháp rà soát độc lập của Gemini

Thực hiện theo đúng quy trình Bước 0 tại `GEMINI.md` Mục 5, Gemini tiến hành rà soát **độc lập** bảng phân công Mục 6 trước khi đọc bản đề xuất của Claude nhằm bảo đảm tính khách quan, không bị định hướng hay dẫn dắt. Khung đối chiếu bao gồm:

1. **Chu trình phát triển phần mềm (SDLC)**: Đảm bảo tính liên tục của dòng chảy thông tin từ giai đoạn tiền dự án/presale, khởi tạo, khảo sát, phân tích & đặc tả, thiết kế, phát triển, UAT, triển khai cho đến sau triển khai.
2. **6 nhóm kiến thức BABOK v3 (IIBA)**:
   - *Business Analysis Planning and Monitoring* (Lập kế hoạch và giám sát phân tích nghiệp vụ).
   - *Elicitation and Collaboration* (Khai thác yêu cầu và cộng tác).
   - *Requirements Life Cycle Management* (Quản lý vòng đời yêu cầu).
   - *Strategy Analysis* (Phân tích chiến lược).
   - *Requirements Analysis and Design Definition - RADD* (Phân tích yêu cầu và định nghĩa thiết kế).
   - *Solution Evaluation* (Đánh giá giải pháp).
3. **Nguyên tắc tổ chức và chất lượng Senior BA**:
   - Nguyên tắc bốn mắt (Four-eyes principle) và kiểm thử độc lập (Independent Verification & Validation).
   - Phù hợp với năng lực cốt lõi được giao tại `GEMINI.md` (tra cứu pháp lý, phân tích thị trường, xử lý đa phương tiện, phản biện chất lượng) và `CLAUDE.md` (điều phối, mô hình hóa, cấu trúc hóa tài liệu).
   - Tuyệt đối nhất quán với nguyên tắc phân quyền và quyền ghi file quy định tại Mục 4.

---

## (A) Kết quả rà soát ĐỘC LẬP của Gemini

Dưới đây là 8 đề xuất độc lập của Gemini (đánh mã M-01 đến M-08), sử dụng thang phân loại mức độ theo Mục 7: **Nghiêm trọng** (sai nghiệp vụ, xung đột quy tắc, thiếu kiểm thử được), **Nên sửa** (thiếu rõ ràng, thiếu ngoại lệ, sai phân công năng lực), **Góp ý** (tối ưu hóa quy trình, hoàn thiện biểu mẫu).

| Mã | Vị trí (Mã việc) | Loại | Mức | Nhận xét / Phân tích hiện trạng | Đề xuất của Gemini | Căn cứ nghiệp vụ (BABOK / SDLC / Thực tiễn) |
|---|---|---|---|---|---|---|
| **M-01** | G-58 | Sửa + Tách | **Nghiêm trọng** | Mâu thuẫn trực tiếp về quyền ghi file: Mục 6 giao Gemini đầu ra "Minutes + decision-log", nhưng Mục 4 quy định thư mục `_shared/` chỉ duy nhất Claude được ghi; `GEMINI.md` Mục 9 cấm tuyệt đối Gemini ghi vào `_shared/`. Gemini không thể cập nhật `_shared/decision-log.md` mà không vi phạm nguyên tắc hệ thống. | Tách G-58 thành: **G-58 Biên bản họp** (Làm = Gemini, Review = Claude, đầu ra lưu tại thư mục `minutes/`). Riêng phần **decision-log**, Gemini chỉ trích xuất các quyết định đề xuất trong biên bản; Điều phối viên Claude chịu trách nhiệm cập nhật vào `_shared/decision-log.md` sau khi có phê duyệt của BA. | Tính toàn vẹn của phân quyền file (Single-writer rule) theo `CLAUDE.md` và `GEMINI.md`. |
| **M-02** | G-19 | Đổi bên làm | **Nên sửa** | G-19 (Yêu cầu pháp lý và tuân thủ chi tiết) hiện phân công Làm = Claude, Review = Gemini. Điều này chưa tận dụng đúng thế mạnh cốt lõi của Gemini về tra cứu văn bản quy phạm pháp luật, số hiệu, ngày hiệu lực và các chế tài chuyên ngành; đồng thời làm đứt gãy mạch nghiên cứu từ G-03 (do Gemini chủ trì). | Đổi sang: **Làm = Gemini, Review = Claude**. Gemini lập bảng yêu cầu tuân thủ chi tiết; Claude review dưới góc độ chuyển hóa thành các yêu cầu chức năng/phi chức năng kiểm thử được và ánh xạ vào RTM. | Năng lực cốt lõi Gemini (`GEMINI.md` Mục 3); nguyên tắc phân công theo thế mạnh. |
| **M-03** | G-66 🆕 | Đổi bên làm / Làm rõ | **Nên sửa** | G-66 (Đánh giá tác động bảo vệ dữ liệu cá nhân - DPIA) hiện phân công Làm = Claude, Review = Gemini. Sau khi Luật Bảo vệ dữ liệu cá nhân 2025 có hiệu lực (01/01/2026), hồ sơ DPIA mang tính pháp lý rất cao, đòi hỏi đối chiếu các biểu mẫu tuân thủ pháp luật chuyên ngành. | Đổi sang: **Làm = Gemini, Review = Claude** (hoặc phân công rõ: Gemini chịu trách nhiệm khung pháp lý và hồ sơ tuân thủ DPIA; Claude phối hợp/review về mô hình hóa luồng dữ liệu kiến trúc). | Yêu cầu tuân thủ Luật Bảo vệ dữ liệu cá nhân số 91/2025/QH15 và Nghị định 356/2025/NĐ-CP. |
| **M-04** | G-42, G-44 | Đổi bên làm | **Nên sửa** | Hiện tại G-42 (Test case & kịch bản UAT) và G-44 (Dữ liệu kiểm thử) đều giao Làm = Claude, Review = Gemini. Claude là người soạn URD (G-25) và SRS (G-26); nếu Claude viết luôn test case và tạo test data thì vi phạm nguyên tắc kiểm thử độc lập, các điểm mù nhận thức (blindspots) của người đặc tả sẽ chuyển hóa nguyên vẹn sang kịch bản kiểm thử. Ngoài ra G-44 chưa nêu rõ quy tắc che giấu/ẩn danh dữ liệu (Data Masking). | Đổi cả G-42 và G-44 sang: **Làm = Gemini, Review = Claude**. Gemini dựa trên URD/SRS đã duyệt để thiết kế test case và bộ dữ liệu kiểm thử độc lập (đảm bảo che giấu thông tin nhạy cảm); Claude review đối chiếu độ phủ với thiết kế hệ thống. | Nguyên tắc Independent Verification & Validation (IV&V) trong SDLC và BABOK v3 (Solution Evaluation). |
| **M-05** | G-28 | Bổ sung đầu ra | **Nên sửa** | G-28 (Mô hình hóa nghiệp vụ và dữ liệu) hiện chỉ có đầu ra "ERD, sequence, state". Sơ đồ ERD đơn thuần chỉ thể hiện cấu trúc thực thể và quan hệ, thiếu hoàn toàn mô tả chi tiết các thuộc tính, kiểu dữ liệu, độ dài, validation rules, khóa chính/ngoại và phân loại độ nhạy cảm dữ liệu. | Bổ sung bắt buộc **Từ điển dữ liệu (Data Dictionary / Data Catalog)** vào đầu ra của G-28. | BABOK v3 Kỹ thuật Data Dictionary (Technique 10.12). |
| **M-06** | G-61 | Đổi bên làm | **Góp ý** | G-61 (Báo cáo tiến độ BA) hiện phân công Làm = Gemini, Review = Claude. Nguồn dữ liệu báo cáo nằm tại `_shared/task-board.md`, `intake-log.md` và issue log do Claude trực tiếp quản trị. Gemini làm sẽ mất công trích xuất lại dữ liệu từ Claude; trong khi Gemini làm bên Review sẽ đảm bảo đánh giá tiến độ một cách khách quan, tránh nguy cơ báo cáo hình thức. | Đổi sang: **Làm = Claude, Review = Gemini**. Claude lập báo cáo từ dữ liệu điều phối; Gemini phản biện và kiểm chứng với thực tế sản phẩm bàn giao. | Vai trò điều phối viên của Claude; tính khách quan của giám sát BA (BABOK Monitoring). |
| **M-07** | G-29 | Đổi mức | **Góp ý** | G-29 (Wireframe / prototype) hiện để mức Bắt buộc (B). Trong thực tế, nhiều dự án đã có đội Product Designer / UI-UX chuyên trách hoặc triển khai phần mềm đóng gói (SaaS/COTS/ERP), việc BA bắt buộc vẽ wireframe chi tiết sẽ gây lãng phí nguồn lực và chồng chéo thẩm quyền thiết kế. | Đổi mức từ **B → Đk** (áp dụng khi dự án không có đội UX chuyên trách, hoặc khi cần prototype nhanh để làm rõ các luồng nghiệp vụ phức tạp). | Thực tiễn tổ chức dự án Agile/Design Thinking và tối ưu hóa chi phí BA. |
| **M-08** | G-09, G-13 | Làm rõ & Tích hợp | **Nên sửa** | G-09 (Business Case) hiện thiếu cơ chế ràng buộc định lượng với G-53 (Đo lường lợi ích). Ngoài ra, 18 công việc mức "Theo điều kiện" (Đk) chưa có văn kiện quy định điều kiện kích hoạt và sự phụ thuộc, dễ gây tranh cãi khi triển khai từng dự án cụ thể. | Thêm **Kế hoạch hiện thực hóa lợi ích (Benefits Realization Plan)** vào G-09. Tích hợp trực tiếp **Ma trận điều kiện kích hoạt và phụ thuộc** vào G-13 (BA Plan) thay vì tạo thêm mã việc rời rạc. | BABOK v3 Strategy Analysis & Business Analysis Planning and Monitoring. |

---

## (B) Nhận xét chi tiết từng đề xuất C-01 … C-14 của Claude

Sau khi hoàn thành rà soát độc lập, Gemini đã nghiên cứu bản đề xuất của Claude tại nhánh `feature/coord-claude:reviews/G-00_claude.md`. Dưới đây là ý kiến phản biện chi tiết của Gemini đối với từng đề xuất của Claude:

| # | Mã Claude | Vị trí | Loại | Quan điểm của Gemini | Phân tích lý do & Đề xuất điều chỉnh |
|---|---|---|---|---|---|
| 1 | **C-01** | G-58 | Sửa + Tách | **ĐỒNG Ý HOÀN TOÀN** | Hoàn toàn trùng khớp với phát hiện độc lập **M-01** của Gemini. Việc tách G-58 thành Biên bản họp (Gemini làm) và chuyển quản lý `decision-log.md` về cho Claude là bắt buộc để triệt tiêu mâu thuẫn quyền ghi file `_shared/`. |
| 2 | **C-02** | G-42, G-44 | Đổi bên làm | **ĐỒNG Ý HOÀN TOÀN** | Hoàn toàn trùng khớp với đề xuất độc lập **M-04** của Gemini. Phân công Gemini làm Test case và Test data đảm bảo tính khách quan của vòng kiểm định độc lập (IV&V). **Đề xuất bổ sung**: Tại G-44, ghi rõ yêu cầu tuân thủ nguyên tắc *Data Masking* (ẩn danh hóa thông tin định danh cá nhân) khi chuẩn bị dữ liệu test. |
| 3 | **C-03** | G-19 | Đổi bên làm | **ĐỒNG Ý HOÀN TOÀN** | Hoàn toàn trùng khớp với đề xuất độc lập **M-02** của Gemini. Giúp phát huy năng lực tra cứu luật của Gemini và liền mạch chuỗi phân tích pháp lý từ G-03 đến G-19. |
| 4 | **C-04** | G-61 | Đổi bên làm | **ĐỒNG Ý HOÀN TOÀN** | Hoàn toàn trùng khớp với đề xuất độc lập **M-06** của Gemini. Claude là người nắm toàn bộ dữ liệu điều phối tại `_shared/`, việc Claude lập báo cáo tiến độ và Gemini review phản biện là phương án hợp lý và hiệu quả nhất. |
| 5 | **C-05** | G-59 | Làm rõ | **ĐỒNG Ý HOÀN TOÀN** | Chuẩn hóa G-59 thành quản lý RAID (Risks, Assumptions, Issues, Dependencies) và đầu ra `RAID log` là rất chuẩn xác theo thông lệ quốc tế và BABOK. Theo dõi Giả định và Phụ thuộc từ đầu sẽ ngăn chặn tối đa rủi ro vỡ phạm vi (Scope Creep). |
| 6 | **C-06** | G-69 🆕 | Thêm | **ĐỒNG Ý HOÀN TOÀN** | Bổ sung việc "Soạn yêu cầu kỹ thuật cho hồ sơ mời thầu / RFP (phía chủ đầu tư)" lấp đúng khoảng trống lớn khi BA đóng vai trò ở phía Bên mua / Chủ đầu tư. |
| 7 | **C-07** | G-70 🆕 | Thêm | **ĐỒNG Ý HOÀN TOÀN** | Bổ sung việc "Xác định phạm vi hợp đồng / SOW và tiêu chí nghiệm thu cấp hợp đồng" giúp kết nối chặt chẽ giữa ước lượng ban đầu (G-07) và nghiệm thu thanh quyết toán (G-46), bảo vệ quyền lợi hợp đồng cho cả hai phía. |
| 8 | **C-08** | G-71 🆕 | Thêm | **ĐỒNG Ý MỘT PHẦN** | Gemini đồng ý về sự cần thiết của nội dung xác định điều kiện kích hoạt các việc Đk và lịch phụ thuộc. Tuy nhiên, **đề xuất KHÔNG tạo thêm mã G-71 riêng** mà nên gộp thẳng vào G-13 theo phương án C-09. Việc tạo thêm mã G-71 làm phình to danh mục và phân mảnh kế hoạch BA không cần thiết. |
| 9 | **C-09** | G-13 | Làm rõ / Gộp | **ĐỒNG Ý HOÀN TOÀN** | Đây là phương án tối ưu để giải quyết C-08. Đầu ra của G-13 (BA Plan) theo chuẩn BABOK v3 vốn đã bao gồm: (1) Kế hoạch tiếp cận & điều kiện kích hoạt các gói công việc, (2) Quy trình quản trị yêu cầu và kiểm soát thay đổi (Change Control Process). |
| 10 | **C-10** | G-09 | Làm rõ | **ĐỒNG Ý HOÀN TOÀN** | Việc bổ sung "Kế hoạch hiện thực hóa lợi ích" vào G-09 tạo sợi dây kết nối logic khép kín: G-09 (Cam kết lợi ích) → G-17 (Thiết lập Baseline KPI) → G-53 (Đo lường lợi ích thực tế). Phần xác minh pháp lý đối với dự án vốn nhà nước đã được Gemini kiểm chứng chi tiết tại Mục C. |
| 11 | **C-11** | G-25, G-38 | Làm rõ | **ĐỒNG Ý HOÀN TOÀN** | Rất cần thiết. Xác định rõ: G-25 chịu trách nhiệm *khởi tạo* Product Backlog ban đầu gắn với Baseline URD; G-38 chịu trách nhiệm *duy trì, làm mịn (refine) và ưu tiên hóa* Backlog trong suốt chu kỳ phát triển sprint. |
| 12 | **C-12** | G-28, G-32, G-47 | Làm rõ | **ĐỒNG Ý HOÀN TOÀN** | Rất xác đáng và trùng khớp với phát hiện **M-05** của Gemini. Bổ sung Từ điển dữ liệu (G-28), Quy tắc đối soát dữ liệu chuyển đổi (G-32) và Yêu cầu chuyển tiếp (G-47) giúp lấp đầy các yêu cầu chuyển giao cốt lõi theo chuẩn BABOK v3. |
| 13 | **C-13** | G-29, G-66, G-03 | Đổi mức | **ĐỒNG Ý VỚI G-29, G-03; ĐỒNG Ý MỘT PHẦN VỚI G-66** | - **G-29 & G-03**: Nhất trí chuyển G-29 sang Đk và giữ G-03 là Đk.<br>- **G-66 (DPIA)**: Nhất trí điều kiện "bắt buộc khi hệ thống xử lý dữ liệu cá nhân". Tuy nhiên, theo Luật Bảo vệ dữ liệu cá nhân 2025 (đã có hiệu lực từ 01/01/2026), hầu hết ứng dụng số đều xử lý dữ liệu cá nhân. Do đó, Gemini đề xuất kết hợp với **M-03**: Đổi bên **Làm = Gemini, Review = Claude** để gắn liền trách nhiệm với G-03 và G-19. |
| 14 | **C-14** | G-55 | Làm rõ | **ĐỒNG Ý HOÀN TOÀN** | Hoàn toàn ủng hộ việc bổ sung phần "Tự đánh giá hiệu quả công việc BA" vào G-55 (đo lường tỷ lệ thay đổi yêu cầu, số defect do sai sót phân tích, độ trễ hỗ trợ...). Điều này giúp hiện thực hóa yêu cầu của BABOK v3 về cải tiến liên tục năng lực tổ chức BA. |

---

## (C) Kết quả xác minh pháp lý các thông tin chưa kiểm chứng

Thực hiện nhiệm vụ tra cứu và kiểm chứng pháp lý độc lập, Gemini đã tiến hành tra cứu văn bản quy phạm pháp luật hiện hành trên các cổng thông tin chính thống của Chính phủ và các cơ quan ban ngành (không dán tài liệu nội bộ ra ngoài). Dưới đây là kết quả kiểm chứng chi tiết:

### 1. Khung pháp lý dự án đầu tư ứng dụng CNTT sử dụng vốn nhà nước (liên quan đến C-10 và G-09)

- **Văn bản gốc**: **Nghị định số 73/2019/NĐ-CP** ngày 05/09/2019 của Chính phủ quy định quản lý đầu tư ứng dụng công nghệ thông tin sử dụng nguồn vốn ngân sách nhà nước (*vẫn đang có hiệu lực thi hành*).
- **Văn bản sửa đổi, bổ sung mới nhất**: **Nghị định số 82/2024/NĐ-CP** do Chính phủ ban hành ngày **10/07/2024**, có hiệu lực thi hành ngay từ ngày ký: **10/07/2024**.
- **Nội dung trọng yếu sửa đổi tác động trực tiếp đến công việc BA**:
  + Cập nhật, sửa đổi các quy định về xác định chi phí phát triển, nâng cấp phần mềm nội bộ; chi phí quản lý dự án và chi phí tư vấn đầu tư ứng dụng CNTT.
  + Sửa đổi, bổ sung chính sách ưu tiên đầu tư, thuê, mua sắm các sản phẩm, dịch vụ công nghệ thông tin sản xuất trong nước.
  + Chuẩn hóa thẩm quyền, trình tự, thủ tục lập, thẩm định và phê duyệt Báo cáo nghiên cứu khả thi, Thiết kế cơ sở, Thiết kế thi công và Dự toán cho các dự án CNTT đặc thù.
- **Nguồn xác thực**:
  + [Cổng Thông tin điện tử Chính phủ](https://chinhphu.vn/): Văn bản ban hành Nghị định 82/2024/NĐ-CP ngày 10/07/2024 (truy cập ngày 17/11/2026).
  + [Cổng thông tin Liên đoàn Thương mại và Công nghiệp Việt Nam (VCCI)](https://vcci.com.vn/): Báo cáo hiệu lực thi hành Nghị định số 82/2024/NĐ-CP (truy cập ngày 17/11/2026).
- **Đánh giá kiểm chứng**: Thông tin của Claude tại C-10 là **Chính xác**. Khi dự án có sử dụng nguồn vốn ngân sách nhà nước, hồ sơ Business Case (G-09) bắt buộc phải tuân thủ cấu trúc Báo cáo nghiên cứu tiền khả thi / khả thi theo quy định tại Nghị định 73/2019/NĐ-CP và Nghị định 82/2024/NĐ-CP.

### 2. Khung pháp lý bảo vệ dữ liệu cá nhân (liên quan đến C-13, G-03, G-19 và G-66)

- **Văn bản tiền đề**: **Nghị định số 13/2023/NĐ-CP** ngày 17/04/2023 của Chính phủ về bảo vệ dữ liệu cá nhân (có hiệu lực từ ngày 01/07/2023).
- **Đạo luật chuyên ngành mới nhất**: **Luật Bảo vệ dữ liệu cá nhân năm 2025** (Số hiệu chính thức: **Luật số 91/2025/QH15**), được Quốc hội khóa XV thông qua tại Kỳ họp thứ 9 ngày **26/06/2025**.
- **Ngày chính thức có hiệu lực thi hành**: Ngày **01/01/2026**.
- **Văn bản hướng dẫn thi hành đồng thời**: **Nghị định số 356/2025/NĐ-CP** ban hành ngày 31/12/2025, có hiệu lực từ ngày **01/01/2026** hướng dẫn chi tiết thi hành Luật Bảo vệ dữ liệu cá nhân.
- **Nội dung trọng yếu tác động đến yêu cầu nghiệp vụ và kỹ thuật**:
  + *Phân loại dữ liệu*: Quy định chi tiết danh mục Dữ liệu cá nhân cơ bản và Dữ liệu cá nhân nhạy cảm (thông tin tài chính, sinh trắc học, dữ liệu định vị, nhật ký hành vi trên không gian mạng...).
  + *Nghĩa vụ lập hồ sơ DPIA (G-66)*: Mọi tổ chức, doanh nghiệp tiến hành thu thập, xử lý dữ liệu cá nhân trên quy mô lớn hoặc xử lý dữ liệu cá nhân nhạy cảm đều bắt buộc phải lập Hồ sơ đánh giá tác động bảo vệ dữ liệu cá nhân (DPIA) theo mẫu quy định và gửi về Cục An ninh mạng và phòng, chống tội phạm sử dụng công nghệ cao (A05 - Bộ Công an).
  + *Quyền của chủ thể dữ liệu*: Bổ sung và quy định chặt chẽ các quyền: được biết, đồng ý/rút lại đồng ý, truy cập, chỉnh sửa, yêu cầu xóa dữ liệu; thiết lập chế tài nghiêm ngặt về thời hạn phản hồi yêu cầu của công dân (phải xử lý trong vòng 02 ngày làm việc).
- **Nguồn xác thực**:
  + [Cổng Thông tin điện tử Chính phủ](https://chinhphu.vn/): Thông tin công bố Luật Bảo vệ dữ liệu cá nhân số 91/2025/QH15 và Nghị định 356/2025/NĐ-CP (truy cập ngày 17/11/2026).
  + [Cổng Thông tin điện tử Bộ Công an](https://bocongan.gov.vn/): Hướng dẫn thực thi Luật Bảo vệ dữ liệu cá nhân và lập hồ sơ đánh giá tác động (truy cập ngày 17/11/2026).
  + [Cơ sở dữ liệu văn bản Thư viện Pháp luật](https://thuvienphapluat.vn/): Toàn văn Luật số 91/2025/QH15 (truy cập ngày 17/11/2026).
- **Đánh giá kiểm chứng**: Thông tin của Claude tại C-13 về mốc hiệu lực 01/01/2026 là **Chính xác**. Gemini bổ sung số hiệu chính thức là **Luật số 91/2025/QH15** và văn bản quy định chi tiết là **Nghị định số 356/2025/NĐ-CP**. Việc lập hồ sơ DPIA (G-66) là nghĩa vụ pháp lý bắt buộc đối với hầu hết các giải pháp phần mềm hiện nay tại Việt Nam.

---

## (D) Ý kiến chuyên môn đối với 3 câu hỏi mở của Claude

Dưới góc độ chuyên môn Senior BA, Gemini đóng góp ý kiến tham vấn cho 3 câu hỏi mở tại Mục 4 của Claude (không thay thế quyền quyết định của BA):

### 1. Về vị trí của BA trong các dự án sắp tới (Phía Chủ đầu tư, Nhà cung cấp hay Cả hai?)

- **Phân tích nghiệp vụ**:
  - Khi BA ở **phía Chủ đầu tư (Enterprise / Client BA)**: Trọng tâm công việc là phân tích bài toán kinh doanh, tính toán ROI/Business Case (G-09), xây dựng yêu cầu kỹ thuật mời thầu RFP (G-69), đánh giá lựa chọn nhà thầu (G-08), giám sát nghiệm thu (G-46) và quản trị thay đổi vận hành nội bộ (G-21, G-48, G-68).
  - Khi BA ở **phía Nhà cung cấp (Vendor / SI BA)**: Trọng tâm là giải đáp RFP và demo giải pháp (G-05, G-06), chốt phạm vi hợp đồng SOW & tiêu chí nghiệm thu kỹ thuật (G-70), đặc tả chi tiết URD/SRS (G-25, G-26) và hỗ trợ đội phát triển/UAT (G-39, G-42, G-45).
- **Khuyến nghị chuyên môn**: Đề xuất BA phê duyệt phương án **"Project Profile Configuration"** trong G-13 (BA Plan):
  + Không nên cố định bảng phân công chỉ phục vụ riêng một phía.
  + Khi khởi động bất kỳ dự án nào, tại G-13 BA chỉ cần tích chọn Profile tương ứng:
    * *Profile A: Phía Chủ đầu tư* → Tự động kích hoạt G-69, G-08, G-46; đánh dấu G-05, G-70 là Không áp dụng.
    * *Profile B: Phía Nhà thầu / SI* → Tự động kích hoạt G-05, G-06, G-70; đánh dấu G-69 là Không áp dụng.
    * *Profile C: Dự án phát triển sản phẩm nội bộ (In-house Product)* → Giữ cấu hình tiêu chuẩn khép kín.

### 2. Về việc có dự án sử dụng vốn nhà nước hay không?

- **Phân tích nghiệp vụ**:
  - Dự án ứng dụng CNTT sử dụng vốn nhà nước bắt buộc phải tuân thủ quy trình đầu tư công theo Nghị định 73/2019/NĐ-CP và Nghị định 82/2024/NĐ-CP. Cấu trúc tài liệu đòi hỏi nhiều nội dung đặc thù (Thiết kế sơ bộ, Thiết kế cơ sở, Thuyết minh dự án đầu tư, Bảng phân tích hiệu quả kinh tế - xã hội, Dự toán chi phí phần mềm theo định mức hướng dẫn của Bộ TT&TT). Khối lượng tài liệu và quy trình thẩm định phức tạp hơn nhiều so với dự án vốn tư nhân.
- **Khuyến nghị chuyên môn**:
  + Giữ nguyên mã G-09 và G-03 trong danh mục dùng chung.
  + Trong thư mục `templates/`, xây dựng thêm một nhánh con chuyên biệt: `templates/gov_it_investment/` chứa các biểu mẫu chuẩn hóa theo Nghị định 73/2019 và Nghị định 82/2024 (Mẫu Báo cáo nghiên cứu khả thi, Mẫu thuyết minh dự án CNTT).
  + Khi BA xác nhận dự án thuộc diện vốn ngân sách nhà nước, Claude và Gemini sẽ tự động kích hoạt bộ template chuyên biệt này để thực hiện G-03, G-09 và G-19.

### 3. Về việc dự án có đội ngũ UI/UX chuyên trách hay không?

- **Phân tích nghiệp vụ**:
  - Nếu dự án có Product Designer / UI-UX chuyên trách: Trọng tâm của BA là làm rõ luồng nghiệp vụ (Business Process), Hành trình người dùng (G-64 - CJM), Kiến trúc thông tin (Information Architecture) và Mô hình hóa dữ liệu (G-28). Nếu BA cố vẽ wireframe chi tiết sẽ dễ gây xung đột chuyên môn về Design System, thẩm mỹ và tính khả dụng (Usability).
  - Nếu dự án không có UI/UX riêng (thường gặp ở các hệ thống Back-office, ERP, hệ thống tác nghiệp nội bộ phức tạp): Wireframe do BA dựng lại đóng vai trò tối quan trọng để trực quan hóa yêu cầu cho Stakeholders và Đội phát triển.
- **Khuyến nghị chuyên môn**:
  + Thống nhất đổi mức G-29 từ **Bắt buộc (B) sang Theo điều kiện (Đk)** như đề xuất tại C-13 và M-07.
  + Điều kiện kích hoạt được ghi rõ trong G-13: "Bắt buộc thực hiện khi dự án không có UI/UX Designer riêng, hoặc khi cần mô phỏng trực quan để chốt baseline yêu cầu cho các màn hình nghiệp vụ phức tạp".

---

## 2. Tổng hợp tác động đến bảng phân công công việc

Sau khi tiếp thu các đề xuất tối ưu của cả Claude và Gemini:

| Chỉ số | Bảng Mục 6 hiện tại | Đề xuất của Claude | Đề xuất thống nhất của Gemini | Ghi chú |
|---|---|---|---|---|
| **Tổng số việc** | 68 việc (62 gốc + 6 🆕) | 71 việc (thêm G-69, G-70, G-71) | **70 việc** (thêm G-69, G-70; gộp G-71 vào G-13) | Tinh gọn quy trình, tích hợp vào BA Plan theo BABOK |
| **Claude làm** | 50 việc | 51 việc | **49 việc** | 50 − G-19 − G-42 − G-44 − G-66 + G-61 + G-69 + G-70 |
| **Gemini làm** | 18 việc | 20 việc | **21 việc** | 18 + G-19 + G-42 + G-44 + G-66 − G-61 |
| **Mâu thuẫn quyền ghi file** | 1 việc (G-58) | 0 việc (đã tách) | **0 việc** (đã giải quyết triệt để) | Gemini phụ trách minutes, Claude ghi decision-log |
| **Nguyên tắc kiểm thử độc lập** | Chưa đảm bảo (Claude làm đặc tả kiêm test) | Đã đảm bảo (Gemini làm G-42, G-44) | **Đã đảm bảo toàn diện** | Nâng cao chất lượng kiểm định yêu cầu độc lập |

---

## 3. Kết luận và các bước tiếp theo

1. Gemini đã hoàn thành độc lập toàn bộ 4 nội dung theo yêu cầu Dispatch G-00 của Claude.
2. Bản nhận xét và kết quả xác minh pháp lý này được cam kết lưu trữ bền vững tại file `reviews/G-00_gemini.md` trên nhánh `feature/review-gemini`.
3. Đề nghị Điều phối viên Claude tổng hợp các nội dung đồng thuận và các điểm đề xuất tinh chỉnh của Gemini vào văn bản `reviews/G-00_thongnhat.md` để trình BA xem xét phê duyệt chính thức.
