<!-- Powered by BMAD™ Core -->

# Development Status Task

## Purpose

- Provide a comprehensive overview of the current BMAD development workflow state
- Display progress across planning and development phases
- Show story status breakdown and completion metrics
- Identify current focus areas and blockers
- Help users understand where they are in the BMAD workflow

## Instructions

### 1. Gather Project Information

Scan the project structure and collect the following information:

**Planning Phase:**

- Check if `docs/prd.md` exists
- Check if `docs/architecture.md` exists
- Check if `docs/project-brief.md` exists
- Count files in `docs/epics/` directory
- Count files in `docs/architecture/` directory (if sharded)

**Development Phase:**

- List all story files in `docs/stories/`
- For each story file, extract:
  - Story title (first H1 heading)
  - Status field
  - Total tasks count
  - Completed tasks count (marked with [x])
  - Agent Model Used (if present)

### 2. Calculate Metrics

**Story Statistics:**

- Total stories count
- Stories by status:
  - Draft (Status: Draft)
  - In Progress (Status: In Progress)
  - Ready for Review (Status: Ready for Review)
  - Completed (Status: Completed)
- Overall completion percentage

**Task Statistics:**

- Aggregate total tasks across all stories
- Aggregate completed tasks across all stories
- Task completion percentage

### 3. Identify Current Focus

**In Progress Stories:**

- List all stories with "Status: In Progress"
- For each, show:
  - Story file path
  - Story title
  - Tasks progress (e.g., "3/7 completed")
  - Last modified date (from file system)

**Blockers:**

- Scan story files for keywords: "blocked", "blocker", "issue", "problem"
- List any stories mentioning blockers

### 4. Present Status Report

Format the output as follows:

```markdown
# BMAD Development Status Report

Generated: [Current Date & Time]

## Planning Phase

- [✅/⏳] Project Brief: [exists/not found]
- [✅/⏳] PRD: [exists/not found]
- [✅/⏳] Architecture: [exists/not found]
- [✅/⏳] Epics: [X files found/not sharded yet]

## Development Phase

### Overall Progress

📊 Total Stories: X

- ✅ Completed: X (XX%)
- 🔄 In Progress: X
- 📝 Ready for Review: X
- 📋 Draft: X

### Task Completion

📝 Total Tasks: X

- ✅ Completed: X (XX%)
- ⏳ Remaining: X

### Current Focus

🎯 Stories in Progress:

1. **[Story Title]**
   - File: docs/stories/story-XXX.md
   - Progress: X/Y tasks completed
   - Last Updated: [date]

2. **[Another Story]**
   - File: docs/stories/story-YYY.md
   - Progress: X/Y tasks completed
   - Last Updated: [date]

### Next Up

📌 Draft Stories Ready to Start:

- [List story titles with Status: Draft]

### Blockers (if any)

⚠️ Issues Requiring Attention:

- [Story]: [blocker description]

## Recommended Next Steps

[Based on current state, suggest what to do next]

- If no PRD: "Start by activating PM agent and creating PRD"
- If PRD exists but no epics: "Activate PO agent and shard PRD into epics"
- If stories exist but none in progress: "Review draft stories and start implementation"
- If stories in progress: "Continue working on [story name]"
- If all completed: "Celebrate! 🎉 Or create new epics for next features"
```

### 5. Interactive Options

After presenting the status, offer these options:

```
What would you like to do next?

1. 📖 View details of a specific story
2. 🚀 Continue working on current story
3. ✨ Start a new story
4. 📊 Generate detailed progress report
5. 🔄 Refresh status
6. ❌ Exit
```

## Usage Examples

### From Any Agent

```
User: "*development-status"
Agent: [Runs this task and displays the report]
```

### Quick Check

```
User: "What's our development progress?"
Agent: [Recognizes intent, runs development-status task]
```

### Before Planning Next Sprint

```
User: "Show me development status before we plan next sprint"
Agent: [Displays comprehensive status]
```

## Notes

- This task is read-only and does not modify any files
- File timestamps come from the file system, not file contents
- Story status is read from the "Status:" line in each story file
- Task completion is determined by `- [x]` vs `- [ ]` checkboxes
- If docs/ directory doesn't exist, report "Project not initialized with BMAD structure"

## Dependencies

This task requires access to:

- Project file system
- Ability to read markdown files
- Ability to parse markdown checkboxes and YAML front matter

## Related Tasks

- `create-next-story.md` - To start working on draft stories
- `review-story.md` - To review completed stories
- `correct-course.md` - If project needs course correction based on status
