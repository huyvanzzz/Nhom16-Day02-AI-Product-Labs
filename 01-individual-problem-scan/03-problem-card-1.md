# Problem Card #1 — Prompt-Debug Loop

> **Card tôi muốn pitch nhất**

---

## Card snapshot

```
┌──────────────────────────────────────────────────────────┐
│ PROBLEM CARD #1                                           │
│                                                           │
│ Problem 1 câu:                                            │
│ Mỗi lần AI generate code, dev phải chạy → debug →        │
│ re-prompt → chạy lại, lặp 3-5 lần trước khi có code chạy │
│                                                           │
│ Ai đang đau?                                              │
│ Developer (tôi) — build tính năng bằng vibe coding        │
│                                                           │
│ Workflow hiện tại:                                        │
│ Prompt intent → AI gen code → Run test → Lỗi?             │
│ → Copy error → Re-prompt → Run → Pass? → (lặp) → Merge   │
│                                                           │
│ Bước nghẽn nhất:                                          │
│ Re-prompt & wait AI sửa (10-15 phút/lần)                  │
│                                                           │
│ Đo thành công bằng gì?                                    │
│ Giảm loop 60%; simple task 0-1 lần, complex 1-2 lần      │
│                                                           │
│ Quick gut: □ No AI □ Rule ☑ Workflow                      │
│            □ Agent □ Chưa biết                            │
└──────────────────────────────────────────────────────────┘
```

---

## Chi tiết

**Problem 1 câu:**
Mỗi khi dùng AI vibe coding, tôi mất 45-90 phút/task chỉ để loop giữa generate → debug → re-prompt, thay vì 15-30 phút nếu AI ra đúng ngay lần đầu.

**Actor:**
Developer cá nhân (solo dev / feature owner) dùng AI code assistant.

**Thời điểm / bối cảnh:**
- Mỗi khi implement feature mới hoặc fix bug bằng AI
- Xảy ra 5-10 lần/ngày
- Đặc biệt nặng khi task có logic phức tạp (API integration, business rule)

**Current workflow 7 bước:**

```
1. [Dev] Viết prompt mô tả feature cần làm
2. [AI] Generate code (30 giây - 2 phút)
3. [Dev] Copy → run/test
4. [Dev] Phát hiện lỗi (runtime error, logic sai, type error)
5. [Dev] Copy error → viết lại prompt bảo AI fix   <-- BOTTLENECK
6. [AI] Generate lại code (30 giây - 2 phút)
7. [Dev] Quay lại bước 3 (lặp 3-5 lần trung bình)
```

**Bottleneck:**
**Bước 5** — Dev phải tự phát hiện lỗi, copy error message, viết lại prompt bảo AI fix. Mỗi lần mất 2-5 phút để diagnostic + viết prompt, cộng 30s-2p chờ AI generate. Lặp 3-5 lần → tổng 10-25 phút/task chỉ cho riêng loop debug.

**Impact:**
- 45-90 phút/task bị mất vì loop debug (estimate từ 3 task/ngày)
- 5-10 lần ngắt flow/tuần → mất tập trung, cognitive load cao
- Nếu task đơn giản (< 30 phút tự viết), loop làm task mất 2-3x thời gian dự kiến

**Success metric:**
- **Phân loại task:**
  - Simple task (≤50 lines, CRUD, component, utility): 3-5 lần → **0-1 lần**
  - Complex task (multi-step business logic, API integration): 3-5 lần → **1-2 lần**
- Thời gian/task:
  - Simple: 30-45 phút → ≤15 phút
  - Complex: 60-90 phút → ≤30 phút
- Dev không phải copy-paste error message thủ công

> **Lưu ý:** Metric này phân loại theo độ phức tạp vì task AI hay gặp cả 2 loại. Task đơn giản (component, CRUD) AI ra đúng cao; task phức tạp (business logic, multi-step) gần như chắc chắn cần ≥1 lần sửa.

**Non-AI alternative:**
- Tự viết tay — mất 15-30 phút nhưng không loop
- Dùng snippet / template cho code mẫu
- Training prompt kỹ hơn ngay từ đầu (few-shot, specification)

