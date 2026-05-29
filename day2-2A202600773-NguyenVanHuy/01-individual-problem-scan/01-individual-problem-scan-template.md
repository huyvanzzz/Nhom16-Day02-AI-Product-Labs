# 01 — Individual Problem Scan

## Scan rộng

| # | Lăng kính | Problem quan sát được | Ai đang đau? | Dấu hiệu thật |
|---|---|---|---|---|
| 1 | Pain từ người khác / Workflow | Cư dân Vinhomes gửi phản ánh về sự cố nhưng khó biết phản ánh đang được xử lý đến đâu | Cư dân, ban quản lý | Cư dân phải hỏi lại, ticket xử lý chậm, trạng thái không rõ |
| 2 | Tốn thời gian | Ban quản lý Vinhomes phải đọc, phân loại và chuyển phản ánh cư dân cho đúng bộ phận | Ban quản lý | Mỗi phản ánh cần đọc nội dung, kiểm tra thông tin, phân loại thủ công |
| 3 | AI có thể tốt hơn | Phản ánh của cư dân thường viết tự do, thiếu ảnh, thiếu vị trí hoặc có nhiều vấn đề trong cùng một phản ánh | Ban quản lý, bộ phận xử lý | Nhân viên phải hỏi lại cư dân hoặc chuyển ticket qua lại giữa các bộ phận |
| 4 | Lặp lại | Bộ phận xử lý phải cập nhật trạng thái phản ánh nhiều lần cho cư dân | Bộ phận kỹ thuật, vệ sinh, an ninh, cư dân | Nếu không cập nhật, cư dân tiếp tục hỏi lại |
| 5 | Tốn thời gian | Khách Vinpearl/VinWonders khó tự chọn lịch trình phù hợp vì có nhiều combo, vé, khách sạn và hoạt động | Khách du lịch, tư vấn viên | Khách phải mở nhiều trang, so sánh nhiều lựa chọn và hỏi tư vấn viên |
| 6 | AI có thể tốt hơn | Khách VinFast mới mua xe điện khó tìm đúng hướng dẫn về sạc pin, bảo dưỡng và cảnh báo xe | Khách mới mua xe, nhân viên tư vấn | Khách phải hỏi hotline/showroom hoặc tự đọc tài liệu dài |
| 7 | Workflow | Bệnh nhân Vinmec không biết cần chuẩn bị giấy tờ gì trước khi khám hoặc tái khám | Bệnh nhân, lễ tân | Đến quầy mới phát hiện thiếu giấy tờ, làm tăng thời gian chờ |
| 8 | Lặp lại / Tốn thời gian | Phụ huynh Vinschool phải theo dõi thông báo, lịch học, bài tập và hoạt động của con từ nhiều nguồn | Phụ huynh, giáo viên | Thông tin nằm rải rác trong app, email, nhóm lớp; dễ bỏ sót thông báo |

---

# Top 3 Problem Cards — Phân tích chi tiết

---

# Problem Card #1 — Vinhomes: Agent hỗ trợ xử lý phản ánh cư dân

## Problem 1 câu

Cư dân Vinhomes khi gửi phản ánh về sự cố trong khu đô thị thường khó theo dõi tiến độ xử lý, còn ban quản lý mất thời gian để kiểm tra thông tin, phân loại phản ánh, giao đúng bộ phận và nhắc xử lý nếu quá hạn.

## Actor

- **Cư dân Vinhomes:** người gặp sự cố và gửi phản ánh.
- **Ban quản lý:** người tiếp nhận, giám sát và xử lý các trường hợp quan trọng.
- **Bộ phận xử lý:** kỹ thuật, vệ sinh, an ninh, lễ tân hoặc nhà thầu.

## Thời điểm / bối cảnh

Khi cư dân gặp vấn đề trong quá trình sinh sống, ví dụ:

- Thang máy lỗi.
- Rò nước.
- Mất điện.
- Vệ sinh chưa đảm bảo.
- Tiếng ồn.
- Vấn đề an ninh.
- Cơ sở vật chất hỏng.

## Current workflow

