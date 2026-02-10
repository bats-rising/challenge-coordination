# Control Repository Setup - Quick Start Guide

This repository is now configured as the **Control Repository** for the Capture the Drone challenge. Follow these steps to complete the setup.

---

## ✅ What's Already Done

All the following files and documentation have been created in this repository:

### 📄 Main Documentation
- ✅ `README.md` - Comprehensive guide for teams and coordinators
- ✅ `.github/MODERATOR_WORKFLOW.md` - Daily workflow and procedures for moderators
- ✅ `.github/PROJECT_BOARD_SETUP.md` - Optional project board setup guide
- ✅ `.github/labels.yml` - Label configuration for the repository

### 📝 Issue Templates
- ✅ `.github/ISSUE_TEMPLATE/help-request.md` - For technical help requests
- ✅ `.github/ISSUE_TEMPLATE/question.md` - For rule/scope clarifications
- ✅ `.github/ISSUE_TEMPLATE/infrastructure-bug.md` - For infrastructure bugs
- ✅ `.github/ISSUE_TEMPLATE/read-first.md` - Guide for using the repository

---

## 🔧 Manual Steps Required

Complete these steps in the GitHub repository settings:

### 1️⃣ Repository Settings

**Repository Name** (if needed):
- Navigate to: Settings → General
- Rename repository to: `capture-the-drone-control` (or keep current name)
- Update description to: *"Central helpdesk, scoring, and coordination hub for the Capture the Drone challenge."*

**Visibility:**
- Navigate to: Settings → General → Danger Zone
- Make repository **public** (if not already)

**Features:**
- Navigate to: Settings → General → Features
- ✅ Enable **Issues**
- ✅ (Optional) Enable **Discussions**
- ✅ (Optional) Enable **Projects**

### 2️⃣ Create Labels

You can create labels either manually or using automation:

**Option A: Manual Creation** (via GitHub UI)
1. Go to: Issues → Labels
2. Click "New label" for each label in `.github/labels.yml`
3. Copy name, color code, and description from the file

**Option B: Automated Creation** (using github-label-sync)
```bash
# Install github-label-sync (requires Node.js)
npm install -g github-label-sync

# Sync labels from labels.yml
github-label-sync --access-token YOUR_TOKEN bats-rising/capture-the-drone-control --labels .github/labels.yml
```

**Required Labels:**

| Name | Color | Description |
|------|-------|-------------|
| `help-request` | `0E8A16` (green) | Request for technical help from other teams |
| `question` | `D876E3` (purple) | Question about challenge rules, scope, or clarification |
| `infra-bug` | `D93F0B` (red) | Bug in challenge infrastructure, inventory, or provided datasets |
| `quality-help` | `FBCA04` (yellow) | Exceptional help deserving bonus collaboration points |
| `radar` | `1D76DB` (blue) | Radar signal processing, tracking algorithms |
| `ros2` | `5319E7` (purple) | ROS2 integration, MCAP parsing |
| `python` | `0052CC` (dark blue) | Python tooling, UV, Click CLI |
| `evaluation` | `C5DEF5` (light blue) | Scoring, metrics, autograding |
| `inventory` | `BFD4F2` (light blue) | Central datasets or resources |

### 3️⃣ Pin the "READ FIRST" Issue

1. Create a new issue using the "READ FIRST" template:
   - Title: `📌 READ FIRST – How to Use This Repository`
   - Copy content from `.github/ISSUE_TEMPLATE/read-first.md`
   - Remove the YAML frontmatter (lines 1-7)
   - Post the issue

2. Pin the issue:
   - Open the newly created issue
   - Click the pin icon in the top right corner
   - Issue will appear at the top of the Issues list

### 4️⃣ Update README Links

Edit `README.md` to add actual links:

**Replace these placeholder sections:**
```markdown
- **Challenge GitHub Classroom Assignment**: [Link to be added]
- **Setup GitHub Classroom Assignment**: [Link to be added]
```

