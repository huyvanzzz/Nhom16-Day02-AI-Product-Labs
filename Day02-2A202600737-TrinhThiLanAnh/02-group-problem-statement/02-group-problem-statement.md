# 02 — Group Problem Statement

> **Bản nộp nhóm — Nhóm 16**
> Thành viên: Nguyễn Mạnh Quý (2A202600643), Đỗ Trung Kiên (2A202600711),
> Trịnh Thị Lan Anh (2A202600737), Nguyễn Văn Huy (2A202600773)
> 
> Bài toán nhóm chọn: **AI-Assisted Security Repository Review**
> Mức chọn: **Workflow** — Quyết định: **Go với scope nhỏ**

---

## Phase 3 — Group Convergence

### Bước 3.1 — Trình bày top 3

Mỗi người trình bày 3 candidates (1–2 phút/candidate). Tổng cộng 11 candidates.

| # | Người đưa ra | Candidate problem | Người gặp vấn đề | Điểm nghẽn | Cảm nhận nhanh |
|---|---|---|---|---|---|
| 1 | Quý | **Prompt-Debug Loop**: AI gen code → lỗi → re-prompt → lặp 3-5 lần | Dev vibe coding (cá nhân) | Dev copy error + viết prompt fix (10-25 phút/task lãng phí vì loop) | Workflow rất rõ, metric cụ thể, lặp hằng ngày |
| 2 | Quý | **Context Reset**: Mỗi session AI mới mất 10-15 phút giải thích lại context | Dev làm 3-5 session AI/ngày | Setup context mỗi session mới (45-75 phút/ngày) | Rule solution (CLAUDE.md) đã có, nghiêng về non-AI |
| 3 | Quý | **AI Code Trust Issue**: Reviewer không biết code nào do AI → trust giảm → review lâu hơn | Dev + Team lead | Reviewer trust giảm → verify everything (review time +40%) | Thiên về quy trình team hơn là AI capability |
| 4 | Kiên | **Discord CLB FAQ lặp lại**: Câu hỏi quy trình trôi mất trong chat, phải hỏi lại | Thành viên mới + người phụ trách | Chờ trả lời 1-3h + trả lời lặp (30-45 phút/tuần) | Workflow rõ, metric đo được, domain cả nhóm hiểu |
| 5 | Kiên | **Study Note Summary**: Tổng hợp ghi chú ôn thi từ slide + recording + sách | Sinh viên ôn thi | Biến nhiều nguồn rời rạc thành bộ ôn có cấu trúc (nhiều giờ/môn) | Impact cao nhưng quality metric khó đo |
| 6 | Kiên | **Tìm quyết định cũ Discord**: Search keyword rồi đọc nhiều thread | Thành viên nhóm | 10-15 phút/lần tìm, nhiều khi không tìm ra | Trùng nhiều với #4 của Kiên |
| 7 | Lan Anh | **Git Security Review**: Clone repo không biết có lỗ hổng gì; tool quét khó hiểu | Dev cá nhân / team nhỏ | Đọc + phân loại cảnh báo lỗi thật/giả (~60 phút/lần) | Actor rõ, bottleneck cụ thể, đo được metric |
| 8 | Lan Anh | **Data Quality Auditor**: Kiểm tra chất lượng dataset thủ công trước khi dùng | Data Analyst team nhỏ | Profiling + tìm lỗi thủ công cho mỗi dataset (45-90 phút) | Non-AI alternative mạnh (Great Expectations) |
| 9 | Lan Anh | **Meeting Assistant**: Sau họp không ai nhớ quyết định gì, action item rơi rụng | PM, trưởng nhóm | Vừa nghe vừa ghi → sót ý, tổng hợp 20-30 phút/cuộc | STT tiếng Việt là rủi ro kỹ thuật |
| 10 | Huy | **Vinhomes Agent**: Cư dân gửi phản ánh khó theo dõi, ban quản lý mất thời gian phân loại | Cư dân + ban quản lý + bộ phận xử lý | Kiểm tra thông tin → phân loại → giao đúng bộ phận (thủ công) | Agent-heavy, scope dễ phình |
| 11 | Huy | **Vinpearl/VinWonders Travel**: Khách khó chọn lịch trình vì quá nhiều lựa chọn | Khách du lịch + tư vấn viên | Tự đọc → so sánh → ghép lịch trình (45-60 phút) | Cần data thời gian thực về giá/phòng |
| — | Huy | **VinFast EV Guide**: Khách mới mua xe điện khó tìm hướng dẫn đúng tình huống | Khách mới mua xe | Tìm đúng hướng dẫn theo tình huống cụ thể | Rủi ro an toàn cao nếu AI sai |

