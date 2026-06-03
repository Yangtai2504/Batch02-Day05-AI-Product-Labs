# Workshop — Mổ App AI Thật

**Người thực hiện:** Huyền
**MSV:** 2A202600650
**App thử:** Ada Health
**Thời gian:** 40 phút
**Hình thức:** cá nhân trước, chia sẻ theo nhóm sau
**Output:** finding note + sketch `as-is / to-be`

## 1. Product hứa gì?

Ada Health hứa giúp user nhanh chóng hiểu triệu chứng, đánh giá mức độ nghiêm trọng và đề xuất hành động y tế phù hợp.

## 2. User nào được hứa giúp?

Người đang có triệu chứng ban đầu (sốt, ho, đau họng, mệt mỏi), cần biết có nên tự chăm sóc, test COVID, hay đi khám.

## 3. Kỳ vọng AI làm được task nào?

- Nhận diện triệu chứng chính ngay khi user nhập.
- Hỏi lại đúng các yếu tố quan trọng (thời gian, độ nặng, dấu hiệu kèm theo).
- Trả kết quả ngắn gọn, rõ ràng và gợi ý hành động tiếp theo.
- Giảm thiểu sự mơ hồ khi có nhiều khả năng chẩn đoán.

## 4. Dùng thật, điểm gãy xuất hiện ở đâu?

### 4.1 Kịch bản dùng
- User mở app, chọn nhập triệu chứng.
- Input: "Tôi bị sốt và đau họng".
- App bắt đầu hỏi từng câu một rồi đưa ra kết quả.

### 4.2 Điều quan sát được
- App hỏi nhiều câu bắt đầu bằng "Bạn có..." ngay cả khi triệu chứng rõ ràng.
- Một số câu hỏi lặp lại cảm giác chung chung, khiến user mất kiên nhẫn.
- Kết quả trả về danh sách nhiều khả năng (Flu, COVID-19, cảm lạnh) mà không xếp thứ tự ưu tiên.
- App không kết luận rõ hành động tiếp theo, chỉ nói "hãy gặp bác sĩ nếu tình trạng nghiêm trọng".

### 4.3 Vấn đề chính
- Flow kéo dài và không hiệu quả với user cần câu trả lời nhanh.
- User bị chuyển từ mục tiêu "muốn biết nên làm gì" sang "phải đọc nhiều khả năng bệnh".
- Thiếu triage: không phân biệt rõ ràng khi cần test ngay, nghỉ ngơi tại nhà hay đi khám.

## 5. Evidence

- Screenshot: màn kết quả Ada Health sau 7 câu hỏi.
- Prompt / input ban đầu: "Tôi bị sốt và đau họng".
- Hành vi quan sát: app vẫn nhận đúng triệu chứng nhưng chưa cho hành động cụ thể.
- Ghi chú thêm: app trả thông tin nguy cơ COVID-19 nhưng không hướng dẫn rõ test hay cách theo dõi triệu chứng.

## 6. 4 paths

| Path | Nội dung |
|---|---|
| Happy | AI xác định đúng triệu chứng chính và trả về 1 hành động ưu tiên: nghỉ ngơi / test COVID / khám ngay. |
| Low-confidence | AI chưa chắc, hỏi thêm 1-2 câu trọng tâm: thời gian sốt, khó thở, mệt mỏi nặng. |
| Failure | AI trả nhiều khả năng bệnh và không chỉ ra hành động cụ thể, user bối rối không biết làm gì. |
| Correction | User sửa triệu chứng hoặc chọn "tôi không chắc", app giữ context và hỏi lại theo hướng rõ ràng. |

## 7. Finding thành quyết định

### Finding
Khi user nhập "Tôi bị sốt và đau họng", app hỏi nhiều câu phụ và trả về danh sách bệnh khả dĩ, dẫn đến user dễ lo lắng và không biết bước tiếp theo.

### Decision
Chuyển trọng tâm từ "dự đoán bệnh" sang "triage hành động".
- Nếu AI đủ tự tin: cho 1 hành động chính cùng lý do.
- Nếu AI không đủ tự tin: hỏi thêm 1-2 câu trọng tâm, không hỏi lan man.
- Nếu user sửa input: giữ logic, không reset toàn bộ flow.

## 8. Sketch as-is / to-be

### As-is
- User nhập triệu chứng → App hỏi nhiều câu sâu/future → Kết quả show nhiều bệnh → User hoang mang.

### To-be
- User nhập triệu chứng → App xác nhận yếu tố quan trọng nhanh → Kết quả show 1 hành động chính + lý do + cảnh báo rõ ràng nếu cần test hoặc khám.

## 9. Điều này đổi gì trong SPEC?

- Thêm requirement: "Ngay khi xác định triệu chứng chính, app phải trả hành động ưu tiên thay vì chỉ liệt kê khả năng".
- Thêm path rõ ràng cho low-confidence: "nếu không đủ dữ liệu, app chỉ hỏi tối đa 2 câu quan trọng".
- Thêm failure mode: "app không được đưa ra nhiều khả năng bệnh cùng lúc nếu user chưa rõ mục tiêu".
- Huyền thực hiện kiểm thử phần này để xác nhận trải nghiệm triage rõ ràng.

## 10. Next steps for Huyền

- Hoàn thiện screenshot và note chi tiết từng câu hỏi của app.
- Ghi lại thời lượng mỗi bước để chứng minh flow có thể rút ngắn.
- Chia sẻ phát hiện với team để cập nhật evidence pack và thin spec.
