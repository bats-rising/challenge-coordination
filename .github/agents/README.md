# Custom GitHub Copilot Agents

This directory contains custom GitHub Copilot agents designed to support the **Capture the Drone** 4-day radar multi-target tracking hackathon.

## Available Agents

### Essential Agents

#### 1. **Radar Signal Processing Expert** 🎯
**File:** `radar_signal_processing_expert.agent.md`  
**Invoke:** `@Radar Expert` or `@Radar Signal Processing Expert`

Specializes in radar data processing, multi-target tracking algorithms (Kalman filters, Particle filters), and ROS2 MCAP radar data interpretation.

**Use for:**
- Understanding Kalman filter mathematics and implementation
- Data association algorithms (Nearest Neighbor, GNN, JPDA)
- Track management (initiation, confirmation, deletion)
- Interpreting radar message formats
- Parameter tuning (process noise, measurement noise, gating)
- Debugging tracking issues (track swapping, lost tracks)

**Example queries:**
```
@Radar Expert Explain how Kalman filter prediction step works
@Radar Expert What's the difference between nearest neighbor and GNN?
@Radar Expert My tracks keep swapping - what could be wrong?
```

---

#### 2. **Python CLI & Tooling Mentor** 🐍
**File:** `senior-python-expert.agent.md`  
**Invoke:** `@Python CLI Mentor` or `@Python Mentor`

Expert in Click CLI framework, Rich console, UV package management, MCAP data handling, and student-friendly Python development for mixed engineering backgrounds.

**Use for:**
- Click CLI development and command structure
- Rich console output and formatting
- UV environment setup with ROS2 integration
- MCAP file reading with rosbag2_py
- Python best practices (type hints, error handling)
- Ruff, mypy, pytest integration
- WSL2 setup for Windows students

**Example queries:**
```
@Python CLI Mentor How do I create a Click command for reading MCAP files?
@Python CLI Mentor Set up UV venv with ROS2 Jazzy
@Python CLI Mentor How do I use Rich to display tracking results?
```

---

#### 3. **ROS2 Integration Specialist** 🤖
**File:** `ros2_integration_specialist.agent.md`  
**Invoke:** `@ROS2 Integration Specialist` or `@ROS2 Specialist`

Specializes in ROS2 Jazzy, MCAP playback, message parsing, timing synchronization, and integrating tracking algorithms with ROS2 data streams.

**Use for:**
- ROS2 fundamentals for beginners (nodes, topics, messages)
- Reading MCAP files with rosbag2_py
- Parsing radar messages and extracting fields
- Handling ROS2 timestamps (nanoseconds → seconds)
- WSL2 + ROS2 Jazzy environment setup
- Integrating tracking algorithms with MCAP data
- Debugging ROS2 issues (import errors, QoS mismatches)

**Example queries:**
```
@ROS2 Integration Specialist How do I read MCAP files in Python?
@ROS2 Integration Specialist What's the ROS2 timestamp format?
@ROS2 Integration Specialist I'm getting 'rclpy not found' errors
```

---

### Nice-to-Have Agents

#### 4. **Data Visualization Coach** 📊
**File:** `data_visualization_coach.agent.md`  
**Invoke:** `@Data Visualization Coach` or `@Visualization Coach`

Expert in matplotlib and plotly for creating tracking visualizations, live plotting, performance metrics visualization, and debugging plots.

**Use for:**
- Plotting radar detections and tracks
- Creating trajectory visualizations
- Live/animated plotting during MCAP playback
- Visualizing performance metrics (MOTA, MOTP)
- Debugging tracking with plots (identifying track swapping, lost tracks)
- Range-azimuth and polar coordinate plots
- Interactive plotly dashboards

**Example queries:**
```
@Data Visualization Coach How do I plot detections and tracks together?
@Data Visualization Coach Create an animation of tracking over time
@Data Visualization Coach How do I visualize MOTA metrics?
```

---

#### 5. **Testing & Validation Guide** ✅
**File:** `testing_validation_guide.agent.md`  
**Invoke:** `@Testing & Validation Guide` or `@Testing Guide`

Specializes in pytest for tracking algorithms, synthetic test dataset generation, and multi-object tracking metrics (MOTA, MOTP).

**Use for:**
- Writing pytest tests for Kalman filters and tracking algorithms
- Generating synthetic test datasets with ground truth
- Calculating MOTA, MOTP, and other tracking metrics
- Testing edge cases (crossing tracks, clutter, missed detections)
- Creating pytest fixtures and parametrized tests
- Achieving test coverage goals (~90%)
- Debugging failed tests

**Example queries:**
```
@Testing & Validation Guide How do I write pytest tests for Kalman filter?
@Testing & Validation Guide Generate synthetic crossing tracks dataset
@Testing & Validation Guide How do I calculate MOTA and MOTP?
```

