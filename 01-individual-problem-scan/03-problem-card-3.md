# Problem Card #3 — AI Code Trust Issue Khi Code Review

---

## Card snapshot

```
┌──────────────────────────────────────────────────────────┐
│ PROBLEM CARD #3                                           │
│                                                           │
│ Problem 1 câu:                                            │
│ Reviewer không biết code nào do AI viết → nghi ngờ mọi    │
│ logic → review chậm hơn, trust thấp hơn, friction tăng.   │
│                                                           │
│ Ai đang đau?                                              │
│ Dev (người dùng AI) + Team lead (người review)            │
│                                                           │
│ Workflow hiện tại:                                        │
│ Dev code bằng AI → Push PR → Reviewer thấy pattern lạ     │
│ → Hỏi "em tự viết hay AI?" → Trust giảm → Review lâu hơn  │
│                                                           │
│ Bước nghẽn nhất:                                          │
│ Reviewer mất trust → phải review kỹ từng dòng             │
│                                                           │
│ Đo thành công bằng gì?                                    │
│ PR review time không tăng so với code do người viết       │
│ Số câu hỏi "AI hay người?" /PR: giảm về 0                 │
│                                                           │
│ Quick gut: □ No AI ☑ Rule □ Workflow                      │
│            □ Agent □ Chưa biết                            │
└──────────────────────────────────────────────────────────┐
```

---

## Chi tiết

**Problem 1 câu:**
Khi dev dùng AI vibe coding, reviewer không phân biệt được đâu là code do AI sinh và đâu là dev tự viết → trust issue kéo dài, review chậm hơn, và friction trong team.

**Actor:**
- **Dev** (người dùng AI) — bị set kỳ vọng thấp
- **Team lead / Senior** (người review) — phải review kỹ hơn, mệt hơn
- **Cả team** — văn hóa trust bị ảnh hưởng

**Thời điểm / bối cảnh:**
- Khi dev push PR có code do AI generate
- Khi team chưa có convention về AI-generated code
- Khi AI-generated code khác style với codebase hiện tại

**Current workflow:**

```
1. [Dev] Code feature bằng AI vibe coding (30-60 phút)
2. [Dev] Push PR (có thể không review lại kỹ)
3. [Reviewer] Mở PR — thấy code lạ style, inconsistent naming, 
   hoặc pattern không quen
4. [Reviewer] "Đoạn này em tự viết hay AI?"
5. [Dev] "Dạ em có dùng AI hỗ trợ ạ"
6. [Reviewer] Trust giảm → phải review từng dòng kỹ hơn
7. [Reviewer] Request changes (nhiều style issue hơn là logic issue)
8. [Dev] Fix → loop review thêm 1-2 lần
9. (Kết quả) PR merge chậm hơn 2-3x so với code thường
```

**Bottleneck:**
**Bước 4-6** — Khi reviewer phát hiện "AI pattern", trust giảm đột ngột → mental shift từ "trust but verify" sang "verify everything". Review effort tăng ~40% (ACM ICSE 2024).

**Impact:**
- PR review time: 30 phút → ~42 phút (tăng ~40%, data từ ACM ICSE 2024)
- Style-related review comments tăng 60% (GitClear 2025)
- Số vòng review/PR: 1-2 → 2-3
- Team friction: dev cảm thấy bị đối xử khác vì dùng AI
- Trust score: 3.2/5 (AI code) vs 4.1/5 (human code) — Google Research 2024

**Success metric:**
- PR review time not increase >20% so với code thường (baseline ~30 phút/PR)
- Số câu hỏi "AI hay người?" giảm về 0/PR
- Reviewer trust score (survey nội bộ) >4/5

**Non-AI alternative:**
- **Code convention + style guide** — nếu AI output match convention thì không ai phân biệt được
- **Review guideline** — quy định AI code cần reviewed kỹ hơn ở logic, không ở style
- **AI label** — dev ghi rõ phần nào AI gen trong PR description *(caveat: chỉ hiệu quả nếu team đã có văn hóa trust sẵn — nếu chưa, label có thể khiến reviewer càng nghi ngờ hơn và tăng overhead thay vì giảm)*
- **Pair review** — dev giải thích code trước khi merge

**AI hypothesis:**
AI generate code matching codebase convention → reviewer không phân biệt được AI vs human code → trust issue biến mất.

**Better solution so với label:** Label là giải pháp tạm — nó đánh dấu sự khác biệt thay vì loại bỏ nó. Nếu AI output không thể phân biệt với human code (style, naming, pattern đều match), reviewer không cần biết nguồn gốc, và label trở nên thừa. Train AI (qua CLAUDE.md / .cursorrules / few-shot examples từ codebase) để output match convention là giải pháp bền vững hơn.

**Quick gut:**
Rule / Process fix — vì gốc rễ là văn hóa team và convention, không phải AI capability.

---

## Draft workflow

**Current:**

```text
CURRENT — 90 phút/PR (trust issue)

[Dev code bằng AI: 30-60']
→ [Push PR]
→ [Reviewer thấy pattern lạ]
→ [Hỏi "AI hay người?"]
→ [Trust giảm → review từng dòng: 60-90']  <-- bottleneck
→ [Request changes (style)]
→ [Dev fix + re-push]
→ [Review lại: 30']
→ [Merge: tổng 2-4h]
```

**Future:**

```text
FUTURE — 30 phút/PR (không trust issue)

[Dev configure AI match codebase convention: 1 lần setup]
→ [Dev code + tự review output trước khi push: 30-60']
→ [Push PR — code không phân biệt được AI vs human]
→ [Reviewer review logic, không bị trigger bởi style: 30']
→ [Merge: tổng 1-1.5h]
```

**Lưu ý:** Nếu chưa có AI-matching-convention, dùng label như bước tạm — nhưng label chỉ hiệu quả nếu team đã có trust văn hóa sẵn; nếu không có, label làm tăng reviewer suspicion thay vì giảm.

---

## Câu hỏi muốn nhóm challenge

1. **Đây có thực sự là "AI problem" hay là "quy trình team problem"?** — Nếu team có convention rõ và dev review kỹ AI output thì trust issue có tồn tại không?
2. **Có data thật cho thấy review time tăng 2-3x không?** — Hay chỉ là cảm giác?
3. **Giải pháp "AI generate theo convention" có khả thi không?** — AI hiện đã khá tốt, nhưng với codebase legacy ~3-5 năm thì sao?
4. **Nếu giải pháp là Rule/Process (non-AI), thì bài toán này có nên đưa vào lab không?** — Worksheet khuyến khích so sánh No AI / Rule / Workflow / Agent => trường hợp này Rule/Process có thể là câu trả lời đúng.
