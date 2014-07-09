<!-- .slide: data-background="img/merging-bg.svg" -->
# Merging

``` bash
$ git merge hotfix master
```

---

## Fast forwards

- 90% of your merges (less for huge teams)

---

## Advanced topics

- merge strategies
- rerere

---

### Strategies

---

#### Recursive

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