```text
Cư dân gặp sự cố
→ gửi phản ánh qua app/hotline/quầy lễ tân
→ ban quản lý tiếp nhận
→ kiểm tra phản ánh có đủ thông tin không
→ hỏi lại cư dân nếu thiếu thông tin
→ phân loại phản ánh
→ giao cho bộ phận xử lý phù hợp
→ bộ phận xử lý sự cố
→ cập nhật trạng thái
→ cư dân xác nhận hoặc phản ánh lại
```

## Bottleneck

Bottleneck chính nằm ở đoạn:

```text
Kiểm tra thông tin → phân loại phản ánh → giao đúng bộ phận → theo dõi tiến độ.
```

Vì phản ánh của cư dân có thể viết tự do, thiếu ảnh, thiếu vị trí hoặc có nhiều vấn đề trong cùng một phản ánh. Nếu phân loại sai hoặc thiếu thông tin, ticket sẽ bị xử lý chậm.

## Impact

- Cư dân không biết phản ánh đang được xử lý đến đâu.
- Cư dân phải hỏi lại nhiều lần.
- Ban quản lý mất thời gian đọc và phân loại thủ công.
- Bộ phận xử lý nhận ticket thiếu thông tin.
- Một số sự cố khẩn cấp có thể chưa được ưu tiên đúng.
- Trải nghiệm cư dân giảm nếu phản ánh chậm được xử lý.

## Success metric

| Metric | Hiện tại | Mục tiêu |
|---|---:|---:|
| Thời gian phản hồi đầu tiên | Chưa đo / giả định 30-60 phút | Dưới 10-15 phút |
| Tỉ lệ ticket thiếu thông tin | Chưa đo | Giảm 30-50% |
| Thời gian phân loại phản ánh | Thủ công từng ticket | Agent gợi ý trong vài giây |
| Số lần cư dân hỏi lại trạng thái | Có thể nhiều lần | Giảm rõ rệt |
| Tỉ lệ ticket chuyển sai bộ phận | Chưa đo | Giảm nhờ phân loại chuẩn hóa |
| Số ticket quá hạn xử lý | Chưa đo | Giảm nhờ nhắc SLA tự động |

## Non-AI alternative

Có thể dùng form cố định và rule-based routing:

```text
Nếu cư dân chọn “thang máy” → chuyển kỹ thuật.
Nếu chọn “vệ sinh” → chuyển vệ sinh.
Nếu chọn “an ninh” → chuyển an ninh.
```

Cách này dễ làm và ít rủi ro. Tuy nhiên, nó chỉ hiệu quả khi cư dân chọn đúng danh mục và nhập đủ thông tin. Nếu cư dân mô tả tự do hoặc phản ánh nhiều vấn đề cùng lúc, rule-based có thể không đủ.

## AI hypothesis

AI/Agent có thể hỗ trợ:

- Đọc nội dung phản ánh dạng tự do.
- Phát hiện thông tin còn thiếu.
- Hỏi cư dân bổ sung nếu cần.
- Phân loại sự cố.
- Xác định mức độ ưu tiên.
- Tạo ticket chuẩn hóa.
- Đề xuất bộ phận xử lý.
- Theo dõi SLA và nhắc nếu quá hạn.
- Viết cập nhật trạng thái dễ hiểu cho cư dân.

## Future workflow

```text
Cư dân gửi phản ánh
→ Agent đọc nội dung
→ Agent kiểm tra thông tin đủ chưa
    → nếu thiếu: hỏi cư dân bổ sung
    → nếu đủ: tiếp tục
→ Agent phân loại sự cố
→ Agent xác định mức độ ưu tiên
→ Agent tạo ticket chuẩn hóa
→ nếu nhạy cảm/khẩn cấp: chuyển ban quản lý xác nhận
→ Agent chuyển ticket đến bộ phận phù hợp
→ bộ phận xử lý sự cố
→ Agent theo dõi SLA
    → nếu gần/quá hạn: nhắc bộ phận xử lý hoặc báo ban quản lý
→ bộ phận xử lý cập nhật kết quả
→ Agent cập nhật trạng thái cho cư dân
→ cư dân xác nhận
    → nếu hài lòng: đóng ticket
    → nếu chưa hài lòng: mở lại hoặc chuyển ban quản lý
```

## Boundary

