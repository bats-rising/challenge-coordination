# GitHub Classroom Integration for Capture the Drone Challenge

<!-- Version: 1.0.0 -->
<!-- Last Updated: 2026-02-09 -->
<!-- Purpose: Guide for migrating the 4-day radar tracking hackathon to GitHub Classroom -->

## Overview

GitHub Classroom is an educational platform that integrates with GitHub to streamline the distribution, management, and evaluation of programming assignments. This document provides comprehensive knowledge for adapting the "Capture the Drone" 4-day hackathon to GitHub Classroom.

## Why GitHub Classroom?

**Benefits for Educational Challenges:**
- **Automated Repository Setup:** Create individual or team repositories from template automatically
- **Roster Management:** Import students from LMS or CSV, manage team formation
- **Autograding:** Run automated tests on student submissions
- **Deadline Enforcement:** Set due dates with optional late submissions
- **Progress Tracking:** Dashboard showing student/team progress and submission status
- **Feedback Integration:** Automated feedback via GitHub Actions
- **Scalability:** Handle multiple cohorts and teams efficiently

**Perfect for Hackathons:**
- Supports team assignments (3-5 students per team)
- Real-time progress monitoring across all teams
- Automated starter code distribution
- Integrated with GitHub Actions for CI/CD
- Built-in deadline management

## Key Concepts

### 1. **Organizations**
- GitHub Classroom requires a GitHub Organization
- One organization can host multiple classrooms
- Organization name: `bats-rising-challenge` (already exists)

### 2. **Classrooms**
- Container for assignments within an organization
- Typically one per course/cohort
- Example: "Capture the Drone - Spring 2026"

### 3. **Assignments**
Two types:
- **Individual Assignments:** Each student gets their own repository
- **Group Assignments:** Teams share a repository (ideal for this hackathon)

### 4. **Rosters**
- Import students via LMS (Canvas, Moodle, etc.) or CSV upload
- Students authenticate with GitHub and select their name from roster
- Prevents duplicate accounts and anonymous participation

### 5. **Template Repository**
- Source code students/teams start with
- This repository (`capture-the-drone`) becomes the template
- Students get a copy with all starter code, tests, and scaffolding

### 6. **Autograding**
- Run automated tests on push/PR via GitHub Actions
- Supports multiple test types: unit tests, I/O tests, command-line tests
- Provides instant feedback to students
- Generates grade reports

## Migration Strategy for "Capture the Drone"

### Phase 1: Organization & Classroom Setup

**1. Verify Organization Access**
- Ensure organization `bats-rising-challenge` exists
- Confirm admin access for instructors
- Add teaching assistants as organization owners/members

**2. Create Classroom**
```
Name: Capture the Drone - [Semester/Year]
Organization: bats-rising-challenge
```

**3. Import Student Roster**
- Prepare CSV with columns: `identifier`, `name`, `email`
- Or connect to institutional LMS (Canvas, Moodle, Blackboard)
- Example CSV:
  ```csv
  identifier,name,email
  student1,Alice Johnson,alice@university.edu
  student2,Bob Smith,bob@university.edu
  ```

### Phase 2: Template Repository Configuration

**Current Repository:** `bats-rising-challenge/capture-the-drone`

**Required Changes:**
1. **Mark as Template:**
   - Settings → Template repository ✓
   - This allows GitHub Classroom to create copies

2. **Clean Up for Students:**
   - Remove instructor-only files (evaluation scripts, answer keys, hidden test data)
   - Keep training data, starter code, documentation
   - Add `.github/classroom/autograding.json` for automated grading

3. **Protect Sensitive Content:**
   - Move evaluation datasets to separate private repository
   - Use GitHub Actions secrets for API keys, evaluation endpoints
   - Ensure ground truth data is not in template

4. **Starter Code Structure:**
   ```
   capture-the-drone/
   ├── .github/
   │   ├── classroom/
   │   │   └── autograding.json          # Autograding configuration
   │   └── workflows/
   │       ├── classroom.yml             # GitHub Classroom autograding workflow
   │       └── tests.yml                 # Student-facing CI tests
   ├── capture_the_drone/
   │   ├── __init__.py
   │   ├── cli.py                        # CLI scaffolding
   │   ├── tracking/
   │   │   ├── __init__.py
   │   │   └── kalman_filter.py         # Starter template (TODO markers)
   │   └── utils/
   │       └── mcap_parser.py            # Utility scaffolding
   ├── tests/
   │   ├── test_kalman_filter.py        # Unit tests (some pre-written)
   │   └── test_mcap_parser.py
   ├── data/
   │   └── training/                     # Training datasets (public)
   ├── docs/
   │   ├── CHALLENGE_OVERVIEW.md
   │   ├── QUICK_START.md
   │   └── setup/
   ├── pyproject.toml
   └── README.md
   ```

