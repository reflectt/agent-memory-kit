# 🧠 Agent Memory Kit

**Stop forgetting how to do things.**

This kit gives AI agents a structured memory system. Born from a real incident — an agent woke up having forgotten *how* to do work it had done yesterday. The raw logs existed, but the procedural knowledge was gone.

---

## The Problem

AI agents have great short-term memory (the conversation) but terrible long-term memory. Most agents:
- Log *what* happened but not *how*
- Lose procedural knowledge between sessions
- Repeat mistakes because they don't track failures
- Have no structured way to improve over time

## The Solution

A 3-layer memory architecture:

| Layer | Purpose | Location |
|-------|---------|----------|
| **Working** | Current task focus | Conversation (automatic) |
| **Long-Term** | Persistent knowledge | `memory/` folder |
| **Feedback** | Learn from outcomes | `memory/feedback.md` |

Long-term memory splits into three types:
- **Episodic** — WHAT happened (daily logs)
- **Semantic** — WHAT I know (curated facts)  
- **Procedural** — HOW to do things (step-by-step guides)

---

## Quick Start

### 1. Copy the templates

```bash
# Create your memory folder
mkdir -p memory/procedures

# Copy templates from this kit
cp templates/ARCHITECTURE.md memory/
cp templates/feedback.md memory/
cp templates/procedure-template.md memory/procedures/
```

### 2. Add to your wake routine

In your `AGENTS.md` or equivalent:

```markdown
### On Wake:
1. Read `memory/ARCHITECTURE.md` (understand the system)
2. Read `memory/YYYY-MM-DD.md` (today + yesterday)
3. Check `memory/procedures/` if doing technical work
```

### 3. Start documenting

When you figure out how to do something → write a procedure.
When something fails → log it in feedback.md.
When the day ends → write your daily entry.

---

## File Structure

```
memory/
├── ARCHITECTURE.md      # How this system works
├── feedback.md          # Success/failure tracking
├── procedures/          # HOW to do things
│   ├── some-task.md
│   └── another-task.md
├── 2026-02-01.md        # Daily logs (episodic)
└── 2026-02-02.md
```

---

## The Three Memory Types

### Episodic Memory (Daily Logs)

**What it is:** Chronicle of events. What happened, when, with whom.

**File:** `memory/YYYY-MM-DD.md`

**Template:**
```markdown
# 2026-02-02

## Summary
One-line overview of the day.

## Events

### [Event Name]
**When:** [timestamp]
**What:** [what happened]
**How:** [steps taken — CRITICAL!]
**Outcome:** [result]
**Lessons:** [what to remember]
```

**Key insight:** Always include the HOW. "Connected to the API" is useless. "Connected to the API via `curl -X POST http://localhost:4444/api/speak`" is useful.

---

### Semantic Memory (Knowledge Base)

**What it is:** Curated facts, relationships, preferences. The distilled wisdom.

**File:** `MEMORY.md` (in workspace root)

**Categories to track:**
- People (preferences, relationships, context)
- Projects (status, goals, blockers)
- Technical (endpoints, patterns, configs)
- Lessons (hard-won wisdom)

**Update:** During weekly reviews, or when you learn something significant.

---

### Procedural Memory (How-To Guides)

**What it is:** Step-by-step processes for tasks you do repeatedly.

**Folder:** `memory/procedures/`

**Template:** See `templates/procedure-template.md`

**When to create:**
- You just figured out something non-obvious
- You did something you'll need to do again
- You're about to end a session after technical work

**The rule:** If you spent >10 minutes figuring something out, document it.

---

## Feedback Loops

The secret weapon. Track what works and what doesn't.

**File:** `memory/feedback.md`

**Template:**
```markdown
### [Date] - [Topic]
**Attempted:** [what you tried]
**Result:** SUCCESS / FAILURE
**Why:** [analysis — why did it work or fail?]
**Next time:** [what to do differently]
```

**Examples:**

```markdown
### Feb 2 - API Integration
**Attempted:** Call external API without rate limiting
**Result:** FAILURE — Got blocked after 50 requests
**Why:** No backoff strategy, hit rate limits
**Next time:** Add exponential backoff, respect rate limit headers

### Feb 2 - Research Approach  
**Attempted:** Look for people building DIY solutions to validate product idea
**Result:** SUCCESS — Found exact validation in subreddit
**Why:** DIY builders = proven demand
**Next time:** Keep this pattern for market research
```

---

## Daily Routine

### On Wake (session start)
1. Read semantic memory (`MEMORY.md`)
2. Read recent episodic memory (today + yesterday's `memory/YYYY-MM-DD.md`)
3. If doing technical work, check `memory/procedures/`

### During Work
- Log significant events to daily file (with HOW)
- Document new procedures when you figure them out
- Note failures and successes in feedback.md

### On Rest (session end)
- Update daily memory with session summary
- If learned something important → update MEMORY.md
- If figured out a process → create procedure doc

---

## Recovery Protocol

When you wake up confused:

1. **Check procedures/** — Is there a doc for what you're trying to do?
2. **Check recent daily logs** — Did past-you document how?
3. **Check feedback.md** — Did this fail before? Why?
4. **Check MEMORY.md** — Any relevant context?
5. **If still stuck** — Research, solve, then DOCUMENT for future-you

---

## Anti-Patterns to Avoid

❌ **"Mental notes"** — They don't survive sessions. Write it down.

❌ **Logging WHAT but not HOW** — "Connected to Homie" vs "Connected via `curl localhost:4444`"

❌ **Skipping procedures** — "I'll remember" → You won't.

❌ **Not tracking failures** — Same mistakes, repeated forever.

❌ **Putting everything in MEMORY.md** — Gets bloated. Daily logs are for events; MEMORY.md is for distilled knowledge.

---

## Installation

1. Copy `templates/` contents to your `memory/` folder
2. Read `ARCHITECTURE.md` once to understand the system
3. Start logging. That's it.

No dependencies. Just markdown files.

---

## Origin

Created by Team Reflectt after their lead agent (Kai 🌊) woke up on Feb 2, 2026 having forgotten how to use tools they'd mastered the day before.

The daily logs showed *what* was accomplished. But the procedural knowledge — the *how* — wasn't captured. This kit ensures that never happens again.

---

*Memory is a skill. Practice it.*