Agent không thay thế hoàn toàn ban quản lý. Agent chỉ hỗ trợ điều phối.

```text
Agent không trực tiếp xử lý sự cố vật lý.
Agent không tự đóng ticket nếu chưa có xác nhận.
Agent không tự quyết định bồi thường hoặc xử phạt.
Agent không thay ban quản lý trong tình huống nhạy cảm.
Agent chỉ hỗ trợ tiếp nhận, hỏi thêm, phân loại, tạo ticket, điều phối, nhắc hạn và cập nhật trạng thái.
```

## Quick gut

```text
Agent
```

## Vì sao chọn làm Card #1

Bài này có actor rõ, workflow rõ, bottleneck cụ thể và có thể giải thích hợp lý vì sao cần Agent. Hệ thống không chỉ phân loại một lần, mà còn cần hỏi thêm, phân nhánh, theo dõi SLA và mở lại ticket nếu cư dân chưa hài lòng.

---

# Problem Card #2 — Vinpearl/VinWonders: Gợi ý lịch trình phù hợp cho khách du lịch

## Problem 1 câu

Khách du lịch khi đặt kỳ nghỉ tại Vinpearl/VinWonders có quá nhiều lựa chọn về khách sạn, vé vui chơi, combo, nhà hàng và hoạt động, nên mất thời gian tự tìm hiểu và khó xây lịch trình phù hợp với số ngày đi, ngân sách, nhóm đi cùng và sở thích.

## Actor

- **Khách du lịch:** người muốn đi Vinpearl/VinWonders nhưng chưa biết nên chọn lịch trình nào.
- **Tư vấn viên:** người phải trả lời câu hỏi và tư vấn combo/lịch trình cho khách.
- **Bộ phận booking:** người xác nhận dịch vụ cuối cùng.

## Thời điểm / bối cảnh

Trước khi khách đặt phòng, mua vé hoặc chọn combo du lịch. Đặc biệt với nhóm khách gia đình, khách có trẻ em, người lớn tuổi hoặc khách đi lần đầu.

## Current workflow

```text
Khách muốn đi Vinpearl/VinWonders
→ vào website/app để xem phòng, vé, combo, ưu đãi
→ đọc nhiều trang thông tin khác nhau
→ so sánh giá, địa điểm, giờ mở cửa, hoạt động
→ hỏi tư vấn viên hoặc người quen
→ tự ghép thành lịch trình
→ chọn combo/dịch vụ
→ đặt phòng hoặc mua vé
```

## Bottleneck

Bottleneck nằm ở bước:

```text
Tự đọc nhiều thông tin → so sánh nhiều lựa chọn → ghép thành lịch trình cụ thể.
```

Khách không chỉ cần xem thông tin, mà còn cần biến nhiều lựa chọn rời rạc thành một kế hoạch phù hợp với nhu cầu riêng.

## Impact

- Khách mất nhiều thời gian trước khi đặt dịch vụ.
- Khách dễ bỏ sót trải nghiệm phù hợp.
- Khách phải hỏi tư vấn viên nhiều lần.
- Tư vấn viên phải trả lời các câu hỏi lặp lại.
- Một số khách có thể bỏ dở quá trình booking vì quá nhiều lựa chọn.

## Success metric

| Metric | Hiện tại | Mục tiêu |
|---|---:|---:|
| Thời gian chọn lịch trình | Giả định 45-60 phút | Dưới 15 phút |
| Số lần khách hỏi tư vấn viên | Nhiều câu hỏi lặp lại | Giảm số câu hỏi cơ bản |
| Tỉ lệ khách hoàn tất booking | Chưa đo | Tăng sau khi xem gợi ý |
| Mức độ hài lòng với lịch trình | Chưa đo | Tăng qua feedback |
| Số bước khách phải tự so sánh | Nhiều bước thủ công | Giảm nhờ gợi ý tự động |

## Non-AI alternative

Có thể dùng:

- Bộ lọc theo ngân sách, số ngày, nhóm khách.
- Combo mẫu.
- Lịch trình mẫu 1 ngày, 2 ngày, 3 ngày.
- FAQ cho khách đi lần đầu.

