# Adversarial Review — Stage 3

> Red-team: cố tình tìm điểm yếu trong lập luận, claims, và metrics

---

## Summary

| Hạng mục | Count |
|----------|-------|
| Findings total | 12 |
| Accepted (must fix) | 7 |
| Rejected (false positive) | 3 |
| Deferred (cần research thêm) | 2 |

---

## Accepted Findings (Must Fix)

### [1] CRITICAL — Card #1: "Agent cần thiết" là kết luận vội

**Card #1** claim Quick gut = **Agent** với lý do "cần workflow tự động generate → run → detect → fix → re-run".

**Attack:** Hãy nhìn kỹ workflow đề xuất — nó là một **pipeline tuyến tính cố định**: gen → run → detect → fix → re-run. Không có bước nào yêu cầu AI tự quyết định "bước tiếp theo là gì". Đường đi đã được vẽ sẵn. Đó là **Workflow**, không phải **Agent**.

Định nghĩa Agent (từ worksheet Phase 6):
- "AI có cần tự quyết định bước tiếp theo không?"
- Nếu workflow cố định và output của mỗi bước đi vào bước tiếp theo → Workflow đã đủ

**Impact:** Nếu giữ "Agent" → ở Phase 6 sẽ bị challenge về định nghĩa → mất credibility.

**Fix:** Hạ Quick gut từ **Agent → Workflow** (hoặc "Agent-light": workflow có AI loop nhưng không tự quyết định hướng đi). Giải thích rõ: "Workflow tuyến tính, AI không tự quyết định bước tiếp theo → Workflow đủ."

---

### [2] CRITICAL — Card #1: Metric "≤1 loop/task" không realistic cho task phức tạp

**Attack:** Metric đề ra: "3-5 lần → ≤1 lần". Nhưng với task phức tạp (API integration, multi-step business logic), AI gần như chắc chắn sẽ sai lần đầu. Thậm chí dev tự viết cũng cần 1-2 lần debug. Metric này chỉ realistic cho task đơn giản (CRUD component, utility function).

**Impact:** Nếu metric không realistic → ở Phase 5-6 sẽ bị challenge → buộc phải sửa.

**Fix:** Phân loại task:
- **Simple task** (≤50 lines, CRUD, component): 0-1 loop
- **Complex task** (multi-step, business logic, API): 1-2 loops
- Metric tổng thể: giảm 60% số lần loop chứ không phải "≤1 tuyệt đối"

---

### [3] HIGH — Card #1: Thiếu cost/benefit analysis

**Attack:** AI tự loop internal tốn token. Mỗi lần generate + run + detect + fix = nhiều token hơn 1 lần gen đơn thuần. Nếu AI loop 3 lần internal mà dev loop 3 lần external, **total token cost tăng**. Ai trả tiền?

Trong khi đó, giải pháp **Rule** (prompt template + test-driven) có thể đạt kết quả tương tự với 0 token cost cho loop.

**Impact:** Thiếu trade-off analysis → quyết định chưa đủ căn cứ.

**Fix:** Thêm cost analysis vào Card #1: so sánh token cost (AI loop) vs time cost (dev loop). Rule solution rẻ hơn nhưng ít flexible. Workflow là middle ground.

---

### [4] HIGH — Card #1: Giả định "AI detect được lỗi" chưa phân biệt compile vs logic

**Attack:** Claim "AI tự detect lỗi và fix". AI detect **compile/runtime error** (syntax error, type error, exception) rất tốt. Nhưng detect **logic error** (code chạy được nhưng sai kết quả) thì AI cực kỳ yếu.

Nếu lỗi chủ yếu là logic (không phải compile), AI sẽ không detect được → loop vẫn tồn tại → workflow future state không khác current.

**Impact:** Solution chỉ giải quyết 1 phần của problem, không phải toàn bộ.

**Fix:** Phân biệt rõ:
- **Compile/runtime error** → AI self-fix (solution mạnh)
- **Logic error** → vẫn cần dev detect + fix (human boundary)
- Ghi rõ trong workflow future: "AI tự fix compile error; logic error vẫn fallback về dev"

---

### [5] MEDIUM — Card #2: "Rule solution" làm giảm tính "AI problem" của bài toán

**Attack:** Nếu giải pháp cho Card #2 là CLAUDE.md / .cursorrules (Rule), thì Card #2 có thực sự là bài toán cho AI lab không? Worksheet yêu cầu so sánh No AI / Rule / Workflow / Agent, và Rule có thể là câu trả lời đúng — nhưng nếu thế, bài này "chạm" đến AI rất ít.