### Bước 3.2 — Gom trùng / cluster

| Cluster | Candidates included | Pattern chung | Ghi chú |
|---|---|---|---|
| **A. AI Code Quality & Debug** | #1 (Quý), #2 (Quý), #3 (Quý) | Vòng lặp debug, context mất, trust issue — đều xoay quanh chất lượng code AI | 3 bài của Quý đều về cùng ecosystem: vibe coding |
| **B. Knowledge/FAQ Retrieval** | #4 (Kiên), #6 (Kiên), #9 (Lan Anh) | Thông tin bị kẹt trong chat/tài liệu → khó tìm lại | Pattern RAG/FAQ retrieval |
| **C. Code/Data Security & Quality** | #7 (Lan Anh), #8 (Lan Anh) | Kiểm tra chất lượng code/data sau khi nhận về | Đều có bước "scan → phân tích → báo cáo" |
| **D. Service/Process Automation** | #10 (Huy), #11 (Huy), #5 (Kiên) | Hỗ trợ quy trình nhiều bước, cần phối hợp nhiều nguồn | Agent-heavy, scope rộng |

### Bước 3.3 — Shortlist

| Candidate | Vì sao vào shortlist | Rủi ro / điều chưa rõ |
|---|---|---|
| **#7 — Git Security Review** | Actor rõ (dev không chuyên security), workflow tuyến tính, bottleneck cụ thể (đọc/lọc cảnh báo), metric đo được (60→15 phút), cả nhóm đều từng clone repo lạ | Nguồn dữ liệu bảo mật cho RAG; AI giải thích lỗ hổng phức tạp có chuẩn không |
| **#4 — Discord CLB FAQ** | Workflow rõ, metric time-to-answer, cả nhóm hiểu domain CLB | Cần KB curate trước; pinned FAQ thủ công (Rule) có đủ không |
| **#1 — Prompt-Debug Loop** | Workflow rất rõ, lặp hằng ngày, có market data xác nhận (Uplevel, GitClear 2024-2025) | Compile vs logic error ratio chưa rõ; solution có tool thị trường đã làm (Cursor, Claude Code) |

### Bước 3.4 — Score để đồng thuận

| Candidate | Actor rõ (1-5) | Workflow rõ (1-5) | Pain evidence (1-5) | Impact đo được (1-5) | Làm trong lab (1-5) | So sánh R/W/A (1-5) | Nhóm hiểu domain (1-5) | **Tổng** |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| **Git Security Review** | 5 | 5 | 4 | 5 | 4 | 5 | 4 | **32** |
| Discord CLB FAQ | 5 | 4 | 4 | 4 | 5 | 4 | 5 | 31 |
| Prompt-Debug Loop | 4 | 5 | 5 | 5 | 3 | 5 | 5 | 32 |

**Candidate nhóm chọn:**

```text
Git Security Review — AI hỗ trợ đọc và giải thích kết quả
quét bảo mật repository
```

**Vì sao chọn:**

```text
- Actor rõ nhất: dev cá nhân / team nhỏ không có chuyên gia bảo mật — 
  ai trong nhóm cũng từng là dev clone repo lạ
- Workflow tuyến tính rõ ràng: clone → scan → đọc → lọc → sửa
- Bottleneck cụ thể: đọc và phân loại hàng trăm cảnh báo lỗi thật/giả
- Metric đo được: thời gian xử lý lỗi Critical/High
- So sánh Rule/Workflow/Agent rất rõ:
  - Rule: chạy Semgrep + sắp xếp severity → giải thích không có
  - Workflow: RAG + LLM giải thích lỗ hổng, dev quyết định
  - Agent: AI tự scan + tự sửa code → quá rộng, rủi ro cao
- Domain: cả nhóm đều là dev, hiểu workflow clone repo và tool quét
```

