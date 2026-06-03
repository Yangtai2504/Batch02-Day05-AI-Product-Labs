# 🚀 Quick Start — Day 05 AI Product Lab

> 5 bước để nhóm có thể bắt đầu ngay lập tức.

---

## 🎯 Big Picture

**Goal:** Từ problem thật → evidence → build slice → thin SPEC đủ để Day 06 code

**Timeline:** 16:00 (pick track) → ~18:00 (draft ready) → tối (polish)

**Output:** 3 files đạt tiêu chuẩn nộp bài

---

## 📋 Your Track: Healthcare → Ada Health

- **Product:** Ada Health (symptom checker AI)
- **Problem space:** People describing symptoms don't know when to see a doctor
- **Our angle:** Natural conversation symptom assessment (instead of form-filling)

---

## ⏱ Right Now (16:00–16:15)

### Step 1️⃣: Assign Roles

Copy-paste and fill out:

```markdown
| Name | Role | Day06 Deliverable |
|---|---|---|
| [Huyền] | Self-use tester | app-teardown.md (observations + 4 paths) |
| [Kiên] | Review collector | evidence-pack.md (positive + negative reviews) |
| [Dương] | SPEC writer | thin-spec.md (pain → build slice → 4 paths) |
| [Dũng] | Prototype builder | Code + UI mockup + system prompt |
| [Lương] | QA tester | Test cases for 4 paths |
| [Huỳnh] | Demo owner | demo_script.md + repo README |
```

**→ Update PROGRESS_TRACKER.md**

---

## 🧪 Step 2️⃣: Self-Use Testing (16:15–16:45)

**Who:** Huyền + Dũng (and whole team observes)  
**Do:** Open Ada Health app and try 3 test cases

### Test Cases:

1. **Clear case:** "Sốt 2 ngày, đau họng"
2. **Vague case:** "Mệt, hơi chóng mặt"
3. **Red flag:** "Đau ngực, khó thở"

### Observe & Log:

For each case, fill this **as you go:**

```markdown
## Test Case 1: Sốt + đau họng

**Input:** [What user types/clicks]

**AI Response:** [What the system asks/outputs]

**Screenshot:** [Take 2-3 screenshots]

**Observations:**
- How many questions did it ask?
- Did it ask relevant follow-ups or waste time?
- How clear was the output (diagnosis + triage level + confidence)?
- Did it explain why?

**4 Paths Observation:**
- Happy: Is it showing clear triage + next action?
- Low-confidence: Does it ask clarifying questions if unsure?
- Failure: What would break this?
- Correction: Can user fix what the AI got wrong?
```

**→ Save in `/Screenshot/` folder and link in app-teardown.md**

---

## 📚 Step 3️⃣: Collect Evidence Fast (16:45–17:15)

**Who:** Kiên (+ Huyền helps organize)

### Go to These Sources & Collect:

| Source | What to Look For | Target # |
|---|---|---|
| Ada App Store reviews | "I liked..." "The problem was..." | 15 positive + 15 negative |
| WebMD Symptom Checker | Same | 15 positive + 15 negative |
| Reddit (r/Health, r/HealthAnxiety) | User complaints or praise | 10 quotes |
| K Health reviews (Trustpilot) | Telehealth feedback | 10 quotes |

### Format Each Review:

```markdown
| # | Quote | Source | User Type | Pain Point |
|---|---|---|---|---|
| P01 | "App helped me understand I probably had flu not COVID" | Ada App Store | Person with anxiety | Too many possibilities, needs clarity |
| N01 | "Updated version is less accurate, lost my chat history" | Ada Google Play | Previous user | Trust issue + data loss |
```

**→ Fill `02-group-spec/evidence-pack.md` sections 2.2 & 2.3**

---

## 💡 Step 4️⃣: Insight → Build Slice (17:15–17:45)

**Who:** Dương (with team input)

### From Evidence, Extract:

1. **Top Pain Cluster:** What problem shows up most?
   ```
   Example from reviews: Users don't just want diagnosis, 
   they want to know urgency + what to do next
   ```

2. **Deeper Need:**
   ```
   Not just: "Symptom checker"
   But: "Conversational assessment that explains thinking"
   ```

3. **Build Slice (Must Be Tiny):**
   ```
   FOR: Person with mild symptoms, no medical background
   
   TASK: Describe symptoms naturally without filling forms
   
   AI DOES: Extract symptoms → ask follow-ups → explain findings
   
   OUTPUT: Triage level (self-care / see doctor / emergency)
            + confidence level
            + why these recommendations
   
   FAILURE HANDLED BY: Confirmation loop (AI asks "did I get this right?")
   ```

**→ Fill thin-spec.md sections 1-4**

---

## 🛠 Step 5️⃣: Owner Plan & Next Steps (17:45–18:00)

