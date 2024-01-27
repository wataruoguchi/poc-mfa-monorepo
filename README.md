# PoC MFA monorepo

## Vocabularies

- PoC: Proof of Concept
- MFA: Micro Frontend Application
- monorepo: a single repository containing multiple distinct projects [\*1](https://monorepo.tools/)

## Why monorepo?

### What I experienced

Micro Frontend architecture can be picked as a solution for gradually updating a legacy monolith frontend application. However, maintaining a bunch of repositories is not the most productive process. I have introduced four repositories for a micro frontend project and noticed maintaining just four repositories is great work.

### Microservice principles

The Fifteen Factor methodology is a great standard for building microservices.

- [The Twelve-Factor App](https://12factor.net/)
- [Beyond the 12 factors: 15-factor cloud-native Java Applications](https://developer.ibm.com/articles/15-factor-applications/)
- [Creating cloud-native applications: 12-factor applications](https://developer.ibm.com/articles/creating-a-12-factor-application-with-open-liberty/)
- [Fifteen Factor App](https://vikasg11.medium.com/fifteen-factor-app-3dc16727ecd7)
- [The fifteen-Factor App](https://domenicoluciani.com/2021/10/30/15-factor-app.html)
- [Cloud native Fifteen Factor Apps](https://www.handsonarchitect.com/2022/08/cloud-native-fifteen-factor-apps.html)

### Conway's Law

[Conway's Law](https://martinfowler.com/bliki/ConwaysLaw.html) tells us that the system and the development organization are mirroring each other. Managing microservices is not easy without the development organization restructured.

### Accepting trade-offs

When the organization is too small to maintain the micro-frontend application, but the organization cannot afford having more developers, we will need to come up with another solution. For addressing the same problem with designing backend microservice architecture, [Modular Monoliths](https://shopify.engineering/deconstructing-monolith-designing-software-maximizes-developer-productivity) can be one of the options.

The point is, "Why do we do microservices?" and if it is reasonable, intentionally ignoring a few of the 15 factors should be an option. "There's no silver bullet."

With the monorepo architecture, we miss only one factor out of the 15, which is [**"Codebase: one codebase tracked in version control"**.](https://12factor.net/codebase) Still, we can respect what the factor wants to solve:

> Multiple apps sharing the same code is a violation of twelve-factor. The solution here is to factor shared code into libraries which can be included through the dependency manager.

### Trick

GitHub actions have a way to deploy an individual application separately by using [`paths` filter](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore). Everything else - the way we compose micro frontends, the way we manage dependencies - can stay the same.

## The monorepo setup

This repository uses [npm's workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces) to compose a monorepo. There is a variety of tools to accomplish this, but let's stick with the simplest method until we face a problem.
