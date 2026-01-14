---
name: campaign-hud
description: Display campaign status dashboard with countdown, phases, and tasks
---

# Campaign HUD

Shows the current state of your GTM campaign at a glance.

## Capabilities

- Show countdown to launch date
- Display current phase and progress
- List this week's priorities
- Show user's assigned tasks
- Track key metrics

## Usage

```
/hud                    # Full dashboard
/hud --compact          # One-line status
/hud --tasks            # Just tasks
/hud --metrics          # Just metrics
```

## Workflow

### Step 1: Read Context

Read these files to build the dashboard:
- `knowledge/ROADMAP.md` - Launch date, phases, milestones
- `knowledge/TASKS.md` or `templates/collaboration/TASKS.md` - Current tasks
- `suggestions/{user}.md` - User's assigned tasks

### Step 2: Calculate Countdown

```
Launch Date: {from ROADMAP.md}
Today: {current date}
Days Remaining: {calculation}
```

### Step 3: Display Dashboard

```
{ASCII art or logo}

{project name} - {days} days to launch

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CURRENT PHASE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Done] → [Current] → [Next] → [Launch]
              ↑
            NOW

Focus: {current phase focus}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
THIS WEEK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
{priority tasks from TASKS.md}

Key Outcomes:
- [ ] {outcome 1}
- [ ] {outcome 2}

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR TASKS (@{username})
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
{tasks assigned to current user}

What do you want to work on?
```

### Compact Mode (--compact)

```
{project} | {days}d to launch | Phase: {phase} | Your tasks: {count}
```

## Output Format

- Use ASCII box drawing for visual structure
- Include progress indicators (checkmarks, arrows)
- Color-code status when terminal supports it
- Keep it scannable - no walls of text

## Example

```
    /\_____/\
   /  o   o  \
  ( ==  ^  == )
   )         (

402.cat - 5 days to launch

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
CURRENT PHASE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
[Foundation] → [Content] → [Final Push] → [Launch]
                              ↑
                            NOW

Focus: Final announcements and coordination

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
THIS WEEK
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
├─ Write launch thread          @goose    IN_PROGRESS
├─ Finalize OG images           @cole     DONE
├─ Schedule tweets              @goose    TODO
└─ Prep Discord announcement    @team     TODO

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
YOUR TASKS (@goose)
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
1. Write launch thread (in progress)
2. Schedule tweets
3. Review final assets

What do you want to work on?
```

## Dependencies

- Requires `knowledge/ROADMAP.md` for launch date
- Works best with `knowledge/TASKS.md` populated
- User tasks from `suggestions/{name}.md`
