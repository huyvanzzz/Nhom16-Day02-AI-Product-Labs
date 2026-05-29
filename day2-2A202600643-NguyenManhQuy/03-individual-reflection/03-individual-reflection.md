# 03 — Individual Reflection

> **Thành viên:** Nguyễn Mạnh Quý (2A202600643)
> Phần này tự viết bằng trải nghiệm thật. AI chỉ dùng để gợi ý câu hỏi tự soi.

---

## 1. Tôi đã tham gia vào phần nào?

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Scan 10 problems về AI vibe coding (Prompt-Debug Loop, Context Reset, Trust Issue, Hallucination...). Dùng AI để gợi ý thêm problem sau khi tự scan. | Có 10 problems cụ thể, mỗi problem có actor + dấu hiệu thật + metric. Bonus: đủ 10 problems, vượt mức tối thiểu 5. |
| Pitch Problem Card | Pitch Card #1 — Prompt-Debug Loop (AI gen → lỗi → re-prompt → lặp). Giải thích workflow 7 bước, bottleneck ở bước copy error + viết prompt fix. | Bài được đưa vào shortlist (32 điểm cùng Git Security Review). |
| Challenge bài của bạn khác | Challenge Lan Anh: "Phần 'giải thích lỗ hổng' có thật sự cần LLM, hay ruleset + mô tả có sẵn của Semgrep đã đủ 70-80%?" Challenge Kiên: "Pinned FAQ thủ công (Rule) có đủ không, có cần AI không?" | Cả hai challenge đều được nhóm ghi nhận và dùng để thu hẹp scope — Lan Anh sửa problem từ "tự động fix" thành "giải thích kết quả scan". |
| Gom trùng / cluster | Đề xuất 4 cluster (AI Code Quality, Knowledge FAQ, Code/Data Security, Service Automation). | Giúp nhóm thấy pattern và shortlist nhanh hơn. |
| Chọn candidate problem | Ban đầu vote Prompt-Debug Loop, nhưng sau khi thấy Git Security Review có điểm mạnh hơn về domain coverage và so sánh R/W/A, đồng ý chuyển. | Cho thấy tôi không cố giữ bài của mình — chấp nhận bài tốt hơn. |
| Validation / research | Mang research có sẵn từ cá nhân (market data 2024-2025 về AI coding, trust issue, context window) vào nhóm. Cung cấp nguồn: GitHub Octoverse, ACM ICSE, Google Research, GitClear. | Nhóm có evidence để chốt "AI tự loop debug đã có tool thị trường làm" → loại Prompt-Debug Loop khỏi shortlist vì ít insight mới. |
| Workflow nhóm | Góp ý vẽ current/future workflow cho Git Security Review. Đề xuất fallback mechanism (AI không chắc → hiển thị cảnh báo gốc). | Workflow nhóm có đủ boundary và phương án quay về. |
| Problem Statement | Góp ý metric: thời gian xử lý Critical/High (60→15 phút) — dựa trên kinh nghiệm cá nhân. Góp ý boundary: AI không tự sửa code. | PS v1 có metric cụ thể và boundary rõ. |
| Rule / Workflow / Agent | Dùng research cá nhân (adversarial review) để lập luận Workflow đủ, không cần Agent. So sánh 3 mức rõ. | Nhóm chọn Workflow, không Agent — quyết định có căn cứ. |
| Decision | Đồng ý Go với scope nhỏ. Đề xuất pilot: 1 repo mẫu, Semgrep + Claude API, bán thủ công. | Pilot cụ thể, có exit criteria. |

---

## 2. Bảng dùng AI

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì bằng nhận định của mình? |
|---|---|---|---|---|
| Scan | Gợi ý thêm problem về AI vibe coding | Gợi ý thêm #8 (AI không detect logic error) và #9 (PM kỳ vọng sai) — hai insights mới | Gợi ý "AI không biết viết test" — tôi thấy không đúng vì AI viết test khá tốt | Bỏ ý đó. Giữ #8 và #9 vì có cơ sở thật. |
| Problem Card | Nhờ AI phản biện Card #1 (Prompt-Debug Loop) dưới góc nhìn skeptical PM | Chỉ ra 7 điểm yếu, trong đó 2 điểm critical: Agent→Workflow (định nghĩa sai) và metric không phân loại task | AI đề xuất một số metric không realistic (≤1 loop tuyệt đối cho mọi task) | Sửa metric: phân loại simple task (0-1 loop) vs complex task (1-2 loops). Hạ Agent→Workflow. |
| Workflow | Dùng AI/Mermaid để vẽ workflow từ mô tả | Nhanh hơn vẽ tay, flow rõ ràng | AI gộp bước "diagnostic lỗi" và "viết prompt fix" thành một | Tách lại vì bottleneck nằm ở bước viết prompt fix. |
| Research | Tìm market data, tool ecosystem, academic papers | Tìm được 12+ nguồn tham khảo (GitHub, ACM ICSE, Google Research, GitClear) | Một số claim về "số lần loop trung bình" không có nguồn gốc rõ — AI ước lượng | Chỉ giữ nguồn có link kiểm tra được. Ghi rõ mức độ tin cậy của từng claim. |
| Problem Statement | Nhờ AI phản biện PS v0 — field nào còn mơ hồ | Chỉ ra quality metric yếu (đo "hiểu" thế nào) | AI đề xuất Agent quá sớm | Nhóm hạ về Workflow, dùng "thời gian" và "số lần Google" làm metric proxy. |
| Rule/Workflow/Agent | So sánh 3 mức với AI | Gợi ý các rủi ro của Agent (permission, hallucination × nhiều bước) | AI thiên về Agent (cho rằng workflow "không thông minh") | Bỏ qua bias của AI. Workflow là lựa chọn đúng vì workflow tuyến tính. |
| Decision | Hỏi AI phân tích rủi ro của Go vs Not Yet | Gợi ý exit criteria hợp lý | — | Giữ nguyên, bổ sung pilot scope từ nhóm. |

