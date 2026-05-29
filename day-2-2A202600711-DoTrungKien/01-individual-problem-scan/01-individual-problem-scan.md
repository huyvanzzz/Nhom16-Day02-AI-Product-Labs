# 01 — Individual Problem Scan

> Bài cá nhân: scan rộng problems từ trải nghiệm thật → chọn top 3 → Problem Card + draft workflow trước/sau cho từng bài.

## Phase 1 — Bảng scan (8 problems)

| # | Lăng kính | Problem quan sát được | Ai đang đau? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | AI tốt hơn / Pain người khác | Clone một repo về nhưng không biết mã nguồn có lỗ hổng bảo mật nào; báo cáo từ tool quét quá khó hiểu | Dev cá nhân / team nhỏ nhận bàn giao repo, không có chuyên gia bảo mật | Mỗi lần audit ~60'; tool quét trả hàng trăm cảnh báo lẫn false positive; từng có vụ lộ API key trong repo |
| 2 | Tốn thời gian | Nhận dataset mới phải kiểm tra chất lượng dữ liệu thủ công trước khi đưa vào báo cáo | Data Analyst / Data Engineer team nhỏ | Mỗi dataset mất 45-90'; nhiều lần báo cáo sai vì dữ liệu trùng/thiếu |
| 3 | Lặp lại / Pain người khác | Sau họp không ai nhớ chính xác đã quyết định gì, ai làm việc gì; biên bản ghi tay sơ sài | PM, trưởng nhóm và thành viên dự án | Họp 60-90' nhưng tổng hợp lại 20-30'; action item rơi rụng, phải họp lại |
| 4 | Pain người khác / Lặp lại | Nhân viên mới hỏi lặp lại cùng một quy trình; tài liệu rải rác nhiều nơi | HR/đào tạo, người mới, người cũ bị hỏi nhiều | Cùng câu hỏi onboarding lặp mỗi đợt tuyển; tài liệu nằm ở Drive/wiki/email |
| 5 | Lặp lại | Copy dữ liệu giữa Excel và phần mềm khác, gửi email báo cáo hằng ngày | Nhân viên văn phòng, kế toán, hành chính | 1-2 tiếng/ngày cho thao tác lặp; hay nhập sai số liệu |
| 6 | Tốn thời gian | Tìm lại quyết định / câu trả lời cũ trong Discord/Slack/thread | Thành viên nhóm, sinh viên | Scroll lại lịch sử chat 10-20'; nhiều khi không tìm ra, phải hỏi lại |
| 7 | Tốn thời gian | Đọc tài liệu dài / PRD / spec trước deadline | Dev, PM, sinh viên | Tài liệu 20-50 trang, đọc 1-2 tiếng mới nắm ý chính |
| 8 | Lặp lại | Viết báo cáo tuần tổng hợp từ nhiều nguồn (Jira, Slack, số liệu) | Người đi làm, trưởng nhóm | Mỗi tuần 60-90'; format lại nhiều, dễ sót việc |

> Gợi ý chấm: 8 problems → đủ điều kiện bonus +3 nếu vẫn cụ thể (đã ghi actor + dấu hiệu thật cho từng dòng).

## Phase 2 — Chọn top 3

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| 1 | #1 Git Security Review (clone repo) | Actor rõ, workflow vẽ được, bottleneck cụ thể (đọc/phân loại cảnh báo), so sánh được Rule/Workflow/Agent | Chất lượng giải thích của LLM với lỗ hổng phức tạp; nguồn dữ liệu bảo mật cho RAG |
| 2 | #2 Data Quality Auditor | Metric đo được rõ (thời gian audit, Data Quality Score), có cả phương án non-AI mạnh để so sánh | Ranh giới giữa rule cứng và phần thật sự cần AI |
| 3 | #3 Trợ Lý Cuộc Họp | Impact dễ thấy, metric thời gian rõ, AI hỗ trợ một bước rõ ràng (STT + tóm tắt) | Độ chính xác STT tiếng Việt; chi phí xử lý audio |