**Vì sao không chọn các candidate còn lại:**

```text
- Discord CLB FAQ: Bài tốt nhưng thiên về non-AI (pinned FAQ đã giải 70%).
  Rule solution có thể đủ → worksheet khuyến khích Rule là kết luận tốt,
  nhưng bài này ít "cơ hội" so sánh AI hơn.

- Prompt-Debug Loop: Workflow rất rõ nhưng đã có tool thị trường giải 
  (Cursor Agent, Claude Code tự loop). Lab sẽ khó tạo insight mới.
  
- Các bài còn lại: scope quá rộng (Vinhomes Agent, VinFast Guide) hoặc
  quality metric khó đo (Study Note, Meeting Assistant).
```

**Nếu có disagreement, nhóm xử lý thế nào:**

```text
Có disagreement giữa Git Security Review (Lan Anh) và Discord CLB FAQ (Kiên).
Nhóm giải quyết bằng scoring table — cả hai cùng điểm (32), nhưng Git Security
Review có lợi thế: (1) cả team đều từng clone repo lạ, (2) so sánh R/W/A rõ
hơn, (3) bài toán gần với AI hơn (cần LLM giải thích, không chỉ Rule).
Kiên đồng ý vì lập luận này.
```

---

## Phase 4 — Quick Validation + Research

### Bước 4.1 — Quick validation

Nhóm thực hiện 2 hình thức: quick interview (3 dev cụ thể) và mini survey (6 người trong lớp).

**Quick interview chi tiết:**
- **Dev A** (bạn cùng lớp, thực tập sinh frontend): "Tôi clone repo từ GitHub về học, không bao giờ check security. Có lần clone một repo React bị lỗi dependency cũ, không biết có nguy hiểm không."
- **Dev B** (bạn cùng lớp, làm project nhóm): "Tôi có chạy Semgrep một lần nhưng thấy ~200 warnings, không biết cái nào quan trọng nên bỏ qua luôn."
- **Dev C** (dev full-time, 2 năm kinh nghiệm): "Team tôi dùng Dependabot cho dependency. Source code thì không ai check. Nếu có tool giải thích lỗ hổng tự động thì tốt."

**Mini survey questions:** (1) "Bạn có từng clone repo GitHub và không biết nó có lỗ hổng không?" (2) "Bạn có thường check security trước khi dùng repo không?" (3) "Nếu có, bạn dùng tool gì?"

| Nguồn | Số người / số mẫu | Tín hiệu xác nhận | Tín hiệu phản bác | Nhóm sửa problem thế nào |
|---|---:|---|---|---|
| Quick interview | 3 dev (2 bạn học, 1 dev đi làm) | 3/3 từng clone repo lạ và không biết có lỗ hổng gì. 2/3 nói "chỉ chạy Semgrep rồi bỏ qua vì đọc không hiểu" | 1 dev nói "dùng Dependabot tự động fix dependency là đủ cho team mình" | Thu hẹp: không phải "tự động fix security", mà là "giải thích kết quả scan cho dev không chuyên — dev tự quyết định fix" |
| Mini survey trong lớp | 6 người | 4/6 từng clone repo từ GitHub, không check security. 3/4 nói "không biết bắt đầu từ đâu" | 2/6 nói "chạy npm audit là đủ" | Làm rõ: npm audit chỉ check dependency, không check source code. Problem thật là check source code security — scope chặt hơn. |
| Kinh nghiệm cá nhân | 4 thành viên nhóm | Quý: từng bị lộ API key trong repo vì không check. Huy: từng nhận repo bàn giao không biết có lỗ hổng gì | — | Metric được điều chỉnh dựa trên kinh nghiệm thật |

**Insight sau validation:**

```text
Pain thật không nằm ở việc "scan security" (tool đã làm tốt). 
Pain nằm ở đoạn SAU KHI scan: dev không đọc được hàng trăm 
cảnh báo kỹ thuật, không phân biệt được lỗi thật vs false 
positive, và không biết cách sửa an toàn.

-> Problem shift: từ "tự động scan security" 
              → "giải thích kết quả scan dễ hiểu + đề xuất cách sửa"
```

### Bước 4.2 — Research giải pháp đã có

