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

Often, you'll want to inspect a merge before it happens.

Use `git fetch`:

```
git-talk$ git fetch kinneyjb
remote: Counting objects: 4, done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 1 (delta 0)
Unpacking objects: 100% (4/4), done.
From https://github.com/kinneyjb/git-talk
 * [new branch]      gh-pages   -> kinneyjb/gh-pages
 * [new branch]      master     -> kinneyjb/master
```

---

If you have local changes, do `git stash` to save them away:

```
git-talk$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.

Changes not staged for commit:

	modified:   slides/merging.md

no changes added to commit (use "git add" and/or "git commit -a")
```

```
git-talk$ git stash
Saved working directory and index state
    WIP on master: 633c37b merging: fill out sections
HEAD is now at 633c37b merging: fill out sections
```

---

Sometimes I'll make a new branch for the merge:

```
git-talk$ git checkout -b kjb
Switched to a new branch 'kjb'
```

Merge a fetched remote branch with `remotename/branchname`:

```
git-talk$ git merge kinneyjb/master
Merge made by the 'recursive' strategy.
 slides/benchmarks.md | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)
```

---

```
$ git log --graph --pretty=format:'%h %an %s'
```

```
*   5e2788f Nathan Typanski Merge remote-tracking branch
                            'kinneyjb/master' into kjb
|\
| * b332517 kinneyjb fixed typos closes #2
* | 633c37b Nathan Typanski merging: fill out sections
* | 4d2ac1f Nathan Typanski fade transition for backgrounds - easier to follow
* | 25a4087 Nathan Typanski expand branches/remotes/ci
* | 3ed07e5 Nathan Typanski more branching
* | 5e1b3ab Nathan Typanski expand tool descriptions
* | 4344a8d Nathan Typanski add gitlab ci
* | 6a339e0 Nathan Typanski tweak formatting
* | 2ba91f4 Nathan Typanski add link to gitbook
* | 3965c22 Nathan Typanski remotes before merging
* | a1dcf95 Nathan Typanski add slides on cloning/forking repo
* | 221c3fe Nathan Typanski wider quotes, non-italic
* | 0a8bf2e Nathan Typanski fill out "tracking changes"
* | 19259c9 Nathan Typanski stop hyphenating titles
* | ecf9034 Nathan Typanski add ci section
* | b404b21 Nathan Typanski join slides for remotes
|/
```

---

Now, put the changes back in master:

```
git-talk$ git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
```

Merging with `--ff-only` means "don't give me a merge commit; just put the new
changes on top of `HEAD`:

```
git-talk$ git merge --ff-only kjb
Updating 633c37b..5e2788f
Fast-forward
 slides/benchmarks.md | 4 ++--
 1 file changed, 2 insertions(+), 2 deletions(-)
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
