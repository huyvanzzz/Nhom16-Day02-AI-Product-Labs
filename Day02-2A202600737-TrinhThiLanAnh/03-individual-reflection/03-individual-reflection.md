# 03 — Individual Reflection

> **Thành viên:** Trịnh Thị Lan Anh (2A202600737)
> Phần này tự viết bằng trải nghiệm thật. AI chỉ dùng để gợi ý câu hỏi tự soi.

---

## 1. Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Scan 8 problems về security, data quality, meeting notes, code review... từ trải nghiệm học tập, làm việc nhóm và thực tập. | 8 problems cụ thể, dùng 4 lăng kính. Đủ điều kiện bonus +3 (vượt 5, còn cụ thể). |
| Pitch Problem Card | Pitch Card #1 — Git Security Review. Trình bày workflow clone repo → scan → đọc cảnh báo → lọc → sửa. Bottleneck: đọc + lọc cảnh báo (60 phút). | Bài được vào shortlist và sau đó được nhóm chọn làm candidate problem chính. |
| Challenge bài của bạn khác | Challenge Quý: "Bài Prompt-Debug Loop của bạn đã có Cursor Agent và Claude Code giải — nhóm có học được gì mới không?" Challenge Kiên: "Pinned FAQ thủ công đã đủ 70%. Phần 30% còn lại (câu hỏi mới) có đáng để làm workflow AI không?" | Challenge với Quý giúp nhóm thấy Git Security Review có nhiều insight mới hơn. Challenge với Kiên giúp nhóm thấy Rule solution mạnh cho Discord FAQ. |
| Gom trùng / cluster | Góp ý cluster "Code/Data Security & Quality" gồm #7 (Git Security Review) và #8 (Data Quality Auditor). | Cluster này được chọn sau scoring. |
| Chọn candidate problem | Bài của tôi (Git Security Review) được chọn. Tôi giải thích vì sao nên chọn: actor cụ thể, workflow rõ, so sánh R/W/A rõ, cả team đều từng là dev. | Nhóm đồng thuận. |
| Validation / research | Thực hiện quick interview với 1 dev đang đi làm (anh họ) — xác nhận pain thật. Tìm research về Semgrep, CodeQL, SonarQube. | Data được dùng trong Phase 4. |
| Workflow nhóm | Vẽ current workflow dựa trên trải nghiệm thực tế khi clone repo từ GitHub. | Workflow có baseline thời gian thực tế. |
| Problem Statement | Điều chỉnh problem sau validation: từ "tự động scan + fix" → "giải thích kết quả scan". Viết boundary dựa trên rủi ro thật (AI hallucination về bảo mật rất nguy hiểm). | PS có focus đúng — không cố gắng giải quyết quá nhiều. |
| Rule / Workflow / Agent | Giải thích vì sao Workflow đủ và Agent là overkill: workflow tuyến tính 3 bước, không cần AI tự lập kế hoạch. | Lập luận này được nhóm dùng trong decision. |
| Decision | Đồng ý Go với scope nhỏ. Góp ý: "Không nên pilot với repo production — dùng repo pet project để test." | Pilot scope an toàn. |

---

## 2. Bảng dùng AI

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Gợi ý thêm problem về security/data quality | Gợi ý #2 (Data Quality Auditor), #3 (Meeting Assistant) — tôi chưa nghĩ tới dưới góc nhìn security | Gợi ý "AI tự động fix lỗ hổng bảo mật" — rủi ro rất cao | Tôi bỏ. Bài toán của tôi là "giải thích", không phải "tự fix". |
| Problem Card | Nhờ AI phản biện Card #1 (Git Security Review) | Chỉ ra "giải thích lỗ hổng" có thể sai nếu LLM hallucinate — đây là risk quan trọng | AI đề xuất Agent ngay từ đầu (cho rằng cần AI tự quyết định bước tiếp theo) | Tôi hạ về Workflow. Agent là overkill cho workflow tuyến tính. |
| Workflow | Dùng AI/Mermaid để vẽ workflow | Nhanh, dễ hình dung | AI vẽ workflow thiếu fallback mechanism và boundary | Tôi thêm: "AI không chắc → hiển thị cảnh báo gốc + link CWE" và "AI giải thích sai → nút báo cáo sai". |
| Research | Tìm tool security scanning (Semgrep, CodeQL, SonarQube) | Tìm được so sánh giữa các tool | AI claim CodeQL "dễ setup" — nhưng tôi biết nó yêu cầu QL language riêng | Tôi sửa: CodeQL mạnh nhưng setup phức tạp, không phù hợp cho dev cá nhân. |
| Problem Statement | Nhờ AI phản biện PS v0 | Chỉ ra thiếu "cách đo baseline" — metric chưa gắn với cách đo cụ thể | — | Tôi thêm cách đo: "đếm thủ công thời gian 1 lần review, ghi log số lần Google". |
| Rule/Workflow/Agent | Hỏi AI: "Rule (Semgrep sorted list) có đủ không?" | AI chỉ ra hạn chế: không giải thích được ngữ cảnh | AI kết luận "Agent là tương lai" — không practical | Tôi bỏ. Workflow là đủ cho pilot. |

