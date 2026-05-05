---
name: skill-finder-en
description: Find, verify, compare, and recommend the best Codex/ChatGPT/AI agent skills for a user's one-line or ambiguous request. Use when the user asks to find skills, recommend skills, installable skills, GitHub skills, skillsmp.com skills, skill marketplace results, workflow skill combinations, or says they need a skill for a domain such as coding standards, video editing, painting, design, research, spreadsheets, presentations, documents, automation, browsing, GitHub, or any task where suitable skills must be discovered from GitHub, https://skillsmp.com/search, official/curated registries, or the web.
---

# Skill Finder

## Goal

Turn a user's short or fuzzy request into an evidence-backed skill recommendation. Infer the task, search current sources, verify candidate skills, rank them, and return the best single skill or skill combination the user can actually use.

Typical requests:

- "I need a skill for coding standards."
- "I want to do a video editing task. Which skills should I use?"
- "I am a painter. Give me the right skills."
- "Find the best GitHub skill for data analysis."

## Core Principles

- Understand the job before searching keywords. Do not only match the user's literal words.
- Always prioritize `https://skillsmp.com/search` and GitHub; expand to official docs, curated registries, awesome lists, marketplace pages, release notes, and author sites when helpful.
- Because skill listings, repos, installation instructions, and maintenance status change over time, verify current information online before recommending.
- Base recommendations on evidence: source links, last activity, README or skill instructions, platform fit, install path, license, and maintenance risk.
- Prefer a short, precise list. Default to 3-7 candidates; if the user asks for the best option, provide one primary recommendation plus 2 alternatives.
- For vague requests, make reasonable inferences and state them. Ask a clarifying question only when platform, privacy, budget, or installation constraints cannot be safely inferred.
- Do not present unverified, nonexistent, stale, or source-unclear skills as definite recommendations.

## Quick Workflow

1. Parse intent:
   - Domain: coding, design, video editing, painting, data, documents, presentations, research, automation, browser, GitHub, product work, etc.
   - Output: one skill, a skill stack, comparison, installation guidance, or alternatives.
   - Platform constraints: Codex skill, ChatGPT GPT/Action, MCP, plugin, CLI, agent workflow.
   - Implied capabilities: for example, "painter" may imply image generation, reference management, portfolio writing, color analysis, social media publishing, copyright, or contracts.

2. Generate search terms:
   - User's wording + synonyms + domain + `skill` + `Codex skill` + `AI agent skill`.
   - English terms even for non-English requests, because skill names and READMEs are often English.
   - Site-specific searches:
     - `site:skillsmp.com/search <keywords>`
     - `site:skillsmp.com <keywords> skill`
     - `site:github.com <keywords> codex skill`
     - `site:github.com <keywords> SKILL.md`

3. Search sources:
   - First: `https://skillsmp.com/search`.
   - First: GitHub repositories, directories, `SKILL.md` files, releases, issues, and READMEs.
   - Then: official registries, author pages, docs sites, package/plugin marketplaces, and reputable curated lists.
   - For non-English users, search in both the user's language and English.

4. Filter candidates:
   - Keep only candidates with a clear name, purpose, and source URL.
   - Keep candidates with an identifiable install/use path, or at least a locatable skill directory/repository.
   - Exclude irrelevant results, pure articles without usable skills, dead pages, mirror spam, and source-unclear entries.
   - For safety-sensitive work such as medical, legal, financial, or account automation, call out limits, trust level, and need for human review.

5. Score and rank:
   - Need fit: 0-5.
   - Installability/usability: 0-5.
   - Maintenance activity: 0-5, based on commits, releases, issues, or update dates.
   - Documentation quality: 0-5, based on README, examples, parameters, and stated limits.
   - Trust: 0-5, based on author, stars/forks, license, community references, or official status.
   - Deduct for stale repos, excessive permissions, unclear install instructions, closed source, exaggerated claims, or platform mismatch.

6. Verify top candidates:
   - Open the candidate source, not just the search result snippet.
   - Check the README or `SKILL.md` for actual capabilities.
   - Check latest activity or update date; if unknown, mark it as "activity not confirmed."
   - For GitHub skills, look for a valid skill structure such as `SKILL.md`, `agents/openai.yaml`, `scripts/`, `references/`, or `assets/`.
   - For skillsmp.com results, verify title, description, install entry, author, or source link.

## Recommendation Format

Default to the user's language unless they ask otherwise.

Return:

1. Conclusion: one sentence naming the best skill or skill stack.
2. Recommendation table:
   - Name
   - Best-fit use case
   - Source link
   - Evidence for trust
   - Main limitation or risk
   - Recommendation level: Strong / Recommended / Optional / Caution
3. Best workflow stack:
   - For a single task, provide the primary skill plus alternatives.
   - For a complex task, provide a chain such as "asset collection -> editing -> subtitles -> publishing."
4. Install or usage advice:
   - For Codex skills, include repository path, skill directory, install command, or manual copy path when verified.
   - If install steps cannot be verified, say "I cannot confirm the install method yet" and give the next verification step.
5. Evidence and date:
   - List verified links.
   - State "Verified on YYYY-MM-DD."

## Handling Ambiguous Requests

For identities, roles, or broad goals, break the request into likely workflows before recommending.

- "I am a painter": image references, color palettes, portfolio organization, artist statements, copyright/contracts, social media, exhibition applications.
- "I need video editing": editing, subtitles, transcription, B-roll search, audio cleanup, thumbnails, publishing copy.
- "Coding standards": linting, code review, architecture rules, commit conventions, documentation standards, language/framework-specific rules.
- "Research": paper search, citation management, data analysis, charts, experiment notes, academic writing.

Start with: "I understand your need as..." and then recommend the closest skill or stack.

## Search Strategy Details

Use multiple queries; do not rely on a single result:

```text
<user keywords> skill
<user keywords> Codex skill
<English domain term> agent skill GitHub
site:github.com <English domain term> SKILL.md
site:skillsmp.com <user keywords>
site:skillsmp.com/search <English domain term>
```

If results are weak:

- Expand synonyms, such as video editing -> post-production, captioning, transcription, ffmpeg.
- Search underlying tool ecosystems, such as `ffmpeg skill`, `premiere automation skill`, or `davinci resolve skill`.
- Check GitHub topics, READMEs, and awesome lists.
- Check official platform or plugin marketplaces.
- Say clearly when no reliable ready-made skill was found, then suggest the scope for creating a new skill.

## Rigor Checklist

Before recommending, verify:

- The name and link are real and openable.
- Recommendation reasons come from page content, not search snippet guesses.
- The skill matches the user's platform and task.
- There is no more official, more active, or more specific alternative.
- A tool/library/plugin is not mislabeled as a skill; if it is not a skill, mark it as an alternative tool.
- A full workflow may require multiple skills.
- Safety, privacy, copyright, account-ban, or license risks are called out.

## Example Output Skeleton

```markdown
I understand your need as: you want to operationalize coding standards, not just format code. That includes review, linting, commit conventions, and team rule documentation.

Best recommendation: ...

| Recommendation | Source | Why it fits | Risk |
|---|---|---|---|
| ... | ... | ... | ... |

Best stack:
1. ... for ...
2. ... for ...

Verified on 2026-05-05 from these sources: ...
```

## When Uncertain

- If result quality is low, do not pad the list. State that no high-confidence match was found and provide the closest candidates.
- If the user asks for maximum accuracy, recommend fewer results with stronger evidence.
- If login, private repos, or paid access blocks verification, mark those parts as unverified.
- If the user wants installation help, confirm the target environment first unless Codex can be reasonably inferred.
