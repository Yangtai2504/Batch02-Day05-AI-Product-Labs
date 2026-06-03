# Example Walkthrough — Cách Điền Từng Phần

> Hướng dẫn từng bước với ví dụ cụ thể từng mục.

---

## 🔍 Example Setup

**Track:** Healthcare  
**Product:** Ada Health  
**User:** 28-year-old person with no medical background, wakes up with fever  

---

---

## 📝 Section 1: Self-Use Evidence (app-teardown.md)

### What You Do:
1. Open Ada Health
2. Type: "I've had a fever since yesterday morning and my throat hurts"
3. Follow the conversation
4. Take screenshots at key moments

### What You Fill In:

```markdown
## 2. Self-Use Evidence — Promise vs Reality

**App Promise:** "Talk to Ada. Get health guidance in minutes."

**Reality:** The app asks 7 follow-up questions before giving output.

---

### Observation 1: Clear Input → Adaptive Questions

**Input:** "Fever since yesterday + sore throat"

**Screenshot:** [image from app showing the initial screen and AI response]

**What App Did:**
- Extracted: fever, sore throat, timing (yesterday)
- Asked follow-up: "Is your throat red? Difficulty swallowing? Cough?"
- Asked context: "Any other symptoms? Taking any medications?"

**Observation:** 
The adaptive questioning is good — it didn't ask irrelevant questions like 
"Do you have rashes?" But each question is one at a time, making the flow 
feel slow. User might get impatient after 5+ turns.

**Path This Shows:** Low-confidence (system asking for more info) + UX friction
```

---

## 💬 Section 2: The 4 Paths

### Happy Path Example

```markdown
### Happy Path: Clear Symptoms → Fast Triage

**What Happens:**
1. User: "Fever, sore throat, no cough"
2. AI: [After 3 questions] "This looks like viral pharyngitis or flu"
3. Output: 
   - Triage: "Likely mild, home care okay"
   - Confidence: 70%
   - Next step: "Rest, hydration, check back if fever > 38.5°C for 3 days"

**User Experience:**
- ✅ Got answer in ~2 min
- ✅ Understood why (fever + sore throat = these conditions)
- ✅ Clear action (what to do at home)
- ✅ Knows when to escalate (temp threshold)

**Screenshot:** [show final output screen]
```

### Low-Confidence Path Example

```markdown
### Low-Confidence Path: Vague Symptom → AI Asks Clarification

**What Happens:**
1. User: "I'm not feeling well, maybe a fever?"
2. AI: "I need to understand better. Have you taken your temperature? 
   What symptoms are bothering you most?"
3. User: "No thermometer, but I feel hot and my stomach is off"
4. AI: [Doesn't jump to diagnosis] 
   "I see fever-like feeling + stomach symptoms. Could be several things. 
   To narrow down: do you have diarrhea or just nausea? Any recent food?"
5. Output:
   - Triage: "Unclear — could be viral, food poisoning, or other"
   - Confidence: 35%
   - Next step: "Take temperature if possible. See doctor if symptoms worsen."

**User Experience:**
- ✅ AI didn't guess or alarm user
- ✅ AI asked relevant clarifications
- ⚠️ Output is less concrete, but honest about uncertainty

**Screenshot:** [show confidence % display]
```

### Failure Path Example

```markdown
### Failure Path: AI Misinterprets → Wrong Recommendation

**What Happens:**
1. User: "Bad headache, I'm tired"
2. AI: [Missing context about fever] 
   "This could be tension headache or migraine. Try rest and OTC pain relief."
3. User: [Didn't mention fever; but has one] 
   "OK, I'll just rest at home"
4. Problem: 
   - User has fever + headache = possible infection, not just tiredness
   - AI missed it because user didn't mention fever (user didn't think it was relevant)
   - User delays seeking help

**Failure Root Cause:**
- App relied too much on user volunteering info
- Didn't have a "catch-all" question like "Any fever or chills?"

**How Ada Actually Handles This:**
- Ada does ask about fever/chills eventually, but only after specific questions
- If user didn't mention it initially, AI might not circle back

**Screenshot:** [show the wrong output]

**Impact:** User sees "mild, treat at home" but actually has viral infection
```

### Correction Path Example

```markdown
### Correction Path: User Corrects AI Understanding

**What Happens:**
1. [From failed interaction above] User says: "Wait, I do have a fever actually"
2. Ada: "Ah, that changes things. Let me reconsider with fever + headache + tired."
3. Updated Output:
   - Triage: "Likely viral infection (flu, cold). Mild to moderate"
   - Recommendation: "Rest, monitor fever. See doctor if fever persists >3 days or gets worse"

**User Experience:**
- ✅ AI updates instantly
- ✅ Explanation changes (now considers fever as main symptom)
- ✅ Recommendation escalates appropriately

**Screenshot:** [show updated output]
```

---

## 🎯 Section 3: Evidence Cluster (evidence-pack.md)

### Example Cluster: "User Needs Clarity on Urgency"

