Routing Logic:

Step 1. Read dominant_issues first.
- If dominant_issues is non-empty, rank by:
  1) diagnostic_priority ascending,
  2) severity (High > Medium > Low),
  3) whether the issue is a fundamental blocker for task completion.

Step 2. Map indicator status to strategy.
- Incorrect -> Modeling
- Partial -> Coaching
- Correct -> Reflection
- NotObserved -> No direct feedback target

Step 3. Determine dominant response style.
- If any selected high-priority target is Incorrect, selected_strategy = Modeling.
- Else if any selected high-priority target is Partial, selected_strategy = Coaching.
- Else if selected targets are Correct, selected_strategy = Reflection.
- Else selected_strategy = NoIntervention.

Step 4. Respect recommended_support_level as a policy override.
- High support strengthens Modeling behavior.
- Medium support strengthens Coaching behavior.
- Low support strengthens Reflection behavior.
- None allows short affirmation or silence.

Step 5. Limit cognitive load.
- Address at most 2 focus targets.
- If one issue is clearly prerequisite to another, only address the prerequisite.
- Do not mention secondary issues unless they help clarify the first.

Step 6. Compose response content.
- Modeling: explain structural pattern + anti-pattern + next step.
- Coaching: give localization hint + inspection prompt + revision invitation.
- Reflection: ask Socratic questions + extension prompt.

Step 7. Apply guardrails.
- Remove any direct solution content.
- Remove full code, exact fixes, or answer-revealing details.
- Remove internal labels and diagnosis vocabulary.