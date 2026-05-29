# Top 3 Problems — Selection

## Bảng chọn

| Rank | Problem | Vì sao chọn | Điều còn chưa chắc |
|---|---|---|---|
| **1** | **Prompt-debug loop** (AI generate → lỗi → re-prompt → lại lỗi) | Workflow rất rõ, lặp lại hằng ngày, có metric số lần loop và thời gian. Impact trực tiếp lên productivity. | Nguyên nhân gốc là do AI hiểu sai hay do prompt tôi viết không rõ? Nếu do prompt thì giải pháp khác. |
| **2** | **Context reset mỗi session mới** | Lặp lại, có thể đo (phút/session), có non-AI alternative (rule file, CLAUDE.md). Cần kiểm chứng mức độ phổ biến. | Có dev nào khác cũng gặp không? Hay chỉ do workflow của tôi? |
| **3** | **AI code trust issue khi code review** | Pain từ team, impact organization-wide. Non-AI alternative rõ (code convention, review guideline). | Đây có thật là "problem của dev" hay là "problem của quy trình review"? Nếu là quy trình thì AI không giải được. |

---

## Lý do không chọn các problem khác

| Problem | Vì sao không vào top 3 |
|---|---|
| File organization messy | Impact thấp, giải bằng convention/rule, không cần AI phức tạp. |
| AI hallucinate package | Impact cao nhưng không lặp lại đủ nhiều (vài lần/tuần). Workflow: phát hiện → fix → xong. Không có workflow lan rộng để tối ưu. |
| Thiếu error handling | Problem thật nhưng có thể giải bằng rule (AI prompt: "luôn thêm error handling") hoặc linter. |
| AI không detect lỗi logic | Impact rất lớn nhưng workflow chưa rõ — lỗi logic khó detect tự động. |
| PM kỳ vọng sai | Không phải problem của dev, không giải trong scope lab. |
| Prompt không lưu lại | Impact thấp, có thể giải bằng tool (lưu chat log / ghi prompt vào file). |
