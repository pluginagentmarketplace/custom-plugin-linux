# /learn - Create Personalized Learning Path

**Create customized learning journeys for any of the 77+ specializations.** Get detailed step-by-step paths with resources, projects, milestones, and progress tracking based on your current level and learning pace.

## Command Syntax

```bash
/learn [specialization] [options]

# Basic usage
/learn react
/learn python
/learn devops

# With level specification
/learn frontend --level beginner
/learn machine-learning --level intermediate
/learn blockchain --level advanced

# With pace specification
/learn golang --pace slow
/learn kubernetes --pace moderate
/learn rust --pace fast

# Combined options
/learn data-engineering --level intermediate --pace fast --focus backend

# Get recommendations
/learn --suggest (recommendations based on interests)
/learn --suggest-from [interest1] [interest2] (suggest paths)
```

## Learning Levels

- **Beginner** (60-120 hours): Starting fresh, building fundamentals
- **Intermediate** (120-200 hours): Building on basics, production-ready
- **Advanced** (120-180 hours): Enterprise-scale, optimization, specialization
- **Mastery** (100+ hours): Research, leadership, architecture

## Pace Options

- **Slow** (10 hours/week): For working professionals, part-time learners
- **Moderate** (15-20 hours/week): Balanced learning, full-time students
- **Fast** (25+ hours/week): Intensive learning, dedicated learners
- **Custom** (specify hours/week): Fine-tune for your schedule

## Output Format

### 1. **Learning Path Overview**
- Current skill level assessment
- Target proficiency level
- Estimated timeline
- Key milestones

### 2. **Phase-by-Phase Breakdown**
Each phase includes:
- Core concepts to master
- Recommended hours per phase
- Key skills to acquire
- Mini-projects for practice
- Checkpoints for self-assessment

### 3. **Detailed Resource Recommendations**
- Curated courses (with links)
- Essential books
- Interactive tutorials
- Community resources
- Practice platforms

### 4. **Project-Based Learning**
- Milestone projects (3-5 per phase)
- Project difficulty progression
- Real-world application examples
- Portfolio-building projects

### 5. **Progress Tracking**
- Weekly checklist
- Skill milestones
- Estimated completion date
- Bookmark next session

### 6. **Interconnected Learning**
- Prerequisite skills needed
- Complementary skills to develop
- Suggested adjacent specializations
- Full learning journey visualization

## Usage Examples

### Example 1: Frontend Developer (Beginner → Intermediate)
```bash
/learn frontend --level beginner --pace moderate
```
Returns: 4-week path covering HTML/CSS → JavaScript → React with weekly milestones

### Example 2: Machine Learning Engineer (Intermediate → Advanced)
```bash
/learn machine-learning --level intermediate --pace fast
```
Returns: 8-week intensive path with deep learning focus and research projects

### Example 3: DevOps Engineer (Getting Started)
```bash
/learn devops --pace slow
```
Returns: 12-week part-time path from Linux basics → Kubernetes mastery

### Example 4: Smart Contract Developer (Fast Track)
```bash
/learn blockchain --level intermediate --pace fast
```
Returns: 6-week intensive program covering Solidity → DeFi development

## Advanced Features

### Customization Options
- `--start-date` - Plan learning with specific start date
- `--time-budget` - Total hours available for learning
- `--focus` - Emphasize specific aspect (e.g., --focus performance)
- `--style` - Learning style preference (visual, hands-on, theory-first)
- `--goals` - Customize by goal (interview prep, job transition, etc.)

### Integration with Other Commands
- `/roadmap [role]` - First explore the role overview
- `/learn [role]` - Then create personalized path
- `/compare [role1] [role2]` - Compare before committing
- `/progress [role]` - Track your learning journey
- `/resources [role]` - Find specific materials

### Export & Sharing
- Export as PDF/markdown
- Share learning plan with mentor
- Import schedule to calendar
- Sync with learning tracking apps

## Weekly Breakdown Example

### Week 1: Foundation
- **Days 1-2**: Core concept videos (5 hours)
- **Days 3-4**: Interactive tutorials (4 hours)
- **Days 5-7**: First mini-project (6 hours)
- **Weekly total**: 15 hours
- **Checkpoint**: Can build basic X application

### Week 2: Advanced Concepts
- **Days 1-3**: Deep-dive tutorials (6 hours)
- **Days 4-5**: Problem-solving exercises (4 hours)
- **Days 6-7**: Milestone project (8 hours)
- **Weekly total**: 18 hours
- **Checkpoint**: Understand advanced patterns

## Success Metrics

Track your progress with:
- Hours completed vs. planned
- Concepts mastered
- Projects completed
- Checkpoints passed
- Estimated time to proficiency
- Skill acquisition rate

## Tips for Success

✅ Stick to your pace - consistency beats intensity
✅ Do hands-on projects - theory + practice = mastery
✅ Join communities - learn with others
✅ Track progress - celebrate milestones
✅ Adjust as needed - adapt learning pace when necessary
✅ Build projects - create portfolio pieces
✅ Seek feedback - code reviews and mentorship accelerate learning

## Related Commands

- `/roadmap [role]` - Explore role overview first
- `/compare [role1] [role2]` - Compare learning paths
- `/resources [role]` - Find learning materials
- `/progress [role]` - Track learning progress

---

**💡 Pro Tip**: Create a learning plan, commit to consistency, and celebrate every milestone completed!
