Collaboratively refine a Linear project and break it down into implementation-ready tickets using proven product development frameworks (Jobs-to-be-Done, Story Mapping, RICE prioritization).

## Inputs
- Linear project ID, name, or URL (required)
- Focus area or milestone (optional)

## Structured Refinement Process

Go through each phase systematically, asking focused questions and suggesting answers based on best practices.

### Phase 1: Discovery (Jobs-to-be-Done)

Ask the user (max 5 questions):
1. **What problem are we solving?** (What's broken or missing?)
2. **For whom?** (User personas - be specific: e.g., "solo letter writers", "campaign creators", "recipients")
3. **What's the job-to-be-done?** (What outcome do users want? Frame as: "When I ___, I want to ___, so I can ___")
4. **What are users doing today?** (Current workarounds, pain points)
5. **Success looks like?** (Observable outcome: "Users can now ___")

**Agent suggestions:** Based on project context:
- Consider privacy/anonymity needs
- Think about rage-to-action conversion
- Consider creator vs solo user needs
- Security and moderation implications

### Phase 2: Scope (Story Mapping)

Ask the user:
1. **User journey steps?** (What's the backbone? e.g., "Discover → Draft → Review → Send → Track")
2. **Must-have features?** (MVP - what's the minimum to deliver value?)
3. **Nice-to-have features?** (v2 - what can wait?)
4. **What's out of scope?** (What are we explicitly NOT doing?)

**Agent suggestions:**
- Map to existing flows (letter builder, campaigns, admin portal)
- Consider mobile vs desktop experience
- Think about email notifications
- Integration points with existing features

### Phase 3: Prioritization (RICE)

**IMPORTANT: Ask about development model first:**
- "Are you using human developers or AI agents?"
- If AI agents: Use token cost in dollars (Claude Sonnet 4.5: ~$3/M input, ~$15/M output)
- If human: Use engineering weeks

For each feature identified, calculate RICE score:
- **Reach**: How many users will this impact? (number or %)
- **Impact**: How much value per user? (0.25 = minimal, 0.5 = low, 1 = medium, 2 = high, 3 = massive)
- **Confidence**: How sure are we? (50% = low, 80% = medium, 100% = high)
- **Effort**: AI agent cost ($) OR engineering weeks (based on development model)
- **Score** = (Reach × Impact × Confidence) / Effort

**AI Agent Effort Estimation:**
- Low cost ($5-15): Simple CRUD, content generation, basic UI
- Medium cost ($20-30): Complex state management, API integration, PDF generation
- High cost ($40+): Full admin UIs, complex workflows, extensive codebase exploration

Present RICE scores and suggest priority order.

### Phase 4: Technical Planning

Ask the user:
1. **Architecture changes needed?** (New services, major refactors?)
2. **Database changes?** (New tables, migrations, schema changes?)
3. **API changes?** (New endpoints, breaking changes?)
4. **Frontend components?** (New pages, shared components?)
5. **Security/privacy considerations?** (Auth, PII, CSP, rate limiting?)
6. **Testing strategy?** (Unit, integration, E2E, manual?)

**Agent suggestions:** Based on project architecture:
- Docker-first development
- Postgres for data storage
- CSP-compliant frontend (no inline scripts/styles)
- HMAC tokens for protected resources
- Rate limiting on sensitive endpoints
- Follow existing patterns in `project-documentation/`

### Phase 5: Dependencies & Risks

Ask the user:
1. **What must be built first?** (Foundation work, prerequisites)
2. **External dependencies?** (Third-party APIs, services)
3. **Known risks?** (Technical complexity, unknowns, scope creep)
4. **Mitigation strategies?** (How to reduce risk?)

**Agent suggestions:**
- Check for conflicts with in-flight work
- Consider rollback plans
- Flag breaking changes
- Identify testing bottlenecks

## Ticket Breakdown

After refinement, generate hierarchical ticket breakdown:

### Structure:
```
Epic: [Theme Name]
├── User Story: [Feature Name]
│   ├── Task: [Backend work]
│   ├── Task: [Frontend work]
│   ├── Task: [Database migration]
│   ├── Task: [Testing]
│   └── Task: [Documentation]
└── User Story: [Another Feature]
    └── ...
```

### Ticket Template:

**Epic:**
- Title: `[Epic] Theme Name`
- Description: High-level goal and success metrics
- Labels: `epic`, `ai-created`
- Priority: Based on RICE score

**User Story:**
- Title: `[Story] As a [persona], I want to [action] so I can [outcome]`
- Description: Include acceptance criteria, RICE score, constraints
- Labels: `story`, `ai-created`
- Priority: Based on RICE score
- Blocks: Related tasks

**Task:**
- Title: `[Task] Specific technical work`
- Description: Implementation notes, files to change, testing approach
- Labels: `task`, `ai-created`, (plus: `backend`, `frontend`, `db`, `test`, `docs`)
- Priority: Inherited from story
- Blocked by: Dependencies

## Output Format

### 1. Project Refinement Summary
Present a markdown document with:
- Problem statement
- User personas
- Jobs-to-be-done
- User journey map
- Feature list with RICE scores
- Technical architecture notes
- Dependencies and risks

### 2. Ticket Breakdown
Present hierarchical breakdown:
- X epics
- Y user stories
- Z tasks
- Total estimated effort: N weeks OR $X (AI agent cost)

Show dependencies as a tree or list.

### 3. Approval Gate
Ask user: "Review the breakdown above. Approve to create all tickets in Linear?"
- If No: Ask what to revise, go back to relevant phase
- If Yes: Proceed to ticket creation

### 4. Ticket Creation
- Create all tickets in Linear using `user-linear-create_issue` tool
- Set proper project assignment
- Add labels (epic, story, task, test, docs, backend, frontend, db)
- Set priorities (0=None, 1=Urgent, 2=High, 3=Normal, 4=Low)
- Create dependencies (blocks, blockedBy relationships)
- Assign to milestones if specified

### 5. Linear Document
Create a project plan document in Linear using `user-linear-create_document`:
- Title: "Project Plan: [Project Name]"
- Content: Full refinement summary (markdown)
- Link to project

### 6. Confirmation
Return:
- Link to Linear project
- Link to project plan document
- List of created tickets with keys
- Next step: "Run `/build-plan [project-name]` to generate implementation phases"

## Rules

- **Structured frameworks only**: Use JTBD, Story Mapping, RICE (not open-ended)
- **Max 5 questions per phase**: Keep it focused
- **Suggest answers**: Based on project context and best practices
- **Single source of truth**: Store everything in Linear (no local docs)
- **Approval required**: Don't create tickets until user approves breakdown
- **Batch creation**: Create all tickets at once after approval
- **Proper relationships**: Set blocks/blockedBy for dependencies
- **Security first**: Flag PII, secrets, CSP violations in constraints
- **Testing included**: Always include test tasks
- **Documentation included**: Always include doc update tasks

## Example Usage

```
User: /project-breakdown "Email Preferences"

Agent: I'll help you break down the Email Preferences project. Let's start with discovery.

Phase 1: Discovery (Jobs-to-be-Done)

1. What problem are we solving?
[Agent waits for answer, then continues through all phases...]

[After all phases complete]

Agent: Here's the breakdown:
- 2 epics
- 5 user stories  
- 15 tasks
- Estimated effort: 3 weeks

Review the breakdown above. Approve to create all tickets in Linear?

User: Yes

Agent: Creating tickets in Linear...
✓ Created ANG-45 [Epic] Email Preferences
✓ Created ANG-46 [Story] As a user, I want to...
[etc.]

Project plan saved to Linear: [link]
Next: Run `/build-plan "Email Preferences"` to generate phases.
```

## Integration with Existing Commands

After `/project-breakdown`:
- Use `/linear ANG-123` to view individual tickets
- Use `/linear-refine ANG-123` to add implementation details
- Use `/build-plan [project]` to generate phased plan
- Use `/project-sync [project]` to track progress
- Use `/docs-update` after completing work
