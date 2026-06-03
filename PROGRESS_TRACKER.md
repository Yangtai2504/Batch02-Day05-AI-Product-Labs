# Day 05 Progress Tracker

> File này để nhóm theo dõi tiến độ từng thành viên trong ngày.

## Status Legend

- ⚪ **Not Started** — Chưa bắt đầu
- 🟡 **In Progress** — Đang làm
- 🟢 **Complete** — Hoàn thành
- ⚠️ **Blocked** — Bị kẹt, cần support

---

## Team Members & Deliverables

| Thành viên | Vai trò | Deliverable | Status | Notes |
|---|---|---|---|---|
| Huyền | Research / Evidence Lead (Self-use) | Self-use evidence table (2-3 test cases), screenshot, observation | ⚪ | |
| Kiên | Research / Evidence Lead (User Reviews) | 15 positive + 15 negative reviews, clustered into pain patterns | ⚪ | |
| Dương | SPEC Writer | Thin SPEC v1: Pain statement, Build slice, 4 paths, Failure mode | ⚪ | |
| Dũng | Prototype Builder | Prototype source code, prompt, UI/interaction screenshot | ⚪ | |
| Lương | QA / Failure Path Tester | Test cases for Happy/Low-conf/Failure/Correction paths | ⚪ | |
| Huỳnh | Demo & Repo Manager | demo_script.md, README.md, video/slide demo | ⚪ | |

---

## Day 05 Milestones

| Time | Milestone | Owner | Status |
|---|---|---|---|
| 16:00 | Track & app selected (Healthcare → Ada Health) | Team | ⚪ |
| 16:15 | Self-use testing starts | Huyền, Dũng | ⚪ |
| 16:45 | Evidence gom + insight drafted | Kiên, Huyền | ⚪ |
| 17:00 | Build slice chốt + owner plan drafted | Dương, Huỳnh | ⚪ |
| 17:30 | Evidence pack DRAFT done | Kiên, Huyền | ⚪ |
| 18:00 | Thin SPEC DRAFT done | Dương | ⚪ |
| Evening | Prototype skeleton starts | Dũng | ⚪ |
| Evening | Test paths sketched | Lương | ⚪ |

---

## Dependency Map

```
Evidence (Huyền, Kiên)
    ↓
Insight & Build Slice (Dương)
    ↓
Thin SPEC (Dương)
    ├→ Prototype skeleton (Dũng)
    │    ↓
    │  Test cases (Lương)
    │    ↓
    │  Demo script (Huỳnh)
    │
    └→ Evidence Pack Final (Kiên, Huyền)
```

---

## Real-Time Notes

### What's Working Well ✅

- (Update as you go)

### Blockers ⚠️

- (Update if stuck)

### Questions for Mentor 💬

- (Track questions for instructor support)

---

## Evidence Collection Progress

### Self-use (Huyền + Dũng test Ada Health)

- [ ] Test case 1: Sốt + đau họng
- [ ] Test case 2: Ho + sốt
- [ ] Test case 3: Đau bụng
- [ ] Screenshot & observation logged
- [ ] 4 paths identified

**Status:** ⚪  
**By:** Huyền  

### User Reviews (Kiên collects from public sources)

- [ ] 15 positive reviews collected from Ada App Store
- [ ] 15 positive reviews collected from WebMD / K Health / Reddit
- [ ] 15 negative reviews collected from Ada App Store
- [ ] 15 negative reviews collected from WebMD / K Health / Reddit
- [ ] Clustered into pain patterns (Trust / Too Many Q / Wrong Rec / etc)
- [ ] Evidence pack table filled

**Status:** ⚪  
**By:** Kiên  

### Competitor Research (Huyền or Kiên)

- [ ] Ada Health tested (3 test cases, Sốt+đau họng, Mệt+chóng, Đau ngực)
- [ ] WebMD tested
- [ ] K Health tested
- [ ] MyVinmec tested
- [ ] Competitor table filled with flow/strength/weakness
- [ ] Patterns extracted

