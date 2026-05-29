# Problem Card #2 — Context Reset Mỗi Session

---

## Card snapshot

```
┌──────────────────────────────────────────────────────────┐
│ PROBLEM CARD #2                                           │
│                                                           │
│ Problem 1 câu:                                            │
│ Mỗi session AI mới, dev mất 10-15 phút giải thích lại     │
│ project structure, tech stack, conventions — và AI vẫn     │
│ sai vì không nhớ context session trước.                    │
│                                                           │
│ Ai đang đau?                                              │
│ Developer (tôi) làm nhiều session AI/ngày                  │
│                                                           │
│ Workflow hiện tại:                                        │
│ Mở chat → Giải thích project → AI hiểu sai → Fix context  │
│ → Bắt đầu task → Hết context → Reset lại                   │
│                                                           │
│ Bước nghẽn nhất:                                          │
│ Giải thích lại context (10-15 phút/session)               │
│                                                           │
│ Đo thành công bằng gì?                                    │
│ Context setup time: 10-15 phút → < 2 phút                 │
│ AI correct-first-attempt rate tăng                         │
│                                                           │
│ Quick gut: □ No AI ☑ Rule □ Workflow                      │
│            □ Agent □ Chưa biết                            │
└──────────────────────────────────────────────────────────┘
```

---

## Chi tiết

**Problem 1 câu:**
Mỗi lần mở session AI mới (hoặc context hết), dev phải giải thích lại project structure, tech stack, conventions — mất 10-15 phút, và AI vẫn thường hiểu sai hoặc quên sau vài message.

**Actor:**
Developer làm nhiều session AI mỗi ngày (3-5 session), mỗi session xử lý một task khác nhau.

**Thời điểm / bối cảnh:**
- Khi bắt đầu ngày mới: session AI đầu tiên
- Khi context window đầy (>50-100 messages): phải start new session
- Khi chuyển task (từ frontend sang backend, từ feature A sang B)

**Current workflow:**

```
1. [Dev] Mở chat AI mới
2. [Dev] Viết context: "Project là..., tech stack gồm..., 
   folder structure là..., conventions là..."
3. [AI] Xử lý task đầu tiên (thường đúng 60-70%)
4. [Dev] Nhận thấy AI hiểu sai context → sửa
5. [AI] Điều chỉnh — nhưng sau 15-20 messages lại quên
6. [Dev] Nhắc lại context (copy-paste từ file note)
7. (Lặp lại)
```

**Bottleneck:**
**Bước 2 & 6** — Viết/nhắc lại context. Mất 10-15 phút mỗi session mới, và 2-5 phút mỗi lần nhắc lại.

Vấn đề kép: mất thời gian + AI vẫn không nhớ đủ lâu.

**Impact:**
- 10-15 phút × 3-5 session/ngày = 30-75 phút/ngày chỉ để setup context
- AI response chất lượng thấp hơn cho 2-3 message đầu (vì chưa hiểu context)
- Frustration vì phải lặp lại — vibe coding mất flow

**Success metric:**
- Context setup time: 10-15 phút → < 2 phút
- AI correct-first-attempt rate: 60-70% → >85%
- Số lần phải nhắc lại context/session: 3-5 lần → 0 lần

**Non-AI alternative:**
- **CLAUDE.md / .cursorrules / project rules file** — đã có sẵn, AI tự đọc. Vấn đề: không phải AI nào cũng support, và rule file không dynamic.
- **Copy-paste template context** — nhanh hơn nhưng vẫn thủ công.
- **Context note trong README** — nhưng AI không tự đọc.

**AI hypothesis:**
Hai hướng khả thi (nhưng chưa mainstream):
- **Persistent memory**: AI nhớ context giữa các session — đã có prototype (Mem0, Claude Projects), nhưng chưa đủ granular để replace manual context setup hoàn toàn.
- **Auto-project-analysis**: AI tự scan repo structure, README, và dependency graph khi bắt đầu session → build mental model mà không cần dev giải thích thủ công.

Cả hai là hướng dài hạn, không phải giải pháp triển khai ngay hôm nay.

**Quick gut:**
**Rule** (CLAUDE.md / project rules) — vì non-AI alternative đã tồn tại và khá hiệu quả.

Bài toán này nghiêng về Rule nhiều hơn AI — đó vẫn là kết luận tốt theo worksheet (điểm ở lập luận, không phải ở độ ngầu của solution). AI hypothesis là upside tiềm năng, không phải giải pháp ưu tiên hiện tại.

---

## Draft workflow

**Current:**

```text
CURRENT — 45-75 phút/ngày cho context overhead

[Mở session mới]
→ Viết context (10-15')
→ Task 1 (AI hiểu ~60%)
→ Nhắc context (3-5')
→ Task 2
→ Nhắc context (3-5')
→ ... → Hết session
```

**Future:**

```text
FUTURE — <10 phút/ngày

[Mở session mới]
→ AI tự đọc project rules file (1-2')
→ AI hiểu context từ file (không cần nhắc lại)
→ Task 1
→ Task 2
→ ... → Hết session (không cần nhắc lại)
```

---

## Câu hỏi muốn nhóm challenge

1. **Đây có thật là "problem cần giải" không?** Hay chỉ là dev chưa biết dùng CLAUDE.md / project rules? — Nếu rule file đã giải quyết được 80% thì bài toán này thuộc về "non-AI alternative", không phải AI problem.
2. **Metric "AI correct-first-attempt >85%" có đo được không?** Ai đo? Dev tự estimate hay có tool đo?
3. **Bài này có overlap với Card #1 không?** — Vì context reset cũng là một nguyên nhân gây prompt-debug loop (AI không hiểu context → code sai → loop).
