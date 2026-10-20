# Product brief: 慢病用药小管家

This brief records the product thinking behind the prototype: who it is for, the problems it targets, and the design decisions on each screen. The persona and all numbers come from the prototype's mock data. They are not user research.

## Who it is for

**Primary user: an older adult managing several chronic conditions.** The prototype's persona is 王伯伯. He has high blood pressure, type 2 diabetes and high cholesterol, and he takes five long-term medications:

| Drug | Purpose tag | Schedule |
| --- | --- | --- |
| 阿司匹林肠溶片 100mg | 抗血栓 (anti-clotting) | once daily, before breakfast |
| 二甲双胍片 0.5g | 降血糖 (lowers blood sugar) | twice daily, after meals |
| 氨氯地平 5mg | 降血压 (lowers blood pressure) | once daily, after dinner |
| 阿托伐他汀 20mg | 降血脂 (lowers cholesterol) | once daily, at bedtime |
| 辅酶Q10 100mg | 护心脏 (heart support, supplement) | once daily, after breakfast |

**Secondary users: family members**, who want to know whether the patient took their medicine without calling every day. The persona has 王小敏 (daughter, follows adherence) and 王晓东 (son, emergency contact).

**Supporting roles: the care team.** That means the patient's specialist (内分泌科 张主任), a cardiologist, and an on-call pharmacist.

## Problems and how the prototype addresses them

| Problem | Response in the prototype |
| --- | --- |
| **Missed or doubled doses.** Several drugs at different times are hard to keep straight. | The Home screen shows one task: a countdown to the next dose, with "taken" and "snooze" buttons. Confirming a dose moves straight on to the next one. The Plan tab shows the whole day as a timeline. |
| **Not knowing what each pill is for**, which leads to skipping "unimportant" ones | Every drug carries a highlighted **purpose tag** (降血压, 降血糖 …) everywhere it appears. |
| **Running out of medicine**, especially for drugs that need a prescription | The Inventory tab counts pills left and estimates a run-out date. A Home alert appears for anything about to run out. Reorders go through 美团买药. |
| **Expired prescriptions and missed follow-up visits** | The Refill tab shows the next visit, prescriptions close to expiry, and one-tap renewal. A Home alert counts down to the visit. |
| **Unsafe combinations**, such as adding an over-the-counter painkiller to a blood thinner | The Interaction checker covers the patient's own drugs plus self-bought ones (for example 布洛芬, ibuprofen). The chat flags food interactions such as grapefruit. |
| **Small text and dense screens** | Three font sizes (标准 / 大字 / 特大), driven by one CSS variable, with larger icons in the bigger modes. Home avoids repeating what the tab bar already offers. |
| **Family worry** | Family members can follow adherence. Two missed doses in a row can notify the emergency contact. |

## Key design decisions

1. **Home shows the next action only.** Navigation lives in the tab bar, and Home deliberately leaves out entry points the tabs already provide. What's left is the next dose, cross-cutting alerts, a 3-number summary, and AI shortcuts.
2. **A clear finish for the day.** When every dose is taken, the countdown card turns green with 今日药品已服用完毕 ("all of today's medicine is taken"). That gives a sense of completion instead of an empty state.
3. **Recording a missed dose is a first-class action.** The confirm sheet offers ✕ 漏服 (missed) next to ✓ 已服用 (taken), so missed doses get recorded rather than silently ignored.
4. **Purpose before name.** For many older patients the generic drug name means little. The purpose tag comes first and is styled as the most prominent element in each row.
5. **The AI sits behind the safety framing.** Every chat screen carries a "for reference only, consult your doctor or pharmacist" note. Interaction results are labeled by severity, not shown as yes/no answers.

## Screen map

```
Home ─┬─ 去续方 / 查看 alerts ──► Refill
      ├─ AI用药咨询 / 相互作用 ──► AI (chat / check)
      └─ 🔍A ───────────────────► Settings
Tab bar: Home · Plan · Inventory · Refill · AI · Health
```

## Proposed success metrics

These metrics would be worth tracking in a real launch. The figures shown in the prototype (for example "93% 7-day adherence") are placeholders.

- **Adherence rate**: doses confirmed as taken ÷ doses scheduled, over 7 and 30 days
- **On-time refill rate**: refills ordered before the estimated run-out date
- **Prescription lapse rate**: prescriptions that expired before renewal
- **Interaction checks per active user**, plus the share of high-risk results followed by a pharmacist consultation
- **Family engagement**: share of patients with at least one linked family member, and how often that member checks in

## From prototype to product

| Area | What a real version needs |
| --- | --- |
| Reminders | Real scheduled notifications (OS notifications, or a mini-program subscription message), voice playback, and escalation to family after missed doses |
| Data | User accounts, a medication schedule stored on a server, dose logs, and stock decremented by actual doses |
| Interaction checking | A licensed drug-interaction database and pharmacist review of high-risk results. Hard-coded rules are not acceptable. |
| AI assistant | An LLM with retrieval over trusted drug labels, strict guardrails and clear escalation to a human pharmacist, plus privacy review of health data |
| Prescriptions | Integration with hospital and internet-hospital systems for renewals and appointments, within local regulations for prescription drugs |
| Accessibility | Semantic buttons and tabs, screen-reader labels, enough color contrast, and support for system font scaling |
| Compliance | Health-data consent, retention policy, and medical-device and online-pharmacy regulatory review |
