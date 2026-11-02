# Slai Agent Runtime

Slai is a privately developed, cross-platform Agent Runtime for work that needs to continue beyond a single conversation, device, or session.

It can be deployed in two forms:

- A **personal long-running Agent Runtime**, deployable on Windows, Linux, macOS, and Android. A personal deployment can coordinate authorized devices across platforms. For example, a Windows deployment can work with Linux, macOS, and Android devices, while an Android deployment can delegate larger or longer-running tasks to other platforms.

- An **account-isolated, multi-tenant server Runtime**. One continuously running process can serve multiple accounts while keeping their work and resources separate. It can coordinate the computers, Android devices, server nodes, and other connected resources authorized for each account while continuing long-running work.

Both deployment forms provide the same core capabilities: multiple interaction channels—including web interfaces, applications, WeChat, QQ, Feishu, and voice—cross-platform operations, understanding goals, investigating problems, making plans, using tools, carrying work forward, checking results, and operating across authorized platforms and devices.

A task can start on one device, use another authorized node for platform-specific work, and return its logs, artifacts, and follow-up work to the same account.

Slai is not tied to any single model provider. Deployments can use mainstream
standard-compatible model APIs, while task execution, tool use, device
coordination, and result checking remain in the Runtime.

Slai's core capabilities come from strong context management and reliable progress on the main task. The Runtime keeps execution aligned with the user's instructions and the ongoing task.

## Why this exists

Slai's developer does not have a programming background and does not need to write code directly to take part in software engineering.

The developer usually expresses a direction, goal, or problem in short, natural language. Slai then investigates the situation, reads code and documentation, identifies the relevant constraints, and works toward a checkable outcome:

```text
Goal or problem
→ investigation and judgment
→ implementation and testing
→ result verification
→ public contribution, record keeping, or follow-up work
```

The developer's role is to provide direction, goal descriptions, and feedback from using Slai. That feedback also helps Slai find, maintain, and improve its own runtime framework.

This is an ongoing experiment in human–AI collaboration: lowering the knowledge barrier that keeps many people from participating in real software engineering, while using AI to carry ideas through to implementations, tests, contributions, and results.

## Model training and capability research

