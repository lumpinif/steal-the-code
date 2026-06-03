# Toolchain

Steal the Code defaults to no-login, no-API-key tools. Paid or authenticated
tools can improve recall, but they must not be required for the core workflow.

## Default Lanes

### Skill Precedents

Use when the user's need may be solved by an existing agent workflow.

```bash
DISABLE_TELEMETRY=1 npx skills find "<idea or workflow>"
DISABLE_TELEMETRY=1 npx skills use <owner>/<repo>@<skill>
```

Do not install a skill until the user asks or the current task clearly needs it.

### Repo Discovery

Use GitHub public repository search first. It works without login, though
unauthenticated requests have stricter rate limits.

```bash
node scripts/github-repo-search.mjs "open source AI dictation Typeless alternative" --limit 20
```

Search multiple query families:

- Product category
- User workflow
- Architecture
- Implementation anchors
- Analogy terms
- Negative terms to filter later

### Community and Product Vocabulary

Use HN Algolia to learn how real builders and users describe the idea.

```bash
node scripts/hn-search.mjs "AI dictation open source Typeless" --limit 10
```

HN is not enough for repo discovery. Use it mainly for vocabulary, pain,
launches, and adoption signals.

### Code Evidence

Use Sourcegraph public Stream API when code-level proof matters.

```bash
node scripts/sourcegraph-search.mjs '"global hotkey" "transcribe" "paste" lang:Swift count:20'
```

Sourcegraph is code search, not idea search. Use it to verify that a repo or
pattern exists in real code.

### Deep Read

Use the lightest deep-read path that answers the question:

```bash
# Read remote repo as compact context.
npx repomix@latest --remote owner/repo --style markdown --compress -o work/owner-repo.md
```

If DeepWiki MCP is available, ask targeted questions:

- What is this repo trying to build?
- What is the main user workflow?
- What architecture and modules matter?
- What should be borrowed or avoided?

## Optional Enhanced Lanes

Use these only when configured and useful:

- Exa: semantic web search for vague idea matching.
- Tavily: web research and extraction.
- Firecrawl: full-page extraction and web crawl.
- Reposeek: repo discovery if a key exists.
- GitHub CLI or GitHub MCP: authenticated repo/code search when already logged in.

## Query Expansion Checklist

For each idea, generate:

- Product keywords
- User workflow keywords
- Architecture keywords
- Implementation keywords
- Protocol/model keywords
- Analogy keywords
- Negative keywords

Example for a Typeless alternative:

```text
Product: AI dictation, voice input, Typeless alternative
Workflow: hold hotkey, speak, release, paste into any app
Architecture: ASR provider, LLM polish provider, local history, settings
Implementation: global hotkey, microphone permission, cursor insertion, clipboard
Protocol/model: Whisper, local ASR, OpenAI-compatible LLM, personal dictionary
Analogy: Wispr Flow, Superwhisper, voice-to-text productivity
Negative: awesome list, tutorial, toy demo, archived
```

## Ranking Signals

Use these in order:

1. User-workflow fit
2. Implementation-shape fit
3. Product intent fit
4. License compatibility
5. Maintenance recency
6. Community signal
7. Stars and forks

Stars are a weak signal. A 30-star repo with the exact workflow can be more
useful than a 10,000-star library that only matches one keyword.