Lý do loại các bài còn lại: #4 và #6 gần với #2/#3 về dạng RAG nên gộp ý; #5 và #8 thiên về automation/script, ít cần AI để học cách so sánh Rule/Workflow/Agent; #7 hơi rộng cho một buổi lab.

---

## Top 3 Problem Cards

### Problem Card #1 — Git Security Review (clone repo)

```text
┌──────────────────────────────────────────────────────┐
│ PROBLEM CARD #1 — Git Security Review                │
│                                                      │
│ Problem 1 câu: Clone một repo về nhưng không biết    │
│    mã nguồn có lỗ hổng bảo mật nào; báo cáo từ tool  │
│    quét quá khó hiểu để biết lỗi nào thật nguy hiểm. │
│                                                      │
│ Ai đang đau? Lập trình viên cá nhân / team dev nhỏ   │
│    nhận bàn giao repo, không có chuyên gia bảo mật.  │
│                                                      │
│ Workflow hiện tại:                                   │
│    1. Clone repo về máy → 2. Chạy tool quét          │
│    (Semgrep/Bandit) → 3. Đọc hàng trăm cảnh báo      │
│    → 4. Tự tra cứu & đánh giá / sửa thủ công         │
│                                                      │
│ Bước nghẽn nhất: Đọc & phân loại cảnh báo,           │
│    lọc lỗi thật/giả      (~60 phút/lần)              │
│                                                      │
│ Đo thành công bằng gì? Thời gian hiểu + xử lý        │
│    lỗi Critical: 60 phút → dưới 15 phút              │
│                                                      │
│ Quick gut: [x] Workflow (RAG + LLM giải thích)       │
│            [ ] No AI [ ] Rule [ ] Agent              │
└──────────────────────────────────────────────────────┘
```

Bản chi tiết:

```text
Problem 1 câu:
Khi clone một repo về, lập trình viên không biết mã nguồn đó có lỗ
hổng bảo mật nào, và kết quả từ tool quét quá khó hiểu để biết lỗi
nào thật sự nguy hiểm và xử lý thế nào.

Actor:
Lập trình viên cá nhân / team dev nhỏ nhận bàn giao hoặc tiếp nhận
repo (open-source, đối tác, dự án cũ); sinh viên học an toàn thông tin.

Thời điểm / bối cảnh:
Ngay sau khi clone một repo lạ về máy và muốn đánh giá nhanh mức độ
an toàn trước khi dùng, đóng góp hoặc đưa vào hệ thống.

Current workflow:
1. Clone repo về máy.
2. Chạy các tool quét (Semgrep, Bandit, CodeQL...).
3. Đọc hàng trăm cảnh báo dạng kỹ thuật, khó hiểu.
4. Tự đoán cảnh báo nào là thật / false positive.
5. Google + StackOverflow để hiểu nguyên nhân.
6. Tự đánh giá rủi ro & sửa thủ công, không chắc đã đúng cách.

Bottleneck:
Bước 3-4: đọc và phân loại cảnh báo, phân biệt lỗi thật với false
positive — tốn ~60 phút/lần và cần kiến thức bảo mật mà dev không có.

Impact:
Dùng/tích hợp một repo còn lỗ hổng (lộ secret/API key, SQL injection,
XSS...) vào hệ thống; dev mất thời gian, dễ bỏ sót cảnh báo quan trọng.

Success metric:
Thời gian hiểu + xử lý lỗi Critical/High: 60 phút → dưới 15 phút.
Tỉ lệ lỗi Critical bị bỏ sót giảm về ~0.

Non-AI alternative:
Ruleset Semgrep cấu hình sẵn + sắp xếp cảnh báo theo severity. Đủ cho
lỗi rõ ràng nhưng không giải thích nguyên nhân/cách sửa theo ngữ cảnh.

AI hypothesis:
RAG trên kết quả scan + tài liệu bảo mật; LLM giải thích lỗ hổng dễ
hiểu, xếp hạng rủi ro, đề xuất/sinh mã sửa; chatbot hỏi đáp về repo.

Quick gut: [x] Workflow
```

