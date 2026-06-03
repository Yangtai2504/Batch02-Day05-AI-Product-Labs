# Workshop — Mổ App AI Thật
> Member 4 — Nguyễn Tiến Dương  
> App: Ada Health | Track: Healthcare

---

## 1. Sản phẩm đã dùng thử

**Ada Health** — AI symptom checker, available trên iOS/Android.

---

## 2. Promise vs Reality

**App hứa gì?**
Giúp user hiểu tình trạng sức khỏe của mình thông qua đánh giá triệu chứng thông minh, đưa ra gợi ý hành động phù hợp (self-care, gặp bác sĩ, hoặc cấp cứu).

**User nào được hứa sẽ được giúp?**
Người có triệu chứng nhẹ đến vừa, chưa biết mức độ nghiêm trọng, muốn tự đánh giá trước khi quyết định có đi khám không.

**Kỳ vọng khi dùng thật:**
Mô tả triệu chứng tự nhiên → App hiểu → Hỏi thêm đúng chỗ → Đưa ra đánh giá rõ ràng và giải thích được tại sao.

**Điểm gãy quan sát được:**
- App yêu cầu trả lời chuỗi câu hỏi có cấu trúc cứng (trắc nghiệm), không phải hội thoại tự nhiên → gây mệt mỏi.
- Kết quả cuối trả ra danh sách nhiều khả năng bệnh (Flu, COVID-19...) với mức độ khác nhau nhưng không giải thích rõ tại sao triệu chứng đó dẫn đến từng kết quả → user bối rối, không biết tin cái nào.
- Không có tín hiệu rõ ràng khi nào AI đang không chắc — tone trình bày kết quả như nhau dù confidence cao hay thấp.

---

## 3. Bốn paths

### Happy path
**Trigger:** User nhập sốt + đau họng 2 ngày, trả lời đủ các câu hỏi follow-up của Ada.  
**AI làm gì:** Hỏi thêm về mức độ sốt, có ho không, tiếp xúc gần ai không → đưa ra kết quả Flu/COVID-19 với mức độ triage "See Doctor within 24h".  
**User thấy gì:** Kết quả có danh sách khả năng bệnh, badge mức độ khẩn, nút "Learn more". Nguồn dẫn được đính kèm.  
**Observation:** Happy path hoạt động ổn khi triệu chứng rõ ràng và user kiên nhẫn trả lời đủ câu hỏi.

### Low-confidence path
**Trigger:** User mô tả "mệt mỏi, hơi chóng mặt" — triệu chứng mơ hồ, không đặc hiệu.  
**AI làm gì:** Tiếp tục hỏi thêm nhưng vẫn ra kết quả cuối với danh sách dài nhiều bệnh khả năng.  
**Điểm gãy:** App không báo hiệu rằng mình đang không chắc — tone tự tin như case rõ ràng. Không có chip "Tôi cần thêm thông tin" hay "Triệu chứng này chưa đủ để đánh giá".  
**Hậu quả:** User không biết kết quả này đáng tin ở mức nào.

### Failure path
**Trigger:** User nhập đau ngực lan ra tay trái + khó thở (red flag rõ ràng).  
**AI làm gì:** Vẫn đi qua flow câu hỏi thông thường trước khi escalate → mất thời gian trong tình huống cần hành động ngay.  
**Điểm gãy:** Red flag keyword không được detect sớm để bypass flow và escalate ngay lập tức. Babylon Health đã phá sản vì lỗi tương tự — bỏ sót dấu hiệu đau tim.  
**Hậu quả:** Với case khẩn cấp thật, mỗi giây đều quan trọng — flow hỏi nhiều câu có thể gây chậm trễ nguy hiểm.

### Correction path
**Trigger:** User thấy kết quả sai (ví dụ app gợi ý bệnh không phù hợp), muốn sửa.  
**AI làm gì:** Không có cơ chế correction rõ ràng — user chỉ có thể bắt đầu lại từ đầu.  
**Điểm gãy:** Không có "Report sai", không có undo, không có chỗ sửa từng triệu chứng đã nhập. Data correction không được log.  
**Hậu quả:** User thoát app thay vì thử lại. Không có signal nào để hệ thống học và cải thiện.

---

## 4. Findings thành product decision

**Finding 1 — Questionnaire fatigue**
```
Khi user phải trả lời chuỗi câu hỏi trắc nghiệm cứng nhắc,
AI thu thập được thông tin nhưng user mất kiên nhẫn và bỏ giữa chừng,
hậu quả là tỉ lệ hoàn thành thấp và data đầu vào không đủ để triage chính xác.
Lỗi thuộc layer UX + Intent.
Nên sửa bằng: conversation-first intake — AI trích xuất triệu chứng từ mô tả tự nhiên,
chỉ hỏi thêm những thông tin thật sự còn thiếu (tối đa 3 lượt).
```

