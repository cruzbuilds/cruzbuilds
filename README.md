## Chris Cruz

I design systems for a living and I hate stopping at the diagram. So I build, ship, and operate the things I design, in public, one small project at a time.

Everything here is a personal project. No work material, no customer material, nothing behind a login.

### What I am building

Leg work - (https://dq8b25qx96wy3.cloudfront.net/) Ask a technical question. Legwork levergaes three agents that plan, research, and read GitHub the open web, and writes you a report where every claim links to its source.

**[shelflife](https://github.com/cruzbuilds/shelflife)** is one inventory of everything that expires: TLS certificates, domains, API keys, licenses, contracts. It checks what it can check live, reports what is coming due with an owner next to each item, and its exit code is the alert, so a cron job or a CI step is the whole integration. It never renews anything and never stores the secret itself. Names and dates only.

**[agentic-swarm](https://github.com/cruzbuilds/agentic-swarm)** is seven AI review agents, each with one narrow job and a written list of what it refuses to let through. They read the same change at once and merge into a single verdict. Every agent is tested against planted defects before it is allowed to review anything real.

**[project-starter](https://github.com/cruzbuilds/project-starter)** is the template the other two came from. One health check wired to CI, guardrails for AI agents working in the repo, decision records, and a place to write down what a project is for before anyone writes code.
