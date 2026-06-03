# Steal the Code

Ask your agent to steal the code first, then build something better.

Steal the Code is a skill for agentic coding. Before an agent designs or builds
a product, feature, module, system, or another skill, it finds real public
open-source precedents, studies what works, and turns that evidence into a
practical implementation plan.

This is not about stealing private code or ignoring licenses. It is about making
agents learn from public builders instead of inventing worse versions of things
that already exist.

## Core Use Case

When you are building something, ask the agent to study the public repos that
already solved most of the problem. Those projects can give the agent better
product instincts, cleaner architecture, proven implementation patterns, and a
clearer sense of what to avoid.

That extra context is the point. The agent is no longer designing from a prompt
alone. It is building with real open-source precedent in view.

## Why

Coding agents can be very good at local implementation and still make weak
product, architecture, or workflow decisions. When they only see the current
prompt and codebase, they often invent designs that look reasonable but are not
how real people expect the product to work.

The best correction signal is usually already public: open-source repos, skills,
launch posts, docs, and community discussions from builders who solved adjacent
problems before. Those precedents show what actually worked, what was overbuilt,
what users cared about, and what implementation shape survived contact with
reality.

Steal the Code turns that evidence into a required step before building. It
makes the agent decompose the idea, find real precedents, read the closest ones,
decide what to use, borrow, avoid, or build new, and carry credits and license
constraints into implementation.

## Install

```bash
npx skills add lumpinif/steal-the-code
```

Use without installing:

```bash
npx skills use lumpinif/steal-the-code@steal-the-code
```

## What It Does

- Decomposes an idea into searchable product, architecture, workflow, and
  implementation intent.
- Searches for skill, repo, product, community, and code precedents.
- Ranks candidates by practical fit, not just popularity.
- Deep-reads the best open-source examples.
- Produces a `Use / Borrow / Avoid / Build New` decision.
- Carries credits, license notes, and constraints into the next coding step.
- Optionally generates an HTML dashboard or short precedent reel for sharing.

## Optional Outputs

The default output is a concise chat brief. When the result is worth sharing or
handing off to another agent, Steal the Code can also produce richer artifacts.

- **HTML Dashboard**: a single local HTML file that compares candidates by fit,
  source, license, platform, takeaways, and `Use / Borrow / Avoid / Build New`.
  Use this when you want a durable visual brief for yourself, a team, or another
  agent.
- **Precedent Reel**: a short HyperFrames or Remotion video that turns the same
  report into a shareable walkthrough. Use this when you want to explain the
  idea publicly or show why the precedent set changes the implementation plan.
- **Candidate JSON**: the source of truth for the brief, dashboard, and reel, so
  later agents can continue from the same evidence instead of rerunning the
  research from scratch.

## Core Principle

Steal ideas. Credit builders. Respect licenses. Build better.

## Example Showcase

The Typeless alternative example can be turned into a visual report and a short
video.

[![Typeless precedent reel](assets/typeless-precedent-reel-contact-sheet.png)](assets/typeless-precedent-reel.mp4)

Click the preview to open the MP4. GitHub README files do not reliably render
repo-hosted videos inline, so the screenshot acts as a stable preview.

## Example

Intent:

```text
Build a free, open-source Typeless alternative.
```

Product reference:

- [Typeless](https://www.typeless.com/)

The skill expands the idea into query families:

```text
AI dictation
voice input in any app
hold hotkey, speak, release
polished text
Whisper / local ASR
LLM cleanup
personal dictionary
app-specific prompt routing
no subscription
```

It finds projects such as:

- [Open-Less/openless](https://github.com/Open-Less/openless)
- [TypeWhisper/typewhisper-mac](https://github.com/TypeWhisper/typewhisper-mac)
- [hehehai/voxt](https://github.com/hehehai/voxt)
- [never13254/GhostType](https://github.com/never13254/GhostType)
- [DoodzProg/AcouZ](https://github.com/DoodzProg/AcouZ)

Then it turns the precedent set into a coding recommendation:

- Use [OpenLess](https://github.com/Open-Less/openless) as the closest
  full-product reference.
- Borrow [TypeWhisper](https://github.com/TypeWhisper/typewhisper-mac)'s local
  engine/plugin direction.
- Borrow [Voxt](https://github.com/hehehai/voxt) and
  [GhostType](https://github.com/never13254/GhostType)'s app-aware prompt
  routing.
- Reference [AcouZ](https://github.com/DoodzProg/AcouZ) for a minimal Windows
  path.
- Avoid building only a Whisper wrapper.
- Build new only with a clear differentiated focus.

## No-Login Default Toolchain

The default workflow prefers tools that an agent can run without user login or
API keys:

- GitHub public repository search
- GitHub public contents/raw APIs
- Hacker News Algolia API
- Sourcegraph public Stream API
- Repomix
- DeepWiki MCP when available
- Local BM25-style candidate ranking

API-key tools such as Exa, Tavily, Firecrawl, and Reposeek can be used as
enhancements, but they are not required.

## Scripts

The scripts are dependency-free Node.js tools for agents.

```bash
node scripts/github-repo-search.mjs "open source typeless alternative AI dictation" --limit 10
node scripts/hn-search.mjs "Typeless open source dictation" --limit 10
node scripts/sourcegraph-search.mjs '"global hotkey" "transcribe" "paste" lang:Swift count:20'
node scripts/rank-candidates.mjs --query "free open source typeless alternative AI dictation" --input examples/typeless-candidates.json --fetch-readme
node scripts/render-html-report.mjs --input examples/typeless-report.json --out outputs/typeless-report.html
```

## Responsible Use

Steal the Code should always surface:

- The source projects used.
- The relevant license for each repo.
- Whether direct code reuse is license-compatible.
- What should be credited in docs, README, or release notes.
- What should be borrowed as an idea instead of copied as code.

If an agent borrows code directly, it must preserve required attribution and
follow the license terms. If license compatibility is unclear, treat the project
as inspiration only until a human verifies it.

## Repository Layout

```text
SKILL.md
references/
  toolchain.md
  output-modes.md
  credits-and-licenses.md
templates/
  precedent-report.schema.json
scripts/
  github-repo-search.mjs
  hn-search.mjs
  sourcegraph-search.mjs
  rank-candidates.mjs
  render-html-report.mjs
examples/
  typeless-candidates.json
  typeless-report.json
```
