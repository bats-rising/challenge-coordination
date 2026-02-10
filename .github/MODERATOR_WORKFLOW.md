# Moderator Workflow Guide

This guide outlines the daily workflow, responsibilities, and procedures for challenge coordinators moderating the Control Repository.

---

## 🎯 Moderator Responsibilities

As a challenge coordinator, you are responsible for:

✅ **Monitoring** all issues (help requests, questions, infrastructure bugs)  
✅ **Validating** quality-help labels and collaboration points  
✅ **Responding** to questions and infrastructure bugs  
✅ **Escalating** complex technical issues to specialist agents  
✅ **Tracking** team progress and identifying blockers  
✅ **Ensuring** fair play and equal opportunities  
✅ **Maintaining** repository health and organization  

---

## ⏰ Daily Review Schedule

### Morning Review (9:00 - 9:30)

**Objectives:**
- Review overnight activity
- Respond to pending questions
- Check for critical blockers

**Tasks:**
1. [ ] Review all open issues from previous day
2. [ ] Respond to any questions opened overnight
3. [ ] Check for infrastructure bug reports
4. [ ] Identify teams with no recent activity (potential blockers)
5. [ ] Update daily challenge announcement (if applicable)

### Midday Review (12:00 - 12:30)

**Objectives:**
- Mid-day progress check
- Answer accumulated questions
- Validate morning collaboration

**Tasks:**
1. [ ] Review new issues since morning
2. [ ] Respond to all open `question` issues
3. [ ] Check help request response times
4. [ ] Identify patterns in common problems
5. [ ] Update documentation if needed
6. [ ] Post midday progress summary

### Evening Review (18:00 - 18:30)

**Objectives:**
- End-of-day summary
- Quality-help validation
- Planning for next day

**Tasks:**
1. [ ] Review all day's activity
2. [ ] Validate `quality-help` labels on closed issues
3. [ ] Calculate and record collaboration points
4. [ ] Check for unresolved critical issues
5. [ ] Post daily summary report
6. [ ] Prepare next day's challenge tasks

### End-of-Day Wrap-up (21:00 - 21:15)

**Objectives:**
- Final check
- Prepare for next morning

**Tasks:**
1. [ ] Quick scan of late issues
2. [ ] Flag any critical overnight issues
3. [ ] Archive resolved issues to project board

---

## 📊 Collaboration Points System

### Point Ranges per Help Type

**Base Points:**
- Text guidance/hints: **15 points**
- Code examples with explanation: **20 points**

**Bonuses:**
- Quick response (<30 minutes): **+10 points**
- Quality help (validated): **+5 points**

**Maximum:** 35 points per help request (20 + 10 + 5)

### Calculating Points

For each **closed help request**:

1. **Identify the helping team(s)**
   - Check who provided the solution
   - Only the team that solved the problem gets points
   - If multiple teams helped, coordinator decides split

2. **Determine base points**
   - Text only: 15 pts
   - Code examples: 20 pts

3. **Check response time**
   - Open timestamp → First helpful comment timestamp
   - If <30 min: +10 pts

4. **Validate quality-help label**
   - Review if help was exceptional
   - Check teaching quality, explanation depth
   - If valid: +5 pts
   - If invalid: remove label, no bonus

5. **Record in tracking sheet**
   - Team name
   - Issue number
   - Points awarded
   - Date/time

---

## ✅ Quality-Help Validation Process

### What Qualifies as Quality Help?

**Yes - Award Bonus:**
- ✅ Explained concepts clearly (teaching-focused)
- ✅ Included code examples with explanations of why they work
- ✅ Asked guiding questions instead of just providing answers
- ✅ Connected to real-world radar applications
- ✅ Went beyond basic troubleshooting
- ✅ Helped team understand, not just fixed their code

**No - Remove Label:**
- ❌ Simple one-line answer
- ❌ Copy-pasted code without explanation
- ❌ Just pointed to documentation
- ❌ Minimal effort response
- ❌ Didn't actually solve the problem

### Validation Steps

1. **Read the entire issue thread**
2. **Evaluate the helping team's response** against quality criteria
3. **Check if the solution actually worked** (issue closed successfully)
4. **Make decision:**
   - Valid: Add comment confirming +5 bonus points
   - Invalid: Remove label, add comment explaining why
5. **Update points tracking sheet**

---

## 🚨 Escalation Procedures

### When to Escalate

Escalate issues to specialist agents when:
- Team blocked for **>2 hours** on technical problem
- Help requests have no responses after **1 hour**
- Complex technical questions beyond your expertise
- Infrastructure bugs require deep technical investigation

### Escalation Paths

#### Technical Issues

**Radar Processing Problems:**
```
@Radar Expert [Link to issue]
Team needs help with [Kalman filtering / tracking / signal processing]
Blocked for [duration], already tried [what they tried]
```

**ROS2/MCAP Issues:**
```
@ROS2 Integration Specialist [Link to issue]
Team struggling with [MCAP parsing / message deserialization]
Blocked for [duration], error: [error message]
```

**Python/Tooling Issues:**
```
@Python CLI Mentor [Link to issue]
Team has problems with [UV / Click / Python tooling]
Blocked for [duration], environment: [OS/versions]
```

#### When Specialist Responds

