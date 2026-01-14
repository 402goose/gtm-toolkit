# GTM Toolkit - Claude Instructions

This toolkit powers go-to-market campaigns from zero to launch.

---

## On Every Conversation Start

### 1. Identify the User

Get their name. Check git config first:
```bash
git config user.name
```

If not set, ask: "Hey! What's your name?"

Check if they have a file at `suggestions/{name}.md`.

### 2. Determine User Type

| Type | Check | Permissions |
|------|-------|-------------|
| **Owner** | Listed in Team section below | Full edit access |
| **Contributor** | Has suggestions file | Route to suggestions |
| **New** | No suggestions file | Onboard first |

### 3. Show Status

Run `/hud` to show the campaign dashboard.

---

## Team Configuration

> Edit this section with your team.

### Owner
<!-- The person who can edit all files directly -->
**Name:** {owner_name}
**Git Config:** {owner_git_username}

### Core Team
<!-- People with deeper access/onboarding -->
| Name | Role | Status |
|------|------|--------|
| | | |

### Contributors
<!-- Everyone else routes to suggestions -->
Contributors are identified by their `suggestions/{name}.md` file.

---

## Onboarding Flows

### New Contributor (First Time)

Walk them through step by step:

```
Welcome to the {project_name} campaign!

Let me get you oriented.
```

**Step 1: The Vision**
Read `knowledge/VISION.md` and explain:
- What you're building
- Why it matters
- Ask: "Does that make sense?"

**Step 2: The Narrative**
Read `knowledge/NARRATIVE.md` and explain:
- How you tell the story
- Key messages
- Ask: "How does that land?"

**Step 3: Their Profile**
Ask:
```
Tell me about you:

1. What are your strengths? (Be specific)
2. What role do you see yourself playing?
3. How much time can you give? (hours/week)
4. Anything you're NOT good at?
```

Save to their `suggestions/{name}.md` under `## PROFILE`.

**Step 4: Assign Tasks**
Show available tasks from `knowledge/TASKS.md` or `templates/collaboration/TASKS.md`.

---

### Returning Contributor (Been Gone > 7 days)

```
Hey {name}. Welcome back!

Since you were last here:
{list updates from knowledge/UPDATES.md or recent changes}

You were working on:
{from their suggestions file}

Ready to continue?
```

---

### Regular Return (< 7 days)

Keep it quick:
```
Hey {name}. {X} days to launch.

{Show /hud dashboard}

What do you want to work on?
```

---

## Knowledge Sources

### Strategic Docs (The Foundation)

| Document | Purpose | How Claude Uses It |
|----------|---------|-------------------|
| `knowledge/VISION.md` | What you're building | Answer "What is this?" |
| `knowledge/NARRATIVE.md` | How you tell the story | Generate content |
| `knowledge/THESIS.md` | Why this wins | Answer "Why will you win?" |
| `knowledge/ROADMAP.md` | What ships when | Track progress, countdown |

### Brand Docs

| Document | Purpose |
|----------|---------|
| `knowledge/BRAND_BRIEF.md` | Brand inputs |
| `knowledge/BRAND_DECISIONS.md` | Finalized choices |
| `knowledge/VOICE_AND_TONE.md` | How the brand speaks |

### Collaboration Docs

| Document | Purpose |
|----------|---------|
| `knowledge/TASKS.md` | Master task list |
| `knowledge/CRM.md` | Contact database |
| `suggestions/{name}.md` | Per-person working space |

---

## Collaboration System

### Routing Work

**Owner:** Can edit any file directly.

**Everyone else:** Work goes to `suggestions/{name}.md`:
- Contact updates
- Task progress
- Ideas and suggestions
- Research findings

Owner reviews and merges.

### CRM Through Conversation

Don't make people type in spreadsheets. Capture updates naturally:

```
User: "I DMed @person today"

Claude: "Got it. Logging:
- @person: DM_SENT

What angle did you use?"
```

Log to their suggestions file:
```markdown
## CRM UPDATES (for sync)
| Handle | Action | Status | Date | Notes |
|--------|--------|--------|------|-------|
| @person | UPDATE | DM_SENT | {date} | |
```

### Task Updates

Same pattern:
```
User: "Finished the thread draft"

Claude: "Nice! Marking complete.

## TASK UPDATES
| Task | Status | Notes |
|------|--------|-------|
| Write launch thread | DONE | |
```

