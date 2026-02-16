Quick project health check and status report. Generates a concise, one-page summary suitable for standups or stakeholder updates.

## Inputs
- Linear project ID or name (required)
- Report type (optional): `brief` (default) | `detailed` | `stakeholder`

## Process

### Step 1: Fetch Project Data
- Project details (`user-linear-get_project`)
- All project tickets (`user-linear-list_issues`)
- Recent milestones and status updates

### Step 2: Calculate Key Metrics

**Progress Metrics**:
- Total tickets
- Completed tickets (%)
- In progress tickets
- Blocked tickets
- Todo tickets

**Velocity Metrics** (if historical data available):
- Tickets completed this week
- Tickets completed last week
- Average velocity (tickets/week)
- Trend (↑ increasing, → stable, ↓ decreasing)

**Timeline Metrics**:
- Project start date
- Target completion date
- Days elapsed / days remaining
- On track? (compare progress % to time elapsed %)

### Step 3: Identify Top Issues

**Top 3 Blockers**:
- Tickets blocking the most other work
- Longest-standing blockers

**Top 3 Risks**:
- High-complexity tickets
- Tickets with scope creep
- Critical path bottlenecks

**Top 3 Wins**:
- Recently completed high-impact tickets
- Milestones achieved
- Blockers resolved

## Output Format

### Brief Report (Default)
```markdown
# [Project Name] Status
*As of [date]*

## At a Glance

**Progress**: Y/X tickets complete (Z%)
**Status**: 🟢 On Track / 🟡 At Risk / 🔴 Critical
**Velocity**: ~N tickets/week (↑/→/↓)
**Completion**: [projected date]

## This Week

**Completed** ✅
- ANG-123: Feature X
- ANG-124: Feature Y

**In Progress** 🚧
- ANG-125: Feature Z (60% done)
- ANG-126: Testing (just started)

**Blockers** 🚫
- ANG-127: Waiting on API access

## Next Week

**Planned**:
- Complete ANG-125, ANG-126
- Start ANG-128, ANG-129

**Risks**:
- ANG-127 blocker may delay Phase 2

## Action Items
1. Resolve ANG-127 blocker (owner: DevOps)
2. Review ANG-130 scope (potential creep)
3. Assign ANG-131 (currently unassigned)
```

### Detailed Report
```markdown
# [Project Name] - Detailed Status Report
*As of [date]*

## Executive Summary

**Overall Health**: 🟡 At Risk
**Progress**: 8/15 tickets (53%)
**Timeline**: Week 3 of 5 (60% elapsed, 53% complete - slightly behind)
**Velocity**: 3.5 tickets/week (declining from 5/week)
**Top Risk**: Velocity decline and 1 critical blocker

## Progress Breakdown

### By Status
- ✅ Done: 8 tickets (53%)
- 🚧 In Progress: 4 tickets (27%)
- 🚫 Blocked: 1 ticket (7%)
- 📋 Todo: 2 tickets (13%)

### By Type
- Epics: 1/2 complete (50%)
- Stories: 4/6 complete (67%)
- Tasks: 3/7 complete (43%)

### By Phase
- Phase 0 (Foundation): 5/5 complete ✅
- Phase 1 (Core): 3/6 in progress 🚧
- Phase 2 (Enhancement): 0/3 not started 📋
- Phase 3 (Launch): 0/1 not started 📋

## Velocity Analysis

**This Week**: 3 tickets completed
**Last Week**: 4 tickets completed
**Average**: 3.5 tickets/week
**Trend**: ↓ Declining

**Concern**: Velocity dropped from 5/week (Week 1) to 3.5/week (current)
**Possible Causes**: Increased complexity, blockers, scope creep

## Timeline Analysis

**Project Duration**: 5 weeks
- Start: Feb 1, 2026
- Target: Mar 7, 2026
- Today: Feb 14, 2026

**Time Elapsed**: 60% (3 of 5 weeks)
**Work Complete**: 53% (8 of 15 tickets)

**Status**: ⚠️ Slightly behind (7% gap)
**Projected Completion**: Mar 10, 2026 (3 days late at current velocity)

## Blockers (1 active)

### 🚫 ANG-127: API Integration
- **Status**: Blocked
- **Blocked by**: Third-party API access (external)
- **Duration**: 5 days
- **Impact**: Blocks 3 downstream tickets (ANG-130, ANG-131, ANG-132)
- **Owner**: External team
- **ETA**: Unknown
- **Mitigation**: Consider mocking API for development

## Risks (3 identified)

### High Priority
1. **ANG-127 Blocker** (Critical)
   - Blocks 3 tickets on critical path
   - No ETA from external team
   - Could delay project by 1 week

### Medium Priority
2. **Velocity Decline** (Concerning)
   - Dropped from 5/week to 3.5/week
   - May indicate complexity increase or team capacity issue
   - Could push completion to Mar 10 (3 days late)

3. **ANG-131 Scope Creep** (Watch)
   - 12 comments, growing requirements
   - In progress for 8 days (estimate was 3 days)
   - Consider splitting into separate tickets

## Wins (Recent)

1. **Phase 0 Complete** ✅
   - All foundation work done
   - Unblocked Phase 1 work

2. **ANG-123 Shipped** ✅
   - Email preference backend complete
   - Tested and deployed

3. **ANG-124 Delivered** ✅
   - Shared component ready
   - Unblocked 2 frontend tickets

## Action Items

### Immediate (This Week)
1. **Resolve ANG-127 blocker**
   - Contact external team for ETA
   - Implement API mock as workaround
   - Owner: [assign]

2. **Review ANG-131 scope**
   - Assess if scope has grown
   - Consider splitting into v1 and v2
   - Owner: [assign]

3. **Investigate velocity decline**
   - Are tickets more complex than estimated?
   - Team capacity issues?
   - Adjust estimates if needed

### This Sprint
4. Complete 4 in-progress tickets
5. Start 2 unblocked todo tickets
6. Update 1 ticket status (ANG-130 - blocker resolved)

### Next Sprint
7. Begin Phase 2 (Enhancement)
8. Address any new blockers
9. Run `/project-sync` again to track progress
```

