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

When this index was refreshed on **2026-10-30 (UTC+08:00)**, GitHub's public `author:huong8373tt-beep is:pr is:merged` query returned **111 merged Pull Requests** authored by this account.

The engineering work covers reliability, type safety, evaluator correctness, Windows compatibility, testing, cloud configuration, compiled-kernel correctness, storage behavior, mobile accessibility, runtime policy enforcement, OpenTelemetry compatibility, and CLI configuration behavior.

### Recent merged contributions

| Project | Merged contribution | Scope |
| --- | --- | --- |
| AMD GAIA | [#6141](https://github.com/amd/gaia/pull/6141), [#6131](https://github.com/amd/gaia/pull/6131), [#6127](https://github.com/amd/gaia/pull/6127), [#6119](https://github.com/amd/gaia/pull/6119), [#6097](https://github.com/amd/gaia/pull/6097), [#6096](https://github.com/amd/gaia/pull/6096), [#6087](https://github.com/amd/gaia/pull/6087), [#6083](https://github.com/amd/gaia/pull/6083), [#6081](https://github.com/amd/gaia/pull/6081), [#6074](https://github.com/amd/gaia/pull/6074), [#6069](https://github.com/amd/gaia/pull/6069), [#6057](https://github.com/amd/gaia/pull/6057), [#6113](https://github.com/amd/gaia/pull/6113) | Improves Documents-folder and remaining chat-workspace tool resolution; prevents undelivered reminder promises; reports settings persistence failures; makes timestamp-tied chat ordering deterministic; restores the Debian desktop command; and adds targeted Slack, email, RAG, UI, TUI, and specification coverage. |
| Tencent TeamAI CLI | [#1571](https://github.com/Tencent/teamai-cli/pull/1571), [#1569](https://github.com/Tencent/teamai-cli/pull/1569), [#1567](https://github.com/Tencent/teamai-cli/pull/1567) | Adds Qoder and Qoder CN session support, aligns graph documents with the wiki method, and enables boolean-literal comparison linting. |
| Microsoft WinGet CLI | [#6588](https://github.com/microsoft/winget-cli/pull/6588), [#6587](https://github.com/microsoft/winget-cli/pull/6587), [#6585](https://github.com/microsoft/winget-cli/pull/6585) | Respects `-WhatIf` in PowerShell package commands, reports an uninstall failure when no MSIX package is found, and supports ARM architectures in package-name normalization. |
| Microsoft PyRIT | [#3625](https://github.com/microsoft/PyRIT/pull/3625), [#3610](https://github.com/microsoft/PyRIT/pull/3610), [#3580](https://github.com/microsoft/PyRIT/pull/3580), [#3577](https://github.com/microsoft/PyRIT/pull/3577) | Adds a result-type regression test for async cleanup, propagates one deadline through Docker sandbox invocation, avoids dynamic attribute evaluation during initializer discovery, and preserves `JsonResponseConfig` subclasses reconstructed from metadata. |
| Microsoft VS Code Spring Boot Dashboard | [#450](https://github.com/microsoft/vscode-spring-boot-dashboard/pull/450) | Avoids full system process scans for liveness checks. |
| AMD GAIA | [#6031](https://github.com/amd/gaia/pull/6031), [#6029](https://github.com/amd/gaia/pull/6029), [#6009](https://github.com/amd/gaia/pull/6009), [#5995](https://github.com/amd/gaia/pull/5995), [#6024](https://github.com/amd/gaia/pull/6024), [#6018](https://github.com/amd/gaia/pull/6018), [#6013](https://github.com/amd/gaia/pull/6013), [#6012](https://github.com/amd/gaia/pull/6012), [#6011](https://github.com/amd/gaia/pull/6011), [#6005](https://github.com/amd/gaia/pull/6005), [#6001](https://github.com/amd/gaia/pull/6001), [#5998](https://github.com/amd/gaia/pull/5998), [#5996](https://github.com/amd/gaia/pull/5996), [#5994](https://github.com/amd/gaia/pull/5994), [#5991](https://github.com/amd/gaia/pull/5991), [#5986](https://github.com/amd/gaia/pull/5986), [#5980](https://github.com/amd/gaia/pull/5980), [#5979](https://github.com/amd/gaia/pull/5979), [#5978](https://github.com/amd/gaia/pull/5978), [#5976](https://github.com/amd/gaia/pull/5976), [#5968](https://github.com/amd/gaia/pull/5968), [#5967](https://github.com/amd/gaia/pull/5967) | Adds chat-profile and stopped-relay regression coverage, resolves relative tools in chat workspaces, isolates document tests, and improves installer, memory, UI, npm, daemon, MCP, RAG, and Windows CI reliability. |
| Tencent TeamAI CLI | [#1540](https://github.com/Tencent/teamai-cli/pull/1540), [#1529](https://github.com/Tencent/teamai-cli/pull/1529), [#1527](https://github.com/Tencent/teamai-cli/pull/1527), [#1525](https://github.com/Tencent/teamai-cli/pull/1525), [#1507](https://github.com/Tencent/teamai-cli/pull/1507), [#1499](https://github.com/Tencent/teamai-cli/pull/1499), [#1494](https://github.com/Tencent/teamai-cli/pull/1494), [#1491](https://github.com/Tencent/teamai-cli/pull/1491), [#1474](https://github.com/Tencent/teamai-cli/pull/1474), [#1473](https://github.com/Tencent/teamai-cli/pull/1473) | Makes Claude duplicate guards and CodeBuddy IDE project gates work on Windows; improves workflow and hook tests; preserves split UTF-8 output; delivers culture blocks; and adds cross-workspace member-setting resolution and provenance. |
| OpenTelemetry Kotlin | [#1330](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1330), [#1325](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1325) | Compares byte-array scope attributes by content and enforces span attribute limits in the compatibility layer. |
| Grafana Pathfinder | [#2234](https://github.com/grafana/grafana-pathfinder-app/pull/2234) | Dispatches progress after mark-complete state persists. |

### Selected merged contributions

| Project | Merged contribution | Scope |
| --- | --- | --- |
| Microsoft PyRIT | [#3277](https://github.com/microsoft/PyRIT/pull/3277), [#3281](https://github.com/microsoft/PyRIT/pull/3281), [#3333](https://github.com/microsoft/PyRIT/pull/3333), [#3351](https://github.com/microsoft/PyRIT/pull/3351) | Adds lifecycle context to scenario, service, runtime, and resource-cleanup errors. |
| Microsoft PyRIT | [#3383](https://github.com/microsoft/PyRIT/pull/3383), [#3411](https://github.com/microsoft/PyRIT/pull/3411) | Improves `Self` typing and subclass regression coverage for factories. |
| Microsoft PyRIT | [#3441](https://github.com/microsoft/PyRIT/pull/3441), [#3456](https://github.com/microsoft/PyRIT/pull/3456), [#3472](https://github.com/microsoft/PyRIT/pull/3472), [#3504](https://github.com/microsoft/PyRIT/pull/3504), [#3531](https://github.com/microsoft/PyRIT/pull/3531) | Makes persisted-value, CLI-view, analytics-label, converter, and registry-inspection behavior exhaustive or statically discovered. |
| Microsoft SWE-bench-Live | [#54](https://github.com/microsoft/SWE-bench-Live/pull/54) | Corrects evaluator handling of pytest `XFAIL` outcomes. |
| Microsoft WinGet CLI | [#6582](https://github.com/microsoft/winget-cli/pull/6582) | Fixes export output paths containing Unicode / emoji characters. |
| Tencent TeamAI CLI | [#1264](https://github.com/Tencent/teamai-cli/pull/1264), [#1291](https://github.com/Tencent/teamai-cli/pull/1291) | Isolates hook-reconcile tests from contributor checkouts and makes report-push retries recover an earlier local commit. |
| Tencent BrowserSkill | [#473](https://github.com/Tencent/BrowserSkill/pull/473) | Documents the correct windowless Windows GUI-host startup boundary for a foreground daemon. |
| Tencent WeKnora | [#4595](https://github.com/Tencent/WeKnora/pull/4595), [#4605](https://github.com/Tencent/WeKnora/pull/4605), [#4645](https://github.com/Tencent/WeKnora/pull/4645), [#4655](https://github.com/Tencent/WeKnora/pull/4655) | Reclaims superseded chunks, supports SQLite similar-page lookup, improves phone sign-in visibility, and clarifies PostgreSQL vector-store requirements. |
| Google Stellar Engine | [#338](https://github.com/google/stellar-engine/pull/338), [#339](https://github.com/google/stellar-engine/pull/339), [#340](https://github.com/google/stellar-engine/pull/340) | Fixes Workbench notebook owners, GitLab Cloud SQL private-network wiring, and conditional VPC Service Controls log-sink ingress. |
| HashiCorp Terraform AzureRM | [#33698](https://github.com/hashicorp/terraform-provider-azurerm/pull/33698) | Removes all deleted Logic App Standard app settings in one apply. |
| Alibaba Skill-Up | [#332](https://github.com/alibaba/skill-up/pull/332) | Records recovered agent-judge calls without exposing provider error text. |
| Soneso Stellar Agent Wallet | [#446](https://github.com/Soneso/stellar-agent-wallet/pull/446), [#449](https://github.com/Soneso/stellar-agent-wallet/pull/449) | Validates complete context rules and counts envelope fees in minimum-reserve checks. |
| Flash Linear Attention | [#1353](https://github.com/fla-org/flash-linear-attention/pull/1353) | Preserves `softplus` and `softplus2` names in compiled Triton kernels. |
| Toolism | [#40](https://github.com/rakeshnitb23/toolism/pull/40) | Adds the opt-in `SL103` rule for removing JSON Schema title annotations. |
| Azure SDK for Python | [#49569](https://github.com/Azure/azure-sdk-for-python/pull/49569) | Preserves local parent sampling decisions in the rate-limited sampler. |
| Microsoft Kiota Ruby | [#192](https://github.com/microsoft/kiota-ruby/pull/192) | Derives OAuth default scopes per request and caches tokens by effective scope. |
| HasteHealth | [#1391](https://github.com/HasteHealth/HasteHealth/pull/1391) | Implements the FHIRPath `trim()` string function and conformance coverage. |
| OpenTelemetry Swift | [#1252](https://github.com/open-telemetry/opentelemetry-swift/pull/1252) | Uses the global logger provider by default for `OTelLogHandler`. |
| OpenTelemetry Kotlin | [#1324](https://github.com/open-telemetry/opentelemetry-kotlin/pull/1324) | Reports lifecycle-operation failure for non-SDK tracer and logger providers. |
| AMD GAIA | [#5808](https://github.com/amd/gaia/pull/5808), [#5814](https://github.com/amd/gaia/pull/5814) | Recognizes contracted negation in claims and stabilizes Windows pip stuck-detection coverage. |

## Public benchmark and run records

- **[Harbor Hub public job records](https://hub.harborframework.com/users/huong8373tt-beep/jobs):** 155 published jobs, including the complete 89-task Terminal-Bench 2.1 run and five-run records for 63 Terminal-Bench 4.0 tasks.
- **[Terminal-Bench 2.1 #217](https://github.com/harbor-framework/terminal-bench-2-1/pull/217):** public Terminal-Bench submission record.
- **[SWE-bench-Live MultiLang C++ #63](https://github.com/SWE-bench-Live/submission/pull/63):** public SWE-bench-Live submission record for the multi-language C++ benchmark.
- **[SWE-bench-Live Python Lite #66](https://github.com/SWE-bench-Live/submission/pull/66):** public SWE-bench-Live submission record for the 300-task Python Lite subset.

These benchmarks exercise different parts of an Agent system. Software-engineering tasks provide structured environments, tools, tests, and artifacts that support iterative correction. Open-ended research, evidence evaluation, multimodal understanding, fine-grained constraints, and exact answer generation depend on model capabilities.

The Runtime uses a stable supporting model to apply its reasoning capabilities. Model capability and Runtime design together shape an Agent's performance on complex, long-running work, and the Runtime benefits greatly as model performance improves.

## Notes

Slai is an independently developed Agent framework project. Its design began in April 2026 and reached its current form in early June 2026 through continuous iteration. Slai Agent Runtime continues to run stably.

The developer looks forward to continued advances in foundation models—including deeper reasoning, more open-ended thinking and exploration, stronger attention mechanisms, and faster token generation—which would be a major benefit to Agent Runtime. As models improve, agents can better understand goals, plan multi-step work, explore solutions, and carry tasks through to completion.

The project documents the pain points encountered during the early use of AI, the design ideas formed around those challenges, and their implementation in a long-term personal assistant system.
