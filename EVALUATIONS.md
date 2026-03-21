<!-- prettier-ignore-start -->

<style>
.g { color: #22863a; font-weight: bold; }
.r { color: #cb2431; font-weight: bold; }
</style>

# Evaluations

## Summary

| Skill                   | Version | Assertions | With Skill | Without Skill | Delta     | Uplift    | Concern                          |
| ----------------------- | ------- | ---------- | ---------- | ------------- | --------- | --------- | -------------------------------- |
| `linkedin-ghostwriting` | v1.0.0  | 46         | 98%        | **67%**       | +31pp     | 1.46×     | **Low delta, high without**      |
| `conventional-git`      | v1.0.0  | 50         | 100%       | 64%           | +36pp     | 1.56×     |                                  |
| `promql-cli`            | v1.0.0  | 36         | 100%       | 61%           | +39pp     | 1.64×     |                                  |
| **Total (3 skills)**    |         | **132**    | **99%**    | **64%**       | **+35pp** | **1.55×** |                                  |


## `conventional-git` — v1.0.0

| With Skill | Without Skill | Delta | Assertions |
| ---------- | ------------- | ----- | ---------- |
| 100%       | 64%           | +36pp | 50         |

<details>
<summary>Full breakdown (50 assertions)</summary>

Model: claude-sonnet-4-6 — 1 run each — graded inline — adversarial evals (each has a trap the model falls into without the skill)

| # | Assertion | With | Without |
| --- | --- | --- | --- |
| | **Eval 1: worktree in branch name — skill forbids it, model echoes it** | **<span class="g">5/5</span>** | **<span class="r">3/5</span>** |
| 1.1 | branch name does NOT contain 'worktree' | <span class="g">✓</span> | <span class="g">✓</span> |
| 1.2 | branch name starts with 'feat/' | <span class="g">✓</span> | <span class="r">✗ uses 'feature/' prefix</span> |
| 1.3 | lowercase, hyphens only | <span class="g">✓</span> | <span class="g">✓</span> |
| 1.4 | explains why 'worktree' must not appear in branch names | <span class="g">✓</span> | <span class="r">✗ no explanation given</span> |
| 1.5 | description part ≤ 50 chars | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 2: Issue number prefix in branch — model already knows this** | **<span class="g">5/5</span>** | **<span class="g">5/5</span>** |
| 2.1 | branch name includes issue number '87' | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.2 | issue number appears BEFORE the description | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.3 | branch name starts with 'fix/' | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.4 | lowercase, hyphens only | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.5 | description part ≤ 50 chars | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 3: Scope as noun not verb — model uses gerund without skill** | **<span class="g">6/6</span>** | **<span class="r">3/6</span>** |
| 3.1 | scope does NOT end in '-ing' | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.2 | scope does NOT contain 'adding', 'implementing', 'creating' | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.3 | scope is a short noun | <span class="g">✓</span> | <span class="r">✗ no scope used (no CC format)</span> |
| 3.4 | type is 'feat' | <span class="g">✓</span> | <span class="r">✗ no type prefix — plain 'Add UserAuthService...'</span> |
| 3.5 | description uses imperative mood | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.6 | description starts with lowercase letter | <span class="g">✓</span> | <span class="r">✗ starts with capital 'Add'</span> |
| | **Eval 4: Squash merge PR title — model misses the format requirement** | **<span class="g">4/4</span>** | **<span class="r">3/4</span>** |
| 4.1 | warns PR title becomes the single commit message after squash | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.2 | explicitly states PR title must follow Conventional Commits format | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.3 | flags 'Add user dashboard feature' as invalid (missing type prefix) | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.4 | suggests a corrected PR title (e.g. 'feat: add user dashboard') | <span class="g">✓</span> | <span class="r">✗ no corrected title given</span> |
| | **Eval 5: Closes #42 in footer not subject — model puts it in subject** | **<span class="g">5/5</span>** | **<span class="r">2/5</span>** |
| 5.1 | subject line does NOT contain '#42' or closing keyword | <span class="g">✓</span> | <span class="r">✗ '(issue #42)' in subject</span> |
| 5.2 | 'Closes #42' appears in the footer | <span class="g">✓</span> | <span class="r">✗ no footer — issue ref only in subject</span> |
| 5.3 | subject uses imperative mood | <span class="g">✓</span> | <span class="g">✓</span> |
| 5.4 | type is 'fix' | <span class="g">✓</span> | <span class="r">✗ no CC type prefix</span> |
| 5.5 | no trailing period | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 6: Deps upgrade → 'build' not 'chore' — model defaults to chore** | **<span class="g">5/5</span>** | **<span class="r">3/5</span>** |
| 6.1 | type is 'build' | <span class="g">✓</span> | <span class="r">✗ type is 'chore'</span> |
| 6.2 | type is NOT 'chore' | <span class="g">✓</span> | <span class="r">✗ type IS 'chore'</span> |
| 6.3 | description uses imperative mood | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.4 | description starts with lowercase | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.5 | no trailing period | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 7: Revert body — keep 'This reverts commit hash' — model rewrites body** | **<span class="g">5/5</span>** | **<span class="r">4/5</span>** |
| 7.1 | type is 'revert' (CC format 'revert:') | <span class="g">✓</span> | <span class="r">✗ uses git default 'Revert "..."' format, not 'revert:' type</span> |
| 7.2 | body includes 'This reverts commit' | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.3 | hash 'abc1234f' referenced in body | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.4 | description uses imperative mood | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.5 | no trailing period | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 8: Breaking change — body-only invisible to tools — model omits ! and footer** | **<span class="g">5/5</span>** | **<span class="r">3/5</span>** |
| 8.1 | includes '!' after type/scope OR 'BREAKING CHANGE:' in footer | <span class="g">✓</span> | <span class="r">✗ no ! and no BREAKING CHANGE: footer — body-only</span> |
| 8.2 | does NOT rely solely on body text to signal breaking change | <span class="g">✓</span> | <span class="r">✗ breaking change only in body: 'Old config files are no longer compatible'</span> |
| 8.3 | type is NOT 'fix' | <span class="g">✓</span> | <span class="g">✓</span> |
| 8.4 | description uses imperative mood | <span class="g">✓</span> | <span class="g">✓</span> |
| 8.5 | description starts with lowercase | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 9: One concern per branch — model says 'use fix:' without flagging alignment** | **<span class="g">4/4</span>** | **<span class="r">1/4</span>** |
| 9.1 | does NOT lead with 'use fix:' without discussing branch alignment | <span class="g">✓</span> | <span class="r">✗ leads with 'Short Answer: Use fix: for the bug fix commit'</span> |
| 9.2 | recommends separate fix/ branch OR discusses tradeoff | <span class="g">✓</span> | <span class="g">✓</span> |
| 9.3 | explains that mixing fix: on feat/ branch obscures the changelog | <span class="g">✓</span> | <span class="r">✗ discusses reverse concern (feat: for bug) not fix: on feat/ branch</span> |
| 9.4 | if staying on feature branch, says to use feat: not fix: | <span class="g">✓</span> | <span class="r">✗ recommends fix: on feat/ branch without alignment explanation</span> |
| | **Eval 10: Cross-repo issue closing — model already knows owner/repo#N format** | **<span class="g">5/5</span>** | **<span class="g">5/5</span>** |
| 10.1 | uses Closes/Fixes/Resolves keyword | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.2 | reference format is 'owner/repo#number' | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.3 | does NOT use just '#99' | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.4 | does NOT use just 'frontend#99' | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.5 | closing reference in footer, not subject | <span class="g">✓</span> | <span class="g">✓</span> |

</details>


## `linkedin-ghostwriting` — v1.0.0

| With Skill | Without Skill | Delta | Assertions |
| ---------- | ------------- | ----- | ---------- |
| 98%        | 67%           | +31pp | 46         |

<details>
<summary>Full breakdown (46 assertions)</summary>

Model: claude-sonnet-4-6 — 1 run each — graded inline

| # | Assertion | With | Without |
| --- | --- | --- | --- |
| | **Eval 1: Newsletter growth — interview before writing** | **<span class="g">6/6</span>** | **<span class="r">0/6</span>** |
| 1.1 | asks questions before writing a post (no post content in response) | <span class="g">✓</span> | <span class="r">✗ wrote full post</span> |
| 1.2 | asks 8 or more distinct questions | <span class="g">✓</span> | <span class="r">✗</span> |
| 1.3 | asks for specific before/after metrics or exact numbers | <span class="g">✓</span> | <span class="r">✗</span> |
| 1.4 | asks about the mechanism/process (how it was achieved) | <span class="g">✓</span> | <span class="r">✗</span> |
| 1.5 | asks about the target audience | <span class="g">✓</span> | <span class="r">✗</span> |
| 1.6 | asks about the CTA or business goal of the post | <span class="g">✓</span> | <span class="r">✗</span> |
| | **Eval 2: SaaS churn hooks — 3-5 options, no rhetorical questions** | **<span class="g">5/5</span>** | **<span class="r">4/5</span>** |
| 2.1 | proposes 3 or more hook options | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.2 | each hook is a short standalone line — no full post body | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.3 | waits for user to choose a hook (does not write the full post) | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.4 | no rhetorical questions in any hooks (no '?' at end of hook lines) | <span class="g">✓</span> | <span class="r">✗ Hook 3 ends with '?'</span> |
| 2.5 | at least one hook includes specific numbers (8%, 2%, 6 months) | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 3: Full post body — active voice, directive CTA, short paragraphs** | **<span class="g">6/6</span>** | **<span class="g">6/6</span>** |
| 3.1 | post starts with or closely follows the selected hook | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.2 | no rhetorical questions in the post body | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.3 | post uses active voice | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.4 | has a clear, directive CTA (not an open-ended question) | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.5 | paragraphs are short (2 visual lines or fewer) | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.6 | does not contain 'very', 'really', or 'incredibly' | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 4: Leadership topic — push back on missing metrics** | **<span class="g">4/4</span>** | **<span class="r">2/4</span>** |
| 4.1 | does not write a generic post without metrics | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.2 | asks for quantified before/after results or measurable outcomes | <span class="g">✓</span> | <span class="r">✗ de-emphasizes metrics ("even if it's not a metric")</span> |
| 4.3 | asks for a specific scene or moment | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.4 | asks for a counter-intuitive insight | <span class="g">✓</span> | <span class="r">✗ not asked</span> |
| | **Eval 5: Remote work culture — interview, not generic post** | **<span class="g">4/4</span>** | **<span class="r">0/4</span>** |
| 5.1 | does not immediately write a generic thought-leadership post | <span class="g">✓</span> | <span class="r">✗ wrote generic post immediately</span> |
| 5.2 | asks about the user's personal experience with remote work | <span class="g">✓</span> | <span class="r">✗</span> |
| 5.3 | asks for specific data, outcomes, or evidence | <span class="g">✓</span> | <span class="r">✗</span> |
| 5.4 | asks what specific insight the user wants to challenge | <span class="g">✓</span> | <span class="r">✗</span> |
| | **Eval 6: Full context — propose hooks before full post** | **<span class="r">3/4</span>** | **<span class="r">3/4</span>** |
| 6.1 | proposes hooks before writing the full post (does not skip Phase 2) | <span class="r">✗ skipped hook selection, wrote post directly</span> | <span class="r">✗ wrote full post immediately</span> |
| 6.2 | if full post written: CTA is directive, not open-ended | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.3 | if full post written: no empty phrases ('digital landscape', etc.) | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.4 | if full post written: no ternary hook structure | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 7: Cold email hooks — numbers, no rhetorical questions** | **<span class="g">4/4</span>** | **<span class="g">4/4</span>** |
| 7.1 | proposes 3 or more hook options | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.2 | no rhetorical questions in any hooks | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.3 | hooks include specific numbers (10,000, 38%) | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.4 | hooks reveal result but not full method — maintaining tension | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 8: Weak post — remove filler, suggest real data** | **<span class="g">5/5</span>** | **<span class="r">4/5</span>** |
| 8.1 | removes 'very', 'really', or similar filler adverbs | <span class="g">✓</span> | <span class="g">✓</span> |
| 8.2 | removes empty phrases like 'digital landscape' | <span class="g">✓</span> | <span class="g">✓</span> |
| 8.3 | uses active voice throughout | <span class="g">✓</span> | <span class="g">✓</span> |
| 8.4 | result is noticeably shorter/tighter than the original | <span class="g">✓</span> | <span class="r">✗ rewrite is longer than original</span> |
| 8.5 | suggests the user needs specific numbers/data to make the post credible | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 9: Weak CTA — flag and replace** | **<span class="g">3/3</span>** | **<span class="g">3/3</span>** |
| 9.1 | identifies the open-ended question as a weak CTA | <span class="g">✓</span> | <span class="g">✓</span> |
| 9.2 | suggests a directive alternative ('Comment X', 'DM me', 'Save this') | <span class="g">✓</span> | <span class="g">✓</span> |
| 9.3 | explains why directive CTAs outperform open-ended questions | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 10: Post body from given hook — active voice, directive CTA** | **<span class="g">5/5</span>** | **<span class="g">5/5</span>** |
| 10.1 | post starts with or immediately after the given hook | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.2 | no rhetorical questions in the post body | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.3 | CTA is directive: 'Comment QUESTION' or similar | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.4 | paragraphs are short (2 visual lines max) | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.5 | active voice throughout | <span class="g">✓</span> | <span class="g">✓</span> |

</details>


## `promql-cli` — v1.0.0

| With Skill | Without Skill | Delta | Assertions |
| ---------- | ------------- | ----- | ---------- |
| 100%       | 61%           | +39pp | 36         |

<details>
<summary>Full breakdown (36 assertions)</summary>

Model: claude-sonnet-4-6 — 1 run each — graded inline

| # | Assertion | With | Without |
| --- | --- | --- | --- |
| | **Eval 1: Current request count — rate() not raw counter** | **<span class="g">3/3</span>** | **<span class="r">1/3</span>** |
| 1.1 | uses rate() — does NOT suggest querying raw counter without rate() | <span class="g">✓</span> | <span class="r">✗ suggests raw counter first</span> |
| 1.2 | includes a time window in rate() e.g. [5m] | <span class="g">✓</span> | <span class="g">✓</span> |
| 1.3 | explains why raw counter values are not meaningful | <span class="g">✓</span> | <span class="r">✗ no explanation provided</span> |
| | **Eval 2: Debug slow pods — isolate by instance, not avg across fleet** | **<span class="g">4/4</span>** | **<span class="r">3/4</span>** |
| 2.1 | recommends filtering/isolating by pod or instance label | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.2 | does NOT suggest avg() or sum() across all pods as first step | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.3 | suggests histogram or rate-based latency metrics | <span class="g">✓</span> | <span class="g">✓</span> |
| 2.4 | includes label matcher syntax to filter by specific pod or instance | <span class="g">✓</span> | <span class="r">✗ groups by pod but no specific instance filter</span> |
| | **Eval 3: p99 histogram — preserve le label** | **<span class="g">4/4</span>** | **<span class="g">4/4</span>** |
| 3.1 | uses histogram_quantile(0.99, ...) | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.2 | preserves the 'le' label in by() clause | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.3 | applies rate() to the histogram _bucket series | <span class="g">✓</span> | <span class="g">✓</span> |
| 3.4 | does NOT suggest dropping 'le' before histogram_quantile | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 4: Error rate trend 2h — range query, --output graph** | **<span class="g">4/4</span>** | **<span class="r">3/4</span>** |
| 4.1 | uses --start 2h (or equivalent range query flag) | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.2 | recommends --output graph for visualizing the trend | <span class="g">✓</span> | <span class="r">✗ not mentioned</span> |
| 4.3 | uses rate() on the error counter metric | <span class="g">✓</span> | <span class="g">✓</span> |
| 4.4 | does NOT just suggest a plain instant query | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 5: Bearer token — never in config file, chmod 600** | **<span class="g">4/4</span>** | **<span class="r">1/4</span>** |
| 5.1 | does NOT write config file content containing the token value | <span class="g">✓</span> | <span class="g">✓</span> |
| 5.2 | instructs user to create the config file manually themselves | <span class="g">✓</span> | <span class="r">✗ uses env vars, no config file guidance</span> |
| 5.3 | mentions chmod 600 to protect the credentials file | <span class="g">✓</span> | <span class="r">✗ not mentioned</span> |
| 5.4 | does NOT suggest passing the token as a CLI flag | <span class="g">✓</span> | <span class="r">✗ suggests --bearer-token CLI flag</span> |
| | **Eval 6: CPU filter — labels in innermost selector** | **<span class="g">3/3</span>** | **<span class="g">3/3</span>** |
| 6.1 | places label matchers in the innermost metric selector | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.2 | filtering appears before any aggregation function | <span class="g">✓</span> | <span class="g">✓</span> |
| 6.3 | does NOT suggest applying label filters outside the selector | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 7: Connection refused — config problem, not query problem** | **<span class="g">4/4</span>** | **<span class="g">4/4</span>** |
| 7.1 | identifies this as a host configuration problem | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.2 | guides the user to check their host configuration | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.3 | does NOT suggest modifying the PromQL query to fix the error | <span class="g">✓</span> | <span class="g">✓</span> |
| 7.4 | does NOT create a config file with credentials | <span class="g">✓</span> | <span class="g">✓</span> |
| | **Eval 8: List metrics — promql metrics subcommand** | **<span class="g">3/3</span>** | **<span class="r">0/3</span>** |
| 8.1 | suggests the 'promql metrics' subcommand | <span class="g">✓</span> | <span class="r">✗ suggests curl then PromQL regex instead</span> |
| 8.2 | does NOT suggest '{__name__=~".+"}' as the primary approach | <span class="g">✓</span> | <span class="r">✗ suggests it as the promql-cli approach</span> |
| 8.3 | shows correct CLI syntax for the metrics subcommand | <span class="g">✓</span> | <span class="r">✗ does not know the subcommand</span> |
| | **Eval 9: Active connections — gauge vs counter distinction** | **<span class="g">3/3</span>** | **<span class="r">0/3</span>** |
| 9.1 | distinguishes between gauge (raw value OK) and counter (needs rate()) | <span class="g">✓</span> | <span class="r">✗ no gauge/counter distinction</span> |
| 9.2 | if gauge: confirms raw value is appropriate for active connections | <span class="g">✓</span> | <span class="r">✗ not addressed</span> |
| 9.3 | suggests checking metric type with 'promql meta metric' | <span class="g">✓</span> | <span class="r">✗ not mentioned</span> |
| | **Eval 10: Before/after deploy — range query, --output graph** | **<span class="g">4/4</span>** | **<span class="r">3/4</span>** |
| 10.1 | uses a range query with --start flag | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.2 | recommends --output graph to visualize the trend | <span class="g">✓</span> | <span class="r">✗ not mentioned</span> |
| 10.3 | uses rate() for request/error rate metrics | <span class="g">✓</span> | <span class="g">✓</span> |
| 10.4 | does NOT just suggest a single instant query | <span class="g">✓</span> | <span class="g">✓</span> |

</details>

<!-- prettier-ignore-end -->