### Phase 3: Group Assignment Creation

**Assignment Configuration:**

```
Assignment Name: Capture the Drone - 4-Day Hackathon
Type: Group Assignment
Max Team Size: 5
Min Team Size: 3
Template Repository: bats-rising-challenge/capture-the-drone
Deadline: [4 days from start] at 18:00
Allow Late Submissions: No (or with penalty)
Grant Students Admin Access: No (prevent destructive changes)
Enable Feedback Pull Request: Yes (creates PR for instructor feedback)
```

**Team Formation Options:**
1. **Manual Assignment:** Instructor creates teams, assigns students
2. **Student Self-Selection:** Students create/join teams via assignment link
3. **Hybrid:** Instructor seeds teams, students join available slots

**Recommendation for Hackathon:** Student self-selection with instructor oversight
- Share assignment invitation link at kickoff
- Students form teams during Day 1 setup
- Instructor can rebalance teams if needed

### Phase 4: Autograding Configuration

**File:** `.github/classroom/autograding.json`

**Milestone-Based Tests:**
- Day 1: Environment setup verification
- Day 2: Single-target tracking tests
- Day 3: Multi-target tracking tests
- Day 4: Full integration tests

**Example Configuration:**
```json
{
  "tests": [
    {
      "name": "Day 1: Environment Setup",
      "setup": "uv sync",
      "run": "pytest tests/test_setup.py -v",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 5,
      "points": 20
    },
    {
      "name": "Day 2: MCAP Parsing",
      "setup": "uv sync",
      "run": "pytest tests/test_mcap_parser.py -v",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 10,
      "points": 30
    },
    {
      "name": "Day 2: Single-Target Tracking",
      "setup": "uv sync",
      "run": "pytest tests/test_single_target.py -v",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 20,
      "points": 50
    },
    {
      "name": "Day 3: Data Association",
      "setup": "uv sync",
      "run": "pytest tests/test_data_association.py -v",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 20,
      "points": 50
    },
    {
      "name": "Day 3: Track Management",
      "setup": "uv sync",
      "run": "pytest tests/test_track_management.py -v",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 20,
      "points": 40
    },
    {
      "name": "Code Quality (Linting)",
      "setup": "uv sync",
      "run": "ruff check capture_the_drone/",
      "input": "",
      "output": "",
      "comparison": "included",
      "timeout": 5,
      "points": 10
    }
  ]
}
```

**GitHub Actions Workflow:** `.github/workflows/classroom.yml`
```yaml
name: GitHub Classroom Workflow

on:
  push:
    branches:
      - main
      - '**'
  pull_request:

jobs:
  build:
    name: Autograding
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.10'
      
      - name: Install UV
        run: curl -LsSf https://astral.sh/uv/install.sh | sh
      
      - name: Install Dependencies
        run: uv sync
      
      - name: Autograding
        uses: education/autograding@v1
        continue-on-error: true
      
      - name: Generate Feedback Report
        uses: education/autograding-grading-reporter@v1
        env:
          POINTS: ${{ steps.autograder.outputs.points }}
```

### Phase 5: Scoring System Adaptation

**Current Scoring (1000 points total):**
1. Tracking Performance (500 pts) - Manual evaluation on Day 4
2. Milestone Achievements (250 pts) - **Automate via GitHub Classroom**
3. Team Collaboration (150 pts) - Manual via help requests
4. Innovation Bonus (100 pts) - Manual assessment

**GitHub Classroom Integration:**

**Autograded Components (250 pts):**
- Milestone tests run automatically on push
- Instant feedback to students
- Points tracked in GitHub Classroom dashboard
- Export to CSV for final grade calculation

**Manual Components (750 pts):**
- **Tracking Performance (500 pts):** Run evaluation script on Day 4
  - Use GitHub API to fetch final repositories
  - Execute evaluation locally or via GitHub Actions
  - Publish results to Google Sheets/CSV