Draft workflow:

```text
CURRENT — ~75 phút / repo
[Clone repo: 2'] → [Chạy tool quét: 8'] → [Đọc cảnh báo: 30']
→ [Lọc thật/giả: 30'] → [Tự sửa/đánh giá: 5']
        ▲ bottleneck: đọc + lọc cảnh báo (60')

FUTURE — ~18 phút / repo
[Upload/clone repo: 2'] → [Tool quét tự chạy: 3']
→ [AI gom + giải thích + xếp hạng rủi ro: 1']
→ [Dev đọc bản giải thích + hỏi chatbot: 10']  ← human boundary
→ [Dev quyết định sửa/bỏ qua: 2']

Boundary: AI chỉ giải thích + đề xuất; dev là người quyết định sửa.
Fallback: AI không chắc / lỗ hổng lạ → hiển thị cảnh báo gốc + link để dev tự xử lý.
```

### Problem Card #2 — AI Data Quality Auditor

```text
Problem 1 câu:
Mỗi lần nhận một dataset mới, Data Analyst phải kiểm tra chất lượng
dữ liệu thủ công và không tin chắc số liệu trong báo cáo dựa trên đó.

Actor:
Data Analyst / Data Engineer trong team nhỏ, chưa có hệ thống data
governance.

Thời điểm / bối cảnh:
Khi nhận file/dataset mới từ nhiều nguồn (CSV, Excel, dump DB) trước
khi đưa vào phân tích hoặc báo cáo.

Current workflow:
1. Nhận file CSV/Excel/dump DB.
2. Mở từng file, kiểm tra bằng mắt + vài hàm pandas.
3. Tìm missing / duplicate / sai định dạng / outlier.
4. Sửa thủ công, ghi chú lại.
5. Mới dám đưa vào phân tích.

Bottleneck:
Bước 2-3 kiểm tra thủ công lặp lại cho mỗi dataset (~45-90 phút) và
dễ bỏ sót lỗi.

Impact:
Báo cáo dựa trên dữ liệu lỗi → quyết định sai; tốn thời gian làm lại.

Success metric:
Thời gian audit 1 dataset: 60 phút → dưới 15 phút; có Data Quality
Score định lượng; tỉ lệ lỗi bị bỏ sót giảm rõ.

Non-AI alternative:
Bộ rule validation cố định (Great Expectations / script pandas) cho
completeness, uniqueness, format. Giải quyết phần lớn lỗi rõ ràng.

AI hypothesis:
LLM + RAG giải thích nguyên nhân lỗi, gợi ý cách làm sạch, trả lời
câu hỏi tự nhiên về dữ liệu; anomaly detection cho outlier/bất thường.

Quick gut: [x] Workflow  (Rule làm phần lớn, AI hỗ trợ giải thích)
```

Draft workflow:

```text
CURRENT — ~60 phút / dataset
[Nhận file: 2'] → [Profiling thủ công: 25'] → [Tìm lỗi: 25']
→ [Ghi chú + sửa: 8']
        ▲ bottleneck: profiling + tìm lỗi thủ công

FUTURE — ~14 phút / dataset
[Upload file: 1'] → [Rule validation tự chạy: 2']
→ [Anomaly detection: 1'] → [AI giải thích lỗi + đề xuất cách sửa: 2']
→ [Analyst xem Data Quality Score + quyết định: 8']  ← human boundary

Boundary: rule + AI chỉ phát hiện & đề xuất; analyst quyết định cách làm sạch.
Fallback: rule không chắc về một cột → đánh dấu "cần người xem", không tự sửa.
```

### Problem Card #3 — AI Trợ Lý Cuộc Họp

