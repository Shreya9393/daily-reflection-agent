# Daily Reflection Tree – Deterministic Reflection Agent

## 1. My Understanding of the Problem
In this assignment, the goal is not just to check whether a day was productive or not, but to guide the user towards structured thinking.

From my perspective, reflection should answer three questions:
1. What happened?
2. Why did it happen?
3. What can I do differently next time?

So, I designed a deterministic system that helps users move from outcome → reasoning → action.

---

## 2. Design Approach

Instead of only checking productivity, I focused on:
- Understanding **why** things happened
- Separating **internal vs external factors**
- Making the system **action-oriented**

---

## 3. Decision Tree Logic

### Step 1: Productivity Check
**Q1: Was your day productive? (Yes/No)**

---

### Case 1: YES (Success Analysis)

**Q2: Why was your day productive?**
- Good planning  
- High focus  
- High energy  
- Task was easy  

**Q3: Can this be repeated tomorrow? (Yes/No)**

**Output:**
- Identify a **Success Pattern**
- Suggest repeating the same approach

---

### Case 2: NO (Failure Analysis)

**Q2: What was the main issue?**
- Time issue  
- Distraction  
- Lack of clarity  
- Low energy  
- Skill gap  

---

## 4. Root Cause Thinking

I further break down each issue:

- Time → Poor planning / Too many tasks  
- Distraction → Mobile / Environment  
- Clarity → Goal unclear / Steps unclear  
- Energy → Lack of rest  
- Skill → Lack of knowledge  

---

## 5. Internal vs External Classification (Key Insight)

**Q: Was this issue in your control?**

- Yes → Internal (skill, energy)
- No → External (time constraints, environment)

This helps the system decide whether to:
- Improve directly  
- Or adapt around constraints  

---

## 6. Action System

Each issue maps to a clear action:

| Issue | Action |
|------|--------|
| Time | Time blocking |
| Distraction | Remove triggers |
| Clarity | Break into smaller tasks |
| Energy | Improve rest |
| Skill | Learn and practice |

---

## 7. Commitment Layer (My Addition)

I added a commitment step because reflection without action is incomplete.

**Q: What will you do differently tomorrow?**

Output:
→ “Your commitment for tomorrow: ______”

---

## 8. Guardrails

To ensure reliability and avoid ambiguity:
- Only predefined options are allowed
- No free-text interpretation
- Same input always produces same output
- Invalid inputs are handled explicitly
- No LLM is used in runtime

---

## 9. Edge Cases

- Invalid input → ask again  
- Multiple issues → focus on primary issue  
- No clear answer → default to clarity problem  

---

## 10. Python Implementation

```python
def reflection_agent():
    goal = input("Was your day productive? (yes/no): ").lower()

    if goal == "yes":
        reason = input("Why was it productive? (planning/focus/energy/easy): ")
        repeat = input("Can this be repeated tomorrow? (yes/no): ")

        print("Success Pattern:", reason)
        print("Suggestion: Repeat this approach.")

    elif goal == "no":
        issue = input("Main issue? (time/distraction/clarity/energy/skill): ").lower()

        if issue == "time":
            print("Cause: Planning issue")
            print("Action: Use time blocking")
        elif issue == "distraction":
            print("Cause: External distractions")
            print("Action: Remove triggers")
        elif issue == "clarity":
            print("Cause: Lack of clarity")
            print("Action: Break tasks")
        elif issue == "energy":
            print("Cause: Low energy")
            print("Action: Improve rest")
        elif issue == "skill":
            print("Cause: Skill gap")
            print("Action: Learn & practice")

        control = input("Was this in your control? (yes/no): ")
        if control == "yes":
            print("You can improve this directly.")
        else:
            print("Plan around this constraint.")

        commitment = input("What will you do differently tomorrow? ")
        print("Commitment:", commitment)

    else:
        print("Invalid input")

reflection_agent()
