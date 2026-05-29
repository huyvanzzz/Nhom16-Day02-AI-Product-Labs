# Workflow — AI-Assisted Security Repository Review

> File phụ cho `02-group-problem-statement.md`
> Mermaid diagram cho current và future workflow

---

## Current Workflow (Before)

```mermaid
flowchart TD
    A["🧑‍💻 Dev: Clone repo lạ<br/>(2 phút)"] --> B["⚙️ Tool: Chạy Semgrep/Bandit<br/>(8 phút)"]
    B --> C["🧑‍💻 Dev: Đọc ~100-500 cảnh báo<br/>dạng kỹ thuật (CWE, OWASP)<br/>(30 phút)"]
    C --> D["🧑‍💻 Dev: Lọc lỗi thật vs<br/>false positive<br/>(30 phút)"]
    D --> E["🧑‍💻 Dev: Google/StackOverflow<br/>tra cách sửa<br/>(10 phút)"]
    E --> F["🧑‍💻 Dev: Sửa thủ công /<br/>bỏ qua (nếu không chắc)<br/>(5 phút)"]

    style A fill:#cfe2ff
    style B fill:#d1e7dd
    style C fill:#f8d7da
    style D fill:#f8d7da
    style E fill:#fff3cd
    style F fill:#cfe2ff
```

### Thông số hiện tại

| Metric | Giá trị | Ghi chú |
|---|---|---|
| Tổng thời gian | ~75 phút/repo | Clone → scan → đọc → lọc → Google → sửa |
| Bottleneck | Bước 3+4 (đọc + lọc): ~60 phút | 75% tổng thời gian |
| Số lượng cảnh báo | 100-500 warnings/repo | Semgrep mặc định ruleset |
| Tỉ lệ false positive | ~30-50% | Tùy ruleset và codebase |
| Lỗi Critical bị bỏ sót | Không đo — nhưng có risk | Dev không chuyên thường bỏ qua không cố ý |

---

## Future Workflow (After)

```mermaid
flowchart TD
    A["🧑‍💻 Dev: Clone repo + upload<br/>(2 phút)"] --> B["⚙️ Rule: Semgrep scan tự động<br/>(3 phút)"]
    B --> C["🤖 AI: Gom + giải thích<br/>+ xếp hạng rủi ro<br/>(1 phút)"]
    C --> D{"🧑‍💻 Dev có câu hỏi?"}
    D -->|"✅ Có"| E["🤖 AI Chatbot: Trả lời<br/>theo ngữ cảnh codebase<br/>(2-5 phút)"]
    D -->|"❌ Không"| F["🧑‍💻 Dev: Đọc bản giải thích<br/>+ quyết định sửa/bỏ qua<br/>(10 phút)"]
    E --> F
    F --> G["✅ Hoàn tất review<br/>(~18 phút)"]

    style A fill:#cfe2ff
    style B fill:#d1e7dd
    style C fill:#e2d9f3
    style E fill:#e2d9f3
    style F fill:#cfe2ff

    subgraph Fallback
        H["🤖 AI không chắc<br/>→ Hiển thị cảnh báo gốc<br/>+ link CWE/OWASP"]
        I["🧑‍💻 Dev báo giải thích sai<br/>→ Feedback loop"]
        J["⚠️ ≥1 Critical<br/>→ Bắt buộc tag<br/>người review thứ 2"]
    end
```

### Thông số kỳ vọng

| Metric | Trước | Sau | Giảm |
|---|---:|---:|---:|
| Tổng thời gian | ~75 phút | ~18 phút | **~76%** |
| Số bước thủ công (dev) | 5/6 | 3/5 | 40% |
| Bottleneck | Đọc + lọc (60') | Dev đọc giải thích (10') | Human boundary |
| Số lần Google/StackOverflow | 5-10 lần | 0-2 lần | **~80%** |
| Lỗi Critical bị bỏ sót | Có risk | ~0 (với AI hỗ trợ) | Mục tiêu |

---

## Fallback & Boundary

### Fallback mechanisms

```text
1. AI không chắc về lỗ hổng
   → Không tự đoán. Hiển thị cảnh báo gốc + link CWE/OWASP.

2. Dev báo giải thích sai
   → Feedback loop: gửi về để cải thiện RAG corpus.
   → Nếu >2 lỗi Critical sai trong 3 lần chạy → dừng pilot.

3. Alert ≥1 Critical severity
   → Bắt buộc tag người review thứ 2 (không để 1 dev tự quyết định).

4. Token cost >$1/repo
   → Chỉ scan critical files (không scan node_modules, test, docs).
```

### Human boundary

```text
AI được phép:      Giải thích cảnh báo, xếp hạng rủi ro, 
                   gợi ý cách sửa (code mẫu tham khảo)

AI không được phép: Tự sửa code lên repo
                    Tự quyết định false positive
                    Tự bịa lỗ hổng không có trong scan results
                    Check infrastructure security (OS, network)
                    Tự động merge PR
```

---

*Workflow file — Nhóm 16 — Day 02 Lab*
