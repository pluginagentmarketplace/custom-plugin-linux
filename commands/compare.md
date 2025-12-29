---
name: compare
description: Compare Specializations Side-by-Side
allowed-tools: Read
---

# /compare - Compare Specializations Side-by-Side

**Compare 2+ specializations to make informed career decisions.** Get detailed side-by-side analysis covering salaries, job market, learning curve, career paths, and more.

## Command Syntax

```bash
/compare [role1] [role2] [role3...]

# Compare languages
/compare javascript python java go rust

# Compare frameworks
/compare react vue angular nextjs

# Compare cloud platforms
/compare aws gcp azure

# Compare roles
/compare product-manager engineering-manager technical-lead

# Compare specializations across domains
/compare frontend backend devops

# With filters
/compare python java go --focus salary
/compare react vue --focus job-market
/compare aws gcp --focus learning-curve
```

## Comparison Dimensions

### 1. **Learning & Skill Requirements**
- Learning curve (1-10 scale)
- Time to intermediate proficiency
- Prerequisite skills needed
- Difficulty factors
- Resource availability

### 2. **Compensation Data**
- Beginner salary range
- Mid-level salary range
- Senior salary range
- Geographic variations
- Industry variations
- Bonus & equity potential

### 3. **Job Market**
- Current demand (🔥 high, 📈 growing, 💼 stable, 📉 declining)
- Number of job openings
- Remote work availability
- Startup adoption
- Enterprise adoption
- Geographic hotspots

### 4. **Career Progression**
- Typical progression path
- Time to senior level
- Specialization opportunities
- Leadership paths
- Adjacent specializations

### 5. **Ecosystem & Community**
- Community size
- Conference presence
- Online resources quantity
- Book availability
- Stack Overflow activity
- GitHub repository count

### 6. **Technology Details**
- Maturity level (new, growing, mature, declining)
- Scalability
- Performance characteristics
- Tool ecosystem
- Integration capabilities

### 7. **Practical Factors**
- Typical team size
- Day-to-day work
- Work-life balance (based on user feedback)
- Remote friendliness
- Contract opportunities

## Output Format

### Comparison Table
Side-by-side comparison of all requested specializations across all dimensions

### Detailed Analysis
- Strengths of each specialization
- Weaknesses/challenges
- When to choose which
- Hybrid approaches

### Decision Matrix
- Scoring based on your priorities
- Weighted comparison
- Recommendation based on goals

## Usage Examples

### Example 1: Language Decision
```bash
/compare python java golang
```
Returns: Detailed comparison of Python (ease), Java (enterprise), Go (performance)

### Example 2: Framework Choice
```bash
/compare react vue angular --focus job-market
```
Returns: React (highest demand), Vue (ease), Angular (enterprise)

### Example 3: Career Path
```bash
/compare engineering-manager technical-lead staff-engineer
```
Returns: Management vs IC progression paths with tradeoffs

### Example 4: Frontend Specialization
```bash
/compare frontend backend full-stack --focus learning-time
```
Returns: Learning time comparison with progression advice

## Advanced Features

### Filter by Criteria
- `--focus salary` - Prioritize compensation comparison
- `--focus job-market` - Emphasize hiring demand
- `--focus learning` - Focus on difficulty and resources
- `--focus community` - Compare community size
- `--focus growth` - Focus on demand growth trends

### Geographic Analysis
- `--location san-francisco` - SF Bay salary & demand
- `--location new-york` - NYC salary & demand
- `--location remote` - Remote work prevalence
- `--location global` - Global averages

### Timeline Analysis
- `--timeline 1-year` - Which is learnable in 1 year?
- `--timeline 5-years` - Long-term career trajectory
- `--for-role [current-role]` - Based on where you are now

### Export Options
- Export comparison table as CSV
- Generate PDF comparison report
- Share comparison with mentor/friend
- Embed in decision documents

## Comparison Dimensions in Detail

| Dimension | What it Measures | Example |
|-----------|-----------------|---------|
| **Learning Curve** | Time to proficiency | React (medium) vs Vue (easy) |
| **Salary Potential** | Income growth | Java ($130-200K) vs Go ($120-180K) |
| **Job Market** | Available positions | React (🔥 highest) vs Vue (📈 good) |
| **Ecosystem** | Tools and resources | Node.js (largest NPM) vs Python (PyPI) |
| **Community** | Support and networking | JavaScript (massive) vs Rust (growing) |
| **Career Path** | Progression options | Full-stack (diverse) vs Data Eng (specialized) |

## Sample Comparison Output

### Languages: Python vs Java vs Go

| Criteria | Python | Java | Go |
|----------|--------|------|-----|
| **Learning Curve** | ⭐⭐ Easy | ⭐⭐⭐⭐ Hard | ⭐⭐⭐ Moderate |
| **Salary (2024)** | $100-150K | $130-200K | $120-180K |
| **Job Market** | 🔥 High | 💼 Very High | 📈 Growing |
| **Best For** | Data, scripts, AI | Enterprise, Android | DevOps, microservices |
| **Time to Proficient** | 4-6 weeks | 10-12 weeks | 8-10 weeks |

## Tips for Using Comparison

✅ Compare 2-3 specializations at a time (easier to decide)
✅ Filter by your priorities first
✅ Consider career growth, not just starting salary
✅ Factor in personal interests and strengths
✅ Review job postings in target roles
✅ Talk to people in those roles
✅ Take the comparison as guidance, not law

## Related Commands

- `/roadmap [role]` - Dive deeper into specific role
- `/learn [role]` - Start learning path for chosen specialization
- `/resources [role]` - Find learning materials for chosen path
- `/progress [role]` - Track progress once you've chosen

---

**💡 Pro Tip**: Choose based on your interests and strengths, not just salary! Passion drives excellence.
