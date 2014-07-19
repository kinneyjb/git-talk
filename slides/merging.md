<!-- .slide: data-background="img/merging-bg.svg" -->
# Merging

``` bash
$ git merge hotfix master
```

---

To merge changes from local branch `hotfix` into local branch `master`:

```
$ git merge hotfix master
```

Merge changes from remote `origin` branch `master`
into local branch `master`

```
$ git pull origin master
```

---

## Strategies

### Fast forward

- Changes go directly on top of the target branch.

### Recursive

- Default for everything that's not fast-forward.
- Common ancestors get joined.
- Handles renames.

---

## Advanced topics

- Different merge strategies
- `git-rerere`

---

### More Strategies

#### Octopus

- Merge several trees (instead of a sequence of branch merges)

---

### More Strategies

#### Ours

- Not really a merge
- Keeps your history, but puts other branch history in the tree

---

### More Strategies

#### Subtree

- Merge an independent project into a subdirectory

---

### rerere

``` bash
$ git config --global rerere.enabled true
```

- Secret Git merge sauce.
- Memorizes how you did a merge so you don't repeat it.
- [Not in the book!](http://git-scm.com/blog/2010/03/08/rerere.html)
- Don't do this unless you know what you're doing.