Nhóm tìm 4 existing solutions/tools, phân tích phần nào họ giải quyết và khoảng trống còn lại.

| Nguồn / tool / case | Link | Họ giải quyết phần nào? | Điểm mạnh | Khoảng trống / rủi ro | Bài học cho nhóm |
|---|---|---|---|---|---|
| **Semgrep** (r2c) | https://semgrep.dev | Scan source code với custom rules, phát hiện vulnerability patterns | Rule engine mạnh, có community rules, OSS. Phát hiện nhanh OWASP Top 10 | Output dạng raw JSON/terminal — khó đọc với dev không chuyên. Không giải thích lỗ hổng theo ngữ cảnh codebase. | Rule component có sẵn và miễn phí. Nhóm chỉ cần thêm layer giải thích. Không cần build scanner từ đầu. |
| **CodeQL** (GitHub) | https://codeql.github.com | Deep semantic analysis, tìm lỗ hổng qua data flow, taint tracking | Rất chính xác, ít false positive, integrated với GitHub | Setup phức tạp, query language riêng (QL). Chậm với codebase lớn. | Đối thủ nặng — nhóm tập trung vào dev cá nhân/team nhỏ không có resource cho CodeQL. |
| **SonarQube / SonarCloud** | https://www.sonarsource.com | Code quality + security scanning, có dashboard, có giải thích (description) | Dashboard đẹp, có giải thích từng rule, tích hợp CI/CD | Giải thích ở mức "generic description", không theo ngữ cảnh code cụ thể. Nhiều tính năng nhưng dev hay bỏ qua security tab. | AI có thể thêm: giải thích theo ngữ cảnh codebase + gợi ý sửa cụ thể. |
| **GitHub Advisory Database + Dependabot** | https://github.com/advisories | Tự động phát hiện + fix dependency vulnerabilities | Auto-fix dependency, tích hợp GitHub | Chỉ check dependency (package.json, requirements.txt), không check source code. | Bổ sung cho source code scanning, không thay thế. |

**Research takeaway:**

```text
Không build scanner từ đầu. Tool thị trường (Semgrep, CodeQL) 
đã giải quyết bước "phát hiện lỗ hổng" rất tốt. Khoảng trống 
thị trường là layer "giải thích + xếp hạng" cho dev không chuyên.

Hướng phù hợp: Workflow gồm:
1. Rule: chạy Semgrep với ruleset bảo mật (miễn phí, OSS)
2. AI: RAG + LLM giải thích từng cảnh báo theo ngữ cảnh code
3. Human: dev đọc giải thích → quyết định fix/bỏ qua

Đây là workflow tuyến tính, không cần Agent.
```

---

## Phase 5 — Workflow + Problem Statement

### Bước 5.1 — Current workflow bản nhóm

```text
CURRENT STATE — 6 bước, ~75 phút / repo

[1️⃣ Dev: Clone repo lạ về máy: 2']
→ [2️⃣ Dev: Chạy tool quét (Semgrep/Bandit): 8']
→ [3️⃣ Dev: Đọc hàng trăm cảnh báo dạng kỹ thuật: 30']  <-- BOTTLENECK
→ [4️⃣ Dev: Lọc lỗi thật vs false positive: 30']           <-- BOTTLENECK
→ [5️⃣ Dev: Google/StackOverflow tra cách sửa: 10']
→ [6️⃣ Dev: Sửa thủ công / quyết định bỏ qua: 5']
```

| Bước | Actor | Input | Output | Thời gian/tần suất | Ghi chú |
|---|---|---|---|---|---|
| 1 | Dev | URL repo / git clone | Source code local | 2 phút | Mỗi lần nhận repo mới |
| 2 | Dev (tool) | Source code | Raw scan report (JSON/terminal) | 8 phút | Semgrep ruleset mặc định |
| 3 | Dev | Raw scan report (100-500 warnings) | Dev hiểu một phần cảnh báo | 30 phút | Cảnh báo kỹ thuật: CWE, OWASP — dev không chuyên không hiểu |
| 4 | Dev | Cảnh báo đã đọc sơ | Danh sách lỗi thật cần xử lý | 30 phút | Phải biết pattern nào là false positive cho codebase này |
| 5 | Dev | Danh sách lỗi thật | Hiểu nguyên nhân + cách sửa | 10 phút | Google/StackOverflow hoặc tài liệu bảo mật |
| 6 | Dev | Hiểu cách sửa | Code đã fix hoặc quyết định bỏ qua | 5 phút | Nếu không chắc → bỏ qua (rủi ro) |