---

## 3. Reflection câu hỏi mở

**Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Tôi thấy bài của Quý (Prompt-Debug Loop) rất giống với trải nghiệm của tôi khi dùng AI coding. Nhưng nhờ challenge của Quý, tôi nhận ra bài của tôi (Git Security Review) có điểm khác biệt: nó giải quyết một vấn đề chưa có tool nào làm tốt (giải thích kết quả scan theo ngữ cảnh), trong khi Prompt-Debug Loop đã có Cursor Agent và Claude Code.

Bài của Kiên (Discord CLB FAQ) cho thấy đôi khi Rule là đủ — không cần phải ép AI vào mọi bài toán.

**Nhóm có lúc nào bị solution-first không?**

Có. Chính tôi lúc đầu cũng nghĩ "làm chatbot là xong" cho Git Security Review. Nhưng sau khi vẽ workflow, tôi thấy bottleneck không phải "không có chatbot", mà là "dev không hiểu cảnh báo" — và chatbot chỉ là công cụ để giải quyết bottleneck đó, không phải mục đích.

**Tôi có thay đổi ý kiến sau khi bị challenge không?**

Có — và nhiều lần. 

Lần 1: Quý challenge "Semgrep ruleset + mô tả CWE có sẵn đã đủ 70-80% → LLM có thật sự cần?" — tôi phải research kỹ hơn và nhận ra mô tả CWE là generic, không theo ngữ cảnh codebase. LLM thật sự có giá trị ở điểm "giải thích theo context".

Lần 2: Kiên hỏi "Nếu LLM giải thích sai một lỗ hổng Critical, ai phát hiện?" — tôi mới nghĩ đến boundary "dev là người quyết định cuối".

Lần 3: Quý challenge "Bài của bạn nghiêng về Agent — hãy xem lại định nghĩa" — tôi nhận ra workflow tuyến tính, Agent là overkill.

**Tôi đóng góp gì thật sự vào artifact cuối?**

- Problem gốc (Git Security Review) — được nhóm chọn.
- Workflow chi tiết từ trải nghiệm thật (clone repo từ GitHub).
- Boundary "AI không tự bịa lỗ hổng" — từ trải nghiệm AI hallucination.
- Quyết định "không pilot với repo production" — từ kinh nghiệm thực tập.

**Điều khó nhất khi viết Problem Statement là gì?**

Thu hẹp problem. Lúc đầu tôi viết problem quá rộng: "clone repo → check security → fix". Sau challenge, tôi thu hẹp thành "giải thích kết quả scan" — bỏ phần "fix" vì AI tự fix code là rủi ro quá cao. Việc thu hẹp này làm problem chặt hơn và quyết định dễ dàng hơn.

**Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**

Tôi sẽ hỏi sớm hơn: "Bài này nhóm có workflow thật để đo baseline không?" — vì tôi thấy vài bài trong shortlist có workflow "giả định" chứ không phải trải nghiệm thật. Baseline từ trải nghiệm thật mới đáng tin.

---

## 4. Mạch lập luận (kiểm tra hiểu bài — 6 điểm)

```text
Problem: Dev clone repo lạ, không biết có lỗ hổng gì, tool quét 
trả cảnh báo khó hiểu.

Workflow: Clone → Semgrep scan → đọc + lọc cảnh báo (nghẽn) → 
Google/StackOverflow → sửa.

Metric: Thời gian xử lý Critical/High 60' → <15'. 
Lỗi Critical bỏ sót ~0. Số lần Google giảm.

Boundary: AI chỉ giải thích + xếp hạng. Không tự sửa code. 
Không tự quyết định false positive. Dev quyết định cuối.

Độ phù hợp AI: Workflow — Rule không giải thích được ngữ cảnh, 
Agent là overkill cho workflow tuyến tính.

Decision: Go scope nhỏ — pilot 1 repo, Semgrep + LLM, 
bán thủ công, có exit criteria.
```

---

*Day 02 Lab — Individual Reflection — Trịnh Thị Lan Anh*
