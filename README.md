# PoC MFA Monorepo Documentation

## Key Terminology

- **PoC (Proof of Concept):** An initial demonstration to verify the concept.
- **MFA (Micro Frontend Application):** A design approach in web development where a frontend app is decomposed into individual, semi-independent "microapps".
- **Monorepo:** A software development strategy where code for many projects is stored in the same repository. For more information, see [Monorepo Tools](https://monorepo.tools/).

## The rationale for Choosing a Monorepo

### Personal Experiences with Micro Frontend Architecture

Micro Frontend architecture is often chosen for the incremental modernization of legacy monolithic frontend applications. In practice, however, managing multiple repositories can significantly hinder productivity. My experience with administering four separate repositories for a single Micro Frontend project underscored the challenges and inefficiencies inherent in this approach.

### Microservice Development Principles

The Fifteen Factor methodology provides a comprehensive framework for building robust microservices. Relevant resources include:

- [The Twelve-Factor App](https://12factor.net/)
- [Creating cloud-native applications: 12-factor applications](https://developer.ibm.com/articles/creating-a-12-factor-application-with-open-liberty/)
- [Beyond the 12 factors: 15-factor cloud-native Java Applications](https://developer.ibm.com/articles/15-factor-applications/)
- [Fifteen Factor App](https://vikasg11.medium.com/fifteen-factor-app-3dc16727ecd7)
- [The fifteen-Factor App](https://domenicoluciani.com/2021/10/30/15-factor-app.html)
- [Cloud native Fifteen Factor Apps](https://www.handsonarchitect.com/2022/08/cloud-native-fifteen-factor-apps.html)

### Implications of Conway's Law

Conway's Law, as outlined in [Martin Fowler's article](https://martinfowler.com/bliki/ConwaysLaw.html), posits a reflective relationship between system architecture and organizational structure. This principle highlights the complexities of managing microservices without parallel restructuring within the development organization.

### Navigating Organizational and Technical Trade-offs

Small organizations facing resource constraints may struggle to maintain a micro-frontend application infrastructure effectively. An alternative approach, such as [Modular Monoliths](https://shopify.engineering/deconstructing-monolith-designing-software-maximizes-developer-productivity), might be more feasible in such scenarios.

It's essential to revisit the core question, "Why adopt microservices?" If certain aspects of the 15-factor framework are not applicable, selectively adapting the methodology can be a strategic choice. The key is to understand and respect the intent behind each factor, rather than adhering rigidly to all fifteen.

For instance, adopting a monorepo approach may appear to contravene the ["Codebase: one codebase tracked in version control"](https://12factor.net/codebase) factor. However, it's possible to align with the underlying principle of this factor, which emphasizes the separation of shared code into libraries that can be managed via a dependency manager.

### Practical Implementation: GitHub Actions

GitHub Actions can be strategically utilized to deploy individual applications within a monorepo. The [`paths` filter](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onpushpull_requestpull_request_targetpathspaths-ignore) enables the selective deployment of specific applications. This approach allows for maintaining the standard practices of micro frontend composition and dependency management.

## Setting Up the Monorepo

This repository employs [npm's workspaces](https://docs.npmjs.com/cli/v7/using-npm/workspaces) to create and manage the monorepo structure. While various tools are available for this purpose, the simplicity of npm's workspaces makes it an ideal choice for initial setup and until more complex solutions are required.
