# Day 05 AI Product Lab — Checklist Hoàn Thành

> Tài liệu này giúp nhóm theo dõi những gì cần hoàn thành vào cuối Day 05.

## Cuối Day 05 Cần Có Gì?

### 1. **Individual Workshop** — Mổ App AI (Bắt buộc)

**File:** `01-invidual-workshop/app-teardown.md` (hoặc `app-teardown_[TênThànhViên].md` cho file cá nhân)

**Yêu cầu:**

- [ ] **Promise vs Reality:** Ghi lại app hứa gì vs thực tế làm được gì
  - Điền dạng: "App hứa [X], khi dùng thấy [Y]"
  - Có ít nhất **3 observations** từ self-use

- [ ] **Evidence:** Mỗi observation đi kèm:
  - [ ] Screenshot (hoặc đã lưu vào `/Screenshot/`)
  - [ ] Quote/input đã thử
  - [ ] Hành vi quan sát được

- [ ] **4 Paths — Bắt buộc phải có:**
  - [ ] **Happy path:** AI đúng, user thấy gì?
  - [ ] **Low-confidence:** AI không chắc, hệ thống phản ứng thế nào?
  - [ ] **Failure:** AI sai, user biết bằng cách nào?
  - [ ] **Correction:** User sửa, hệ thống học lại không?

- [ ] **Finding thành Product Decision:** Format:
  ```
  Khi user [trigger],
  AI/product [failure],
  hậu quả là [impact].
  Lỗi thuộc layer [promise/intent/data-tool/safety/UX recovery].
  Nên sửa bằng [requirement/UX/fallback/human role/test case].
  ```

- [ ] **Sketch as-is / to-be:**
  - [ ] As-is: flow hiện tại, đánh dấu điểm gãy
  - [ ] To-be: flow đề xuất, path được sửa

---

### 2. **Evidence Pack** — Gom Bằng Chứng (Bắt buộc)

**File:** `02-group-spec/evidence-pack.md`

**Yêu cầu:**

- [ ] **Mục 1 - Nhóm & Track:**
  - [ ] Tên nhóm
  - [ ] Track: Healthcare (hoặc track khác nếu đổi)
  - [ ] Product/app đã chọn: Ada Health (hoặc app khác)
  - [ ] Build slice đang nghĩ (1 đoạn ngắn mô tả ý tưởng ban đầu)

- [ ] **Mục 2 - Self-use Evidence:**
  - [ ] Ít nhất **2-3 observations** từ self-use Ada Health
  - [ ] Mỗi observation có: observation, screenshot/link, path liên quan, điều học được
  - [ ] Bảng được điền đầy đủ

- [ ] **Mục 3 - User / Review / Social Evidence:**
  - [ ] **Positive reviews:** Ít nhất 15 review/observation từ:
    - [ ] Ada App Store
    - [ ] WebMD App Store
    - [ ] K Health Trustpilot
    - [ ] MyVinmec / Vinmec
    - [ ] Reddit discussions
  
  - [ ] **Negative reviews:** Ít nhất 15 review/observation từ các nguồn trên
  
  - [ ] Mỗi review ghi: # / Quote / Source / User type / Pain point

  - [ ] **Evidence clusters:** Gom review theo pattern:
    - [ ] Trust issue
    - [ ] Too many questions
    - [ ] Wrong recommendation
    - [ ] Confusing input/output
    - [ ] Decision support needs

- [ ] **Mục 4 - Competitor Evidence:**
  - [ ] Ít nhất 3 app được test: Ada Health, WebMD, K Health, Babylon, ChatGPT, MyVinmec
  - [ ] Cùng input cho tất cả (ví dụ: sốt + đau họng)
  - [ ] Bảng điền: App / User flow / Strength / Weakness / Pattern học được

- [ ] **Mục 5 - Evidence → Insight:**
  - [ ] Xác định evidence nổi bật nhất
  - [ ] Viết insight dạng: "User không chỉ cần [X], họ thật ra cần [Y], vì [evidence]"

- [ ] **Mục 6 - Evidence đổi SPEC như thế nào:**
  - [ ] Tick các mục thay đổi (user / pain / build slice / auto/aug / 4 paths / failure mode / owner)
  - [ ] Ghi rõ 1-2 thay đổi quan trọng và lý do

---

### 3. **Thin SPEC v1** — Cam Kết Build Ngày Hôm Sau (Bắt buộc)

**File:** `02-group-spec/thin-spec.md` (hoặc copy từ `thin-spec-template.md`)

**Yêu cầu:**

- [ ] **Mục 1 - Track, Product, User:**
  - [ ] Track: Healthcare
  - [ ] Product/app thật: Ada Health
  - [ ] User cụ thể (không quá chung chung)
  - [ ] Nhóm có phải user thật không? Khác ở đâu?

- [ ] **Mục 2 - Evidence Summary:**
  - [ ] Bảng với các cột: Evidence / Nguồn / User/pain nói lên gì / SPEC phải đổi gì
  - [ ] Ít nhất 5-6 evidence chính

- [ ] **Mục 3 - Pain Statement:**
  - [ ] Dạng: "User đang gặp khó ở [điểm], vì [nguyên nhân], dẫn tới [hậu quả]"
  - [ ] Phải có bằng chứng trace từ evidence