---

### Support Agents

#### 6. **Challenge Coordinator** 🎪
**File:** `challenge_coordinator.agent.md`  
**Invoke:** `@Challenge Coordinator`

Orchestrates the 4-day hackathon via GitHub Issues, manages milestones, tracks team progress, and provides pedagogical feedback.

**Use for:**
- Creating GitHub issues for challenge tasks
- Tracking team progress across 4-day timeline
- Providing pedagogical feedback on PRs
- Coordinating between specialist agents
- Scope management (keeping tasks achievable)

---

#### 7. **Jekyll & GitHub Pages Expert** 📄
**File:** `jekyll_github_pages_expert.agent.md`  
**Invoke:** `@Jekyll & GitHub Pages Expert`

Expert in Jekyll, GitHub Pages, documentation structure, and static site generation with focus on educational content and Mermaid diagrams.

**Use for:**
- Creating and maintaining Jekyll-based GitHub Pages sites
- Writing technical documentation with Mermaid diagrams
- Setting up navigation and site structure
- Validating links and ensuring accessibility
- Explaining technical concepts (e.g., WSL2 virtualization)
- Migrating documentation to GitHub Pages format

**Example queries:**
```
@Jekyll & GitHub Pages Expert Create a documentation site for the hackathon
@Jekyll & GitHub Pages Expert Add Mermaid diagram explaining WSL2 architecture
@Jekyll & GitHub Pages Expert Validate all documentation links are working
```

---

#### 8. **Agent Maintainer** 🛠️
**File:** `agent_maintainer.agent.md`  
**Invoke:** `@Agent Maintainer`

Maintains and optimizes GitHub Copilot custom agents, ensuring they follow best practices.

**Use for:**
- Reviewing and refactoring agent definitions
- Creating new custom agents
- Validating agent frontmatter and structure
- Agent quality assurance

---

## Quick Reference

| Task | Ask This Agent |
|------|----------------|
| Kalman filter math | @Radar Expert |
| Data association algorithms | @Radar Expert |
| MCAP file reading | @ROS2 Integration Specialist |
| ROS2 timestamp handling | @ROS2 Integration Specialist |
| Click CLI development | @Python CLI Mentor |
| UV environment setup | @Python CLI Mentor |
| Plotting tracking results | @Data Visualization Coach |
| Creating animations | @Data Visualization Coach |
| Writing pytest tests | @Testing & Validation Guide |
| MOTA/MOTP metrics | @Testing & Validation Guide |
| GitHub issue creation | @Challenge Coordinator |
| Documentation site setup | @Jekyll & GitHub Pages Expert |
| Mermaid diagrams | @Jekyll & GitHub Pages Expert |
| Creating new agents | @Agent Maintainer |

## Agent Best Practices

All agents in this directory follow GitHub Copilot best practices:

- ✅ Valid YAML frontmatter with name and description
- ✅ Clear role definition and responsibilities
- ✅ Explicit security and scope boundaries
- ✅ Example use cases (good tasks, delegation, refusals)
- ✅ Validation and testing approach
- ✅ Continuous improvement section
- ✅ File size < 500 lines (most < 300 lines)
- ✅ Pedagogical focus for mixed-skill student teams

## File Structure

```
.github/
├── agents/
│   ├── README.md (this file)
│   ├── agent_maintainer.agent.md (174 lines)
│   ├── challenge_coordinator.agent.md (243 lines)
│   ├── data_visualization_coach.agent.md (378 lines)
│   ├── jekyll_github_pages_expert.agent.md (292 lines)
│   ├── radar_signal_processing_expert.agent.md (195 lines)
│   ├── ros2_integration_specialist.agent.md (281 lines)
│   ├── senior-python-expert.agent.md (238 lines)
│   └── testing_validation_guide.agent.md (437 lines)
└── instructions/
    └── agent_maintenance_workflow.md
```

## Contributing

When creating or modifying agents:

1. Follow the structure in existing agents
2. Keep files under 500 lines (target < 300)
3. Include clear example use cases
4. Define explicit security boundaries
5. Maintain pedagogical tone for students
6. Test with GitHub Copilot CLI if available
7. Update this README when adding new agents

## References

- [GitHub Copilot Custom Agents Configuration](https://docs.github.com/en/copilot/reference/custom-agents-configuration)
- [Best Practices for Coding Agent](https://docs.github.com/en/copilot/tutorials/coding-agent/get-the-best-results)
- [How to Write Great agents.md](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/)
- [Agent Maintenance Workflow](../instructions/agent_maintenance_workflow.md)

---

**Last Updated:** 2026-02-05  
**Total Agents:** 8  
**For Questions:** Tag @Challenge Coordinator or @Agent Maintainer
