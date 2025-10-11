# Development Status Usage Guide

## 📊 BMAD Now Has Development Status Viewing!

### Method 1: Using BMad Master Agent (Recommended)

```
# In Claude Code
/bmad-master

BMad Master: "I am BMad Master, I can execute any BMad task"

# View development status
*development-status

# Or simply say
"Show development status"
"What's the development progress?"
"Where are we at?"
```

### Method 2: Using Any Agent + task Command

```
# Any agent works
/dev
*task development-status

# Or
/pm
*task development-status
```

## 📋 Output Example

After running `*development-status`, you will see:

```markdown
# BMAD Development Status Report

Generated: 2024-01-15 14:30:00

## Planning Phase

- ✅ Project Brief: docs/project-brief.md
- ✅ PRD: docs/prd.md
- ✅ Architecture: docs/architecture.md
- ✅ Epics: 3 files found

## Development Phase

### Overall Progress

📊 Total Stories: 8

- ✅ Completed: 2 (25%)
- 🔄 In Progress: 1
- 📝 Ready for Review: 0
- 📋 Draft: 5

### Task Completion

📝 Total Tasks: 45

- ✅ Completed: 12 (27%)
- ⏳ Remaining: 33

### Current Focus

🎯 Stories in Progress:

1. **User Registration Feature**
   - File: docs/stories/story-003.md
   - Progress: 3/7 tasks completed
   - Last Updated: 2024-01-15

### Next Up

📌 Draft Stories Ready to Start:

- Story 004: User Login
- Story 005: Password Reset
- Story 006: Create Task
- Story 007: Edit Task
- Story 008: Delete Task

### Blockers

⚠️ No blockers detected

## Recommended Next Steps

Continue working on story-003 (User Registration).
3 out of 7 tasks remaining.

---

What would you like to do next?

1. 📖 View details of a specific story
2. 🚀 Continue working on current story
3. ✨ Start a new story
4. 📊 Generate detailed progress report
5. 🔄 Refresh status
6. ❌ Exit
```

## 🎯 Common Use Cases

### Scenario 1: Starting Your Day

```bash
# Open project
cd /path/to/your/project

# In Claude Code
/bmad-master
*development-status

# See output:
# "You were on story-003 yesterday, completed 3/7 tasks"
# "Recommend continuing story-003"

# Decide to continue
/dev
"Continue implementing story-003"
```

### Scenario 2: Team Progress Reporting

```bash
/bmad-master
*development-status

# Copy the output
# Send to Slack/Email:
"Project Progress Update:
- Total: 8 stories
- Completed: 2 (25%)
- In Progress: 1
- This week's goal: Complete story-003 and story-004"
```

### Scenario 3: Resuming After Project Pause

```bash
# Returning to project after a week
/bmad-master
*development-status

# Output shows:
# "Last work: story-003, progress 3/7"
# "Completed: story-001, story-002"

# Quickly restore context
/dev
"Open story-003, continue from task 4"
```

### Scenario 4: Checking Sprint Readiness

```bash
/bmad-master
*development-status

# Output shows:
# "Epic 1: 5 stories, all completed ✅"
# "Epic 2: 3 stories, 2 drafts 📋"

"Good, Epic 1 is done, starting Epic 2"
/sm
"Create next story from Epic 2"
```

## 🔧 Advanced Usage

### Combining with Other Tools

```bash
# 1. Check status
/bmad-master
*development-status

# 2. Discover slow progress, analyze why
*task correct-course

# 3. Decide to adjust plan
/pm
"Based on current progress, we need to adjust Sprint scope"

# 4. Check status again
*development-status
```

### Creating Custom Dashboard

```bash
# Create script for periodic status checks
cat > check-daily-status.sh << 'EOF'
#!/bin/bash
echo "===== Daily Status Report ====="
date

# Use grep for quick statistics
echo ""
echo "Stories by Status:"
grep -h "Status:" docs/stories/*.md | sort | uniq -c

echo ""
echo "Task Completion:"
total_tasks=$(grep -h "^- \[" docs/stories/*.md | wc -l)
done_tasks=$(grep -h "^- \[x\]" docs/stories/*.md | wc -l)
echo "Done: $done_tasks / $total_tasks"

echo ""
echo "Files Changed Today:"
find docs/stories -type f -mtime -1 -name "*.md"

echo ""
echo "===== End Report ====="
EOF

chmod +x check-daily-status.sh

# Run daily
./check-daily-status.sh
```

## 💡 Tips and Tricks

### 1. Regular Checks

```bash
# Every morning
*development-status

# After completing each story
*development-status

# Every Friday for weekly summary
*development-status
```

### 2. Combine with Git

```bash
# Check status
*development-status

# Commit progress
git add docs/stories/story-003.md
git commit -m "progress: story-003 at 3/7 tasks"

# Push
git push
```

### 3. Troubleshooting

**Issue**: Status displays incorrectly

```bash
# Check file format
cat docs/stories/story-003.md | grep "Status:"

# Should be:
Status: In Progress

# Not:
status: in progress  ← lowercase doesn't work
Status:In Progress   ← no space doesn't work
```

**Issue**: Task count errors

```bash
# Check checkbox format
cat docs/stories/story-003.md | grep "^\- \["

# Correct format:
- [ ] Task description
- [x] Completed task

# Incorrect format:
-[ ] No space
- [] Missing x or space
```

## 📚 Related Resources

- **Task File**: `bmad-core/tasks/development-status.md`
- **Agent Configuration**: `bmad-core/agents/bmad-master.md`
- **User Guide**: `docs/user-guide.md`

## 🎉 Summary

**BMAD has 2 ways to view development status:**

1. ✅ **Built-in Task**: `*development-status` (New!)
2. ✅ **Manual Scripts**: Write your own bash scripts

**Recommended: Use built-in task** because:

- No extra installation required
- Works in any agent
- Consistent output format
- Provides smart recommendations

Get started:

```bash
/bmad-master
*help
# See command list, including development-status
*development-status
# View current development status
```
