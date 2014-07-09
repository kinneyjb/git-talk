<!-- .slide: data-background="img/merging-bg.svg" -->
# Merging

``` bash
$ git merge hotfix master
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

---

#### Octopus

---

#### Ours

---

#### Subtree

---

### rerere

``` bash
$ git config --global rerere.enabled true
```

- Secret Git merge sauce.
- Memorizes how you did a merge so you don't repeat it.
- [Not in the book!](http://git-scm.com/blog/2010/03/08/rerere.html)
- Don't do this unless you know what you're doing.
