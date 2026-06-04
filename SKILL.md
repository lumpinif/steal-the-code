---
name: steal-the-code
description: Finds real public open-source precedents before an agent designs or builds a product, feature, module, system, or skill. Use when a user has an idea, asks for architecture or implementation direction, wants open-source references, wants to avoid AI slop, mentions competitors or alternatives, or asks the agent to "steal the code" before building.
---

# Steal the Code

Ask your agent to steal the code first, then build something better.

This skill uses public open-source projects as evidence before important product,
architecture, implementation, or skill-design decisions. "Steal" means study
public code, learn from proven patterns, credit builders, respect licenses, and
turn the lessons into a better implementation plan.

## Default Workflow

1. **Clarify intent**
   - Write one sentence for the user's actual goal.
   - Identify product, workflow, architecture, implementation, protocol/model,
     analogy, and negative keywords.
   - Do this even when the user is still at idea stage.

2. **Route precedent lanes**
   - Skill precedents: search existing skills when the user may need a workflow
     or agent capability.
   - Open-source alternative directories: when the user names a product, SaaS,
     or category and wants an open-source replacement, use public alternative
     directories as candidate seed sources.
   - Repo precedents: search public GitHub repositories for open-source systems,
     modules, and implementation patterns.
   - Product/community precedents: search HN or the web for real-world naming,
     demand, pain, and product expectations.
   - Code evidence: use Sourcegraph or repo reads to verify that candidates
     really implement the relevant patterns.

3. **Search with expanded queries**
   - Do not rely on one phrase.
   - Search several query families: product category, user workflow,
     architecture, implementation anchors, analogies, and exclusions.
   - Prefer no-login tools first. See [Toolchain](references/toolchain.md).

4. **Read the best candidates**
   - Start with README, topics, license, stars, forks, update recency, and docs.
   - Treat directory results as leads only. Verify the GitHub repo, license,
     maintenance, and real code before using or borrowing from a candidate.
   - Deep-read only the most relevant projects.
   - Use Repomix, DeepWiki, local code search, or direct repo inspection when
     the candidate is likely to shape implementation.

5. **Rank by practical fit**
   - Fit to the idea matters more than stars.
   - Prefer projects with matching user workflow and implementation shape.
   - Penalize awesome lists, toy demos, abandoned repos, incompatible licenses,
     and projects that only match keywords but not intent.

6. **Return a decision**
   - `Use`: directly use or test this project/skill.
   - `Borrow`: learn product, architecture, workflow, or implementation patterns.
   - `Avoid`: do not copy this direction; explain why.
   - `Build New`: no precedent fits enough, or the user has a clear
     differentiating constraint.

## Required Output

Always include:

- The intent as understood.
- The query families used or recommended.
- Ranked skill/repo/product precedents, separated by source type.
- Practical lessons for product and architecture.
- A `Use / Borrow / Avoid / Build New` decision.
- Credits and license notes for every repo that influenced the recommendation.
- Concrete constraints to carry into the next coding step.

## Optional Outputs

Offer these when useful:

- **HTML Dashboard** for visual comparison and sharing.
- **Precedent Reel** for short-form demos. Do not treat video generation as a
  built-in dependency. If the environment has video skills or tools available,
  choose the best fit:
  - Use **HyperFrames** for fast HTML-first explainers, dashboard-to-video
    walkthroughs, and short social reels.
  - Use **Remotion** for React-first video projects, reusable templates,
    parameterized compositions, or a larger programmatic video system.
- **Candidate JSON** for another agent to continue the work from the same source
  of truth.

Use [Output Modes](references/output-modes.md) for structure and
[Credits and Licenses](references/credits-and-licenses.md) for attribution rules.