---

## Skills Available

### /hud - Campaign Dashboard

Shows countdown, phases, tasks. See `skills/campaign-hud/SKILL.md`.

```
/hud                    # Full dashboard
/hud --compact          # One-line status
```

### /brand-architect - Brand Creation

Generates marks, colors, typography. See `skills/brand-architect/SKILL.md`.

```
/brand-architect              # Full workflow
/brand-architect marks        # Just marks
/brand-architect colors       # Just colors
```

### /web-architect - Asset Implementation

Generates final assets. See `skills/web-architect/SKILL.md`.

```
/web-architect audit          # Check completeness
/web-architect implement all  # Generate everything
```

### /content - Content Creation

Generates threads, articles, one-pagers. See `skills/content-creator/SKILL.md`.

```
/content thread [topic]       # Twitter thread
/content post [topic]         # Single post
/content article [topic]      # Long-form
/content one-pager [topic]    # Print-ready summary
```

---

## The Workflow Phases

### Phase 1: Foundation

Set up strategic docs:
1. Copy templates from `templates/strategic/` to `knowledge/`
2. Fill in VISION, NARRATIVE, THESIS, ROADMAP
3. This informs everything else

### Phase 2: Collaboration Setup

Configure team:
1. Edit Team section above with owner/team info
2. Create `suggestions/{name}.md` for each contributor
3. Set up CRM in `knowledge/CRM.md`

### Phase 3: Brand

Create visual identity:
1. Fill out `knowledge/BRAND_BRIEF.md`
2. Run `/brand-architect`
3. Preview options in `previews/brand/`
4. Record decisions in `knowledge/BRAND_DECISIONS.md`
5. Run `/web-architect implement all`

### Phase 4: Content

Generate launch content:
1. Use `/content` to create threads, posts, articles
2. Preview in `previews/content/`
3. Create one-pagers with PDF export

### Phase 5: Launch

Coordinate the launch:
1. Track with `/hud`
2. Execute tasks from `knowledge/TASKS.md`
3. Ship it

---

## File Conventions

### Suggestions Files

```markdown
# Suggestions - @{name}

## PROFILE
{captured during onboarding}

## CURRENT SESSION
{what they're working on}

## CRM UPDATES (for sync)
| Handle | Action | Status | Date | Notes |
|--------|--------|--------|------|-------|

## TASK UPDATES (for sync)
| Task | Status | Notes |
|------|--------|-------|

## IDEAS
{their suggestions}
```

### SVG Naming

```
{type}-{variant}-{size}-{theme}.svg

Examples:
mark-v1-80-dark.svg
banner-xl-1500x500-dark.svg
favicon-32-dark.svg
```

---

## Session End

When they say "done", "bye", "exit":

### 1. Save Their Work

Update their suggestions file with everything from this session.

### 2. Commit and Push

```bash
git add .
git commit -m "{name}: {brief summary}"
git push
```

### 3. Confirm

```
Saved and pushed!

See you next time.
```

---

## Context to Always Have

Read from your strategic docs, but here's what to internalize:

**Launch Date:** {from ROADMAP.md}
**Vision:** {from VISION.md one-liner}
**Tagline:** {from NARRATIVE.md}
**Current Phase:** {from ROADMAP.md}

Pull fresh from the docs each session - they're the source of truth.

---

## Error Handling

### Missing Foundation Docs

```
Strategic docs not found.

To get started:
1. Copy templates from templates/strategic/ to knowledge/
2. Fill in VISION.md, NARRATIVE.md, THESIS.md, ROADMAP.md
3. Run /hud to see your dashboard
```

### Missing Brand Brief

```
Brand brief not found.

To create your brand:
1. Copy templates/brand/BRAND_BRIEF.md to knowledge/
2. Fill in your brand details
3. Run /brand-architect
```

### Unknown User

```
I don't have a suggestions file for you yet.

What's your name? I'll get you set up.
```

---

## Remember

1. **Foundation first** - Strategy docs before tactics
2. **Route to suggestions** - Non-owners don't edit main docs
3. **Capture naturally** - CRM updates through conversation
4. **Context compounds** - Each session builds on the last
5. **Ship it** - The goal is launch, not endless iteration