**AI hypothesis:**
AI tự detect lỗi ngay khi generate — nhưng cần phân biệt:
- **Compile/runtime error** (syntax, type, exception): AI detect và tự fix TỐT — solution mạnh
- **Logic error** (code chạy được nhưng sai kết quả): AI detect YẾU — vẫn cần dev phát hiện

Solution focus: AI tự loop fix compile/runtime error. Logic error vẫn fallback về dev. Kỳ vọng 70-80% lỗi là compile/runtime, 20-30% là logic.

**Cost analysis (AI loop vs dev loop):**
- 1 lần loop AI internal: ~500-2000 tokens (gen + run + detect + fix) ≈ $0.01-0.04
- 1 lần loop dev: ~5-10 phút ≈ $1-3 (theo salary $60-100K)
- Break-even: AI loop 100 lần internal = 1 lần dev loop (về cost)
- Trade-off: AI loop rẻ hơn nhiều, nhưng quality thấp hơn (không detect logic error)

**Quick gut:**
**Workflow** (không phải Agent) — vì workflow tuyến tính cố định: generate → run → detect → fix → re-run. AI không cần tự quyết định bước tiếp theo (định nghĩa Agent theo worksheet Phase 6). Đây là pipeline đã được vẽ sẵn, thuộc Workflow.

> **Phân biệt:** Agent = AI tự quyết định bước tiếp theo. Ở đây, các bước gen→run→detect→fix→re-run đã được xác định trước → Workflow đủ. Nếu sau này AI cần tự quyết định 'nên test thêm case nào' hoặc 'nên hỏi dev để clarify requirement', lúc đó mới cần Agent.

---

## Draft current workflow

```text
CURRENT STATE — 60-90 phút/task

[1 Prompt: 2-5']
→ [2 AI gen code: 1']
→ [3 Run/test: 1-2']
→ [4 Phát hiện lỗi: 2-5']
→ [5 Viết prompt fix (copy error): 3-5']  <-- BOTTLENECK
→ [6 AI gen lại: 1']
→ [7 Chạy lại: 1-2']
→ (lặp 3-5 lần, mỗi lần 5-10 phút)
→ [8 Pass → Merge: 5']

Tổng: 7 bước + 3-5 vòng lặp
Thời gian hữu ích: ~15 phút (viết code đúng)
Thời gian lãng phí: ~45-75 phút (loop debug)
```

## Draft future workflow

```text
FUTURE STATE — 20-30 phút/task

[1 Dev prompt: 2-5']
→ [2 AI gen + tự chạy test: 1']
→ [3 AI detect error + tự sửa: 2-5']  <-- AI tự loop
→ [4 AI re-run: 1']
→ [5 AI trả code đã pass test: 1']
→ [6 Dev review + merge: 10-15']     <-- human boundary

Tổng: 6 bước, 0 vòng lặp thủ công
}
```

**Fallback:**
- AI loop >3 lần không pass → báo dev: 'Code chưa pass test X. Error: ...' → dev handle thủ công
- Logic error detected by dev → fix prompt hoặc tự sửa (không nằm trong scope AI loop)

---

## Câu hỏi muốn nhóm challenge

1. **Workflow vs Agent — ranh giới ở đâu?** Tôi đã hạ Quick gut từ Agent xuống Workflow. Nhưng nếu AI cần tự quyết định 'nên chạy test case nào' hoặc 'cần hỏi dev để clarify', có cần Agent không? Hay Workflow vẫn đủ?
2. **Compile error vs logic error — phân bổ thực tế là bao nhiêu?** Tôi ước lượng 70-80% lỗi là compile/runtime, 20-30% là logic. Có data nào xác nhận không? Hay task càng phức tạp thì % logic error càng cao?
3. **Cost trade-off có thực sự là 100:1?** AI loop rẻ hơn dev loop ~100x về cost, nhưng quality thấp hơn (không fix logic). Nhóm nghĩ trade-off này có đáng không? Hay 'rẻ nhưng sai' vẫn là vấn đề?
4. **Bài này có overlap với Card #2 (context reset) không?** Nếu fix context reset (AI hiểu project rõ hơn), loop có giảm đáng kể không? Có nên gộp 2 bài không?
