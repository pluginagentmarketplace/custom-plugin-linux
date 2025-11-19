# /resources - Curated Learning Materials

**Discover the best learning materials for any specialization.** Find courses, books, communities, tutorials, tools, and projects ranked by quality and user ratings.

## Command Syntax

```bash
/resources [specialization] [options]

# Get all resource types
/resources react
/resources python
/resources kubernetes

# Filter by resource type
/resources frontend --type courses
/resources backend --type books
/resources devops --type communities

# Filter by cost
/resources machine-learning --free (free only)
/resources golang --paid (paid only)
/resources aws --price-range 0-100

# Filter by level
/resources javascript --level beginner
/resources rust --level intermediate
/resources kubernetes --level advanced

# Filter by popularity
/resources react --trending (most popular now)
/resources python --top-rated (highest rated)
/resources typescript --recently-updated

# Advanced filtering
/resources frontend --type courses --level beginner --format video
/resources backend --type books --language english --recent
```

## Resource Types

### 1. **Online Courses**
- Structured learning paths
- Video tutorials
- Interactive exercises
- Quizzes and assessments
- Certificates of completion
- Platforms: Udemy, Coursera, Pluralsight, Educative, etc.

### 2. **Books**
- Comprehensive reference
- Deep dives
- Theory and best practices
- Both printed and ebooks
- All proficiency levels

### 3. **Communities**
- Discord servers
- Slack groups
- Reddit communities
- Forums
- Networking opportunities

### 4. **Tutorials & Articles**
- Step-by-step guides
- Blog posts
- Video tutorials
- Medium articles
- Dev.to posts
- Technical documentation

### 5. **Interactive Platforms**
- Hands-on coding
- Gamified learning
- Real-world projects
- Coding challenges
- Pair programming

### 6. **Tools & Frameworks**
- Official documentation
- GitHub repositories
- Sample projects
- Boilerplates
- Developer tools

### 7. **Podcasts & Videos**
- Educational podcasts
- YouTube channels
- Conference talks
- Webinars
- Live streams

### 8. **Projects & Templates**
- GitHub projects
- Open source contributions
- Project ideas
- Starter templates
- Real-world examples

## Output Format

### Course Recommendations
```
Top Courses for React Development
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. ⭐ "React - The Complete Guide" (Udemy)
   ├─ Instructor: Maximilian Schwarzmüller
   ├─ Duration: 48 hours
   ├─ Level: Beginner → Advanced
   ├─ Students: 2M+
   ├─ Rating: 4.8/5 (450K reviews)
   ├─ Cost: $14.99 (often on sale)
   └─ Best for: Comprehensive React mastery

2. ⭐ "The Joy of React" (Josh Comeau)
   ├─ Duration: 12 hours interactive
   ├─ Level: Beginner → Intermediate
   ├─ Rating: 4.9/5
   ├─ Cost: $97
   └─ Best for: Modern React patterns

3. "React Query & Server State" (TkDodo)
   ├─ Duration: Self-paced
   ├─ Level: Intermediate → Advanced
   ├─ Rating: 4.8/5
   ├─ Cost: Free (open source guide)
   └─ Best for: Advanced data fetching
```

### Book Recommendations
```
Must-Read Books for React Developers
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

1. "Learning React" (Alex Banks & Eve Porcello)
   ├─ Format: Paperback / Kindle
   ├─ Pages: 350
   ├─ Best for: Fundamentals
   └─ Price: $45 / $20 Kindle

2. "React Patterns" (Michael Chan)
   ├─ Format: Ebook
   ├─ Best for: Advanced patterns
   └─ Price: $29 (online course)
```

### Community Resources
```
Active React Communities
━━━━━━━━━━━━━━━━━━━━━━━━

Discord:
- React Official Discord (50K+ members)
- Reactiflux (100K+ members)

Reddit:
- r/reactjs (500K+ subscribers)
- r/Frontend (800K+ subscribers)

Forums:
- Stack Overflow
- Dev.to Community
- CSS-Tricks
```