**Finding 2 — Kết quả không có giải thích**
```
Khi AI trả ra danh sách nhiều khả năng bệnh mà không giải thích
triệu chứng nào dẫn tới từng kết quả,
hậu quả là user bối rối, không biết tin cái nào, mất trust vào hệ thống.
Lỗi thuộc layer UX Recovery + Trust.
Nên sửa bằng: kèm theo mỗi kết quả một dòng giải thích ngắn
"Kết quả này dựa trên: [triệu chứng X, Y, Z]".
```

**Finding 3 — Red flag không được xử lý ưu tiên**
```
Khi user nhập triệu chứng có red flag (đau ngực + khó thở),
AI vẫn đi qua toàn bộ flow câu hỏi thông thường thay vì escalate ngay,
hậu quả là chậm trễ nguy hiểm trong tình huống cần hành động tức thì.
Lỗi thuộc layer Safety.
Nên sửa bằng: red flag keyword detection ở bước đầu tiên —
nếu detect được, bypass flow và hiển thị ngay "Gọi cấp cứu 115" trước khi làm bất cứ điều gì khác.
```

**Finding 4 — Không có correction path**
```
Khi user nhận kết quả sai và muốn sửa,
app không cung cấp cơ chế nào ngoài bắt đầu lại từ đầu,
hậu quả là user thoát app và hệ thống mất đi signal để cải thiện.
Lỗi thuộc layer UX Recovery + Learning Signal.
Nên sửa bằng: correction log có moderation — user có thể "report sai" hoặc
chỉnh sửa từng triệu chứng đã nhập, data được queue để human review trước khi dùng để cập nhật rule.
```

---

## 5. Sketch AS-IS / TO-BE

### AS-IS — Flow hiện tại Ada Health

```
[User mở app]
      │
      ▼
[Nhập triệu chứng ban đầu (free text)]
      │
      ▼
[App chuyển sang questionnaire cứng]     ← ĐIỂM GÃY 1: mất tính tự nhiên
 Hỏi 10-15 câu trắc nghiệm liên tiếp
      │
   ┌──┴──────────────────────────┐
   │                             │
[User trả lời đủ]          [User bỏ giữa chừng]  ← ĐIỂM GÃY 2: drop-off cao
   │                             │
   ▼                             ▼
[Kết quả: danh sách bệnh       [Không có kết quả]
 + mức độ triage]
   │
   ▼
[Hiện kết quả — không giải thích  ← ĐIỂM GÃY 3: user bối rối
 tại sao từng bệnh được gợi ý]
   │
   ▼
[User muốn sửa → không có chỗ]   ← ĐIỂM GÃY 4: không có correction path
[User gặp red flag → vẫn hỏi tiếp]  ← ĐIỂM GÃY 5: red flag không được ưu tiên
```

### TO-BE — Flow đề xuất

```
[User mở app]
      │
      ▼
[User mô tả triệu chứng tự nhiên]
      │
      ▼
[AI detect red flag keyword?]        ← CẢI TIẾN 1: kiểm tra red flag ngay
   │                    │
  [Có]                [Không]
   │                    │
   ▼                    ▼
[Hiện ngay:        [AI trích xuất triệu chứng từ mô tả]
 "Gọi 115 ngay"]    + Hỏi thêm tối đa 3 lượt          ← CẢI TIẾN 2: conversation-first
                        │
                        ▼
                   [AI phân loại triage]
                   Self-care / See Doctor / Emergency
                        │
                        ▼
                   [Kết quả + giải thích]               ← CẢI TIẾN 3: kèm lý do
                   "Dựa trên: sốt 38.5°C, đau họng 2 ngày"
                        │
                   ┌────┴──────────────────┐
                   │                       │
              [AI tự tin]           [AI không chắc]     ← CẢI TIẾN 4: signal uncertainty
                   │                       │
              [Hiện kết quả]        [Hiện: "Chưa đủ thông tin
                                     để đánh giá chính xác"
                                     + chip: Mô tả thêm /
                                     Hỏi bác sĩ]
                        │
                        ▼
                   [User muốn sửa → Report sai]         ← CẢI TIẾN 5: correction path
                   Data → queue → human review → update rule
```

---

## 6. Tự kiểm trước khi nộp

- [x] Có ít nhất 1 screenshot hoặc observation cụ thể (từ evidence-pack Member 1).
- [x] Có đủ 4 paths — đánh dấu rõ path nào thiếu trong product hiện tại.
- [x] Findings được viết thành product decision, không chỉ là nhận xét.
- [x] Sketch có AS-IS và TO-BE.
- [x] Mỗi finding nói rõ sẽ đổi gì trong SPEC: red flag detection, conversation-first intake, explanation layer, correction log với moderation.
