
 
# AI UX Patterns
 
Designing AI features is still an emerging practice where interaction patterns like streaming, confidence, editability, and failure recovery are not yet standardized and teams are building shared understanding in real time. This skill captures those evolving patterns and turns them into a usable reference for making consistent product decisions across AI features. It helps map feature ideas directly to proven interaction choices and common edge cases so teams can design and ship with more clarity.

## Frameworks this skill builds on
 
The patterns in this skill are tactical — they answer "what specifically to ship" — and they sit on top of strategic guidelines from established research:
 
- **Microsoft HAX (Human-AI Interaction) guidelines** by Amershi et al. (CHI 2019) are the primary anchor. HAX defines 18 design guidelines for AI products at the strategic level ("Make clear what the system can do," "Convey the consequences of user actions"). This skill operationalizes HAX — mapping each pattern to one or more guidelines and adding the specific UI choices, copy, and failure modes HAX doesn't go into.
- **Google PAIR Guidebook** and **NN/g's AI usability heuristics** inform several patterns, especially around input scaffolding, error recovery, and the philosophy of designing for uncertainty.
See `references/_frameworks.md` for the full pattern-to-HAX mapping, the guidelines not yet operationalized (kept honest about gaps), and citation info.
 
## When to use
 
Use this skill any time the user is making AI feature design decisions — early scoping, design critique, spec review, or post-launch debugging. Don't wait for them to say "pattern." If they describe an AI feature and ask "how should this work" or "what are we missing," map it to patterns.
 
## How to use
 
1. **Get the feature description.** One or two sentences is enough. If the user gave less, ask: "What's the feature, who's the user, and where does it live in the product?" Don't go deeper than that — the patterns are the value, not a full discovery interview.
2. **Identify which patterns apply.** Most AI features touch four to seven patterns from the index below. Don't force all fifteen — pick the ones that genuinely matter for this feature. If you're unsure whether a pattern applies, lean toward including it as Consider rather than dropping it.
3. **Rank each pattern** by criticality. Use these definitions:
   - **Must address** — if undesigned, the feature breaks or trust collapses badly. The designer can't ship without addressing this. Usually 2-3 patterns.
   - **Should address** — noticeably better with this designed; designer can defer for v1 if they're explicit about it. Usually 1-3 patterns.
   - **Consider** — relevant under specific conditions. Worth surfacing so the designer can decide whether to dig in. Usually 1-3 patterns.
4. **Read reference files only for Must and Should patterns.** Each pattern lives in `references/<pattern-name>.md`. Distill for the feature at hand — don't recite the reference verbatim. Consider patterns can be summarized from memory in one line; you don't need to read their reference files.
5. **Write the TL;DR.** Two to three sentences naming the central tension and the highest-leverage decisions. The designer should be able to stop reading there if they only need direction.
6. **Write detail blocks for Must and Should patterns** using the format below. Skip detail blocks for Consider patterns — the one-line summary in the ranking section is enough.
7. **End with "The hard part" summary** — two to three sentences naming the central tension. Designers steal this language for design reviews, so make it useful.
## Output format
 
Use this exact structure. The combination of TL;DR + ranking + lighter detail blocks is what makes the output scannable for designers under time pressure.
 
```
### [Feature in one phrase]
 
[2-3 sentence TL;DR. Name the central tension and the 2-3 highest-leverage decisions for this feature. The designer should be able to stop reading here if they only need direction.]
 
---
 
**Must address**
- **[Pattern name]** — [one-line summary of why this is critical for this feature]
- [...]
 
**Should address**
- **[Pattern name]** — [one-line summary of why this matters but isn't critical]
- [...]
 
**Consider**
- **[Pattern name]** — [one-line summary of when this becomes relevant]
- [...]
 
---
 
[For each pattern in Must address and Should address, write a detail block:]
 
#### [Pattern name]
The decision: [the question the designer needs to answer]
Recommendation: [concrete UI guidance, with specific elements/copy/thresholds where possible]
Watch for: [what teams ship that breaks — be specific about the broken behavior]
Revisit if: [the signal that this decision was wrong]
 
[Do NOT write detail blocks for Consider patterns. The one-line summary above is enough — they're flagged so the designer can dig in if they want, but the skill shouldn't force the depth.]
 
---
 
**The hard part:** [Two or three sentences naming the central tension. This is the designer's elevator pitch in their next design review.]
```
 