### Stakeholder Report
```markdown
# [Project Name] - Stakeholder Update
*Week of [date]*

## Summary

We're 53% complete with the Email Preferences project, slightly behind schedule due to a third-party API blocker. We've completed all foundation work and are making progress on core features. Projected completion is Mar 10 (3 days after target).

## Progress

- **Completed**: 8 of 15 tickets (53%)
- **On Track**: Phase 0 (Foundation) complete ✅
- **In Progress**: Phase 1 (Core Features) - 3 of 6 tickets done
- **Timeline**: Week 3 of 5

## Key Accomplishments

- Email preference backend shipped
- Shared component framework ready
- Database migrations complete

## Current Focus

- Frontend integration (ANG-125)
- Comprehensive testing (ANG-126)
- Resolving API access blocker (ANG-127)

## Risks & Mitigation

**Risk**: Third-party API blocker (ANG-127)
- Impact: Could delay 3 dependent tickets
- Mitigation: Implementing API mock for development

**Risk**: Velocity declining
- Impact: May push completion by 3 days
- Mitigation: Reviewing ticket complexity and team capacity

## Next Milestone

**Phase 1 Complete** (Target: Feb 21)
- 3 tickets remaining
- On track if blocker resolves this week

## Questions / Decisions Needed

- Approve API mock approach for ANG-127?
- Should we defer ANG-131 enhancements to v2?
```

## Rules

- **Be concise**: One-page summary for brief, 2-3 pages for detailed
- **Focus on insights**: Not just data, but what it means
- **Action-oriented**: Every issue should have a suggested action
- **Honest assessment**: Don't sugarcoat problems
- **Constructive framing**: Problems are opportunities
- **Stakeholder-friendly**: Non-technical language for stakeholder reports
- **Privacy-conscious**: No PII or sensitive info
- **Single source of truth**: All data from Linear

## Report Type Differences

**Brief** (default):
- Quick overview
- Top 3 items per category
- Suitable for daily standups
- ~1 page

**Detailed**:
- Full breakdown
- All tickets listed
- Trend analysis
- Suitable for weekly reviews
- ~2-3 pages

**Stakeholder**:
- Non-technical language
- Focus on outcomes, not tasks
- Risks and mitigation
- Suitable for client/exec updates
- ~1 page

## Example Usage

```
User: /project-status "Email Preferences"

Agent: Generating status report...

# Email Preferences Status
*As of Feb 14, 2026*

[Brief report follows...]

For detailed report: `/project-status "Email Preferences" detailed`
For stakeholder update: `/project-status "Email Preferences" stakeholder`
```

## Integration with Other Commands

- After `/build-plan`: Use `/project-status` to track against plan
- Before standups: Quick health check
- For stakeholder updates: Use stakeholder report type
- To investigate issues: Use `/project-sync` for detailed analysis
- To refine tickets: Use `/linear-refine ANG-123`

## Automation Suggestions

Consider running `/project-status` automatically:
- Every Monday morning (weekly update)
- Before sprint planning
- After major milestones
- When velocity changes significantly

## Health Score Algorithm

```
Healthy (🟢):
- progress_pct >= time_elapsed_pct - 5%
- stale_tickets < 3
- critical_blockers == 0
- velocity_trend != declining

At Risk (🟡):
- progress_pct >= time_elapsed_pct - 20%
- stale_tickets < 6
- blockers < 3
- velocity_trend == declining

Critical (🔴):
- progress_pct < time_elapsed_pct - 20%
- stale_tickets >= 6
- blockers >= 3 OR 1 unresolvable blocker
- velocity dropped > 50%
```
