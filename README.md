## Chris Cruz

I design systems for a living and I got tired of stopping at the diagram. So I am learning to build, ship, and operate the things I design, in public, one small project at a time.

Everything here is a personal project. No work material, no customer material, nothing behind a login.

### What I am building

**[shelflife](https://github.com/cruzbuilds/shelflife)** is one inventory of everything that expires: TLS certificates, domains, API keys, licenses, contracts. It checks what it can check live, reports what is coming due with an owner next to each item, and its exit code is the alert, so a cron job or a CI step is the whole integration. It never renews anything and never stores the secret itself. Names and dates only.

**[agentic-swarm](https://github.com/cruzbuilds/agentic-swarm)** is seven AI review agents, each with one narrow job and a written list of what it refuses to let through. They read the same change at once and merge into a single verdict. Every agent is tested against planted defects before it is allowed to review anything real.

**[project-starter](https://github.com/cruzbuilds/project-starter)** is the template the other two came from. One health check wired to CI, guardrails for AI agents working in the repo, decision records, and a place to write down what a project is for before anyone writes code.

### How they fit together

project-starter is the skeleton. agentic-swarm reviews every pull request on everything I build. shelflife is the first real project built that way, and it keeps the receipts: [docs/review-log.md](https://github.com/cruzbuilds/shelflife/blob/main/docs/review-log.md) records every finding the agents caught, whether I would have caught it myself, and what I overrode.

So far: 37 findings across 5 pull requests, none overridden, and by my own count 21 of the 33 actionable ones I would have missed reading the diff alone. The best one was a request forgery hole the security agent proved by standing up a server and watching my code walk into it. That code was an hour old and I felt fine about it.

### The idea behind all of it

Write down what you are building and why, before you build it. Make one command that tells you whether the repo is healthy. Record the decisions that would be expensive to reverse. Let something adversarial read your work before a human does. Then say plainly what is not finished.

None of that is new. It is just rarely all in one place on a small project, which is the part I wanted to prove out.
