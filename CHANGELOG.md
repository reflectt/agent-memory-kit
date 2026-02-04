# Changelog

All notable changes to the Agent Memory Kit.

---

## [2.0.0] - 2026-02-03

### Added - Compaction Survival Features

**Problem:** Every compaction = context loss. Pre-compaction flush was manual, key context required re-reading files.

**Solution:** Structured pre-compaction flush system + quick context snapshots.

#### New Files
- `templates/compaction-survival.md` — Complete guide to surviving compactions
- `templates/context-snapshot-template.md` — Quick "save state" template
- `helpers/check-compaction.sh` — Token limit checker
- `INSTALLATION.md` — Step-by-step setup guide

#### Improvements
- **context-snapshot.md** — New file type for pre-compaction state capture
  - Current focus
  - Active decisions
  - Running subagents
  - Next actions
  - Recent wins & blockers
  - Notes to future-self

- **Updated wake routine** — Added post-compaction context snapshot check
- **Updated daily routine** — Added pre-compaction flush step (~160K tokens)
- **Heartbeat integration** — Token limit checks can be added to HEARTBEAT.md

#### Key Features
1. **Automatic reminder system** — Check tokens during heartbeat
2. **Structured flush checklist** — Never forget what to capture
3. **Quick re-orientation** — context-snapshot.md = <2 min to full context
4. **Reduced re-reading** — Focus on recent + relevant, not everything

#### Documentation Updates
- README.md — Added Compaction Survival section
- ARCHITECTURE.md — Added compaction routine
- SKILL.md — Updated file list

### Changed
- Daily routine now includes token monitoring
- Wake routine prioritizes context-snapshot.md for post-compaction

### Impact
- **Before:** Manual flush, 5+ min re-orientation after compaction, frequent context loss
- **After:** Structured flush, <2 min re-orientation, minimal context loss

---

## [1.0.0] - 2026-02-02

### Initial Release

#### Core Features
- 3-layer memory architecture (Working, Long-term, Feedback)
- Episodic memory (daily logs)
- Semantic memory (MEMORY.md)
- Procedural memory (procedures/)
- Feedback loops (feedback.md)

#### Templates
- ARCHITECTURE.md
- feedback.md
- procedure-template.md
- daily-template.md

#### Documentation
- README.md (full guide)
- SKILL.md (quick reference)

---

## Future Improvements (Ideas)

- [ ] Automatic token usage detection script
- [ ] Compaction frequency analytics (track how often)
- [ ] Context snapshot versioning (keep last 3)
- [ ] Procedure usage tracking (which HOWs are accessed most?)
- [ ] Integration with OpenClaw status API for automated checks

---

*This kit is actively used by Team Reflectt. Improvements come from real pain points.*
