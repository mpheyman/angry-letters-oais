Sync Linear project status and identify tickets needing attention. Provides progress summary, blockers, and action items.

## Inputs
- Linear project ID or name (required)
- Specific milestone (optional): Focus on tickets in a particular milestone
- Time window (optional): e.g., "last 7 days" or "this sprint"

## Process

### Step 1: Fetch Current State
Use Linear tools to fetch:
- Project details (`user-linear-get_project`)
- All project tickets (`user-linear-list_issues` with project filter)
- Recent activity (comments, status changes)

### Step 2: Categorize Tickets

Group tickets by status:
- **Todo**: Not started
- **In Progress**: Actively being worked on
- **Blocked**: Waiting on dependencies or external factors
- **Done**: Completed
- **Cancelled**: No longer needed

### Step 3: Identify Issues Needing Attention

Flag tickets that need action:

**Stale Tickets** (no updates in 7+ days):
- In Progress but no recent activity
- Blocked with no resolution plan
- Todo tickets that should have started

**Missing Information**:
- No acceptance criteria
- No priority set
- No estimate/effort
- No assignee (if work has started)

**Dependency Issues**:
- Blocked tickets where blocker is Done (update status)
- Circular dependencies
- Blockers that are themselves blocked

**Scope Creep Risks**:
- Tickets with many comments (potential scope expansion)
- Tickets that have been in progress for >2 weeks
- Tickets with "needs refinement" label

### Step 4: Calculate Progress Metrics

**Completion Rate**:
- Total tickets: X
- Completed: Y (Z%)
- In Progress: N
- Blocked: M

**Velocity** (if historical data available):
- Tickets completed per week
- Trend (increasing/decreasing/stable)

**Burn Rate**:
- Tickets remaining
- Current velocity
- Projected completion date

### Step 5: Identify Blockers

For each blocked ticket:
- What's blocking it?
- Who owns the blocker?
- When will it be resolved?
- Can we work around it?

## Output Format

### 1. Progress Summary
```markdown
# Project Sync: [Project Name]
*Last synced: [timestamp]*

## Progress Overview

**Total Tickets**: X
- ✅ Done: Y (Z%)
- 🚧 In Progress: N
- 🚫 Blocked: M
- 📋 Todo: P

**Velocity**: ~X tickets/week
**Projected Completion**: [date] (based on current velocity)
```

### 2. Recent Activity
```markdown
## What's Changed (Last 7 Days)

**Completed** ✅
- ANG-123: Email preference backend (completed 2 days ago)
- ANG-124: Shared component (completed 4 days ago)

**Started** 🚧
- ANG-125: Frontend integration (started 1 day ago)
- ANG-126: Testing (started 3 days ago)

**Blocked** 🚫
- ANG-127: Deployment (blocked by infrastructure)
```

### 3. Tickets Needing Attention
```markdown
## Action Items

### Stale Tickets (No Updates in 7+ Days)
- **ANG-128**: Email template rendering
  - Status: In Progress
  - Last updated: 9 days ago
  - Assignee: [name]
  - **Action**: Check status, unblock or reassign

### Missing Information
- **ANG-129**: Advanced preferences
  - Missing: Acceptance criteria, priority
  - **Action**: Run `/linear-refine ANG-129` to add details

### Dependency Issues
- **ANG-130**: Frontend polish
  - Status: Blocked by ANG-124
  - But ANG-124 is Done!
  - **Action**: Update ANG-130 status to unblocked

### Scope Creep Risks
- **ANG-131**: User dashboard
  - In Progress for 15 days
  - 12 comments (scope expanding?)
  - **Action**: Review scope, consider splitting into multiple tickets
```

