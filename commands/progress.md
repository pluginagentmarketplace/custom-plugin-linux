---
name: progress
description: Track Your Learning Journey
allowed-tools: Read
---

# /progress - Track Your Learning Journey

**Monitor your development progress across any specialization.** Track hours, skills acquired, projects completed, milestones, and estimated completion time.

## Command Syntax

```bash
/progress [role] [options]

# View overall progress
/progress react
/progress machine-learning
/progress devops

# Time period filters
/progress frontend --period week
/progress backend --period month
/progress python --period all

# Detailed reports
/progress react --detailed
/progress kubernetes --export pdf
/progress ai-engineer --compare-to-plan

# Milestone tracking
/progress fullstack --show-milestones
/progress blockchain --next-checkpoint
```

## Tracking Dimensions

### 1. **Time Investment**
- Total hours invested
- Hours per week average
- Consistency tracking
- Time vs. plan comparison
- Estimated hours remaining

### 2. **Skill Acquisition**
- Skills mastered (completed)
- Skills in progress
- Skill proficiency level
- Required skills checklist
- Skills ahead of schedule
- Skills behind schedule

### 3. **Projects & Milestones**
- Projects completed
- Projects in progress
- Project difficulty progression
- Portfolio quality assessment
- Milestone achievement dates
- Next upcoming milestones

### 4. **Knowledge Assessment**
- Checkpoint exam scores
- Quiz performance
- Self-assessment results
- Estimated current level
- Time to next level

### 5. **Consistency Metrics**
- Learning streak (consecutive days)
- Average session length
- Most active days
- Consistency score (%)
- Optimal learning pattern

### 6. **Comparison & Benchmarking**
- Progress vs. planned pace
- Progress vs. cohort average
- Progress vs. historical data
- Acceleration opportunities
- Potential bottlenecks

## Output Format

### Dashboard Overview
```
React Roadmap Progress
━━━━━━━━━━━━━━━━━━━━━━
Level: Intermediate 2/4
Completion: 45% ████░░░░░░ (180/400 hours)
Timeline: 8 weeks elapsed / 12 weeks remaining
Status: ON TRACK ✓

Last Activity: 2 hours ago
Weekly Average: 18 hours
Learning Streak: 14 days
```

### Detailed Breakdown by Section
```
Module 1: React Fundamentals
├─ JSX & Components: ✓ Complete
├─ Hooks: ✓ Complete
├─ State Management: 🔄 In Progress (75%)
└─ Advanced Patterns: ⏳ Not Started

Module 2: Advanced React
├─ Performance Optimization: ⏳ Not Started
├─ Testing: ⏳ Not Started
└─ Production Patterns: ⏳ Not Started
```

### Skills Inventory
```
Acquired Skills (12):
✓ JSX Syntax
✓ Functional Components
✓ React Hooks (useState, useEffect, useContext)
✓ Component Composition
✓ Props & State Management
✓ Event Handling
✓ Conditional Rendering
✓ Lists & Keys
✓ Forms Handling
✓ API Integration
✓ Error Handling
✓ Debugging with React DevTools

In Progress (4):
🔄 Performance Optimization (65%)
🔄 Testing with Jest (40%)
🔄 React Query (55%)
🔄 Code Splitting (30%)

Not Yet Started (8):
⏳ Server Components (Next.js)
⏳ Suspense & Transitions
⏳ Custom Hooks (Advanced)
⏳ Animation Libraries
⏳ State Management (Redux)
⏳ GraphQL Integration
⏳ Monorepos
⏳ Accessibility (A11y)
```

### Projects Completed
```
1. ✓ Todo App (Beginner) - 10 hours
   └─ HTML/CSS/JS, local storage
2. ✓ Weather App (Beginner) - 12 hours
   └─ API integration, state management
3. ✓ Blog Platform (Intermediate) - 45 hours
   └─ CRUD, authentication, database
4. 🔄 E-commerce Site (Intermediate) - 20/60 hours
   └─ Shopping cart, payments, user profiles
```

### Milestones Achieved
```
Milestone 1: React Fundamentals ✓ (Week 1-2)
├─ Completed on: 2024-11-10 (on time)
└─ Key skill: Building React components

Milestone 2: Hooks Mastery ✓ (Week 3-4)
├─ Completed on: 2024-11-24 (2 days early)
└─ Key skill: Advanced state management

Milestone 3: API Integration ✓ (Week 5-6)
├─ Completed on: 2024-12-08 (on time)
└─ Key skill: Real-world data fetching

Milestone 4: Blog Project → IN PROGRESS
├─ Started on: 2024-12-09
├─ Expected completion: 2025-01-06
├─ Progress: 45%
└─ Key skill: Full CRUD operations
```

## Usage Examples

### Example 1: Weekly Progress Review
```bash
/progress frontend --period week
```
Returns: Hours invested this week, skills acquired this week, this week vs. plan

### Example 2: Detailed Progress Report
```bash
/progress machine-learning --detailed --export pdf
```
Returns: Comprehensive PDF report with all metrics and visualizations

### Example 3: Milestone Tracking
```bash
/progress kubernetes --show-milestones --compare-to-plan
```
Returns: Achieved milestones vs. planned milestones with timeline view

### Example 4: Find Next Checkpoint
```bash
/progress rust --next-checkpoint
```
Returns: What to tackle next, estimated hours, recommended resources

## Advanced Features

### Analytics & Insights
- Learning velocity trends
- Skill acquisition rate
- Optimal learning sessions
- Best times to learn
- Productivity patterns
- Efficiency metrics

### Predictions
- Estimated completion date
- Time to proficiency at current pace
- Acceleration scenarios ("What if I learn 25 hours/week?")
- Optimal schedule recommendations

### Comparisons
- `--compare-to-peers` - How you compare to others
- `--compare-to-plan` - Actual vs. planned progress
- `--compare-to-median` - Median pace for this specialization

### Goal Setting
- Set milestone target dates
- Define skill acquisition goals
- Project completion targets
- Adjust learning pace recommendations

### Export Options
- Export as PDF report
- Generate learning certificate
- Share progress with mentor
- Export data for portfolio
- Create accountability buddy reports

## Progress Indicators

| Indicator | Meaning |
|-----------|---------|
| ✓ Complete | Fully mastered, ready for practice |
| 🔄 In Progress | Currently learning, X% complete |
| ⏳ Not Started | Planned but not yet started |
| 📈 Ahead | Faster than planned pace |
| 🎯 On Track | Following planned schedule |
| ⚠️ Behind | Slower than planned pace |
| 🚀 Accelerated | Catching up after slowdown |

## Tips for Progress Tracking

✅ Review progress weekly - stay motivated
✅ Celebrate small wins - build momentum
✅ Adjust plan if needed - be flexible
✅ Identify obstacles early - seek help
✅ Share progress with mentor - accountability
✅ Track projects in portfolio - showcase work
✅ Maintain consistency - better than intensity

## Related Commands

- `/roadmap [role]` - Understand full learning map
- `/learn [role]` - Create personalized path
- `/resources [role]` - Find learning materials
- `/compare [role1] [role2]` - Compare specializations

---

**💡 Pro Tip**: Consistent progress (even 10 hours/week) beats sporadic intense sessions. Track weekly for motivation!