```text
Problem 1 câu:
Sau mỗi cuộc họp, không ai nhớ chính xác đã quyết định gì và ai phụ
trách việc gì; biên bản ghi tay sơ sài nên action item hay rơi rụng.

Actor:
PM / trưởng nhóm và thành viên tham gia nhiều cuộc họp dự án.

Thời điểm / bối cảnh:
Trong và ngay sau các cuộc họp nhóm/dự án.

Current workflow:
1. Họp, vừa nghe vừa cố ghi chép.
2. Ghi biên bản tay sơ sài.
3. Sau họp cố nhớ lại quyết định + việc được giao.
4. Gõ lại, gửi cho mọi người (hoặc quên gửi).
5. Người vắng mặt phải hỏi lại từng người.

Bottleneck:
Bước 1-3: vừa nghe vừa ghi nên sót ý; tổng hợp lại tốn 20-30'/cuộc.

Impact:
Action item không ai làm, việc trễ, phải họp lại; người vắng mất thông tin.

Success metric:
Thời gian ra biên bản + action items: 30 phút → dưới 5 phút; tỉ lệ
action item có đủ owner + deadline tăng rõ.

Non-AI alternative:
Template biên bản chuẩn + một người ghi chép chuyên trách. Giúp được
nhưng vẫn tốn người và vẫn sót khi họp nhanh.

AI hypothesis:
Speech-to-Text chuyển âm thanh thành transcript; LLM tóm tắt + trích
action items (người phụ trách, deadline); RAG hỏi đáp nội dung họp.

Quick gut: [x] Workflow
```

Draft workflow:

```text
CURRENT — ~30 phút sau họp (chưa tính sót việc)
[Vừa họp vừa ghi] → [Nhớ lại + gõ biên bản: 20']
→ [Soạn action item: 8'] → [Gửi: 2']
        ▲ bottleneck: nghe + ghi + nhớ lại

FUTURE — ~5 phút sau họp
[Ghi âm họp] → [STT tạo transcript: tự động]
→ [AI tóm tắt + trích action item: 1']
→ [PM rà soát + sửa owner/deadline: 4']  ← human boundary
→ [Tự đẩy action item sang Jira/Notion]

Boundary: AI tạo nháp; PM xác nhận trước khi giao việc.
Fallback: đoạn audio không rõ → giữ transcript thô, đánh dấu "cần xác nhận".
```

---

## Card muốn pitch nhất + challenge (Phase 2/3)

Card tôi muốn pitch nhất:

```text
Problem Card #1 — Git Security Review (clone repo)
```

Vì sao:

```text
Actor và bottleneck rõ nhất, metric đo được bằng thời gian, và là bài
cho thấy rõ vì sao chọn Workflow chứ chưa cần Agent — dễ lập luận chặt.
```

Câu hỏi tôi muốn nhóm challenge:

```text
- Phần "giải thích lỗ hổng" có thật sự cần LLM, hay ruleset + mô tả
  có sẵn của Semgrep đã đủ 70-80% case?
- Nếu LLM giải thích sai một lỗ hổng Critical, ai/điều gì phát hiện?
```

---

## Tự kiểm hiểu bài — mạch cho bài #1 (chuẩn bị cho phần hỏi nhanh 6đ)

- **Problem:** dev clone repo lạ, không biết có lỗ hổng gì, báo cáo tool khó hiểu.
- **Workflow:** clone → quét → đọc & lọc cảnh báo (nghẽn) → đánh giá/sửa.
- **Metric:** thời gian hiểu + xử lý lỗi Critical 60′ → dưới 15′; lỗi Critical bỏ sót ~0.
- **Boundary:** AI chỉ giải thích + xếp hạng + đề xuất; dev quyết định sửa. AI không tự sửa code lên repo.
- **Độ phù hợp AI:** chọn **Workflow** (RAG + LLM hỗ trợ một bước rõ ràng). Chưa cần **Agent** vì không cần tự lập kế hoạch nhiều bước/đổi bước động; **Rule** đơn thuần (chỉ chạy Semgrep) không giải thích được nguyên nhân + cách sửa theo ngữ cảnh.