### 4. Blockers Deep Dive
```markdown
## Current Blockers (M tickets)

### ANG-132: API Integration
- **Blocked by**: Third-party API access
- **Owner**: External team
- **ETA**: Unknown
- **Mitigation**: Can we mock the API for now?

### ANG-133: Database Migration
- **Blocked by**: Staging environment access
- **Owner**: DevOps team
- **ETA**: This week
- **Mitigation**: Test locally first

**Recommendation**: Focus on unblocked work while waiting on these.
```

### 5. Health Score
```markdown
## Project Health: 🟢 Healthy / 🟡 At Risk / 🔴 Critical

**Indicators**:
- ✅ On track for timeline (75% complete, 80% of time elapsed)
- ⚠️ 3 stale tickets need attention
- ✅ No critical blockers
- ⚠️ Velocity declining (was 5/week, now 3/week)

**Overall**: 🟡 At Risk
**Reason**: Velocity declining, needs investigation
```

### 6. Recommendations
```markdown
## Next Steps

1. **Immediate Actions**:
   - Update ANG-130 status (blocker resolved)
   - Check on ANG-128 (stale for 9 days)
   - Refine ANG-129 (missing acceptance criteria)

2. **This Week**:
   - Complete 3 in-progress tickets
   - Start 2 unblocked tickets
   - Resolve 1 blocker (ANG-133)

3. **Watch List**:
   - ANG-131: Scope creep risk
   - Velocity trend: Investigate decline

4. **Consider**:
   - Can we parallelize work to increase velocity?
   - Should we defer low-priority tickets to v2?
```

## Rules

- **Be concise**: Focus on actionable insights, not exhaustive lists
- **Highlight problems**: Stale, blocked, missing info
- **Provide solutions**: Suggest specific actions
- **Calculate metrics**: Progress %, velocity, burn rate
- **Identify risks**: Scope creep, timeline slippage, blockers
- **No local storage**: All data from Linear (single source of truth)
- **Respect privacy**: Don't expose PII or sensitive info
- **Be constructive**: Frame issues as opportunities to improve

## Example Usage

```
User: /project-sync "Email Preferences"

Agent: Fetching project status from Linear...

# Project Sync: Email Preferences
*Last synced: Feb 14, 2026 4:30 PM*

## Progress Overview

**Total Tickets**: 15
- ✅ Done: 8 (53%)
- 🚧 In Progress: 4 (27%)
- 🚫 Blocked: 1 (7%)
- 📋 Todo: 2 (13%)

**Velocity**: ~4 tickets/week
**Projected Completion**: Feb 28, 2026

[Full report follows...]

## Action Items
- 2 stale tickets need attention
- 1 blocked ticket can be unblocked
- 1 ticket needs refinement

Next: Address action items, then run `/project-status` for stakeholder update.
```

## Integration with Other Commands

- After `/build-plan`: Use `/project-sync` regularly to track progress
- For stale tickets: Use `/linear ANG-123` to investigate
- For missing info: Use `/linear-refine ANG-123` to add details
- For status reports: Use `/project-status` for concise summary
- After completing work: Use `/docs-update` to update documentation

## Advanced Features

### Trend Analysis
If run multiple times, track trends:
- Velocity over time
- Blocker resolution rate
- Scope creep indicators

### Smart Notifications
Proactively flag:
- Tickets that will miss deadlines
- Dependencies about to become blockers
- Team members overloaded (too many assigned tickets)

### Milestone Progress
If milestone specified:
- Focus on tickets in that milestone
- Calculate milestone completion %
- Identify risks to milestone deadline

## Health Score Calculation

**🟢 Healthy** (all true):
- Progress >= timeline % (e.g., 50% done, 50% of time elapsed)
- <3 stale tickets
- <2 critical blockers
- Velocity stable or increasing

**🟡 At Risk** (any true):
- Progress < timeline % by 10-20%
- 3-5 stale tickets
- 2-3 blockers
- Velocity declining

**🔴 Critical** (any true):
- Progress < timeline % by >20%
- >5 stale tickets
- >3 blockers or 1 unresolvable blocker
- Velocity dropped >50%
- Scope creep evident
