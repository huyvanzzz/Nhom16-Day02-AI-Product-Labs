# Future Workflow — Card #3 AI Code Trust Issue

## Nguyên lý: Convention + Label — ai cũng biết code nào từ AI và đánh giá đúng mức

```mermaid
flowchart TD
    A["🧑‍💻 Dev: Code feature bằng AI<br/>(30-60 phút)"] --> B["🧑‍💻 Dev: Self-review code AI<br/>theo convention của team<br/>(10-15 phút)"]
    B --> C["🧑‍💻 Dev: Push PR + label rõ<br/>'Phần X do AI generate'"]
    C --> D["👀 Reviewer: Mở PR"]
    D --> E{"👀 Có label AI gen không?"}
    E -->|"Có"| F["👀 Reviewer: Ưu tiên review<br/>LOGIC (không review style)"]
    E -->|"Không"| G["👀 Reviewer: Review bình thường<br/>(style + logic)"]
    F --> H["👀 Reviewer: Chỉ request changes<br/>nếu logic sai"]
    H --> I["🧑‍💻 Dev: Fix logic + re-push"]
    I --> J["✅ Merge<br/>Tổng: 1-1.5 giờ"]
    G --> J

    style B fill:#d1e7dd
    style C fill:#d1e7dd
    style F fill:#cff4fc
```

## Thông số

| Metric | Trước | Sau kỳ vọng | Ghi chú |
|---|---|---|---|
| Review time/PR | 60-120 phút | 30-45 phút | Chỉ review logic cho AI code |
| Số vòng review | 3-4 | 1-2 | Giảm style-related cycles |
| Số comment/PR | 15-25 | 5-10 | Chỉ comment logic |
| Team friction | Cao | Thấp | Convention rõ → trust rõ |
| Dev tự review | Không bắt buộc | Bắt buộc | Dev phải self-review AI output |

## Fallback

```
Không label AI gen → reviewer mặc định review bình thường (style + logic).
Label sai = trust issue nghiêm trọng hơn.
```

## Human boundary

- Dev phải self-review AI output trước push (bắt buộc)
- Reviewer vẫn review logic (AI có thể sai logic dù pass test)
- Convention team phải được thống nhất trước, không áp đặt

## Risk & mitigation

| Risk | Mitigation |
|---|---|
| Dev lợi dụng label → không review AI output | Policy: label AI = dev đã review. Nếu bug do AI → dev chịu trách nhiệm |
| Reviewer vẫn review style dù có label | Training reviewer: focus logic, ignore style cho AI code |
| Team có convention khác nhau | Thống nhất convention trong PR template |
