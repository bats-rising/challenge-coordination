# GitHub Project Board Setup Guide

This guide explains how to set up and use a GitHub Project Board for managing help requests and tracking challenge progress.

---

## 🎯 Purpose

The **Help Requests** project board provides:
- Visual overview of all open help requests
- Quick identification of unresolved issues
- Progress tracking across the challenge
- Moderation workflow support

---

## 📋 Creating the Project Board

### Step 1: Create the Project

1. Go to the **Projects** tab in the Control Repository
2. Click **New project**
3. Select **Board** view
4. Name it: **"Help Requests Tracker"**
5. Description: *"Track and manage help requests, questions, and infrastructure bugs during the challenge"*

### Step 2: Configure Columns

Create three columns with the following settings:

#### Column 1: 📥 Open
- **Automation:** Add newly created issues with label `help-request`, `question`, or `infra-bug`
- **Purpose:** All new issues start here

#### Column 2: 🔄 In Progress
- **Automation:** Move here when issue is assigned or has comments
- **Purpose:** Issues being actively worked on (teams responding)

#### Column 3: ✅ Resolved
- **Automation:** Move here when issue is closed
- **Purpose:** Completed help requests and resolved issues

---

## 🔧 Automation Rules

### Auto-add New Issues
```
When: Issue is opened
If: Has label `help-request` OR `question` OR `infra-bug`
Then: Add to "Open" column
```

### Auto-move to In Progress
```
When: Issue receives a comment from someone other than the issue author
Then: Move to "In Progress" column
```

### Auto-move to Resolved
```
When: Issue is closed
Then: Move to "Resolved" column
```

---

## 📊 Using the Board

### For Coordinators

**Daily Review (12:00 and 18:00):**
1. Check **Open** column for new issues
2. Verify **In Progress** issues are receiving responses
3. Review **Resolved** column for `quality-help` validation

**Weekly Archive:**
- Archive **Resolved** column at the end of each challenge day
- Keeps board focused on active issues

### For Teams

**Finding Help Opportunities:**
1. Browse the **Open** column for unanswered help requests
2. Check domain labels to find questions matching your expertise
3. Respond quickly (<30 min) for bonus points

**Tracking Your Requests:**
- See where your help requests are in the pipeline
- Monitor when teams start responding (moves to In Progress)

---

## 🏷️ Custom Views

Create filtered views for specific needs:

### View: Urgent Help Requests
- **Filter:** Label = `help-request` AND title contains `[URGENT]`
- **Sort:** Created date (oldest first)
- **Purpose:** Identify teams blocked for >2 hours

### View: Infrastructure Bugs
- **Filter:** Label = `infra-bug` AND state = open
- **Sort:** Priority (custom field)
- **Purpose:** Track high-priority infrastructure issues

### View: Quality Help Candidates
- **Filter:** Label = `quality-help` AND state = closed
- **Sort:** Closed date (newest first)
- **Purpose:** Validate quality-help claims for bonus points

---

## 📈 Metrics to Track

Use the project board to monitor:

### Daily Metrics
- **Open issues:** Should trend down throughout the day
- **Average time to first response:** Target <30 minutes
- **Issues closed:** Indicates progress and successful collaboration

### Weekly Metrics
- **Total help requests:** Gauge overall challenge difficulty
- **Most common domains:** Identify areas needing more documentation
- **Teams most active in helping:** Recognize top collaborators

---

## 🔄 Alternative: GitHub Projects (Beta)

For more advanced features, consider **GitHub Projects (Beta)**:

### Additional Features
- Custom fields (priority, estimated difficulty, etc.)
- Multiple views (table, board, timeline)
- Advanced filtering and grouping
- Iteration planning

### Recommended Custom Fields
1. **Priority:** Low, Medium, High, Critical
2. **Domain:** Radar, ROS2, Python, Evaluation, Inventory
3. **Response Time:** <30min, <1hr, <2hr, >2hr
4. **Collaboration Points:** Calculated value

### Sample Table View
| Issue | Team | Domain | Priority | Response Time | Status | Points |
|-------|------|--------|----------|---------------|--------|--------|
| Help: Kalman filter diverging | Team Alpha | Radar | High | 15min | Resolved | 30 |
| Question: Evaluation deadline | Team Beta | Evaluation | Low | 2hr | Open | 0 |

---

## 🎓 Best Practices

### For Coordinators

**Do:**
- Review board at scheduled times (12:00, 18:00)
- Archive resolved issues regularly
- Use custom views for focused reviews
- Track metrics for challenge improvements

**Don't:**
- Manually move cards (let automation work)
- Archive issues before validating `quality-help`
- Ignore issues stuck in "Open" for >1 hour

### For Teams

**Do:**
- Check board for help opportunities
- Monitor your own issue progress
- Close issues promptly when resolved

**Don't:**
- Move cards manually
- Spam the board with duplicate issues
- Leave resolved issues open

---

## 🔗 Integration with Labels

The project board works best when combined with proper labeling:

**Essential Labels for Board Automation:**
- `help-request`
- `question`
- `infra-bug`
- `quality-help`

**Domain Labels for Filtering:**
- `radar`
- `ros2`
- `python`
- `evaluation`
- `inventory`

---

## 📝 Summary

**Setup Time:** ~15 minutes  
**Maintenance:** 5 minutes per review session  
**Benefits:**
- ✅ Visual progress tracking
- ✅ Quick identification of blocked teams
- ✅ Automated workflow management
- ✅ Metrics for challenge improvement

**Next Steps:**
1. Create the project board in GitHub
2. Set up automation rules
3. Configure custom views
4. Share board link with all teams
5. Include board in daily standup reviews

---

For questions about project board setup, contact the challenge coordinators.