**With actual URLs:**
```markdown
- **Challenge GitHub Classroom Assignment**: https://classroom.github.com/a/YOUR_ASSIGNMENT_ID
- **Setup GitHub Classroom Assignment**: https://classroom.github.com/a/YOUR_SETUP_ID
```

### 5️⃣ (Optional) Create Project Board

Follow the guide in `.github/PROJECT_BOARD_SETUP.md` to:
1. Create a new GitHub Project
2. Configure columns (Open, In Progress, Resolved)
3. Set up automation rules
4. Create custom views for filtering

### 6️⃣ Share with Teams

Once setup is complete:
1. **Announce** the Control Repository in your team communication channel
2. **Include** the repository link in challenge kickoff materials
3. **Add** the link to GitHub Classroom assignment READMEs
4. **Pin** the repository URL in team chat for easy access

---

## 📋 Pre-Challenge Checklist

Before the challenge starts, verify:

- [ ] Repository is public and visible
- [ ] Issues are enabled
- [ ] All labels are created
- [ ] "READ FIRST" issue is pinned
- [ ] README links are updated with actual URLs
- [ ] Issue templates are working (test by creating a sample issue)
- [ ] Moderators have reviewed the workflow documentation
- [ ] Collaboration points system is understood
- [ ] Escalation paths are confirmed
- [ ] (Optional) Project board is configured

---

## 👥 Moderator Preparation

Moderators should:

1. **Read** `.github/MODERATOR_WORKFLOW.md` completely
2. **Understand** the collaboration points system
3. **Set up** daily review schedule (9:00, 12:00, 18:00, 21:00)
4. **Prepare** a points tracking spreadsheet or tool
5. **Test** issue templates by creating sample issues
6. **Bookmark** specialist agent contacts for escalations

---

## 🎯 First Day Actions

On Day 1 of the challenge:

1. **Post welcome message** in the Control Repository
2. **Remind teams** about the "READ FIRST" pinned issue
3. **Monitor** for initial setup questions
4. **Be available** for infrastructure bug reports
5. **Encourage** teams to help each other early

---

## 📊 Testing the Setup

Create test issues to verify everything works:

1. **Test Help Request:**
   - Click "New issue"
   - Select "Help Request" template
   - Verify all fields appear correctly
   - Close without submitting

2. **Test Labels:**
   - Create a draft issue
   - Try applying each label
   - Verify colors and descriptions

3. **Test Project Board** (if configured):
   - Create a test issue with `help-request` label
   - Verify it appears in "Open" column
   - Close the issue and verify it moves to "Resolved"

---

## 🔗 Important Files Reference

| File | Purpose |
|------|---------|
| `README.md` | Main guide for all teams |
| `.github/MODERATOR_WORKFLOW.md` | Daily moderator procedures |
| `.github/PROJECT_BOARD_SETUP.md` | Project board configuration |
| `.github/labels.yml` | Label definitions |
| `.github/ISSUE_TEMPLATE/help-request.md` | Technical help template |
| `.github/ISSUE_TEMPLATE/question.md` | Clarification template |
| `.github/ISSUE_TEMPLATE/infrastructure-bug.md` | Infrastructure bug template |
| `.github/ISSUE_TEMPLATE/read-first.md` | Usage guide (to be pinned) |

---

## ❓ Questions?

If you have questions about the setup:
1. Review the documentation files
2. Check the MODERATOR_WORKFLOW.md for detailed procedures
3. Refer to the original issue requirements

---

## ✅ Definition of Done

The Control Repository is ready when:

✅ Repository is public and discoverable  
✅ Issue templates enforce proper structure  
✅ All labels are created and documented  
✅ "READ FIRST" issue is pinned  
✅ README links to GitHub Classroom assignments  
✅ Moderators understand workflow and point system  
✅ All challenge communication routes through this repo  
✅ Classroom repos stay code-only  
✅ Collaboration scoring is feasible and transparent  

---

**Next Steps:**
1. Complete manual setup steps above
2. Test all functionality
3. Announce to teams
4. Begin Day 1 of challenge!

---

Good luck with the Capture the Drone challenge! 🎯📡