- **Collaboration (150 pts):** Track via GitHub Issues
  - Label help requests with `help-request`
  - Monitor issue closures and quality ratings
  - Calculate points using GitHub GraphQL API

- **Innovation (100 pts):** Review during presentations
  - Use rubric from CHALLENGE_OVERVIEW.md
  - Record scores in spreadsheet

**Final Grade Calculation:**
- Combine autograding JSON export + manual scores
- Python script to merge and rank teams
- Publish leaderboard to GitHub Pages

### Phase 6: Student Workflow

**Day 0: Pre-Hackathon Setup**
1. Instructor creates GitHub Classroom assignment
2. Shares assignment invitation link via email/LMS
3. Students accept assignment, authenticate with GitHub
4. Select name from roster (links GitHub account to student ID)

**Day 1: Team Formation & Setup**
1. Students create/join teams via Classroom interface
2. Team repository created automatically from template
3. Students clone repository: `gh repo clone bats-rising-challenge/capture-the-drone-team-alpha`
4. Run setup scripts, verify autograding passes Day 1 tests
5. First push triggers GitHub Actions → instant feedback

**Days 2-3: Development**
1. Students work in team repository
2. Commit frequently to main or feature branches
3. Autograding runs on every push (instant milestone feedback)
4. Use GitHub Issues for help requests (collaboration points)
5. Instructors monitor progress via Classroom dashboard

**Day 4: Final Submission**
1. Deadline enforcement: 18:00 (6 PM)
2. GitHub Classroom locks repositories after deadline (optional)
3. Instructor runs final evaluation script on all team repos
4. Combines autograding + manual scores
5. Publishes final leaderboard

### Phase 7: Instructor Dashboard

**GitHub Classroom Features:**
- **Assignment Dashboard:** List of all teams and repositories
- **Progress View:** See which teams have accepted assignment
- **Autograding Results:** Real-time pass/fail status for each test
- **Download Repositories:** Bulk export for offline evaluation
- **Roster Management:** Track GitHub account linkage

**Typical Workflow:**
1. Morning: Check dashboard for overnight progress
2. Identify teams with failing tests (red status)
3. Review recent commits for stuck teams
4. Provide targeted feedback via GitHub Issues or PR comments
5. Update Google Sheets with collaboration points (noon, 6 PM)
6. Post daily summary to GitHub Discussions

### Phase 8: Post-Hackathon Analysis

**Export Data:**
- Download autograding results as CSV
- Export repository statistics (commits, PRs, issues)
- Collect manual evaluation scores
- Survey student feedback (Google Forms linked in README)

**Continuous Improvement:**
- Review which milestones were too easy/hard (adjust autograding)
- Identify common failure points (improve starter code/docs)
- Analyze collaboration patterns (refine help request system)
- Update template repository for next cohort

## Technical Implementation Details

### Repository Access Control

**Template Repository (Source):**
- Private (before hackathon start)
- Public (during hackathon) - allows students to see starter code
- Contains training data, docs, scaffolding

**Student Team Repositories:**
- Private by default (prevents copying between teams)
- Team members have write access
- Instructors have admin access
- Organization members (TAs) can view all repos

### Handling Multiple Cohorts

**Classroom Per Cohort:**
- "Capture the Drone - Spring 2026"
- "Capture the Drone - Fall 2026"

**Template Versioning:**
- Tag releases: `v1.0-spring2026`, `v2.0-fall2026`
- Improve starter code between cohorts
- Maintain backward compatibility with older cohorts

### Preventing Cheating

**Code Similarity Detection:**
- Use GitHub Classroom's built-in plagiarism detection
- Or integrate MOSS (Measure of Software Similarity)
- Run after deadline, flag suspicious pairs

**Repository Privacy:**
- Keep student repos private
- Prevent public forks
- Disable forking in organization settings

**Late Submission Prevention:**
- Set hard deadline in Classroom
- Or use GitHub Actions to check commit timestamps
- Reject evaluation if commits after deadline

### Autograding Best Practices

**Test Design:**
- Start with simple smoke tests (imports work, CLI runs)
- Progress to functional tests (correct output format)
- End with performance tests (tracking accuracy)
- Use fixtures for consistent test data

**Timeout Management:**
- Set generous timeouts (students may have slower implementations)
- Balance between catching infinite loops and allowing complex algorithms

