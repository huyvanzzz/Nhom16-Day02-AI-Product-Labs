# 03 — Individual Reflection

> **Thành viên:** Đỗ Trung Kiên (2A202600711)
> Phần này tự viết bằng trải nghiệm thật. AI chỉ dùng để gợi ý câu hỏi tự soi.

---

## 1. Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Scan 10 problems từ trải nghiệm ở CLB AI (khoảng 40 thành viên) và học tập: câu hỏi Discord lặp lại, tổng hợp ghi chú ôn thi, tìm quyết định cũ, standup update, meeting notes... | Có 10 problems cụ thể, dùng 4 lăng kính. Bonus: scan vượt mức tối thiểu 5. |
| Pitch Problem Card | Pitch Card #1 — Discord CLB FAQ lặp lại. Trình bày workflow: cần thông tin → search trượt → hỏi #general → chờ 1-3h → trả lời → lại trôi. Bottleneck: chờ + trả lời lặp. | Bài được đưa vào shortlist (31 điểm — sát nút với bài thắng). |
| Challenge bài của bạn khác | Challenge Quý: "Compile error vs logic error ratio thực tế là bao nhiêu? Nếu 80% là logic thì AI không self-fix được." Challenge Lan Anh: "Semgrep ruleset + mô tả CWE có sẵn — LLM có thật sự cần thiết hay chỉ làm đẹp?" | Challenge của tôi giúp Quý thêm cost analysis và phân biệt compile/logic error. Challenge với Lan Anh giúp nhóm research kỹ Semgrep output trước khi kết luận. |
| Gom trùng / cluster | Góp ý cluster "Knowledge/FAQ Retrieval" gồm bài của tôi (#1 Discord, #3 tìm quyết định cũ) và #9 của Lan Anh (Meeting Assistant). | Cluster này sau không được chọn, nhưng giúp nhóm thấy pattern RAG có thể reuse. |
| Chọn candidate problem | Ban đầu muốn chọn Discord CLB FAQ. Sau scoring table, thấy Git Security Review có lợi thế về so sánh R/W/A và market evidence. Đồng ý chuyển. | Tôi không giữ bài của mình vì nhận thấy Git Security Review thật sự cho thấy rõ hơn Rule vs Workflow vs Agent. |
| Validation / research | Thực hiện quick interview với 2 bạn trong CLB (không phải nhóm) về Discord FAQ. Kết quả: 2/2 xác nhận pain thật, 1/2 nói pinned FAQ đã giải 60%. | Dữ liệu này được nhóm dùng để so sánh với các bài khác. |
| Workflow nhóm | Góp ý phân bổ thời gian cho từng bước trong current workflow Git Security Review (dựa trên experience clone repo). | Workflow có baseline thời gian cụ thể cho từng bước. |
| Problem Statement | Góp ý boundary: "AI không tự bịa lỗ hổng" — đây là risk tôi thấy từ trải nghiệm dùng AI coding. | Boundary này được đưa vào PS v1. |
| Rule / Workflow / Agent | Đặt câu hỏi: "Rule (Semgrep sorted list) có giải được 70-80% case không?" — giúp nhóm so sánh kỹ Rule vs Workflow. | Nhóm kết luận Rule không giải thích được ngữ cảnh → chọn Workflow. |
| Decision | Đồng ý Go. Góp ý exit criteria: "Nếu AI giải thích sai >2 lỗi Critical trong 3 lần chạy → dừng." | Exit criteria được đưa vào decision. |

---

## 2. Bảng dùng AI

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Gợi ý thêm problem sau khi tự scan 5 problems | Gợi ý thêm #5 (tìm quyết định cũ Discord), #6 (phân loại email), #8 (feedback form report), #10 (member onboarding) | AI gợi ý "AI tutor cho môn học" — quá rộng, không có workflow cụ thể | Bỏ. Giữ #5 và #8 vì có dấu hiệu thật trong CLB. |
| Problem Card | Nhờ AI phản biện Card #1 (Discord FAQ) | Chỉ ra "trả lời đúng" đo thế nào — metric quality yếu | AI đề xuất agent tự động trả lời mọi câu hỏi, kể cả câu nhạy cảm | Tôi thêm boundary: bot không trả lời câu nhạy cảm, không chắc thì tag người. |
| Workflow | Dùng AI chuyển mô tả workflow thành Mermaid | Nhanh, visible | AI gộp bước "chờ" và "trả lời" — nhưng tôi muốn tách vì bottleneck nằm ở cả 2 | Tách lại thành 2 bottleneck riêng (độ trễ cho người hỏi, thời gian lặp cho người trả lời). |
| Research | Tìm các tool Q&A cho Discord | Gợi ý Botpress, Tidio, ChatGPT Discord bot | AI claim "Discord search built-in đã đủ tốt" — nhưng tôi biết nó không search được semantic | Bỏ claim đó. Dùng research về RAG và Discord bot pattern. |
| Problem Statement | Nhờ AI phản biện PS v0 | Chỉ ra boundary còn mơ hồ ("AI không làm gì sai") | — | Tôi sửa boundary thành các câu cụ thể, có thể kiểm tra được. |
| Rule/Workflow/Agent | Hỏi AI so sánh 3 mức cho bài Discord FAQ | AI chỉ ra Rule (pinned FAQ) rẻ nhất và có thể đủ cho 70% case | AI kết luận "luôn chọn Rule" — nhưng không tính đến chi phí duy trì FAQ thủ công | Tôi bổ sung: FAQ thủ công tốn công curate, dễ lỗi thời. Workflow (RAG bot) tự động hơn. |

---

## 3. Reflection câu hỏi mở

**Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Tôi thấy cùng là "câu hỏi lặp lại" nhưng context khác nhau hoàn toàn. Bài của tôi (Discord CLB) khác bài của Quý (AI coding loop) và khác bài của Lan Anh (security review). Cùng pattern "lặp lại" nhưng workflow, actor, bottleneck khác → giải pháp khác. Điều này cho thấy không nên vội gộp problem vào một cluster chỉ vì "cùng dạng".

**Nhóm có lúc nào bị solution-first không?**

Có. Lúc đầu khi nhóm thảo luận về Git Security Review, Huy nói ngay "làm chatbot là xong". Tôi phải hỏi lại: "Chatbot làm gì? Ở bước nào? Ai kiểm tra output?" — những câu hỏi này buộc nhóm vẽ workflow trước khi chọn solution.

**Tôi có thay đổi ý kiến sau khi bị challenge không?**

Có. Tôi từng nghĩ Discord CLB FAQ là bài mạnh nhất vì tôi hiểu domain nhất. Nhưng sau khi Quý challenge "Pinned FAQ thủ công (Rule) đã đủ 70% → bài này nghiêng về non-AI, ít cơ hội so sánh R/W/A", tôi nhận ra bài của mình thật sự có thể giải bằng Rule, và trong lab AI, bài nào cho thấy rõ Rule vs Workflow vs Agent mới có giá trị học tập cao hơn.

**Tôi đóng góp gì thật sự vào artifact cuối?**

- Quick interview data (2 bạn CLB) — dù không được dùng trực tiếp cho Git Security Review nhưng giúp nhóm hiểu quy trình validation.
- Boundary "AI không tự bịa lỗ hổng" — xuất phát từ trải nghiệm AI hallucination.
- Exit criteria cụ thể (nếu AI sai >2 lỗi Critical trong 3 lần → dừng).

**Điều khó nhất khi viết Problem Statement là gì?**

Phân biệt "bottleneck" và "impact". Lúc đầu tôi viết bottleneck là "chờ 1-3 tiếng" và impact cũng là "chờ 1-3 tiếng" — gần như giống nhau. Sau challenge của Quý, tôi hiểu: bottleneck là nguyên nhân (bước nào làm chậm), impact là hậu quả (người dùng bị ảnh hưởng thế nào). Hai thứ khác nhau.

**Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**

Tôi sẽ hỏi sớm hơn: "Metric này đo thế nào? Có baseline thật không?" — vì tôi thấy vài metric trong Phase 3 còn là guesswork. Có baseline thật mới biết AI có cải thiện hay không.

---

## 4. Mạch lập luận (kiểm tra hiểu bài — 6 điểm)

```text
Problem: Dev clone repo lạ, không biết có lỗ hổng bảo mật nào,
tool quét trả hàng trăm cảnh báo khó hiểu.

Workflow: Clone → Semgrep scan → đọc + lọc cảnh báo (nghẽn 60') →
Google/StackOverflow → sửa/bỏ qua.

Metric: Thời gian xử lý Critical/High 60' → <15'.
Lỗi Critical bỏ sót ~0. Số lần Google 5-10 → 0-2.

Boundary: AI chỉ giải thích. Không tự sửa code. Không tự bịa lỗ hổng.
Dev quyết định cuối.

Độ phù hợp AI: Workflow (Rule + AI giải thích + Human decide).
Không Agent vì workflow tuyến tính cố định.

Decision: Go scope nhỏ. Pilot 1 repo, Semgrep + LLM API,
bán thủ công, đo thời gian và độ chính xác.
```

---

*Day 02 Lab — Individual Reflection — Đỗ Trung Kiên*
