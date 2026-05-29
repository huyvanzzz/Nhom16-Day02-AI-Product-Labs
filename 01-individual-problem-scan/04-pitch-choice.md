# Pitch Choice

## Card tôi muốn pitch nhất

**Card #1 — Prompt-Debug Loop**

## Vì sao

1. **Workflow rõ nhất** — có thể vẽ từng bước, từng bottleneck rõ ràng. Metric cụ thể (số lần loop, thời gian/task).
2. **Tôi gặp hằng ngày** — không giả định, không research. Mỗi lần vibe coding là gặp.
3. **Impact đo được** — biết chính xác mất bao nhiêu thời gian vì loop.
4. **Có thể so sánh các mức** — No AI (tự viết tay), Rule (prompt template), Workflow (tool chain gen→run→fix), Agent (AI tự quyết định bước tiếp theo).

> **Lưu ý:** Quick gut ban đầu là Agent nhưng sau adversarial review được hạ xuống Workflow. Pipeline gen→run→detect→fix→re-run là tuyến tính cố định → Workflow đủ, không cần Agent.
5. **Không quá rộng** — scope là một bước trong coding workflow, không phải "xây AI coding platform".

## Câu hỏi tôi muốn nhóm challenge

1. **Bottleneck thật sự là ở đâu?** — Ở bước "dev copy error và viết lại prompt" (bước 5) hay ở bước "AI gen code sai ngay từ đầu" (bước 2)?
   - Nếu ở bước 2: giải pháp là cải thiện prompt quality → thuộc Rule/Process.
   - Nếu ở bước 5: giải pháp là AI tự loop debug → thuộc Agent/Workflow.

2. **"AI tự loop debug" có thật sự giảm thời gian không?** — Hay chỉ chuyển thời gian từ dev loop sang AI loop, tổng thời gian không đổi?

3. **Bài này có competition với Card #2 (context reset) không?** — Vì context reset cũng là nguyên nhân gây loop. Nếu fix context reset trước, loop có giảm không?