Cách này đơn giản và dễ triển khai. Tuy nhiên, nó chưa cá nhân hóa tốt nếu khách có nhiều ràng buộc như trẻ em, người lớn tuổi, ngân sách cụ thể, sở thích nghỉ dưỡng/vui chơi/ẩm thực.

## AI hypothesis

AI có thể hỗ trợ:

- Hỏi nhu cầu của khách.
- Tóm tắt các lựa chọn phù hợp.
- Gợi ý lịch trình theo số ngày, nhóm khách và ngân sách.
- Giải thích vì sao nên chọn lịch trình đó.
- Đề xuất combo phù hợp.
- Cho phép khách chỉnh lại lịch trình.

## Future workflow

```text
Khách nhập nhu cầu
    - địa điểm
    - số ngày
    - số người
    - ngân sách
    - có trẻ em/người lớn tuổi không
    - sở thích: nghỉ dưỡng, vui chơi, ẩm thực, Safari, show

→ hệ thống lọc lựa chọn cơ bản bằng rule
→ AI tổng hợp các dịch vụ phù hợp
→ AI draft lịch trình
→ khách xem và chỉnh
→ tư vấn viên/hệ thống booking xác nhận giá, vé, phòng, giờ mở cửa
→ khách đặt dịch vụ
```

## Boundary

```text
AI không tự đặt dịch vụ.
AI không cam kết giá, vé, phòng hoặc giờ mở cửa nếu chưa được hệ thống booking xác nhận.
AI không thay tư vấn viên trong các trường hợp phức tạp.
AI chỉ hỗ trợ gợi ý lịch trình và combo dựa trên thông tin có sẵn.
```

## Quick gut

```text
Workflow
```

Có thể phát triển thành Agent sau này nếu hệ thống được kết nối với dữ liệu thời gian thực như tình trạng phòng, vé, giá và lịch hoạt động.

## Vì sao chưa chọn làm Card #1

Bài này hay, nhưng scope dễ bị rộng thành “AI travel planner”. Nếu muốn làm tốt cần dữ liệu cập nhật về giá, phòng, vé, giờ mở cửa và combo. Vì vậy, trong giai đoạn đầu nên chọn Workflow hơn là Agent.

---

# Problem Card #3 — VinFast: Hỗ trợ khách mới dùng xe điện

## Problem 1 câu

Khách hàng mới mua xe điện VinFast thường phải tự tìm hiểu nhiều thông tin về sạc pin, bảo dưỡng, cảnh báo xe và cách sử dụng tính năng, nên dễ hỏi lại hotline/showroom hoặc xử lý sai tình huống cơ bản.

## Actor

- **Khách mới mua xe điện VinFast:** người cần hướng dẫn sử dụng xe.
- **Nhân viên tư vấn/showroom:** người phải trả lời các câu hỏi lặp lại.
- **Bộ phận kỹ thuật/hậu mãi:** người xử lý các trường hợp phức tạp hoặc cần kiểm tra xe.

## Thời điểm / bối cảnh

Sau khi khách nhận xe và bắt đầu sử dụng xe điện trong đời sống hằng ngày. Các vấn đề thường gặp có thể là:

- Cách sạc pin.
- Thời điểm cần bảo dưỡng.
- Ý nghĩa cảnh báo trên xe.
- Cách dùng app hoặc tính năng xe.
- Khi nào cần gọi hỗ trợ kỹ thuật.

## Current workflow

```text
Khách nhận xe
→ đọc hướng dẫn sử dụng hoặc nghe tư vấn ban đầu
→ trong quá trình dùng xe gặp câu hỏi/tình huống mới
→ tự tìm trong tài liệu, app, website hoặc Google
→ nếu không hiểu thì gọi hotline/showroom
→ nhân viên giải thích hoặc hướng dẫn đặt lịch service
```

## Bottleneck

Bottleneck nằm ở bước:

```text
Khách phải tìm đúng hướng dẫn theo tình huống cụ thể.
```

Tài liệu có thể dài, còn câu hỏi của khách thường mang tính tình huống. Ví dụ: “Xe báo cảnh báo này thì có nên chạy tiếp không?”, “Sạc như thế nào để tốt cho pin?”, “Bao lâu cần bảo dưỡng?”.