---

## 3. Reflection câu hỏi mở

**Tôi học được gì khi nghe top 3 problems của các bạn khác?**

Tôi học được rằng cùng một vai trò "developer" nhưng mỗi người có pain khác nhau. Kiên đau về CLB FAQ (vì bạn làm CLB), Lan Anh đau về security review (vì bạn từng gặp lộ API key), Huy đau về quy trình Vinhomes (vì bạn ở chung cư). Cùng là dev nhưng trải nghiệm thật khác nhau — điều này cho thấy scan cá nhân là bước không thể bỏ qua.

**Nhóm có lúc nào bị solution-first không?**

Có. Ở đầu Phase 3, Huy nói ngay "làm Agent cho Vinhomes" trước khi vẽ workflow. Lan Anh cũng hơi nghiêng về Agent cho Git Security Review. Tôi phải nhắc nhóm: "Vẽ workflow trước, xem bottleneck ở đâu, rồi mới chọn mức." Sau khi vẽ, cả hai đều hạ từ Agent xuống Workflow.

**Tôi có thay đổi ý kiến sau khi bị challenge không?**

Có. Ban đầu tôi chắc chắn Prompt-Debug Loop là bài tốt nhất. Nhưng sau khi Lan Anh challenge "bài của bạn đã có tool thị trường giải (Cursor, Claude Code) → nhóm sẽ không học được gì mới", tôi nhận ra bài của mình dù có workflow rõ nhưng thiếu insight mới. Đó là lúc tôi đồng ý chuyển sang Git Security Review.

Ngoài ra, adversarial review của tôi (tự phản biện Card #1) phát hiện tôi đã nhầm Agent thành Workflow — đây là bài học lớn về định nghĩa Agent.

**Tôi đóng góp gì thật sự vào artifact cuối?**

- Research market data (GitHub Octoverse, ACM ICSE, GitClear) — cung cấp evidence cho quyết định.
- Adversarial review framework — giúp nhóm kiểm tra claims trước khi viết PS.
- Metric và boundary cụ thể cho PS v1.
- Lập luận Workflow > Agent — dùng định nghĩa từ worksheet.

**Điều khó nhất khi viết Problem Statement là gì?**

Viết boundary. Lúc đầu tôi viết boundary quá rộng ("AI không làm gì sai"). Sau challenge của Kiên, tôi thu hẹp thành "AI không tự sửa code, không tự quyết định false positive, không tự bịa lỗ hổng". Boundary tốt là boundary có thể kiểm tra được — nếu AI vi phạm, ai đó có thể phát hiện.

**Nếu làm lại, tôi sẽ challenge nhóm mạnh hơn ở điểm nào?**

Tôi sẽ hỏi nhóm sớm hơn: "Metric này đo bằng cách nào? Ai đo?" — vì nhiều metric trong Phase 3 còn mơ hồ. Câu hỏi này buộc nhóm phải cụ thể hóa cách đo, giúp PS chặt hơn.

---

## 4. Mạch lập luận (kiểm tra hiểu bài — 6 điểm)

```text
Problem: Dev clone repo lạ, không biết có lỗ hổng bảo mật nào,
tool quét trả hàng trăm cảnh báo khó hiểu.

Workflow: Clone → scan → đọc & lọc cảnh báo (nghẽn) → sửa/bỏ qua.

Metric: Thời gian xử lý Critical/High 60' → <15'.
Tỉ lệ lỗi Critical bỏ sót ~0.
Số lần Google/StackOverflow 5-10 → 0-2.

Boundary: AI chỉ giải thích + xếp hạng. Dev quyết định sửa/bỏ qua.
AI không tự sửa code. Không check infrastructure security.

Độ phù hợp AI: Workflow (Rule scan → AI giải thích → Human decide).
Không phải Agent vì workflow tuyến tính, không cần tự lập kế hoạch.
Không phải Rule vì rule không giải thích được theo ngữ cảnh codebase.

Decision: Go scope nhỏ. Pilot 1 repo, Semgrep + LLM, bán thủ công,
đo thời gian và độ chính xác.
```

---

*Day 02 Lab — Individual Reflection — Nguyễn Mạnh Quý*
