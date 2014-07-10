<!-- .slide: data-background="img/background.svg" -->
# Workflows

- Git lets you use whatever workflow you want.
- Structure is still helpful.

---

## Centralized

<img src="img/centralized-workflow.png">

- Basically SVN.

---

## Integration manager

<img src="img/integration-manager-workflow.png">

- Good for small teams.

---

## Dictator and lieutentants

<img src="img/dictator-lieutenants-workflow.png">

- Linux kernel.

---

## Git Flow

> "A successful Git branching model"

<img src="img/git-flow.png">

---

## `master`

- Deployment branch
- Commits are deployments
- Each commit gets a tag
- Each commit should be a merge commit

---

<!-- .slide: data-background="img/gitflow-master-tag.svg" -->

---

## `develop`

- Where work happens
- Main staging tree for `master`

---

<!-- .slide: data-background="img/gitflow-develop.svg" -->

---

## Release branches

- e.g., `release-1.2`
- only bugfixes
- merge into `master` and `develop`

---

<!-- .slide: data-background="img/gitflow-release-merge.svg" -->

---

## Hotfix branches

- Patches to `master` branch
- Merge back into `develop`

---

<!-- .slide: data-background="img/gitflow-hotfix.svg" -->

---

<!-- .slide: data-background="img/gitflow-hotfix-develop.svg" -->