## Usage Examples

### Example 1: Find Best React Courses
```bash
/resources react --type courses --level beginner
```
Returns: Top-rated beginner React courses with reviews and pricing

### Example 2: Free Python Resources
```bash
/resources python --free --type courses --type books
```
Returns: Free courses and books for Python learning

### Example 3: Machine Learning Trending Resources
```bash
/resources machine-learning --trending --type courses
```
Returns: Currently trending ML courses and materials

### Example 4: Kubernetes Community Resources
```bash
/resources kubernetes --type communities
```
Returns: Active Kubernetes communities with membership info

## Resource Filtering Options

### By Cost
- `--free` - Free resources only
- `--paid` - Paid resources only
- `--price-range [min]-[max]` - Filter by price

### By Format
- `--format video` - Video courses
- `--format text` - Books and articles
- `--format interactive` - Hands-on coding
- `--format mixed` - Combination of formats

### By Language
- `--language english`
- `--language spanish`
- `--language (any language)`

### By Recency
- `--recent` - Recently published
- `--trending` - Currently trending
- `--top-rated` - Highest rated
- `--most-reviewed` - Most popular

### By Duration
- `--duration-hours 0-10` (short courses)
- `--duration-hours 10-50` (medium)
- `--duration-hours 50+` (comprehensive)

### By Learning Style
- `--style visual` - Video-heavy
- `--style hands-on` - Project-based
- `--style theory` - Concept-focused
- `--style mixed` - Balanced

## Advanced Resource Discovery

### Personalized Recommendations
```bash
/resources react --based-on-learning-style hands-on --based-on-goals interview-prep
```
Returns: Resources matched to your learning style and goals

### Curated Learning Paths
```bash
/resources machine-learning --create-learning-bundle
```
Returns: Recommended sequence of resources for optimal learning

### Cost Estimation
```bash
/resources full-stack --estimate-cost
```
Returns: Total cost of learning with budget options

### Time Estimation
```bash
/resources python --estimate-hours [level]
```
Returns: Estimated hours for recommended resources

## Quality Metrics

Resources are rated on:
- **Rating**: User reviews (1-5 stars)
- **Reviews**: Number of ratings (popularity)
- **Recency**: Last updated (currency)
- **Community**: Active discussions
- **Career Value**: Job market relevance
- **Accessibility**: Ease of learning

## Resource Categories

### Free Resources
- **Documentation**: Official docs, tutorials
- **YouTube**: Educational channels
- **GitHub**: Open source projects, guides
- **Dev.to**: Community articles
- **FreeCodeCamp**: Complete courses

### Premium Resources
- **Udemy**: Affordable courses ($10-50)
- **Coursera**: Full specializations ($200-400)
- **Pluralsight**: Professional development ($400/year)
- **egghead.io**: Expert video lessons ($300/year)
- **Frontend Masters**: Advanced courses ($300/year)

### Specialized Resources
- **LinkedIn Learning**: Career-focused
- **A Cloud Guru**: Cloud-specific
- **PluralSight**: Enterprise training
- **O'Reilly**: Technical books
- **Manning**: Deep-dive books

## Tips for Using Resources

✅ Start with free resources (docs, YouTube)
✅ Invest in 1-2 paid courses per specialization
✅ Join communities for support
✅ Mix learning styles (video + books + hands-on)
✅ Check review dates (avoid outdated materials)
✅ Read recent reviews (get honest feedback)
✅ Try free previews before buying
✅ Combine multiple resources for mastery

## Related Commands

- `/roadmap [role]` - Understand specialization overview
- `/learn [role]` - Create personalized learning path
- `/progress [role]` - Track your learning with resources
- `/compare [role1] [role2]` - Compare specialization resources

---

**💡 Pro Tip**: Quality > Quantity. Use 2-3 excellent resources instead of many mediocre ones!
