---
name: leadership
description: Engineering leadership skill - Team management, culture, growth, strategy
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [team_building, feedback, planning, mentoring, conflict] }
    context: { type: string, enum: [startup, enterprise, remote, hybrid] }
  required: [task]

output_schema:
  type: object
  properties:
    strategy: { type: string }
    action_items: { type: array }
    frameworks: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Engineering Leadership Skill

## PURPOSE
Engineering team leadership, culture building, and organizational effectiveness.

## CORE COMPETENCIES
```
People Management:
├── Hiring & onboarding
├── 1:1s & feedback
├── Performance reviews
├── Career development
└── Conflict resolution

Team Building:
├── Culture & values
├── Psychological safety
├── Team structure
├── Diversity & inclusion
└── Remote team management

Strategic:
├── Roadmap planning
├── Resource allocation
├── Cross-team coordination
├── Stakeholder management
└── Technical vision
```

## LEADERSHIP FRAMEWORKS

### 1:1 Meeting Structure
```
1:1 Framework (30-60 min):
├── Check-in (5 min)
│   └── "How are you doing?"
│
├── Their agenda (15-20 min)
│   └── Topics they want to discuss
│
├── Your feedback (10 min)
│   └── Specific, actionable, timely
│
├── Career growth (10 min)
│   └── Progress, goals, blockers
│
└── Action items (5 min)
    └── Clear next steps
```

### Feedback Model (SBI-I)
```
Situation: Where/when it happened
Behavior: What you observed (factual)
Impact: Effect on team/project
Intent: Ask about their perspective

Example:
"In yesterday's standup (S), when you interrupted
the junior dev explaining their blocker (B), it
shut down the discussion and they seemed hesitant
to share more (I). Can you help me understand what
was going on for you? (I)"
```

### Team Health Metrics
```yaml
Delivery:
  - Sprint velocity trend
  - Cycle time
  - Deployment frequency
  - Change failure rate

Engagement:
  - eNPS score
  - Retention rate
  - 1:1 skip rate
  - Participation in discussions

Growth:
  - Promotions
  - Skill development
  - Knowledge sharing
  - Innovation initiatives
```

### Career Ladder Framework
```
IC Track:
├── L1: Junior Engineer
│   └── Learns and executes well-defined tasks
├── L2: Engineer
│   └── Independently completes features
├── L3: Senior Engineer
│   └── Owns components, mentors others
├── L4: Staff Engineer
│   └── Cross-team technical leadership
├── L5: Principal Engineer
│   └── Organization-wide technical strategy
└── L6: Distinguished Engineer
    └── Industry-level impact

Management Track:
├── M1: Engineering Manager
│   └── Manages 4-8 engineers
├── M2: Senior Manager
│   └── Manages managers or large team
├── M3: Director
│   └── Multiple teams, org strategy
├── M4: VP Engineering
│   └── Department leadership
└── M5: CTO
    └── Company technical vision
```

## HIRING FRAMEWORK
```
Interview Process:
├── Resume screen (async)
├── Recruiter call (30 min)
├── Technical phone screen (45 min)
├── On-site/Virtual (4-5 hours)
│   ├── Coding
│   ├── System design
│   ├── Behavioral
│   └── Team fit
└── Debrief & decision

Scorecard:
├── Technical skills
├── Problem solving
├── Communication
├── Collaboration
├── Culture alignment
└── Growth potential
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Low morale | Lack of purpose | Connect work to impact |
| High turnover | Growth gaps | Career conversations |
| Team conflict | Unclear norms | Establish team agreement |
| Burnout | Unsustainable pace | Prioritize ruthlessly |
