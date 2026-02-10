# 🧰 Environment Setup Assignment (Individual)

## 📋 Overview

This is an **individual assignment** to set up your development environment for the "Capture the Drone" radar tracking challenge. Complete this **before teams are formed**.

**This assignment is:**
- ✅ Individual (not team-based)
- ✅ Collaborative (helping others is encouraged)
- ✅ Non-competitive (no points, no ranking)
- ✅ Prerequisite for the team challenge

---

## 🎯 Learning Objectives

By completing this assignment, you will:
1. Set up WSL2 (Windows Subsystem for Linux) on Windows or equivalent on other OS
2. Install ROS2 Jazzy and verify functionality
3. Configure Python development environment with UV package manager
4. Install and test MCAP tooling for ROS2 data replay
5. Verify your environment is ready for the radar tracking challenge

---

## ✅ Assignment Tasks

### 1️⃣ WSL2 Setup (Windows users) or Linux Environment

**Windows Users:**
- [ ] Install WSL2 with Ubuntu 22.04 or later
- [ ] Configure WSL2 resources (memory, CPU)
- [ ] Install Windows Terminal (optional but recommended)

**Mac/Linux Users:**
- [ ] Verify you have a compatible Linux distribution or macOS environment
- [ ] Ensure you have access to a terminal with bash/zsh

**Documentation:** [WSL Installation Guide](https://learn.microsoft.com/en-us/windows/wsl/install)

---

### 2️⃣ ROS2 Jazzy Installation

- [ ] Add ROS2 apt repository
- [ ] Install ROS2 Jazzy Desktop
- [ ] Source ROS2 setup in your `.bashrc` or `.zshrc`
- [ ] Verify installation with `ros2 --version`
- [ ] Test with a sample talker/listener demo

**Documentation:** [ROS2 Jazzy Installation](https://docs.ros.org/en/jazzy/Installation.html)

**Verification Command:**
```bash
ros2 run demo_nodes_cpp talker
# In another terminal:
ros2 run demo_nodes_cpp listener
```

---

### 3️⃣ Python & UV Setup

- [ ] Install Python 3.10 or later
- [ ] Install UV package manager: `pip install uv` or `curl -LsSf https://astral.sh/uv/install.sh | sh`
- [ ] Verify UV installation: `uv --version`
- [ ] Create a test virtual environment with UV

**Documentation:** [UV Documentation](https://github.com/astral-sh/uv)

**Verification Command:**
```bash
python3 --version
uv --version
uv venv test-env
source test-env/bin/activate
```

---

### 4️⃣ MCAP Tooling Installation

- [ ] Install MCAP CLI tools
- [ ] Install Python MCAP library
- [ ] Download sample MCAP file (link provided in assignment)
- [ ] Verify you can read MCAP metadata

**Installation:**
```bash
# Install MCAP CLI
pip install mcap-cli

# Install Python MCAP library with ROS2 support
pip install mcap mcap-ros2-support
```

**Verification Command:**
```bash
mcap info sample_radar_data.mcap
```

---

### 5️⃣ Development Tools (Optional but Recommended)

- [ ] Install VS Code or your preferred editor
- [ ] Install Python extension for your editor
- [ ] Install ROS extension for your editor (if available)
- [ ] Configure linting and formatting tools

---

## 🆘 Getting Help

**If you encounter setup issues, DO NOT struggle alone!**

### Use the Control Repository for All Setup Questions

🔗 **[Capture the Drone - Control Repository](https://github.com/bats-rising/challenge-coordination)**

**To get help:**
1. Go to the Control Repository: [https://github.com/bats-rising/challenge-coordination](https://github.com/bats-rising/challenge-coordination)
2. Click "Issues" → "New Issue"
3. Select the **"Setup Help"** template
4. Fill in all required fields (OS, ROS2 version, error messages, what you've tried)
5. Submit and wait for help from classmates or instructors

**Before asking:**
- [ ] Search existing issues – your problem might already be solved
- [ ] Read error messages carefully
- [ ] Try basic troubleshooting (restart terminal, check installation steps)

**Important Notes:**
- ⚠️ **Do NOT ask setup questions via email, chat, or other channels** – use the Control Repository issues
- ✅ Helping others is encouraged but **not scored or tracked**
- 🤝 This is a **collaborative, non-competitive** phase
- 📚 Solutions are visible to everyone, creating a knowledge base for the class

---

## 📤 Submission Instructions

### What to Submit

Create a **verification document** (PDF or Markdown) showing:

1. **Screenshots** demonstrating:
   - WSL2 or Linux terminal with `uname -a` output
   - `ros2 --version` output
   - `uv --version` output
   - `mcap info` command on the sample MCAP file
   - ROS2 talker/listener demo running

2. **Brief reflection** (2-3 sentences) on:
   - What was the most challenging part of the setup?
   - What resources or help did you find most useful?

### How to Submit

**Option A: GitHub Classroom (if configured):**
- Upload your verification document to this repository
- Commit and push to the `main` branch
- Autograding will verify file existence

**Option B: Learning Management System:**
- Export verification document as PDF
- Upload to the assignment on Canvas/Moodle/etc.

**Deadline:** [To be announced by instructor]

---

## ✅ Definition of Done

Your environment setup is complete when:

- ✅ All verification commands run successfully
- ✅ You can start a ROS2 node without errors
- ✅ UV can create and manage virtual environments
- ✅ You can read MCAP file metadata
- ✅ You've submitted verification screenshots
- ✅ **You're ready for the team challenge to begin!**

---

## 🚀 What's Next?

After completing this setup:

1. **Wait for team formation** – Teams will be announced before the challenge
2. **Review radar basics** (optional) – Brush up on coordinate systems, Kalman filters
3. **Explore ROS2 concepts** (optional) – Topics, messages, nodes
4. **Be ready** – The 4-day challenge starts soon!

---

## 📚 Additional Resources

### Official Documentation
- [WSL Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
- [ROS2 Jazzy Docs](https://docs.ros.org/en/jazzy/)
- [UV Package Manager](https://github.com/astral-sh/uv)
- [MCAP Documentation](https://mcap.dev/)

### Troubleshooting Guides
- [WSL Common Issues](https://learn.microsoft.com/en-us/windows/wsl/troubleshooting)
- [ROS2 Installation Troubleshooting](https://docs.ros.org/en/jazzy/Installation/Troubleshooting.html)

### Learning Resources
- [ROS2 Tutorials](https://docs.ros.org/en/jazzy/Tutorials.html)
- [Python Virtual Environments Guide](https://docs.python.org/3/tutorial/venv.html)

---

## 🤝 Collaboration Policy

**For this individual assignment:**
- ✅ **Allowed:** Asking for help via Control Repository issues
- ✅ **Allowed:** Helping others with setup problems
- ✅ **Allowed:** Sharing resources, documentation links, troubleshooting tips
- ❌ **Not allowed:** Submitting someone else's verification screenshots as your own

**Remember:** The goal is for YOU to have a working environment. Help is encouraged, but you must complete the setup yourself.

---

## ❓ Questions About the Assignment?

For **setup help** (technical issues):
- Use the Control Repository: [Setup Help Issues](https://github.com/bats-rising/challenge-coordination/issues/new?template=setup-help.md)

For **assignment clarification** (requirements, deadlines, grading):
- Use the Control Repository: [Question Issues](https://github.com/bats-rising/challenge-coordination/issues/new?template=question.md)

---

**Good luck with your setup! 🧰🚀**