Slai Agent Runtime primarily uses cloud-model APIs for engineering work today. [Slai Model Lab](https://github.com/huong8373tt-beep/slai.life-model-lab-docs) is a separate private system for training, model runtime, and experimentation. It explores a longer-term direction in which individuals can train, operate, and evaluate more of their own models as personal compute, hardware efficiency, and accessible models improve.

The systems are complementary: Runtime work can organize structured task experience, while Model Lab studies how selected private experience can be reviewed, used for training, and evaluated before informing later Runtime work. Its experiments span text, speech, image, video, multimodal, and homegrown models.

Together, they develop the training, model-operation, and evaluation foundations for future personal AI systems.

## Local runtime and cloud control plane

Slai can run on, or connect to:

```text
Windows · Linux · macOS · Android
```

Local deployments support conversation, research, file and browser work, authorized desktop or device operations, builds, tests, evaluations, and open-source collaboration.

### Multi-agent and authorized-device coordination

The runtime has native foreground/background agent coordination. A task can move between runtime instances, ports, and authorized cross-platform nodes, then return its results and follow-up work to the same project. Authorized Android devices can provide device operations; registered Linux servers can provide controlled builds, tests, downloads, and maintenance work.

### Long-running work

A work thread can continue through tool runs, test failures, CI waits, reviews, checkpoints, and recoverable restarts for hours or days; a project can be maintained across days or months. The ongoing task is preserved across sessions, allowing authorized users to view or continue it from another connected device.

In observed continuous, non-cold-start work, stable requests and provider prompt-cache reuse can yield roughly **95–99%** input-token cache hits, varying by provider, model, and task.

### Cloud control plane

An optional server deployment can stay online to coordinate an account's authorized nodes and route platform-specific work without depending on one foreground device. With account-owner direction and authorization, Slai can carry work from investigation and implementation through validation, Pull Request follow-up, and record keeping. A queued task, a running job, and a verified result are treated as different states.

## Public upstream contributions

### How public upstream contribution work began

Slai's public upstream contribution work began unexpectedly on August 25, 2026.

While running SWE-bench-Live benchmark tasks, Slai Agent Runtime independently found that the migrated evaluator did not preserve the original SWE-bench semantics for pytest `XFAIL` results. Rather than treating this only as a local benchmark issue, it investigated the evaluator behavior, checked the original grading rules, prepared a focused patch, and submitted it to the official Microsoft repository:

- [microsoft/SWE-bench-Live #54](https://github.com/microsoft/SWE-bench-Live/pull/54) - Fix evaluator handling of pytest `XFAIL` outcomes.

The SWE-bench-Live maintainer publicly thanked this account for the detailed report, confirmed that the migrated evaluator needed to preserve the original SWE-bench behavior, and merged the fix on August 29, 2026. The developer also received the maintainer notification through GitHub email.

After seeing Slai identify the issue, investigate it, implement the correction, and contribute a useful upstream fix, the developer authorized Slai to participate in open-source contributions. The developer provides the account, direction, operating boundaries, and submission responsibility; Slai handles investigation, implementation, testing, submission, and follow-up through normal upstream review processes.

### From code generation to completed contributions

Many Agents can now read code and generate plausible fixes. In real upstream work, however, implementation is only one stage: the harder task is carrying a real problem through repository rules, technical evidence, automated checks, maintainer feedback, and final delivery.

Slai uses public upstream contribution work as a practical test of that end-to-end capability. Depending on the repository and issue, a contribution can require:

1. Identifying a real, useful problem.
2. Reading issues, discussions, reports, and user feedback.
3. Understanding maintainer intent, plans, and constraints.
4. Reading contribution guides, engineering rules, and project conventions.
5. Confirming that external contribution and any required agreements are allowed.
6. Searching issues, Pull Requests, branches, and commits to avoid duplicate work.
7. Defining the problem boundary, contribution scope, and acceptance criteria.
8. Obtaining the source and establishing a reproducible baseline.
9. Preparing dependencies, build tooling, and the test environment.
10. Reproducing the original problem before changing code.
11. Reading the relevant architecture, call paths, and data flow.
12. Determining the root cause rather than only treating a symptom.
13. Designing and implementing the smallest project-compatible fix.
14. Checking compatibility, error paths, edge cases, and platform behavior.
15. Adding regression coverage for the reported behavior.
16. Running targeted tests, full tests, builds, formatting, and static checks as required.
17. Reviewing the final diff, commits, artifacts, and change boundaries.
18. Preparing a clear Pull Request with the problem, approach, and verification evidence.
19. Following CI, maintainer review, requested changes, rebases, and merge conflicts.
20. Confirming the merged state and retaining publicly verifiable records.

The difficult part is therefore not merely generating a function. It is maintaining sound judgment across problem selection, repository rules, environment setup, implementation, validation, communication, and follow-through until the result is genuinely deliverable. Slai treats public contributions not as a count of submissions, but as a real-world test of whether an Agent can complete a reviewable engineering loop.

When this index was refreshed on **2026-11-02 (UTC+08:00)**, GitHub's public `author:huong8373tt-beep is:pr is:merged` query returned **179 merged Pull Requests** authored by this account.

The engineering work covers reliability, type safety, evaluator correctness, Windows compatibility, testing, cloud configuration, compiled-kernel correctness, storage behavior, mobile accessibility, runtime policy enforcement, OpenTelemetry compatibility, CLI configuration behavior, security scanning, process lifecycle handling, and SDK authentication.

### Recent merged contributions

Recent work from the latest merged wave spans agent runtime behavior, developer tooling, memory safety, security analysis, cloud infrastructure, and test reliability.

| Project | Merged contribution | Scope |
| --- | --- | --- |
| AMD GAIA | [#6386](https://github.com/amd/gaia/pull/6386), [#6350](https://github.com/amd/gaia/pull/6350), [#6288](https://github.com/amd/gaia/pull/6288), [#6281](https://github.com/amd/gaia/pull/6281), [#6280](https://github.com/amd/gaia/pull/6280), [#6279](https://github.com/amd/gaia/pull/6279), [#6278](https://github.com/amd/gaia/pull/6278), [#6274](https://github.com/amd/gaia/pull/6274), [#6273](https://github.com/amd/gaia/pull/6273), [#6267](https://github.com/amd/gaia/pull/6267), [#6255](https://github.com/amd/gaia/pull/6255) | Makes evaluation-fixture publication atomic and recoverable; protects TUI configuration reads and writes with shared locks; exposes loaded model state; normalizes invalid trailing assistant messages; reports failed saves; adds Telegram force-stop; exercises release locking against real Git; isolates test state; and improves Windows cleanup, opt-in 3D generation, and documentation integrity. |
| Tencent TeamAI CLI | [#1648](https://github.com/Tencent/teamai-cli/pull/1648), [#1646](https://github.com/Tencent/teamai-cli/pull/1646), [#1645](https://github.com/Tencent/teamai-cli/pull/1645), [#1642](https://github.com/Tencent/teamai-cli/pull/1642), [#1641](https://github.com/Tencent/teamai-cli/pull/1641), [#1639](https://github.com/Tencent/teamai-cli/pull/1639), [#1638](https://github.com/Tencent/teamai-cli/pull/1638), [#1635](https://github.com/Tencent/teamai-cli/pull/1635), [#1634](https://github.com/Tencent/teamai-cli/pull/1634), [#1632](https://github.com/Tencent/teamai-cli/pull/1632) | Strengthens type-aware linting, agent indexes, uninstall cleanup for relocated tool homes, cross-platform path handling, diagnostics, and user-rule behavior. |
| Microsoft PyRIT | [#3654](https://github.com/microsoft/PyRIT/pull/3654), [#3625](https://github.com/microsoft/PyRIT/pull/3625), [#3610](https://github.com/microsoft/PyRIT/pull/3610), [#3580](https://github.com/microsoft/PyRIT/pull/3580), [#3577](https://github.com/microsoft/PyRIT/pull/3577) | Improves exhaustive token dispatch, gather-result typing, Docker-sandbox deadline propagation, safe initializer discovery, and response-config subclass preservation in Microsoft's generative-AI security evaluation framework. |
| ThatOpen web-ifc | [#2331](https://github.com/ThatOpen/engine_web-ifc/pull/2331) | Releases native vectors used for GUID mapping on both success and exceptional paths, with regression coverage for WebAssembly resource cleanup. |
| Stellar Agent Wallet | [#532](https://github.com/Soneso/stellar-agent-wallet/pull/532) | Corrects a CLI command-index link and verifies the documentation/install surface with the project's preflight gates. |
| CI/CD security | [glsec #1111](https://github.com/glsec/glsec/pull/1111), [#1112](https://github.com/glsec/glsec/pull/1112) | Corrects GitLab CI security rules for environment teardown actions and protected CI variables, with Go regression coverage. |

### Selected merged contributions

Selected work across major technology companies, developer platforms, cloud infrastructure, observability, security, and lower-level runtimes.

| Project | Merged contribution | Scope |
| --- | --- | --- |
| Microsoft SWE-bench-Live | [#54](https://github.com/microsoft/SWE-bench-Live/pull/54) | Corrects evaluator handling of pytest `XFAIL` outcomes, preserving original SWE-bench grading semantics. |
| Microsoft PyRIT | [#3277](https://github.com/microsoft/PyRIT/pull/3277), [#3281](https://github.com/microsoft/PyRIT/pull/3281), [#3333](https://github.com/microsoft/PyRIT/pull/3333), [#3351](https://github.com/microsoft/PyRIT/pull/3351), [#3383](https://github.com/microsoft/PyRIT/pull/3383), [#3411](https://github.com/microsoft/PyRIT/pull/3411), [#3441](https://github.com/microsoft/PyRIT/pull/3441), [#3456](https://github.com/microsoft/PyRIT/pull/3456), [#3472](https://github.com/microsoft/PyRIT/pull/3472), [#3504](https://github.com/microsoft/PyRIT/pull/3504), [#3531](https://github.com/microsoft/PyRIT/pull/3531), [#3577](https://github.com/microsoft/PyRIT/pull/3577), [#3580](https://github.com/microsoft/PyRIT/pull/3580), [#3610](https://github.com/microsoft/PyRIT/pull/3610), [#3625](https://github.com/microsoft/PyRIT/pull/3625), [#3654](https://github.com/microsoft/PyRIT/pull/3654) | Lifecycle diagnostics, typing, sandbox deadlines, registry discovery, CLI behavior, converters, analytics labels, and security-evaluation runtime reliability. |
| Microsoft Azure SDK for Python | [#49569](https://github.com/Azure/azure-sdk-for-python/pull/49569) | Preserves OpenTelemetry rate-limited sampling decisions across child spans and requests. |
| Microsoft WinGet CLI | [#6582](https://github.com/microsoft/winget-cli/pull/6582), [#6585](https://github.com/microsoft/winget-cli/pull/6585), [#6587](https://github.com/microsoft/winget-cli/pull/6587), [#6588](https://github.com/microsoft/winget-cli/pull/6588) | Improves Unicode and ARM package-path handling, uninstall failure reporting, and PowerShell `-WhatIf` behavior. |
| Microsoft VS Code ecosystem | [Spring Boot Dashboard #450](https://github.com/microsoft/vscode-spring-boot-dashboard/pull/450) | Replaces full-machine process scans with targeted Node liveness checks, removing a dependency and reducing Windows watchdog overhead. |
| Microsoft Kiota | [Ruby #192](https://github.com/microsoft/kiota-ruby/pull/192) | Derives OAuth default scopes per request and keys cached tokens by effective scope, preventing cross-host token reuse. |
| AMD GAIA | [#6176](https://github.com/amd/gaia/pull/6176), [#6152](https://github.com/amd/gaia/pull/6152), [#6151](https://github.com/amd/gaia/pull/6151), [#6150](https://github.com/amd/gaia/pull/6150), [#6120](https://github.com/amd/gaia/pull/6120), [#6080](https://github.com/amd/gaia/pull/6080) | Recovers connector saves after crashes; preserves explicit context-window choices; serializes database upgrades; validates VRAM; improves Undo semantics; and packages starter skills. |
| Tencent TeamAI CLI | [#1600](https://github.com/Tencent/teamai-cli/pull/1600), [#1601](https://github.com/Tencent/teamai-cli/pull/1601), [#1604](https://github.com/Tencent/teamai-cli/pull/1604), [#1642](https://github.com/Tencent/teamai-cli/pull/1642), [#1645](https://github.com/Tencent/teamai-cli/pull/1645), [#1648](https://github.com/Tencent/teamai-cli/pull/1648) | Handles BOM-prefixed configuration, moves policy checks into lint tooling, protects cross-platform home resolution, maintains agent indexes, and cleans replaced tool homes. |
| Tencent WeKnora | [#4595](https://github.com/Tencent/WeKnora/pull/4595), [#4605](https://github.com/Tencent/WeKnora/pull/4605), [#4645](https://github.com/Tencent/WeKnora/pull/4645), [#4655](https://github.com/Tencent/WeKnora/pull/4655) | Reclaims superseded chunks, supports SQLite similar-page lookup, improves phone sign-in visibility, and clarifies PostgreSQL vector-store requirements. |
| Tencent BrowserSkill | [#473](https://github.com/Tencent/BrowserSkill/pull/473) | Clarifies daemon startup for windowless GUI hosts. |
| Google Stellar Engine | [#338](https://github.com/google/stellar-engine/pull/338), [#339](https://github.com/google/stellar-engine/pull/339), [#340](https://github.com/google/stellar-engine/pull/340) | Fixes notebook ownership, GitLab Cloud SQL private-network wiring, and conditional VPC Service Controls log-sink ingress. |
| Alibaba Skill-up | [#332](https://github.com/alibaba/skill-up/pull/332) | Discloses recovered agent judge calls in evaluation reports. |
| HashiCorp Terraform AzureRM | [#33698](https://github.com/hashicorp/terraform-provider-azurerm/pull/33698) | Removes all deleted Logic App Standard app settings in one apply. |
| Grafana Pathfinder | [#2234](https://github.com/grafana/grafana-pathfinder-app/pull/2234) | Dispatches progress only after completion persistence succeeds. |
| OpenTelemetry | [Swift #1252](https://github.com/open-telemetry/opentelemetry-swift/pull/1252), [Kotlin #1324](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1324), [#1325](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1325), [#1330](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1330) | Improves global logger-provider behavior, lifecycle failure reporting, byte-array attribute comparison, and span attribute limits. |
| Flash Linear Attention | [#1353](https://github.com/fla-org/flash-linear-attention/pull/1353) | Preserves `softplus` names in Inductor-generated Triton kernels without changing numerical algorithms or backend selection. |
| CI/CD security | [glsec #1111](https://github.com/glsec/glsec/pull/1111), [#1112](https://github.com/glsec/glsec/pull/1112) | Strengthens GitLab CI security analysis for teardown semantics and contributor-controlled variables. |
| Stellar Agent Wallet | [#446](https://github.com/Soneso/stellar-agent-wallet/pull/446), [#449](https://github.com/Soneso/stellar-agent-wallet/pull/449) | Validates ContextRule data before deriving counts and includes envelope fees in minimum-reserve checks. |

### Upstream release acknowledgement

AMD's [GAIA v0.25.2](https://github.com/amd/gaia/releases/tag/v0.25.2), [v0.25.3](https://github.com/amd/gaia/releases/tag/v0.25.3), and [v0.25.4-rc1](https://github.com/amd/gaia/releases/tag/v0.25.4-rc1) release notes list [@huong8373tt-beep](https://github.com/huong8373tt-beep) in their **Contributors** sections. In v0.25.3 and v0.25.4-rc1, the account is the first named community contributor.

The credited work spans chat-workspace and Documents path resolution, daemon restart and foreground-chat behavior, home-first search, gateway-token restoration, context-window and VRAM handling, database upgrades, Undo behavior, vision-model guidance, relay and email behavior, documentation, and test and CI reliability.


## Public benchmark and run records

- **[Harbor Hub public job records](https://hub.harborframework.com/users/huong8373tt-beep/jobs):** 155 published jobs, including the complete 89-task Terminal-Bench 2.1 run and five-run records for 63 Terminal-Bench 4.0 tasks.
- **[Terminal-Bench 2.1 #216](https://github.com/harbor-framework/terminal-bench-2-1/pull/216):** public Terminal-Bench submission record.
- **[SWE-bench-Live MultiLang C++ #63](https://github.com/SWE-bench-Live/submission/pull/63):** public SWE-bench-Live submission record for the multi-language C++ benchmark.
- **[SWE-bench-Live Python Lite #66](https://github.com/SWE-bench-Live/submission/pull/66):** public SWE-bench-Live submission record for the 300-task Python Lite subset.

These benchmarks exercise different parts of an Agent system. Software-engineering tasks provide structured environments, tools, tests, and artifacts that support iterative correction. Open-ended research, evidence evaluation, multimodal understanding, fine-grained constraints, and exact answer generation depend on model capabilities.

The Runtime uses a stable supporting model to apply its reasoning capabilities. Model capability and Runtime design together shape an Agent's performance on complex, long-running work, and the Runtime benefits greatly as model performance improves.

## Notes

Slai is an independently developed Agent framework project. Its design began in April 2026 and reached its current form in early June 2026 through continuous iteration. Slai Agent Runtime continues to run stably.

The developer looks forward to continued advances in foundation models—including deeper reasoning, more open-ended thinking and exploration, stronger attention mechanisms, and faster token generation—which would be a major benefit to Agent Runtime. As models improve, agents can better understand goals, plan multi-step work, explore solutions, and carry tasks through to completion.

The project documents the pain points encountered during the early use of AI, the design ideas formed around those challenges, and their implementation in a long-term personal assistant system.

For questions, collaboration, or other inquiries about Slai and its public engineering work, you are welcome to contact [wlyo@outlook.com](mailto:wlyo@outlook.com).