**Who:** Huỳnh (facilitator) + whole team

### Finalize This Table (Put in thin-spec.md section 8):

| Owner | Task | Deliverable | Start When |
|---|---|---|---|
| Huyền | Finish app-teardown.md | All 4 paths + findings + sketch | Now |
| Kiên | Finish evidence clusters | Competitor table + clusters | Now |
| Dương | Complete thin-spec.md | All 8 sections + no placeholders | Now |
| Dũng | Prototype skeleton | Conversation UI + system prompt | After SPEC clear |
| Lương | Test plan | 4 path test cases | After prototype outline |
| Huỳnh | Demo prep | demo_script.md + link all files | After SPEC final |

### Before 18:00, Confirm:

- [ ] Everyone knows their role
- [ ] Thin SPEC draft is readable
- [ ] No blocker stopping progress
- [ ] Understand what builds on what (Evidence → SPEC → Prototype)

---

## 🌙 Tonight (After 18:00)

**Goal:** Polish the 3 main files

### For Kiên & Huyền:
- [ ] Finish evidence pack (all sections complete)
- [ ] Double-check sources are accessible
- [ ] Evidence clusters make sense

### For Dương:
- [ ] Thin SPEC final (all 8 sections done, no TODOs)
- [ ] Trace each section back to evidence (can explain why)
- [ ] 4 Paths are concrete (not vague descriptions)
- [ ] Failure mode is real (not theoretical)

### For Dũng:
- [ ] Code/mock framework ready (can be Jupyter + mock API)
- [ ] System prompt drafted (even if not perfect)
- [ ] Happy path mockable by morning

### For Lương:
- [ ] Test cases written (4 inputs + expected outputs)
- [ ] Ready to test prototype tomorrow

### For Huỳnh:
- [ ] README.md updated with role descriptions
- [ ] demo_script.md skeleton written
- [ ] Can walk through evidence → SPEC → prototype story in 5 min

---

## 🚨 Red Flags — Stop & Ask for Help

- ❌ "We don't know which app to pick" → Pick Ada Health, move on
- ❌ "The evidence is weak" → OK, that's why Day 06 is test + iterate
- ❌ "We can't demo build slice in 3-5 min" → Cut scope, save to backlog
- ❌ "SPEC section is still blank/TODOs" → Discuss with team, fill together
- ❌ "Prototype is too complex" → Use wizard-of-oz or mockup, save AI for later
- ❌ "Owner plan unclear" → Clarify in PROGRESS_TRACKER, ping mentor

---

## 📁 File Checklist for Nộp Bài (Day 06)

```
Your-Repo-Name/
├── 01-invidual-workshop/
│   └── app-teardown.md ✅ (yours, with your findings)
├── 02-group-spec/
│   ├── evidence-pack.md ✅ (team's evidence)
│   ├── thin-spec.md ✅ (team's spec + owner plan)
│   └── synthesis-decide-toolkit.md ✅ (if you filled it)
├── README.md ✅ (your reflection)
└── PROGRESS_TRACKER.md ✅ (optional, for your own tracking)
```

---

## 💬 Questions to Ask Mentor

Print this and ask:

```
1. "Our build slice is: [describe]. Is this scope right for Day 06?"
2. "We're seeing [evidence cluster]. Does this change our pain statement?"
3. "We chose [Auto/Aug/Conditional]. Does this make sense for health domain?"
4. "Our failure mode is [describe]. How should we prototype this?"
5. "We're blocked on [X]. What's the workaround?"
```

---

## 🎬 Demo Script Draft (For Tomorrow Morning)

```markdown
## 60-Second Pitch

"We picked Healthcare / Ada Health. We noticed people don't just want 
diagnosis, they want triage + action. Our prototype lets users describe 
symptoms naturally, and AI explains the reasoning. Here are 4 paths we'll test."

## 4 Paths Walkthrough

- Happy: [show screenshot of clear symptom → triage → next action]
- Low-conf: [show how AI asks for clarification if unsure]
- Failure: [show what breaks & how we prevent it]
- Correction: [show how user can fix AI's mistake]

## Key Learnings from Evidence

- [Top 3 pain points from reviews]
- [Why we picked this build slice]
```

---

## 📞 Mentor Contact

**[Instructor name & contact]**

**Office Hours:** [Time]

**Slack:** #day05-help

---

## Good Luck! 🍀

You've got this. Evidence → SPEC → Build → Test.

**16:00:** "What are we building?"  
**17:00:** "Here's evidence it matters"  
**18:00:** "Here's what we'll build tomorrow"  
**19:00:** "Here's how we'll test it"  

Start now. Ask for help early. You'll have a solid Day 06.

---

*— Batch 02 Day 05 · AI Product Kickoff Sprint*
