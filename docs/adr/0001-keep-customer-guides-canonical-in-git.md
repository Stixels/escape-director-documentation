# Keep customer guides canonical in Git

Customer-facing Product Guides are maintained as Markdown in the documentation repository and published through GitBook because this keeps changes reviewable, versioned, and easy to update. Featurebase and the application may surface curated copies or direct links for high-value In-App Help, but they are distribution surfaces rather than independent sources of truth; any copied article must identify its canonical repository page so the two versions can be checked together.

## Consequences

- GitBook remains the complete, public documentation experience.
- Featurebase Messenger should contain only the small set of articles that materially helps someone without leaving their current workflow.
- The application should link directly to the most relevant Product Guide when its context is known.
- A Featurebase copy must not introduce instructions or terminology that are absent from its canonical Product Guide.