1. **Synthesize** their technical guidance into student-friendly language
2. **Post** in the original issue with actionable steps
3. **Follow up** within 30 minutes to check if unblocked
4. **Document** the solution for future reference

---

## 📋 Daily Summary Report Template

Post at 18:00 in team communication channel:

```markdown
## 📊 Daily Summary - Day [X] - [Date]

### 🎯 Progress Overview
- **Help Requests:** [X] opened, [Y] resolved, [Z] open
- **Questions:** [X] answered
- **Infrastructure Bugs:** [X] reported, [Y] fixed

### 🏆 Top Collaborators Today
1. **Team [Name]:** [X] points - [brief description of help]
2. **Team [Name]:** [X] points - [brief description of help]
3. **Team [Name]:** [X] points - [brief description of help]

### 🔥 Hot Topics
- [Most common issue type]
- [Frequently asked questions]
- [Common blockers]

### ⚠️ Teams Needing Attention
- **Team [Name]:** [Status/blocker]
- **Team [Name]:** [Status/blocker]

### ✅ Wins Today
- [Positive development]
- [Team breakthrough]
- [Resolved complex issue]

### 📌 Reminders for Tomorrow
- [Day X+1 milestone]
- [Important deadline]
- [Scheduled event]

---
**Next Review:** Tomorrow at 12:00
```

---

## 🛡️ Fair Play Enforcement

### Monitoring for Issues

**Watch for:**
- Teams copying complete solutions
- Spam or duplicate issues
- Abuse of quality-help label
- Unfair point gaming
- Non-participants creating issues

### Response Procedures

#### Code Copying
1. **Evidence:** Check if solution was copy-pasted without understanding
2. **Action:** Comment on issue, warn both teams
3. **Penalty:** No collaboration points awarded
4. **Severe:** Report to instructors for academic integrity review

#### Spam / Duplicates
1. **Identify:** Same issue posted multiple times
2. **Action:** Close duplicates, leave one open
3. **Comment:** "Closing as duplicate of #[number]"

#### Quality-Help Abuse
1. **Review:** Validate all quality-help labels
2. **Action:** Remove invalid labels
3. **Comment:** Explain why not qualified for bonus

#### Non-Participant Issues
1. **Verify:** Check if user is enrolled in challenge
2. **Action:** Comment asking for team affiliation
3. **If unaffiliated:** Close with "Issues limited to challenge participants"

---

## 📈 Metrics to Track

### Issue Metrics
- Total issues by type (help, question, bug)
- Average resolution time
- Response time distribution
- Issues per team

### Collaboration Metrics
- Total points by team
- Most helpful teams
- Quality-help validation rate
- Common help topics

### Challenge Health Metrics
- Teams with no activity (potential dropouts)
- Critical blockers >2 hours
- Infrastructure bug frequency
- Documentation gaps (questions about same topic)

### Export Weekly
- Use GitHub's issue export feature
- Import to spreadsheet for analysis
- Generate graphs for final presentation
- Identify improvement areas for next challenge

---

## 📝 Moderator Checklist

### Daily Tasks
- [ ] Morning review (9:00)
- [ ] Midday review (12:00)
- [ ] Evening review (18:00)
- [ ] Post daily summary (18:00)
- [ ] End-of-day wrap-up (21:00)

### Per Issue Tasks
- [ ] Respond within SLA (questions: 6hr, bugs: 1hr)
- [ ] Add appropriate domain labels
- [ ] Escalate if blocked >2hr
- [ ] Validate quality-help on close

### Weekly Tasks
- [ ] Archive resolved issues
- [ ] Export metrics
- [ ] Review common patterns
- [ ] Update documentation
- [ ] Team progress report

### Challenge-End Tasks
- [ ] Final points calculation
- [ ] Publish leaderboard
- [ ] Conduct retrospective
- [ ] Archive repository
- [ ] Document lessons learned

---

## 🤝 Moderator Team Coordination

### If Multiple Moderators

**Assign roles:**
- **Lead Moderator:** Overall coordination, final decisions
- **Technical Moderator:** Escalations, specialist coordination
- **Points Moderator:** Collaboration scoring, validation

**Communication:**
- Use private moderator channel
- Tag handoffs between review times
- Share decision-making on edge cases

**Handoff Template:**
```markdown
## Handoff [Time]

**Active Issues:**
- #[number]: [Status, needs attention by X time]
- #[number]: [Status, escalated to specialist]

**Pending Validations:**
- #[number]: quality-help label to review

**Heads Up:**
- Team [Name] blocked on [issue]
- [Other important context]
```

---

## 📞 Emergency Contacts

**Critical Infrastructure Failure:**
- Contact: [System admin]
- Escalation: [Backup contact]

**Academic Integrity Issues:**
- Contact: [Course instructor]
- Process: [Academic policy link]

**Student Welfare Concerns:**
- Contact: [Student services]
- Emergency: [University helpline]

---

## ✅ Summary

**Time Commitment:** ~2 hours/day  
**Peak Activity:** Challenge hours (9:00 - 21:00)  
**Critical Times:** 12:00 and 18:00 reviews  

**Success Metrics:**
- All questions answered within 6 hours
- All infrastructure bugs addressed within 1 hour
- No team blocked >2 hours
- Fair and transparent collaboration scoring

---

For questions about moderator workflow, contact the challenge lead coordinator.