- [ ] **Mục 4 - Build Slice:**
  - [ ] Dạng: "Cho [user cụ thể] đang [task/workflow], prototype dùng AI để [augment/automate hành động hẹp], tạo ra [output], và xử lý [failure mode] bằng [mitigation]"
  - [ ] Đủ nhỏ để demo trong 3-5 phút
  - [ ] Rõ ràng cái gì là out of scope

- [ ] **Mục 5 - Auto/Aug Decision:**
  - [ ] [ ] Augmentation: AI gợi ý, user quyết
  - [ ] [ ] Conditional automation: AI tự làm trong case hẹp, case mơ hồ chuyển người
  - [ ] [ ] Automation: AI tự quyết
  - [ ] Viết lý do chọn (vì sao chọn Auto hay Aug?)
  - [ ] Viết Human role là gì

- [ ] **Mục 6 - Four Paths:**
  - [ ] **Happy:** User mô tả rõ, AI trích xuất đúng, hỏi follow-up, ra kết quả → user thấy gì?
  - [ ] **Low-confidence:** User cung cấp thông tin chưa đủ → AI nhận biết độ chắc chắn thấp, hỏi thêm
  - [ ] **Failure:** AI suy luận sai / đánh giá sai mức độ nguy hiểm → kết quả không phù hợp
  - [ ] **Correction:** User phát hiện lỗi / bổ sung thông tin → AI cập nhật, giải thích vì sao đổi

- [ ] **Mục 7 - Failure Mode Nguy Hiểm Nhất:**
  - [ ] Mô tả: "Nếu [trigger], AI [failure], hậu quả là [impact]"
  - [ ] Ghi rõ prototype xử lý bằng cách nào
  - [ ] Ghi rõ owner kiểm thử path này

- [ ] **Mục 8 - Owner Plan:**
  - [ ] Bảng với: Thành viên / Việc phụ trách / Bằng chứng cần có trong repo
  - [ ] Các role: Research / SPEC / Prototype / Test / Demo / Repo
  - [ ] Mỗi người ghi deliverable cụ thể

---

## Thứ Tự Làm (Gợi Ý)

```timeline
16:00  | Chọn track/app (Healthcare → Ada Health)
16:15  | Các thành viên self-use Ada Health + tìm evidence nhanh
16:45  | Gom evidence → viết insight
17:00  | Chốt build slice + owner plan
Tối    | Hoàn thiện evidence pack + thin SPEC draft
```

---

## Red Flags — Đừng Nộp Nếu:

- [ ] ❌ Build slice vẫn là "AI assistant cho healthcare" (quá chung chung)
- [ ] ❌ Không có evidence (bịa ra ý tưởng mà không thử thực tế)
- [ ] ❌ Thành viên không rõ vai trò/owner (ai làm gì trong Day 06?)
- [ ] ❌ Failure mode không có hoặc vẫn chung chung
- [ ] ❌ Evidence không có nguồn / link hoặc không thể trace được
- [ ] ❌ Thin SPEC chỉ copy template mà không có những con số/quyết định cụ thể
- [ ] ❌ 4 Paths chỉ mô tả vòng (happy/low-conf/failure/correction) mà không ghi rõ **prototype cần code/mock gì cụ thể**

---

## Công Cụ Hỗ Trợ

1. **Template:** 
   - `01-invidual-workshop/app-teardown.md` (hướng dẫn cách mổ app)
   - `02-group-spec/evidence-pack.md` (template evidence + example)
   - `02-group-spec/thin-spec-template.md` (template thin SPEC + example)

2. **Toolkit:**
   - `02-group-spec/synthesis-decide-toolkit.md` (từ evidence đến build slice)

3. **Screenshots:**
   - `/Screenshot/` folder có ảnh Ada Health từ self-use

---

## Ghi Chú Quan Trọng

- **Evidence Pack phải CÓ NGUỒN NGOÀI NHÓM** (review, social, competitors) — không chỉ self-use
- **Build Slice phải DEMO ĐƯỢC trong 3-5 phút sáng Day 06** — đừng quá tham
- **Failure Mode phải là RỦI RO THẬT** — từ evidence hoặc design sai, không phải lẽ ra không xảy ra
- **Owner Plan phải RÕNG CÁC HỘI CHÚNG từng người** — tránh "ai cũng phụ trách tất cả"
- **Thin SPEC là CAM KẾT BUILD** — mỗi section phải đủ cụ thể để coder biết bắt đầu từ đâu

---

## Cách Nộp Bài (Day 06)

Mỗi học viên nộp **một repo cá nhân**:

```
Day06-MãHọcViên-HọVàTên/
├── 01-invidual-workshop/
│   └── app-teardown.md (hoặc app-teardown_[TênThànhViên].md)
├── 02-group-spec/
│   ├── evidence-pack.md (bản cuối nhóm)
│   ├── thin-spec.md (bản cuối nhóm)
│   └── synthesis-decide-toolkit.md (nếu nhóm ghi rõ)
└── README.md (reflection cá nhân về vai trò + AI hỗ trợ + bài học)
```

---

**Xong chưa? Bắt đầu nha!** 🚀

Last updated: June 3, 2026