**Status:** ⚪  
**By:** Kiên  

---

## Evidence → Insight → Build Slice

### Evidence Synthesis (Kiên + Dương)

- [ ] Evidence clusters drafted
- [ ] Top 5-6 evidence points identified
- [ ] Insight statement written

**Status:** ⚪

### Build Slice Chốt (Dương + Team)

- [ ] Pain statement finalized
- [ ] User cụ thể confirmed
- [ ] AI decision type chosen (Augmentation / Conditional Auto / Auto)
- [ ] Build slice 1-liner ready
- [ ] 4 paths outlined
- [ ] Failure mode identified

**Status:** ⚪

---

## Spec & Prototype Readiness

### Thin SPEC Draft (Dương)

- [ ] Section 1: Track/User ✓
- [ ] Section 2: Evidence summary ✓
- [ ] Section 3: Pain statement ✓
- [ ] Section 4: Build slice ✓
- [ ] Section 5: Auto/Aug decision ✓
- [ ] Section 6: 4 Paths detailed ✓
- [ ] Section 7: Failure mode ✓
- [ ] Section 8: Owner plan ✓

**Status:** ⚪

### Prototype Skeleton (Dũng)

- [ ] Conversational UI mock (Figma / HTML / Jupyter)
- [ ] System prompt drafted
- [ ] Input/output format defined
- [ ] Happy path walkthrough possible

**Status:** ⚪

### Test Plan (Lương)

- [ ] Happy path test case ready
- [ ] Low-confidence path test case ready
- [ ] Failure path test case ready
- [ ] Correction path test case ready

**Status:** ⚪

---

## Final Deliverables Check

### Individual Workshop (Huyền's app-teardown.md)

- [ ] Promise vs reality
- [ ] 3+ observations with screenshot
- [ ] 4 paths described
- [ ] Finding → product decision
- [ ] Sketch as-is / to-be

**Status:** ⚪  
**Due by:** EOD

### Evidence Pack (evidence-pack.md)

- [ ] Team info + track
- [ ] Self-use evidence table
- [ ] 15 positive + 15 negative reviews
- [ ] Competitor evidence table
- [ ] Evidence clusters
- [ ] Insight derived
- [ ] How evidence changed SPEC

**Status:** ⚪  
**Due by:** EOD

### Thin SPEC (thin-spec.md)

- [ ] All 8 sections filled
- [ ] No placeholders
- [ ] Evidence traced to SPEC changes
- [ ] 4 paths concrete (not vague)
- [ ] Failure mode specific & testable

**Status:** ⚪  
**Due by:** EOD

---

## Team Sync Points

### 16:30 — First Check-in (10 min)

**Questions:**
- Self-use: Any blockers finding bugs?
- Evidence: Sources accessible?
- Plan: Still on track?

### 17:15 — Mid-day Sync (10 min)

**Checkpoint:**
- Evidence clusters: What patterns emerged?
- Build slice: Is 3-5 min demo doable?
- Prototype: What's the tech stack?

### 18:30 — Evening Review (15 min)

**Assessment:**
- Evidence pack DRAFT: Coverage enough?
- Thin SPEC DRAFT: Clarity check?
- Demo: Can Huỳnh narrate it by morning?
- Blockers: What needs overnight work?

---

## Notes for Next Day (Day 06 Morning)

### What Worked

- (To add)

### What to Improve

- (To add)

### Fallback Plan if Behind

- If evidence incomplete: Use minimal evidence + strong hypothesis
- If prototype incomplete: Use UI mockup + wizard-of-oz demo
- If test cases not ready: Demo happy + failure paths, skip low-conf/correction
- If spec not final: Use this Draft + annotate changes during demo

---

**Last Updated:** [Add date]  
**Updated By:** [Add name]
