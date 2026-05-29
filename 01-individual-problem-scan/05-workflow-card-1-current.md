# Current Workflow — Card #1 Prompt-Debug Loop

```mermaid
flowchart TD
    A["🧑‍💻 Dev: Viết prompt<br/>mô tả feature<br/>(2-5 phút)"] --> B["🤖 AI: Generate code<br/>(30s - 2 phút)"]
    B --> C["🧑‍💻 Dev: Copy code → Run<br/>(1-2 phút)"]
    C --> D{"✅ Code chạy đúng?"}
    D -->|"❌ Lỗi runtime / type / logic"| E["🧑‍💻 Dev: Diagnostic lỗi<br/>(2-5 phút)"]
    E --> F["🧑‍💻 Dev: Copy error →<br/>Viết prompt fix<br/>(3-5 phút)"]
    F --> G["🤖 AI: Generate lại<br/>(30s - 2 phút)"]
    G --> C
    D -->|"✅ Pass"| H["🧑‍💻 Dev: Review + Merge<br/>(5 phút)"]

    style D fill:#fff3cd
    style E fill:#f8d7da
    style F fill:#f8d7da
```

## Thông số

| Metric | Giá trị | Ghi chú |
|---|---|---|
| Tổng bước | 7 bước | Không tính vòng lặp |
| Số lần loop trung bình | 3-5 lần/task | Task đơn giản: 1-2; phức tạp: 5-8 |
| Thời gian mỗi loop | 5-10 phút | Diagnostic + prompt + gen |
| Tổng thời gian/task | 60-90 phút | Có thể lên 2h với task lớn |
| Thời gian hữu ích | ~15 phút | Code đúng + review |
| Thời gian lãng phí | 45-75 phút | Loop debug |

## Bottleneck chính

**Bước 5-6: Dev copy error + viết prompt fix + chờ AI generate lại.**

Đây là điểm nghẽn vì:
- Dev bị ngắt flow (đang nghĩ về solution → phải chuyển sang diagnostic mode)
- Viết prompt fix yêu cầu đọc hiểu error message → thời gian cognitive
- Chờ AI generate lại (dù 30-60s) làm gãy mạch suy nghĩ
- Mỗi lần loop làm tăng frustration và giảm trust vào AI