**Evidence IDs:** P01, P02, P09, P10, P11, P04

**From Positive Reviews:**
```
P01: "Review said app helped distinguish between might have flu vs COVID, 
     not just 'you might be sick'"
     
P02: "User appreciated that app didn't just list diseases, but said 
     'you'll probably be fine, stay home' vs 'you need emergency care'"

P09: "Review: 'Panic attack app helped me realize I probably wasn't dying'"
     
P10: "Review: 'Appendicitis symptoms — app correctly recommended urgent care'"
```

**From Negative Reviews:**
```
N05: "WebMD update gave scary results for stomach pain without asking 
     severity or other context"
```

**What This Pattern Means for Product:**

```
The core need is NOT "diagnose me accurately"
The core need is "tell me on a scale how worried I should be + what to do"

Users will tolerate some uncertainty in diagnosis,
but NOT uncertainty in urgency level.
```

**Product Implication:**
→ Output must always include:
  1. Triage level (not just diagnosis)
  2. Explanation (why this level)
  3. Action (what to do)
  4. Escalation rule (when to ignore AI and seek help)

---

## 📋 Section 4: Build Slice (thin-spec.md)

### BEFORE Evidence:

```
"Build an AI health assistant that helps people understand 
if they need to see a doctor."
```

❌ **Problems:**
- Too broad (who? what interaction? what output?)
- Not trace-able to evidence
- Hard to test

### AFTER Evidence:

```
FOR: Adult with mild/unclear symptoms who isn't sure if it's serious

TASK: Naturally describe "what's bothering them" 
      (not fill out a form)

AI DOES:
- Extract symptoms from conversation
- Identify missing critical info (fever? duration? other symptoms?)
- Ask clarifying questions if needed
- Rate triage: self-care / urgent / emergency
- Explain findings (why these conditions, why this triage)

OUTPUT:
{
  "likely_conditions": ["viral pharyngitis", "flu"],
  "triage_level": "self-care",
  "confidence": "70%",
  "reasoning": "Your fever + sore throat + 1 day duration suggests viral infection. 
               No red flags like difficulty breathing or high fever.",
  "action": "Rest, hydration, OTC pain relief if needed",
  "escalate_if": "Fever stays > 38.5°C after 3 days, or difficulty breathing"
}

HANDLES FAILURE BY:
- Confirming back: "So I heard: fever since yesterday, sore throat, no cough. Right?"
- Asking clarification: "When you say 'fever,' did you measure it?"
- Showing confidence: "I'm 70% sure, not 100%. These could also be..."
```

✅ **Why This is Better:**
- Specific user (adult, mild symptoms)
- Specific task (natural description, not form)
- Specific AI action (extract → clarify → rate → explain)
- Specific output (triage + reasoning + action)
- Specific failure handling (confirmation + clarification + confidence)

---

## 🔄 Section 5: Four Paths in Action (thin-spec.md section 6)

### Happy Path Prototype Behavior

```markdown
**User Input:** "I've had a fever and sore throat since yesterday morning. 
               I'm taking ibuprofen but it only helps for 4 hours."

**AI Step 1:** [Extracts symptoms]
"OK, so fever + sore throat for about 24 hours, managed with ibuprofen. 
 I need a bit more info. Have you had any cough or difficulty swallowing?"

**User:** "No cough, but swallowing hurts. Should I be worried?"

**AI Step 2:** [Asks follow-ups]
"Any runny nose, nausea, or other symptoms? And is anyone else at home sick?"

**User:** "Runny nose yes. My roommate was sick last week."

**AI Step 3:** [Formulates output]
"Based on fever + sore throat + runny nose + exposure, this is likely 
viral pharyngitis or common cold.

Triage: Self-care (not urgent)
Confidence: 75%

What to do:
- Rest and hydration are most important
- OTC pain relief as you're doing (ibuprofen)
- Throat lozenges can help swallowing
- Most get better in 3-5 days

Come back or see doctor if:
- Fever goes above 39°C
- Symptoms last > 1 week
- You have difficulty breathing
- Rash appears

This is not a diagnosis — if you're concerned, see your doctor."

**Prototype Shows:**
✅ Natural conversation flow
✅ Triage level clear (self-care)
✅ Reasoning transparent (why these conditions)
✅ Action-oriented next steps
✅ Clear escalation rules
```

### Low-Confidence Path Prototype Behavior