Notes on the format:
- The TL;DR is the most important part. Designers under time pressure read only it; make sure it earns its place by naming the tension specifically (not "trust matters").
- Bold the pattern *names* in the ranking section but not the line content. The eye should land on substance, not labels.
- Inside detail blocks, the field labels ("The decision:", "Recommendation:") are NOT bolded. The lighter visual treatment is intentional — heavy bolding on every line makes the output dense and harder to scan.
- "Watch for" replaces older "Failure mode" language because it sounds more like a designer at a whiteboard and less like a reference textbook. Same content, warmer voice.
## Voice
 
Write like someone who has been burned by these patterns, not like someone who read about them. Specific examples beat principles every time:
 
- Weak: "Confidence indicators help users calibrate trust."
- Strong: "Showing a 73% confidence score sounds precise but users round it to 'might be wrong.' If you can't act differently at 73 vs. 91, hedge in language ('I'm not sure, but...') instead of a number."
Avoid AI-design clichés ("delight," "magic," "reduce cognitive load," "leverage," "unlock"). Name specific UI elements, specific copy, specific anti-patterns. Where there's research to point to, name it briefly. Where there's only opinion, own that with "I'd lean toward X because Y."
 
The reason: this skill is read by designers who can tell within ten seconds whether the writer has shipped AI features or just read about them. Generic advice gets ignored; specific advice gets quoted in design reviews.
 
## Pattern index
 
The full pattern set lives in `references/`. Read only the files for the patterns you'll discuss in the output. Each file is short — a paragraph or two — so reading two or three is cheap.
 
The first pattern, **designing-for-uncertainty**, is foundational — it's the meta-frame that the other patterns operationalize. Read it for almost every feature even when you don't write a block about it explicitly; it informs which trust surfaces matter most.
 
1. **designing-for-uncertainty** — the binary→probabilistic shift; trust as a designed surface; source/confidence/boundary signals
2. **streaming-vs-batch** — when to stream output, how to handle interruption, what NOT to make clickable mid-stream
3. **citations-and-sources** — inline vs. footnoted, hover behavior, dead-link handling, when citations hurt
4. **rag-and-retrieval-ux** — surfacing what was retrieved, what wasn't, and how the user steers the search
5. **confidence-and-hedging** — score vs. badge vs. language; when confidence indicators backfire
6. **refusal-and-fallback** — "I don't know" UX; how to avoid dead-ends; offering an out
7. **regenerate-and-undo** — placement, labeling, history surfacing, "regenerate from here"
8. **latency-and-loading** — skeleton vs. shimmer vs. status text; what users tolerate vs. abandon
9. **input-scaffolding** — chat vs. form vs. hybrid; suggested prompts; constraint surfacing
10. **editable-output** — when to make AI output directly editable; tracking user edits; re-running with edits in context
11. **memory-and-context** — what the AI remembers (session, user, team); inspectable and editable memory surfaces
12. **feedback-and-correction** — thumbs up/down vs. granular correction vs. behavioral signals; when each is worth designing
13. **permissions-and-safety-friction** — confirm-before-action, dry-run, undo windows for agentic features
14. **agent-roles-and-boundaries** — tool/assistant/copilot/agent; scope, approval thresholds, reporting cadence, stop conditions
15. **empty-and-first-run** — what to show before the user has used the feature; the "what can I ask?" problem
## Patterns NOT to recommend
 
A few patterns get hyped but rarely earn their place. Avoid suggesting:
- Personality / "AI as character" framing unless the brand explicitly calls for it
- Animated typing dots that aren't tied to actual streaming
- Confidence percentages without an action that changes at different thresholds
- "Magic" or "✨" language in copy
If the user asks about these directly, explain why they often hurt more than they help. The reason to flag this list explicitly: AI feature design is full of cargo-culted patterns that ship because they look like other AI products, not because they work.
 
## Edge cases
 
**The user describes a non-AI feature.** Tell them the skill is for AI features specifically and ask if they meant to invoke a different design skill. Don't try to apply the patterns to non-AI UX — the recommendations won't be specific or useful.
 
**The user gives a one-word description ("chatbot").** Ask one clarifying question: who's the user and what's the job-to-be-done. Then proceed.
 
**The user asks about a pattern not in the index.** If it's a real AI UX pattern (e.g., multi-turn correction, RAG attribution, tool-call previews), respond from general design knowledge but flag that it's outside the indexed set. Don't fabricate a reference file.
 
**The feature is agentic (takes actions, not just generates content).** Patterns 9 (permissions) and 5 (regenerate/undo) carry more weight. Lead with permissions — agentic features fail catastrophically when this is wrong, and gently when content patterns are wrong.