**Partial Credit:**
- Use pytest markers for different point values
- Run all tests even if some fail
- Sum points from passing tests

**Debugging Support:**
- Print helpful error messages
- Include test data in repository
- Allow students to run tests locally before pushing

## Migration Checklist

### Pre-Hackathon (2 weeks before)
- [ ] Set up GitHub Classroom for organization
- [ ] Create classroom: "Capture the Drone - [Semester]"
- [ ] Import student roster (CSV or LMS)
- [ ] Convert repository to template
- [ ] Remove evaluation datasets (move to private repo)
- [ ] Create autograding configuration (`.github/classroom/autograding.json`)
- [ ] Set up GitHub Actions workflow (`.github/workflows/classroom.yml`)
- [ ] Write milestone tests (Day 1, 2, 3 verification)
- [ ] Create group assignment in Classroom
- [ ] Test assignment flow with dummy student accounts
- [ ] Prepare invitation link for students

### Day 0 (Kickoff Preparation)
- [ ] Share assignment invitation link via email/LMS
- [ ] Post instructions in course portal
- [ ] Prepare kickoff slides (explain GitHub Classroom workflow)
- [ ] Set up monitoring dashboard (Classroom + Google Sheets)

### Day 1 (Hackathon Start)
- [ ] Monitor team formation (ensure all students join)
- [ ] Check repository creation (all teams should have repos)
- [ ] Verify Day 1 autograding runs successfully
- [ ] Respond to setup issues via help requests

### Days 2-4
- [ ] Daily dashboard check (morning and evening)
- [ ] Process help requests twice daily (noon, 6 PM)
- [ ] Update collaboration points in spreadsheet
- [ ] Monitor autograding status (identify struggling teams)
- [ ] Provide feedback via GitHub Issues/PRs

### Day 4 (Evaluation)
- [ ] Confirm deadline enforcement (6 PM)
- [ ] Download all team repositories (bulk export)
- [ ] Run final evaluation script on each team
- [ ] Combine autograding + manual scores
- [ ] Calculate final rankings
- [ ] Publish leaderboard to GitHub Pages
- [ ] Announce winners and schedule presentations

### Post-Hackathon
- [ ] Export all data (autograding, commits, issues)
- [ ] Send student feedback survey
- [ ] Conduct retrospective with teaching team
- [ ] Document improvements for next cohort
- [ ] Update template repository with lessons learned

## Common Issues & Solutions

**Issue:** Students can't accept assignment
- **Solution:** Check roster, ensure GitHub username matches identifier

**Issue:** Autograding fails due to dependency installation
- **Solution:** Pin exact versions in `pyproject.toml`, test on fresh Ubuntu environment

**Issue:** Tests timeout on complex algorithms
- **Solution:** Increase timeout in `autograding.json`, or use smaller test datasets

**Issue:** Teams formed with unequal sizes
- **Solution:** Use Classroom team management to rebalance, allow mid-hackathon adjustments

**Issue:** Students accidentally expose private key in commit
- **Solution:** Use GitHub secret scanning alerts, teach immediate key revocation

**Issue:** Students lose work due to Git conflicts
- **Solution:** Provide Git tutorial on Day 1, encourage frequent pulls, use feature branches

## Resources

### GitHub Classroom Documentation
- [GitHub Classroom Overview](https://docs.github.com/en/education/manage-coursework-with-github-classroom)
- [Creating Group Assignments](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/create-a-group-assignment)
- [Using Autograding](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/use-autograding)
- [Monitoring Student Progress](https://docs.github.com/en/education/manage-coursework-with-github-classroom/teach-with-github-classroom/monitor-students-progress-with-the-assignment-overview-page)

### GitHub Actions for Education
- [GitHub Actions for Education](https://github.com/education/autograding)
- [Autograding Action](https://github.com/marketplace/actions/autograding)
- [Grading Reporter](https://github.com/marketplace/actions/autograding-grading-reporter)

### Best Practices
- [Teaching with GitHub Classroom](https://github.blog/2020-03-18-set-up-your-digital-classroom-with-github-classroom/)
- [Autograding Best Practices](https://github.blog/2020-06-17-how-github-classroom-and-autograding-revolutionized-my-classroom/)

---

**Implementation Note:** This migration maintains the pedagogical philosophy of the hackathon (hands-on learning, collaboration, real-world tools) while adding automation and scalability through GitHub Classroom.