```markdown
**User Input:** "I'm not feeling great, kinda out of it"

**AI Step 1:** [Recognizes vague]
"I want to help figure this out. 'Out of it' could mean a few things. 
 Are you experiencing:
 - Fatigue / low energy?
 - Brain fog / trouble focusing?
 - Dizziness?
 - All of the above?"

**User:** "Mostly dizzy I think"

**AI Step 2:** [Narrows down]
"Dizziness could have many causes. Let me ask:
 - Do you have a fever or chills?
 - Any headache?
 - Did you eat/drink enough today?"

**User:** "No fever, yes headache, skipped breakfast"

**AI Step 3:** [Shows uncertainty]
"I'm seeing: dizziness + headache + possible dehydration. 
 This COULD be just dehydration from skipping breakfast,
 but could also be early signs of migraine or virus.

Confidence: 45% — not high enough to recommend strongly

What I'd suggest:
1. Drink water and eat something (could resolve dehydration-related dizziness)
2. Monitor: if dizzy continues after food/water, might be something else
3. If headache worsens or dizziness continues: see a doctor

I don't have enough information to be confident, 
so please trust your gut and see a doctor if you're concerned."

**Prototype Shows:**
✅ AI explicitly says "I'm not sure"
✅ Asks clarifying questions
✅ Doesn't jump to diagnosis
✅ Suggests monitoring + escalation
✅ Doesn't hide uncertainty behind false confidence
```

### Failure Path Prototype Behavior

```markdown
**User Input:** "Chest pain"

**AI Step 1:** [Treats as potential red flag]
⚠️ IMPORTANT: You mentioned chest pain. 
 I need to ask critical questions because this needs immediate attention.

 Do you have:
 - Shortness of breath? YES / NO
 - Pain spreading to arm/shoulder/jaw? YES / NO  
 - Nausea or sweating? YES / NO
 - Heart racing or irregular? YES / NO"

**User:** [Clicks "YES" to shortness of breath]

**AI Step 2:** [Escalates immediately]
🚨 URGENT: You described chest pain + shortness of breath.

PLEASE CALL EMERGENCY (911 / 112 / LOCAL) NOW
DO NOT WAIT FOR DOCTOR APPOINTMENT
DO NOT DRIVE YOURSELF

This could be a heart attack or other serious condition.

If you called emergency, stop using this app.
If it's a false alarm, it's better to be safe. Doctors will check you.

DO NOT rely on this app for chest pain + breathing difficulty.

**Prototype Shows:**
✅ Red-flag detection with specific questions
✅ Immediate escalation (don't guess)
✅ Clear emergency instruction
✅ Avoids liability (not AI diagnosis, clear escalation)
```

### Correction Path Prototype Behavior

```markdown
**Background:** User already got output: "Likely viral pharyngitis, self-care"

**User Correction:** "Wait, I also just realized I have a rash on my arms"

**AI Step 1:** [Updates understanding]
"A rash + fever + sore throat changes things. 
 This could indicate:
 - Strep throat (sometimes has rash)
 - Scarlet fever (fever + rash + sore throat)
 - Viral exanthem

 This group needs faster attention."

**AI Step 2:** [Re-triages]
NEW Triage: URGENT (see doctor same day or next morning)
Confidence: 80% (higher because rash adds more info)

This is different from before because the rash suggests bacterial infection 
or more serious viral infection, not just common cold.

"

**Prototype Shows:**
✅ User can update information
✅ AI re-processes with new data
✅ Triage level escalates appropriately
✅ Explanation changes (not just 'output updated')
✅ Shows why confidence increased
```

---

## 🎯 Section 6: Failure Mode Definition (thin-spec.md section 7)

### Failure Mode: Misses Red Flag

```markdown
**Trigger:** User describes chest pain, but in vague language

User: "It's like pressure in my chest when I move. Feels weird."

**AI's Potential Mistake:** 
Doesn't recognize this might be cardiac issue. 
Treats as musculoskeletal or anxiety.
Recommends: "Rest and stretching"

**Hacked Outcome:**
User rests at home for hours while having early heart attack symptoms.

**Root Cause:**
- AI prompt didn't include "red flag" checklist
- Didn't ask about shortness of breath / spread to arm
- Prioritized "natural conversation" over safety checks

**How Prototype Prevents:**
Add explicit rule:
IF user mentions [chest pain, breathing trouble, severe headache, etc]:
  → ALWAYS ask detailed red-flag questions
  → ESCALATE to emergency if any YES
  → Don't try to diagnose

**Test Case for Day 06:**
Input: "Chest pressure when I move"
Expected: AI asks breathing/arm pain/racing heart, THEN 
          either gives safe triage or escalates, not just "stretch"
```

---

## 🏆 What Makes All This Work

| Part | Why It Matters |
|---|---|
| Evidence from real users | Not guessing what people want |
| 4 Paths | Realistic because we tested all of them |
| Build Slice constraint | Day 06 team can actually build it |
| Failure Mode specific | We know what could go wrong + how to catch it |
| Triage-first (not diagnosis-first) | Respects health domain risk |

---

## 🚀 Ready to Fill In Yours?

1. Pick a test case (use Ada Health or your app)
2. Fill in self-use evidence (screenshots + observations)
3. Find the 4 paths
4. Collect user reviews (~5-10 to start, add more tonight)
5. Extract insight (what users really need)
6. Shrink build slice to "demo in 3 min"
7. Identify the ONE failure mode that scares you most
8. Write it down

**Good luck!**

---

*Template Example · Day 05 AI Product Lab*