**Bottleneck chính:**

```text
Bước 3 + 4: đọc và phân loại cảnh báo lỗi thật/giả.
Tốn ~60 phút / lần (75% tổng thời gian). Yêu cầu kiến thức bảo mật 
mà dev không có → dễ bỏ sót lỗi Critical hoặc mất thời gian với 
false positive.
```

### Bước 5.2 — Future workflow bản nhóm

```text
FUTURE STATE — 5 bước, ~18 phút / repo

[1️⃣ Dev: Clone repo + Upload/path: 2']            -- Dev làm
→ [2️⃣ Rule: Chạy Semgrep tự động: 3']             -- Rule
→ [3️⃣ AI: Gom + giải thích + xếp hạng rủi ro: 1']  -- Workflow step
→ [4️⃣ Dev: Đọc bản giải thích + hỏi chatbot: 10']   -- Human boundary
→ [5️⃣ Dev: Quyết định sửa/bỏ qua: 2']              -- Human boundary

Fallback:
- AI không chắc / lỗ hổng lạ → hiển thị cảnh báo gốc + link CWE/OWASP
- LLM giải thích sai → dev có nút "báo cáo sai" → feedback loop
- Alert ≥1 Critical → bắt buộc tag người review thứ 2
```

**Before/after impact:**

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---:|---:|---|
| Số bước | 6 | 5 | Bước "lọc thật/giả" được AI hỗ trợ |
| Tổng thời gian | ~75 phút | ~18 phút | Giảm ~76% — target chính |
| Số bước thủ công (dev) | 5/6 | 3/5 | Dev vẫn clone, đọc giải thích, quyết định |
| Bottleneck chính | Đọc + lọc cảnh báo (60') | Dev đọc giải thích (10') | Human boundary — bottleneck chấp nhận được |
| Risk mới | Bỏ sót lỗi Critical | LLM hallucination — giải thích sai | Dev vẫn là người quyết định cuối |

### Bước 5.3 — Problem Statement v0

| Field | Nội dung |
|---|---|
| **Actor** | Developer cá nhân / team dev nhỏ nhận bàn giao hoặc clone repository lạ, không có chuyên gia bảo mật trong team. |
| **Workflow** | Clone repo → chạy tool quét (Semgrep/Bandit/CodeQL) → đọc hàng trăm cảnh báo kỹ thuật → tự lọc lỗi thật vs false positive → Google/StackOverflow tra cách sửa → sửa thủ công hoặc bỏ qua. |
| **Bottleneck** | Bước đọc và phân loại cảnh báo lỗi thật/giả (bước 3-4) tốn khoảng 60 phút/lần (75% tổng thời gian), yêu cầu kiến thức bảo mật chuyên sâu mà dev không có. |
| **Impact** | Mỗi lần security review mất ~75 phút. Dev dễ bỏ sót lỗi Critical (lộ secret, SQL injection, XSS). Nếu dùng repo có lỗ hổng, hệ thống production bị ảnh hưởng. |
| **Success Metric** | Thời gian hiểu và xử lý lỗi Critical/High: từ ~60 phút xuống dưới 15 phút. Tỉ lệ lỗi Critical bị bỏ sót: giảm đáng kể (mục tiêu <5% so với baseline hiện tại). Số lần dev phải Google/StackOverflow: từ ~5-10 lần/repo → 0-2 lần. |
| **Boundary** | AI không tự sửa code lên repo. AI không tự quyết định lỗi nào là false positive — dev là người quyết định cuối. AI chỉ giải thích dựa trên kết quả scan + tài liệu bảo mật, không tự bịa thêm lỗ hổng. Không xử lý lỗ hổng ở mức infrastructure (OS, network). |

---

## Phase 6 — Rule / Workflow / Agent + Decision

### Bước 6.0 — Bài toán nhóm nằm ở ô nào?

Ma trận: (Độ mơ hồ thấp/cao) × (Độ phức tạp thấp/cao).

