---
name: pm
description: Product management skill - Strategy, discovery, roadmaps, stakeholders
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [discovery, planning, prioritization, analysis, launch] }
    stage: { type: string, enum: [ideation, validation, development, growth, maturity] }
  required: [task]

output_schema:
  type: object
  properties:
    strategy: { type: string }
    roadmap: { type: object }
    metrics: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Product Management Skill

## PURPOSE
Product strategy, discovery, planning, and go-to-market execution.

## CORE COMPETENCIES
```
Discovery:
├── Customer research
├── Problem validation
├── Opportunity sizing
├── Competitive analysis
└── Jobs-to-be-done

Strategy:
├── Vision & mission
├── Product strategy
├── Roadmap planning
├── OKRs & KPIs
└── Go-to-market

Execution:
├── Agile/Scrum
├── Prioritization frameworks
├── Stakeholder management
├── Launch planning
└── Iteration & learning
```

## PRODUCT FRAMEWORKS

### PRD Template
```yaml
Product Requirements Document:

Overview:
  - Problem statement
  - Target users
  - Success metrics

User Stories:
  - As a [user], I want [goal], so that [benefit]

Requirements:
  - Must have (P0)
  - Should have (P1)
  - Nice to have (P2)

Design:
  - Wireframes/mockups
  - User flows

Technical:
  - Architecture notes
  - Dependencies
  - Risks

Timeline:
  - Milestones
  - Launch date

Success Criteria:
  - Metrics to measure
  - Target values
```

### Prioritization: RICE Framework
```
RICE = (Reach × Impact × Confidence) / Effort

Reach: # users affected per quarter
Impact: 3=massive, 2=high, 1=medium, 0.5=low, 0.25=minimal
Confidence: 100%=high, 80%=medium, 50%=low
Effort: Person-months

Example:
Feature A: (10000 × 2 × 0.8) / 3 = 5333
Feature B: (5000 × 3 × 1.0) / 2 = 7500
→ Prioritize Feature B
```

### OKR Framework
```
Objective: Qualitative, inspiring goal
├── KR1: Measurable result (baseline → target)
├── KR2: Measurable result
└── KR3: Measurable result

Example:
Objective: Become the most loved product in our category
├── KR1: Increase NPS from 30 to 50
├── KR2: Reduce churn from 5% to 3%
└── KR3: Achieve 4.5+ app store rating

Grading:
├── 0.0-0.3: Failed
├── 0.4-0.6: Made progress
└── 0.7-1.0: Delivered
```

### Product Metrics (AARRR Pirate Metrics)
```
Acquisition:
├── Traffic sources
├── CAC (Customer Acquisition Cost)
└── Conversion rates

Activation:
├── Signup completion
├── First value moment
└── Onboarding completion

Retention:
├── DAU/MAU ratio
├── Cohort retention curves
└── Feature usage frequency

Revenue:
├── ARPU/ARPPU
├── LTV (Lifetime Value)
├── LTV:CAC ratio (target 3:1+)
└── MRR/ARR

Referral:
├── Viral coefficient
├── NPS
└── Referral conversion rate
```

### Jobs-to-be-Done Framework
```
JTBD Statement:
When [situation], I want to [motivation],
so I can [expected outcome].

Example:
"When I'm commuting to work, I want to
learn something new, so I can feel
productive with my time."

→ Insight: Audio content for commuters
```

## GO-TO-MARKET CHECKLIST
```
Pre-Launch:
[ ] Beta testing complete
[ ] Documentation ready
[ ] Support team trained
[ ] Marketing assets prepared
[ ] Analytics instrumented
[ ] Feature flags configured

Launch:
[ ] Staged rollout plan
[ ] Monitoring dashboards
[ ] On-call rotation set
[ ] Announcement scheduled
[ ] Sales enablement done

Post-Launch:
[ ] Metrics review (D1, D7, D30)
[ ] User feedback collection
[ ] Bug triage process
[ ] Iteration planning
[ ] Retrospective
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Feature creep | No clear vision | Align on strategy |
| Low adoption | Wrong problem | Validate with users |
| Stakeholder conflict | Misaligned priorities | RICE + transparency |
| Missed deadlines | Scope ambiguity | Clear acceptance criteria |