## Impact

- Khách mất thời gian tìm hướng dẫn.
- Hotline/showroom nhận nhiều câu hỏi lặp lại.
- Khách có thể hiểu sai hướng dẫn.
- Một số tình huống đơn giản đáng lẽ tự xử lý được nhưng vẫn phải gọi hỗ trợ.
- Trải nghiệm sau mua bị giảm nếu khách cảm thấy khó dùng xe điện.

## Success metric

| Metric | Hiện tại | Mục tiêu |
|---|---:|---:|
| Số câu hỏi lặp lại gửi hotline/showroom | Chưa đo | Giảm theo tuần/tháng |
| Thời gian khách tìm được hướng dẫn đúng | Giả định 15-30 phút | Dưới 5 phút |
| Tỉ lệ câu hỏi cơ bản tự xử lý được | Chưa đo | Tăng lên |
| Số trường hợp phải chuyển kỹ thuật viên | Chưa đo | Chỉ chuyển khi thật sự cần |
| Mức độ hài lòng sau mua | Chưa đo | Tăng qua khảo sát |

## Non-AI alternative

Có thể dùng:

- FAQ cố định.
- Video hướng dẫn.
- Checklist sử dụng xe mới.
- Bộ lọc câu hỏi theo chủ đề: sạc, pin, bảo dưỡng, cảnh báo, app.
- Hotline tư vấn.

Cách này phù hợp cho các câu hỏi phổ biến, nhưng chưa tốt với câu hỏi viết theo ngữ cảnh cụ thể của từng khách.

## AI hypothesis

AI có thể hỗ trợ:

- Hiểu câu hỏi tự nhiên của khách.
- Tìm đúng phần hướng dẫn liên quan.
- Tóm tắt câu trả lời dễ hiểu.
- Đưa checklist an toàn cho các tình huống đơn giản.
- Phân biệt tình huống cơ bản và tình huống cần chuyển kỹ thuật viên.
- Gợi ý đặt lịch service nếu cần.

## Future workflow

```text
Khách gặp câu hỏi/tình huống khi dùng xe
→ khách nhập câu hỏi vào hệ thống
→ AI hiểu tình huống và xác định chủ đề
→ hệ thống tra nguồn hướng dẫn chính thức
→ AI tóm tắt hướng dẫn dễ hiểu
→ nếu là tình huống đơn giản: đưa checklist xử lý cơ bản
→ nếu có dấu hiệu rủi ro: khuyến nghị liên hệ hotline hoặc đặt lịch service
→ khách xác nhận đã xử lý được hay cần hỗ trợ thêm
```

## Boundary

```text
AI không thay kỹ thuật viên.
AI không tự chẩn đoán lỗi nghiêm trọng của xe.
AI không hướng dẫn can thiệp kỹ thuật nguy hiểm.
AI chỉ giải thích hướng dẫn chính thức và chuyển người dùng đến hotline/service khi cần.
Các vấn đề liên quan an toàn phải được chuyển cho nhân viên thật.
```

## Quick gut

```text
Workflow
```

Chưa nên chọn Agent ngay vì liên quan đến an toàn kỹ thuật. Giai đoạn đầu nên là Workflow: AI hiểu câu hỏi, tìm nguồn chính thức, tóm tắt hướng dẫn và chuyển kỹ thuật viên khi cần.

## Vì sao chưa chọn làm Card #1

Bài này có impact tốt, nhưng rủi ro cao hơn vì liên quan đến kỹ thuật xe, pin, sạc và an toàn. Nếu AI trả lời sai, hậu quả có thể nghiêm trọng hơn. Vì vậy boundary phải rất chặt và cần nguồn chính thức.

---

# Kết luận chọn card

| Card | Đánh giá nhanh |
|---|---|
| Vinhomes | Phù hợp nhất nếu muốn chọn Agent vì có nhiều bước phân nhánh, theo dõi và điều phối |
| Vinpearl/VinWonders | Phù hợp nếu muốn bài thiên về cá nhân hóa, nhưng nên chọn Workflow trước |
| VinFast | Có impact nhưng rủi ro kỹ thuật/an toàn cao hơn, cần boundary chặt |