```text
Ô nhóm chọn: Độ phức tạp thấp — Độ mơ hồ thấp
```

**Vì sao:**

```text
Độ phức tạp thấp:
- Workflow tuyến tính: scan → giải thích → quyết định
- 3 bước chính, output mỗi bước đi vào bước tiếp theo
- Chỉ có 1 nguồn dữ liệu chính (kết quả scan)

Độ mơ hồ thấp:
- Output "giải thích lỗ hổng" có thể khác nhau về wording, nhưng nội 
  dung phải chính xác dựa trên CWE/OWASP — không được bịa
- Xếp hạng rủi ro theo severity (Critical/High/Medium/Low) — khá rõ
- Không cần AI tự quyết định "bước tiếp theo"
```

### Bước 6.1 — So sánh Rule / Workflow / Agent

| Mức | Phương án cho bài toán nhóm | Khi nào đủ | Rủi ro | Chọn? |
|---|---|---|---|---|
| **Rule** | Semgrep ruleset + severity sort + CWE description có sẵn. Dev tự đọc và tự search. | Nếu dev đã có kiến thức bảo mật cơ bản, chỉ cần sorted list | Không giải thích theo ngữ cảnh codebase. Dev không chuyên vẫn không hiểu. Output khô khan. | Không chọn — không giải quyết được bottleneck |
| **Workflow** | Rule (Semgrep scan) → AI (RAG + LLM giải thích + xếp hạng) → Human (dev quyết định) | Workflow tuyến tính, mỗi bước rõ ràng. AI chỉ hỗ trợ một bước: "giải thích". Không cần AI tự lập kế hoạch. | LLM hallucination: giải thích sai lỗ hổng. Token cost cho codebase lớn. | **Chọn** |
| **Agent** | Agent tự clone repo, tự chạy scan, tự phân tích, tự hỏi dev clarify, tự quyết định fix/bỏ qua | Cần khi workflow nhiều nhánh, nhiều tool, cần tự đổi hướng | Quá rộng. Permission nguy hiểm. Rủi ro hallucination × nhiều bước. | Không chọn — overkill |

**Mức chọn:**

```text
Workflow
```

**Vì sao chọn:**

```text
1. Workflow tuyến tính: scan → giải thích → quyết định. 
   Các bước cố định, AI không cần tự lập kế hoạch.
2. Rule (Semgrep) đã giải quyết bước "phát hiện" rất tốt. 
   Chỉ cần thêm layer AI "giải thích" — không cần build lại.
3. Human review rõ: dev đọc giải thích → quyết định sửa/bỏ qua.
   AI sai → dev vẫn là người kiểm soát cuối.
4. So với Agent: không cần permission tự sửa code lên repo.
   Risk thấp hơn, scope chặt hơn.
```

**Vì sao không chọn mức đơn giản hơn (Rule):**

```text
Rule (Semgrep + severity sort) không giải quyết được bottleneck:
dev không hiểu cảnh báo kỹ thuật. Rule không thể giải thích 
"tại sao dòng code này là SQL injection" trong ngữ cảnh codebase 
cụ thể. Đây là tác vụ ngôn ngữ tự nhiên → cần LLM.

Non-AI alternative (chỉ dùng Semgrep + Google) vẫn tồn tại như
fallback. Nếu AI không available, dev quay về workflow cũ.
```

