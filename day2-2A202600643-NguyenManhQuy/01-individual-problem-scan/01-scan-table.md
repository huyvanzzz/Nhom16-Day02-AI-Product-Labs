# Phase 1 — Individual Scan

> **Vai trò:** Developer làm việc với AI vibe coding (Claude, Cursor, Copilot)
> **Bối cảnh:** Build project cá nhân và tính năng cho product bằng AI assistant hằng ngày

---

## Bảng scan — 10 problems

| # | Lăng kính | Problem quan sát được | Ai đang đau? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Lặp lại + Tốn thời gian | **Prompt-debug loop**: AI generate code → chạy lỗi → copy lỗi → re-prompt → lại chạy. Mỗi task loop 3-5 lần. | Dev (tôi) | Mỗi lần loop mất 15-30 phút. Task nhỏ (30' viết tay) thành 2h vì loop. |
| 2 | Lặp lại | **Context reset**: Mỗi session mới phải giải thích lại project structure, tech stack, conventions. AI mất context sau ~50 dòng. | Dev (tôi) | 10-15 phút/session để re-setup. Ngày có 3-4 session → 45-60 phút vô ích. |
| 3 | Tốn thời gian | **AI over-engineering**: AI sinh code phức tạp hơn cần — factory pattern cho button, abstract class cho utility function. | Dev (tôi) | Phải đọc hiểu → prune → refactor. Thêm 30-50% thời gian so với code cần. |
| 4 | Lặp lại | **Prompt không lưu lại**: Không biết prompt nào đã dùng, AI đã generate cái gì. Task tương tự tuần sau phải prompt lại từ đầu. | Dev (tôi) | Không có history → phải tìm lại trong chat log → mất 5-10 phút/lần. |
| 5 | Pain từ người khác | **Trust issue khi code review**: Reviewer không biết code do AI hay người viết → nghi ngờ mọi logic. | Dev + Team lead | Code bị reject/re-review nhiều hơn. "Đoạn này em có hiểu không?" |
| 6 | AI có thể tốt hơn | **AI hallucinate package/API**: AI đề xuất package không tồn tại, API đã deprecated, hoặc method sai tên. | Dev (tôi) | Debug 10-20 phút mới phát hiện nguyên nhân do hallucination. |
| 7 | Tốn thời gian | **Thiếu error handling**: AI sinh happy path, dev phải tự thêm try/catch, validation, loading state, empty state. | Dev (tôi) | Mỗi function phải thêm 3-5 dòng error handling thủ công. Lặp lại → lãng quên → bug. |
| 8 | AI có thể tốt hơn | **AI không tự detect được lỗi logic**: Test case cơ bản pass nhưng logic sai vì AI hiểu sai requirement. | Dev (tôi) | Phải tự viết test hoặc chạy manual để phát hiện. Mất 30-60 phút mỗi bug logic. |
| 9 | Pain từ người khác | **Kỳ vọng sai từ PM**: PM nghĩ vibe coding = 10x năng suất → deadline gấp → quality giảm. | Dev + PM | Deadline unrealistic, phải giải thích lại quy trình. Stress tăng. |
| 10 | Lặp lại | **File organization messy**: AI tạo file ở sai folder, thiếu consistent naming. Phải move/rename thủ công. | Dev (tôi) | Mỗi lần tạo file mới phải move vào đúng cấu trúc. Dễ quên → tech debt. |

---

## Sử dụng AI

AI được dùng để **gợi ý thêm problem** sau khi tự scan. Prompt:

```
Tôi là developer làm việc với AI vibe coding (Claude, Cursor).
Công việc hằng ngày: viết code bằng AI assistant, debug code do AI sinh, review và refactor.

Tôi đã có các problem:
1. AI generate code sai → loop debug nhiều lần
2. Mỗi session mới phải re-setup context
3. AI over-engineering code
4. Reviewer trust issue
5. Hallucination package/API

Hãy gợi ý thêm problem theo 4 lăng kính.
```

**AI gợi ý thêm:** 3, 4, 8, 9, 10. Trong đó ý #9 về kỳ vọng sai từ PM và #8 về logic error detection là insights mới tôi chưa nghĩ tới và có cơ sở thật.

**AI gợi ý bị bỏ:** "AI không biết viết test" — tôi thấy không đúng vì AI viết test khá tốt, vấn đề là test sai logic chứ không phải không viết được.
