# Agent Maintainer - Detailed Workflow and Standards

## Quality Standards

Each custom agent must meet these criteria aligned with [GitHub Copilot best practices](https://docs.github.com/en/copilot/tutorials/coding-agent/get-the-best-results):

### Success Metrics

Track these metrics to measure agent effectiveness:
- **Agent file size:** Target <300 lines, max 500 lines
- **User satisfaction:** Gather feedback via issues, PR comments, or surveys
- **Response quality:** Track "helpful" vs. "needs revision" responses
- **Maintenance burden:** Time spent on updates per quarter
- **Adoption rate:** How frequently agents are invoked
- **Iteration cycles:** Number of clarifications needed per task

### 1. Frontmatter Requirements
```yaml
---
name: [Clear, concise agent name - max 30 chars]
description: [Single-line description of agent purpose - max 100 chars]
instructions: [Optional: path to separate instructions file]
---
```

### 2. Content Structure
- **Role Overview:** Clear 2-3 sentence summary of agent purpose
- **Core Competencies:** Bullet-pointed expertise areas (avoid excessive detail)
- **Responsibilities:** Specific, actionable tasks the agent should perform
- **Communication Style:** How the agent should interact with users
- **Quality Standards:** Expected outputs and behaviors
- **Security and Scope Boundaries:** Explicit constraints on what agent can/cannot do
- **Example Use Cases:** Concrete examples of good and bad tasks
- **Validation and Testing:** How agent ensures quality outputs
- **Continuous Improvement:** How agent stays current with best practices

### 3. Documentation Separation
- **Keep in agent file:** Role definition, core competencies, communication style
- **Move to instructions.md:** Detailed workflows, extensive examples, long checklists
- **Move to prompts/:** Reusable prompt templates, query patterns
- **Move to docs/:** Project-specific context, historical decisions, onboarding guides

### 4. File Naming
- Use descriptive, lowercase names with underscores: `dsp_specialist.agent.md`
- Avoid generic names like `agent1.md` or `helper.md`
- Match file name to agent's primary role

### 5. Maintenance
- Include creation/last updated date in comments
- Reference related issues or PRs
- Link to relevant GitHub documentation
- Add testing notes if CLI validation was performed

## Review Checklist

When reviewing an agent, validate:

### Basic Structure
- [ ] Frontmatter is valid YAML and includes required fields
- [ ] Agent name is unique and descriptive
- [ ] Description accurately summarizes agent purpose
- [ ] Role overview is concise (< 250 words)
- [ ] Agent file size is reasonable (< 500 lines as guideline)

### Content Quality
- [ ] Responsibilities are specific and actionable
- [ ] Communication style is clearly defined
- [ ] No project-specific implementation details in agent file
- [ ] Excessive content has been moved to separate files
- [ ] Links to external documentation are current and accessible

### Best Practices Compliance
- [ ] **Security boundaries** - Explicit scope constraints defined
- [ ] **Example use cases** - Good and bad task examples provided
- [ ] **Validation approach** - Quality assurance methods specified
- [ ] **Continuous improvement** - Maintenance and update strategy included
- [ ] **Context awareness** - Project-specific context provided where relevant
- [ ] **Right type of work** - Agent is scoped to appropriate task types
- [ ] **Iterative feedback** - Agent supports collaborative refinement

### Testing and Validation
- [ ] Testing has been performed with GitHub Copilot CLI (when available)
- [ ] Agent aligns with current GitHub best practices
- [ ] No conflicts with other agents in the repository
- [ ] Sample queries tested and produce expected behavior

## Refactoring Workflow

### Step 1: Inventory
- List all agents in `.github/agents/` directory
- Document current state (line count, purpose, issues)
- Identify agents that need refactoring

### Step 2: Prioritize
- Identify agents most in need of refactoring
- Focus on:
  - Agents exceeding 500 lines
  - Missing or invalid frontmatter
  - Inconsistent naming
  - Excessive inline documentation

### Step 3: Extract
- Move excessive content to appropriate files:
  - Detailed workflows → `instructions/`
  - Reusable templates → `prompts/`
  - Project context → `docs/`
- Keep agent file focused on role and competencies

### Step 4: Streamline
- Optimize remaining agent content
- Remove redundancy
- Ensure clarity and actionability
- Target: <300 lines for complex agents, <150 for simple ones

### Step 5: Test
- Validate with GitHub Copilot CLI (if available)
- Check YAML frontmatter syntax
- Verify instructions path references
- Test agent behavior with sample queries

### Step 6: Document
- Update related documentation
- Create/update `.github/agents/README.md`
- Document changes in PR description
- Link to relevant issues

### Step 7: Deploy
- Create PR with clear description of changes
- Reference original issue
- Tag relevant reviewers
- Ensure CI passes

### Step 8: Monitor
- Gather feedback from users
- Track agent performance
- Iterate based on feedback
- Update as GitHub evolves features

## Example Refactoring

### Before: Bloated Agent (500+ lines)

```yaml
---
name: Build Expert
description: Expert in CMake and build systems
---

## Role
You are a build system expert...

## Detailed CMake Syntax Guide
[300 lines of CMake documentation copied from official docs]

## Complete Project History
[150 lines of historical context about build decisions]

## All Possible Build Commands
[100 lines of command examples with full explanations]
```

### After: Streamlined Agent (<200 lines)

**Agent file** (`.github/agents/build_expert.agent.md`):
```yaml
---
name: Build Expert
description: Expert in CMake and build systems
instructions: ../.github/copilot/instructions/build_expert_instructions.md
---

## Role
You are a build system expert specializing in modern CMake...
[Concise role definition and competencies - 150 lines total]
```

**Instructions file** (`.github/copilot/instructions/build_expert_instructions.md`):
```markdown
# Build Expert - Detailed Instructions

## CMake Best Practices
[Detailed workflows and examples]

## Project Build History
[Historical context and decisions]

## Common Build Commands
[Command reference with examples]
```

**Result:** Agent file reduced from 500 to 180 lines, detailed content preserved in separate file.

## Agent Versioning and Change Tracking

### Version Management
- Use comments at top of agent file to track versions:
  ```markdown
  <!-- Version: 1.2.0 -->
  <!-- Last Updated: 2025-11-20 -->
  <!-- Related PR: #123 -->
  ```
- Document breaking changes in PR descriptions
- Link significant updates to GitHub issues
- Consider maintaining CHANGELOG.md for major agent updates

### Change Documentation
- **Minor updates:** Update "Last Updated" date, describe in commit message
- **Major refactoring:** Increment version, create detailed PR description
- **Breaking changes:** Document migration path for users
- **Deprecation:** Announce in advance, provide alternatives

## File Structure Recommendations

```
.github/
├── agents/
│   ├── dsp_specialist.agent.md
│   ├── build_expert.agent.md
│   ├── agent_maintainer.agent.md
│   └── README.md  (Overview of all agents)
├── copilot/
│   ├── instructions/
│   │   ├── dsp_specialist_instructions.md
│   │   ├── build_expert_instructions.md
│   │   └── agent_maintenance_workflow.md
│   └── prompts/
│       ├── code_review_template.md
│       └── documentation_template.md
└── docs/
    └── agent_architecture.md  (High-level documentation)
```

## Decision Framework

When best practices conflict, prioritize in this order:
1. **Security** - Never compromise on security constraints or sensitive data access
2. **GitHub official guidelines** - Follow documented best practices
3. **Team conventions** - Respect established project patterns
4. **Maintainability** - Prefer clarity and simplicity over optimization
5. **Performance/optimization** - Optimize only when necessary

## Best Practices

### Frontmatter
- Keep descriptions under 100 characters
- Use clear, descriptive names
- Reference instructions file when agent is complex
- Ensure valid YAML syntax (no tabs, proper indentation)

### Content Organization
- **Concise Role Overview:** 2-3 sentences maximum
- **Bullet-pointed Competencies:** Avoid paragraphs
- **Specific Responsibilities:** Actionable items only
- **Clear Communication Style:** How agent should respond
- **Security Boundaries:** Explicit scope and constraints (NEW)
- **Example Use Cases:** Concrete good/bad examples (NEW)
- **Validation Approach:** Quality assurance methods (NEW)
- **Continuous Improvement:** Update and maintenance strategy (NEW)

### Documentation Separation
- **Agent file:** What the agent does and how it behaves
- **Instructions file:** Detailed workflows and examples
- **Prompts file:** Reusable query templates
- **Docs:** Project context and architectural decisions

### Naming Conventions
- Use lowercase with underscores: `my_agent.agent.md`
- Be descriptive: `dsp_specialist.agent.md` not `agent1.agent.md`
- Match file name to agent role
- Always use `.agent.md` extension

### Security Best Practices (NEW)
- **Define explicit boundaries** - What agent can and cannot modify
- **Protect sensitive areas** - Configs, secrets, safety-critical code
- **Require review for critical changes** - Don't automate everything
- **Enable rollback** - All changes must be reversible
- **Document security constraints** - Make them visible to users

### Task Scoping Best Practices (NEW)
- **Match agent to task type** - Use right agent for right work
- **Provide rich context** - Give agents visibility into codebase
- **Break down complexity** - Split large tasks into smaller pieces
- **Enable iteration** - Support refinement and feedback
- **Validate outputs** - Always review and test agent changes

### Maintenance
- Regular reviews (quarterly or when GitHub updates features)
- Track changes in version control
- Document decisions in PR descriptions
- Test before deploying
- Gather user feedback and iterate
- Stay current with GitHub Copilot releases

## Common Issues and Solutions

### Issue: Agent file too large (>500 lines)
**Solution:** Extract detailed content to instructions file

### Issue: Missing frontmatter
**Solution:** Add minimal YAML frontmatter with name and description

### Issue: Generic agent name
**Solution:** Rename to descriptive name matching role

### Issue: Project-specific implementation details
**Solution:** Move to project documentation or instructions file

### Issue: Redundant content across agents
**Solution:** Create shared instructions file or consolidate agents

### Issue: Outdated documentation links
**Solution:** Update to current GitHub documentation URLs

### Issue: Complex workflows in agent file
**Solution:** Extract to separate instructions file, reference via frontmatter

## Testing Guidelines

### Manual Testing
1. Read agent file as if you were Copilot
2. Verify role and responsibilities are clear
3. Check that instructions are actionable
4. Ensure no ambiguity in behavior

### CLI Testing (when available)
```bash
# Install GitHub Copilot CLI
npm install -g @github/copilot-cli

# Test agent locally
gh copilot test-agent .github/agents/my_agent.agent.md

# Validate with sample queries
gh copilot ask --agent my_agent "Sample query here"
```

### Testing with GitHub Copilot CLI

```bash
# Validate agent syntax and structure
gh copilot validate .github/agents/agent_maintainer.agent.md

# Interactive testing session
gh copilot chat --agent agent_maintainer

# Test specific query
echo "Review all agents for best practices" | gh copilot chat --agent agent_maintainer

# Test with context from file
gh copilot chat --agent agent_maintainer --file .github/agents/example_agent.agent.md \
  --query "Is this agent following best practices?"
```

### Integration Testing
1. Test agent in real repository context
2. Verify instructions file references work
3. Check that agent provides helpful responses
4. Validate no conflicts with other agents

## Constraints

- **Respect GitHub Limits:** Agent files have size and complexity limits
- **Maintain Backward Compatibility:** Changes shouldn't break existing workflows
- **Preserve Agent Intent:** Refactoring should enhance, not alter, agent purpose
- **Document Changes:** All modifications must be tracked in issues/PRs
- **Test Before Deploy:** Always validate with CLI before merging

## GitHub Copilot Best Practices Integration

This workflow integrates best practices from official GitHub documentation:

### From "Get the Best Results" Guide
1. **Clear and well-scoped issues** - Agents have clear boundaries and example use cases
2. **Right type of work** - Agents specify what tasks they excel at
3. **Rich context** - Agents include project-specific context awareness
4. **Break down complex tasks** - Agents support incremental work
5. **Security boundaries** - Explicit constraints on sensitive operations
6. **Review and test** - Validation approaches built into agent definitions
7. **Iterative feedback** - Agents support collaborative refinement
8. **Continuous learning** - Agents include maintenance strategies

### From "Great agents.md" Guide
- **Define persona** - Clear role overview and communication style
- **Set scope** - Explicit boundaries and constraints
- **List commands** - Example use cases with concrete queries
- **Specify stack** - Technology context and dependencies
- **Code style** - Formatting and conventions where relevant
- **Set hard boundaries** - What agents must not do

### Implementation in This Repository
- ✅ All agents have security and scope boundaries sections
- ✅ Each agent includes example use cases
- ✅ Validation and testing approaches specified
- ✅ Continuous improvement sections added
- ✅ Context awareness documented
- ✅ Quality standards enforced through checklists
- ✅ Regular review process established

## References

- [GitHub Copilot Custom Agents Configuration](https://docs.github.com/en/copilot/reference/custom-agents-configuration)
- [GitHub Copilot CLI for Custom Agents](https://gh.io/customagents/cli)
- [Best Practices for Custom Agents](https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot)
- [Get the Best Results with Coding Agent](https://docs.github.com/en/copilot/tutorials/coding-agent/get-the-best-results)
- [How to Write Great agents.md](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/)

---

**Last Updated:** November 2025
**Related Issue:** [#6 - Review and refactor custom coding agents](https://github.com/bosch-engineering/defence.dsp/issues/6)
