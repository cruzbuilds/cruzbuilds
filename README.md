## Chris Cruz

I design systems for a living and I hate stopping at the diagram. So I build, ship, and operate the things I design, in public, one small project at a time.

Everything here is a personal project. No work material, no customer material, nothing behind a login.

### Built and shipped

**[Legwork](https://dq8b25qx96wy3.cloudfront.net/)** is a three agent research team, live and open to anyone. Ask a technical question and it plans the research, reads GitHub and the open web, and writes a short report where every claim links to its source. It runs on Amazon Bedrock AgentCore with Strands Agents, as a fixed graph of agents rather than an open ended orchestrator, under a hard spend ceiling and per visitor rate limits. The examples on the page point it at security research, such as which vulnerabilities are being actively exploited right now.

**Holmes** is an AI security investigator. Hand it an incident and it forms a hypothesis, decides which lookups could change its verdict (indicator reputation, asset context, ATT&CK technique mapping, served read only by a local MCP server), and stops once the answer is clear. It returns a verdict, the evidence in order, and a proposed response, in plain English a manager can read. It treats the incident as untrusted evidence and flags any text inside it that tries to give instructions. It proposes and never executes. Strands Agents and Claude on Amazon Bedrock, running on synthetic data. A local proof of concept, not public yet.

**[shelflife](https://github.com/cruzbuilds/shelflife)** is one inventory of everything that expires: TLS certificates, domains, API keys, licenses, contracts. It checks what it can check live, reports what is coming due with an owner next to each item, and its exit code is the alert, so a cron job or a CI step is the whole integration. It never renews anything and never stores the secret itself. Names and dates only. Released as v0.1.0, and it has run every morning since 2026-09-17 against the things my own projects depend on.

**[agentic-review-swarm](https://github.com/cruzbuilds/agentic-review-swarm)** is five AI review agents, each with one narrow job and a written list of what it refuses to let through. They read the same change at once and merge into a single verdict. Every agent is tested against planted defects before it is allowed to review anything real. It reviewed every pull request on shelflife: 37 findings, none overridden. Installs in Claude Code and Kiro.

**[Five Critics or One Good Prompt](https://github.com/cruzbuilds/Five-Critics-or-One-Good-Prompt)** is the experiment that tested the swarm instead of assuming it worked. Predictions were sealed before any run. The swarm tied one strong prompt on confirmed defects, 38 each, and a 24 word prompt found every merge blocking defect in every run. Four of five predictions failed, all of it is published, and the result changed the swarm's architecture. [agentic-review-lab](https://github.com/cruzbuilds/agentic-review-lab) is the front door to that whole line of work.

**[project-starter](https://github.com/cruzbuilds/project-starter)** is a template for new projects. One health check wired to CI, guardrails for AI agents working in the repo, decision records, and a place to write down what a project is for before anyone writes code. shelflife started from it.

### What I'm building

**Holmes and the Clean-up Crew.** The next version of Holmes, on Bedrock AgentCore. Holmes investigates an alert and contains the threat; a second agent, the Clean-up Crew, sweeps for the same indicators elsewhere, removes what the attacker left, and hardens against a repeat. Both agents only read and propose. One gate acts on their proposals, people stay informed, and anything can be undone. The design is written around a real cloud cryptojacking pattern. It is not built yet.

**Hybrid review, V2 of the swarm.** Experiment 001 showed the swarm's narrow lanes let its most important finding go unowned. V2 adds one broad reviewer next to the specialists and an arbiter that keeps any serious finding, whichever lane it fits. It is built and evaluated on its own tests, and not yet compared against V1. A V3 branch is exploring bounded agentic investigation.

**Experiment 002.** V2 one pass review against the same reviewers allowed to investigate. The hypotheses and protocol are sealed. Nothing has run.

**Legwork, the deferred pieces.** An AgentCore Gateway in front of retrieval, Cedar authorization per agent, and a browser as a third retrieval tier. Specified, not started.

**shelflife in the field.** A month of daily runs to settle whether thirty days is the right window and whether the alerts are useful or annoying. After that, a self contained HTML report published on a schedule, so the report lives at a URL instead of a terminal.