### Bước 6.2 — Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Developer cá nhân / team dev nhỏ nhận bàn giao repo, không có chuyên gia bảo mật. |
| **Workflow** | Clone repo → chạy Semgrep → AI gom + giải thích + xếp hạng → dev đọc + hỏi chatbot → dev quyết định. |
| **Bottleneck** | Đọc và phân loại ~100-500 cảnh báo bảo mật dạng kỹ thuật, tốn ~60 phút/lần, cần chuyên môn bảo mật. |
| **Impact** | ~75 phút/repo. Dễ bỏ sót lỗi Critical. Nếu deploy repo có lỗ hổng → ảnh hưởng production. |
| **Success Metric** | Thời gian xử lý Critical/High: 60 phút → <15 phút. Lỗi Critical bỏ sót: mục tiêu <5% (so với baseline hiện tại). Số lần Google/StackOverflow: 5-10 → 0-2. |
| **Boundary** | AI KHÔNG tự sửa code, KHÔNG tự quyết định false positive, KHÔNG tự bịa lỗ hổng. Chỉ giải thích kết quả scan. Dev quyết định cuối. |
| **AI intervention point** | Sau bước Semgrep scan (Rule), trước bước dev đọc cảnh báo. AI nhận raw scan results → output: bản giải thích + xếp hạng rủi ro + gợi ý cách sửa. |
| **Mức chọn** | **Workflow**: Rule (Semgrep) → AI (RAG + LLM giải thích) → Human (dev quyết định). |
| **Rủi ro & người thật kiểm tra** | Rủi ro 1: LLM hallucination — giải thích sai lỗ hổng Critical. Mitigation: dev vẫn đọc và quyết định. Rủi ro 2: Token cost cho codebase >10K lines. Mitigation: chỉ scan file thay đổi, không scan toàn bộ. Người thật kiểm tra: dev review từng lỗ hổng trước khi quyết định. |

### Bước 6.3 — Final decision

| Câu hỏi | Yes / Not Yet / No | Ghi chú |
|---|---|---|
| Actor và workflow đã rõ chưa? | **Yes** | Dev clone repo lạ; workflow 6 bước đã vẽ rõ |
| Baseline và success metric đã đo được chưa? | **Yes** | Baseline ~75 phút; target <18 phút; metric đo bằng thời gian và tỉ lệ bỏ sót |
| Có data/input đủ dùng chưa? | **Yes** | Input = raw scan results từ Semgrep (OSS, free). RAG corpus = tài liệu OWASP, CWE, Semgrep rule docs |
| Nếu AI sai, hậu quả có chấp nhận được không? | **Yes** | AI không tự sửa code. Dev đọc + quyết định. AI sai = dev bỏ qua hoặc tự search. Không ảnh hưởng production. |
| Có người review/owner vận hành không? | **Yes** | Chính dev là người review, không cần thêm người. |
| Có cách non-AI đơn giản hơn không? | **Yes** | Chỉ chạy Semgrep + Google — rẻ hơn, không hallucination. Nhưng không giải quyết được bottleneck. |

**Decision:**

```text
Go với scope nhỏ (pilot).
```

**Lý do:**

```text
1. Problem rõ, workflow rõ, metric rõ — đủ điều kiện để pilot.
2. Critical risk được kiểm soát: AI không tự sửa code, dev quyết định cuối.
3. Có non-AI fallback: Semgrep + Google (workflow cũ).
4. Chi phí thấp: Semgrep free + LLM API cost ước lượng ~$0.05-0.20/repo (dựa trên Claude API pricing ~$3/1M input tokens, estimate cho codebase ~5K lines ~10-50K tokens). Cần kiểm chứng với codebase lớn hơn.
5. Học được pattern RAG + LLM cho security domain — transferable sang 
   các bài toán "giải thích kết quả scan" khác (Data Quality, Infra Scan).
```

**Pilot nhỏ nhất:**

```text
- Scope: 1 repo mẫu (project <5K lines, 1-2 languages: Python/JS)
- Tool: Semgrep OSS + Claude API (hoặc Gemini)
- Cách chạy: bán thủ công — dev chạy Semgrep → paste output vào 
  prompt chuẩn → AI trả bản giải thích → dev đọc + đánh giá
- Đo: thời gian từ lúc có scan results đến lúc dev quyết định xong
- Duration: 2-3 lần chạy với 2-3 repo khác nhau
- Success: thời gian giảm ≥50%, dev hiểu được lỗi mà không cần 
  Google thêm
```

**Exit / rollback:**

```text
- Nếu AI giải thích sai >2 lỗi Critical trong 3 lần chạy → dừng pilot,
  quay về Rule (Semgrep + severity sort) — vẫn tốt hơn baseline.
- Nếu token cost >$1/repo → cần optimization (chỉ scan critical files)
  hoặc dùng model rẻ hơn.
- Nếu dev vẫn phải Google >5 lần dù có AI giải thích → AI chưa đủ tốt,
  cần fine-tune RAG corpus.
```

---

*Day 02 Lab — Group Problem Statement — Nhóm 16*