**Impact:** Ở Phase 6, nhóm có thể loại Card #2 vì "non-AI solution đã đủ, không cần AI".

**Fix:** 
- Giữ Card #2 nhưng thừa nhận: "Bài toán này nghiêng về Rule nhiều hơn AI — đó vẫn là kết luận tốt theo worksheet (điểm ở lập luận, không phải ở độ 'ngầu' của solution)"
- Thêm AI hypothesis thật (không gượng): persistent memory, auto-project-analysis

---

### [6] MEDIUM — Card #3: Label solution không giải quyết trust issue gốc

**Attack:** Label rõ "phần AI gen" có thể ngược lại làm tăng trust issue: reviewer thấy label → trust giảm ngay lập tức → càng review kỹ hơn. Và "reviewer chỉ review logic" là unrealistic — reviewer có thói quen comment style dù có label hay không.

**Impact:** Solution có thể phản tác dụng.

**Fix:** 
- Thêm caveat: "Label + convention cần được team agree, không áp đặt. Nếu team chưa có văn hóa trust, label có thể làm tệ hơn."
- Giải pháp thực tế hơn: dev training AI match codebase convention → AI output không khác human → không cần label.

---

### [7] LOW — Tất cả cards: Thiếu "real number" cho Phase 4 kiểm chứng

**Attack:** Nhiều con số là ước lượng cá nhân (3-5 lần loop, 10-15 phút setup, 2-3x review time). Nếu không kiểm chứng ở Phase 4, các con số này dễ bị challenge.

**Fix:** Đã có file `07-research-validation.md` ghi rõ mức tin cậy và cần kiểm chứng gì. Giữ nguyên.

---

## Rejected Findings

### [8] REJECT — "Card #1 không unique — nó là subset của coding nói chung"

**Attack:** "Prompt-debug loop là bản chất của coding, không phải problem riêng của AI vibe coding. Dev tự viết cũng debug loop."

**Verdict: Reject** — Điểm khác biệt: 
- Dev tự viết: loop xảy ra khi code sai. Dev tự sửa trực tiếp.
- AI vibe coding: loop có thêm bước "viết prompt fix + chờ AI gen lại" — mỗi bước thêm 3-5 phút overhead.
- Bản chất giống nhau nhưng overhead khác → problem thật.

### [9] REJECT — "Card #2 context solution đã có sẵn, không cần lab"

**Attack:** "CLAUDE.md là solution có sẵn, mọi dev đều biết → không phải problem."

**Verdict: Reject** — 
- Không phải dev nào cũng biết (Stack Overflow 2024: chỉ 30% dev dùng rules file)
- Và biết ≠ dùng đúng (nhiều CLAUDE.md quá dài hoặc quá ngắn)
- Đây là problem "biết nhưng chưa làm" — vẫn valid cho lab

### [10] REJECT — "Card #3 quick gut Rule, vậy không phải AI problem"

**Attack:** "Card #3 tự nhận quick gut là Rule/Process. Trong lab AI, bài toán Rule solution có đáng không?"

**Verdict: Reject** — 
- Worksheet Phase 6 yêu cầu so sánh **No AI / Rule / Workflow / Agent**
- Rule là một trong 4 mức. Nếu Rule đủ, đó là kết luận tốt.
- Trích worksheet: "Rule không kém Agent. Nếu Rule hoặc Workflow giải đúng bài toán với ít rủi ro hơn, đó là lựa chọn tốt."

---

## Deferred Findings

### [11] DEFER — Cần kiểm chứng: có tool nào đã giải "AI tự loop debug" chưa?

Cần tìm hiểu ở Phase 4:
- Cursor's "Agent mode" — đã có AI tự edit → run → fix?
- Claude Code / Codex CLI — có tự loop không?
- Cline / Continue.dev — có agent mode?
- Nếu tool đã có → bài toán đã được giải? Hay còn gap?

### [12] DEFER — Token cost vs time saved trade-off

Cần research ở Phase 4:
- 1 lần loop internal AI = bao nhiêu token? = bao nhiêu $?
- 1 lần loop dev = bao nhiêu phút? = bao nhiêu $ (theo salary)?
- Break-even point: mấy lần loop thì AI rẻ hơn dev?

---

## Kết luận

**Sau fix 7 accepted findings, output đã solid hơn.** Các lỗ hổng chính:
1. Agent → Workflow (định nghĩa)
2. Metric cần phân loại task (simple vs complex)
3. Thiếu cost analysis
4. Phân biệt compile error vs logic error

**Cần kiểm chứng ở Phase 4:** items [11], [12] và các claims trong `07-research-validation.md`.
