# 03 — Individual Reflection

> **Thành viên:** Nguyễn Văn Huy (2A202600773)
> Phần này tự viết theo trải nghiệm thật của tôi trong bài cá nhân 01 và bài nhóm 02. AI chỉ được dùng để gợi ý câu hỏi tự soi, không thay tôi chốt quyết định.

---

## 1. Đóng góp của tôi trong bài cá nhân 01

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Scan cá nhân | Tôi tự scan 8 problems từ trải nghiệm quanh Vinhomes, Vinpearl/VinWonders, VinFast, Vinmec và Vinschool. | Có nhiều candidate khác nhau, giúp tôi không bị chốt sớm vào một ý tưởng duy nhất. |
| Chọn top 3 | Tôi chọn 3 problem có workflow rõ nhất: xử lý phản ánh cư dân Vinhomes, gợi ý lịch trình du lịch, và hướng dẫn khách mới dùng xe điện. | Có bộ top 3 đủ để pitch với nhóm; trong đó card Vinhomes là card mạnh nhất của tôi ở phase cá nhân. |
| Viết Problem Card #1 | Tôi mô tả rõ actor, current workflow, bottleneck, impact, metric, non-AI alternative và AI hypothesis cho card Vinhomes. | Card này có actor rõ, workflow nhiều bước và có thể cân nhắc Agent, nên dễ pitch với nhóm. |
| Draft workflow | Tôi vẽ current workflow và future workflow cho bài toán phản ánh cư dân. | Nhìn rõ bước kiểm tra thông tin → phân loại → giao bộ phận là bottleneck chính. |
| Dùng AI ở phase 1 | Tôi dùng AI để gợi thêm problem và phản biện xem ý nào quá rộng hoặc chưa có workflow thật. | AI giúp tôi thấy rõ hơn các pain liên quan đến service/process automation, nhưng tôi bỏ các ý quá rộng như “AI travel planner toàn năng”. |

---

## 2. Đóng góp của tôi trong bài nhóm 02

| Hoạt động | Tôi đã làm gì? | Kết quả / ảnh hưởng |
|---|---|---|
| Pitch Problem Card | Tôi pitch các candidate như Vinhomes Agent, Vinpearl/VinWonders travel và VinFast EV Guide. | Nhóm thấy được góc nhìn về service/process automation và các bài toán nhiều bước. |
| Challenge bài của bạn khác | Tôi challenge các bạn khác ở chỗ scope, metric và boundary. | Nhóm phải kiểm tra lại xem bài nào thật sự có workflow rõ và bài nào bị solution-first. |
| Gom trùng / cluster | Tôi góp ý cho các candidate thuộc nhóm service/process automation. | Nhóm nhìn ra pattern chung là quy trình nhiều bước, dữ liệu rời rạc và cần người thật kiểm tra. |
| Chọn candidate problem | Dù bài cá nhân của tôi là bài service, tôi đồng ý với nhóm khi bài được chọn cuối cùng là Git Security Review vì bài đó có metric và so sánh Rule / Workflow / Agent rõ hơn. | Nhóm chốt được candidate cuối cùng sau scoring và validation. |
| Validation / research | Tôi tham gia đọc và đối chiếu research về Semgrep, CodeQL, SonarQube, và quick interview của nhóm. | Nhóm có bằng chứng để thu hẹp problem từ “scan + fix” thành “giải thích kết quả scan”. |
| Workflow / Problem Statement | Tôi góp ý workflow current/future, boundary và cách viết Problem Statement theo hướng rõ người thật kiểm tra cuối. | PS v1 chặt hơn, tránh đẩy AI sang tự quyết định thay người dùng. |
| Rule / Workflow / Agent | Tôi cùng nhóm so sánh 3 mức và chấp nhận kết luận Workflow là hợp lý hơn Agent cho bài nhóm. | Nhóm có quyết định rõ ràng: Go với scope nhỏ. |

---

## 3. Bảng tôi dùng AI như thế nào

| Phase | Tôi dùng AI để làm gì? | AI hữu ích ở đâu? | AI sai/hời hợt ở đâu? | Tôi sửa gì? |
|---|---|---|---|---|
| Scan cá nhân | Hỏi AI gợi thêm problem quanh Vinhomes, Vinpearl, VinFast, Vinmec, Vinschool | AI giúp tôi mở rộng góc nhìn về service/process automation | Có ý quá rộng kiểu “AI trợ lý du lịch toàn năng” hoặc thiếu workflow cụ thể | Tôi chỉ giữ problem có actor, workflow và dấu hiệu thật |
| Problem Card | Nhờ AI phản biện card Vinhomes để xem bottleneck và metric có đủ rõ không | AI chỉ ra phần nào cần đo thời gian, phần nào cần boundary rõ hơn | AI dễ đẩy sang Agent quá sớm | Tôi giữ Agent chỉ ở mức cân nhắc, không khẳng định ngay |
| Workflow | Dùng AI để viết lại current/future workflow cho gọn hơn | AI giúp flow rõ, dễ nhìn | AI có xu hướng gộp nhiều bước điều phối vào một chỗ | Tôi tách lại các bước hỏi thêm, phân loại, giao bộ phận, theo dõi SLA |
| Research | Hỏi AI gợi ý solution tương tự cho bài service hoặc travel | AI giúp tôi nghĩ ra các pattern gợi ý lịch trình, FAQ, hướng dẫn xe điện | AI nói rất tự tin dù chưa kiểm nguồn | Tôi chỉ giữ ý nào có dấu hiệu thật hoặc có thể kiểm chứng |
| Problem Statement | Nhờ AI phản biện PS v0 để xem actor, metric, boundary còn mơ hồ không | AI chỉ ra cần nói rõ người kiểm tra cuối là ai | AI có xu hướng làm bài toán rộng hơn mức cần thiết | Tôi thu hẹp lại theo workflow thực tế và boundary rõ ràng |
| Rule / Workflow / Agent | Hỏi AI so sánh 3 mức giải pháp | AI giúp tôi thấy Rule đôi khi đã đủ cho một số case | AI hay thích giải pháp “thông minh” hơn là giải pháp đúng bối cảnh | Tôi dựa vào workflow thật và chấp nhận kết luận của nhóm |

---

## 4. Bài học của tôi

- Tôi thấy cùng là một bài toán service, nhưng nếu workflow rõ thì mới biết nên dùng Rule, Workflow hay Agent.
- Tôi hiểu rõ hơn rằng problem tốt, đáng làm không chỉ là problem liên quan đến AI, mà phải có actor, bottleneck và metric rõ.
- Tôi học được cách challenge nhóm theo hướng thực dụng: hỏi xem metric đo thế nào, boundary ở đâu và ai là người kiểm tra cuối.
- Tôi cũng học được cách dùng AI đúng hơn: dùng để mở rộng góc nhìn và phản biện, không dùng để chốt thay mình.

---

## 5. Nếu làm lại

```text
Nếu làm lại, tôi sẽ validate baseline sớm hơn ở phase 1 và phase 2, đặc biệt là số lần phản ánh hoặc câu hỏi lặp lại và thời gian người dùng chờ phản hồi. Tôi cũng sẽ challenge nhóm mạnh hơn ở chỗ metric đo như thế nào, để tránh viết problem statement dựa quá nhiều vào cảm giác của mình.
```

---

*Day 02 Lab — Individual Reflection — Nguyễn Văn Huy*
