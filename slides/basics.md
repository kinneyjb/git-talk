<!-- .slide: data-background="img/background.svg" -->
# Basics

---

## Learning

The hardest part of Git is the jargon.

- *commit*
- *staging area*
- *working directory*
- `HEAD`
- *heads*
- *checkout*
- *clone*
- *push*
- *remote*

---

<img src="img/git-folder.svg" />

---

<img src="img/dirty-work.svg" />

---

## Staging area

The **staging area** holds changes that are about to be committed.

- Commits are multi-step:
  - Change the file.
  - Add your changes (to the staging area).
  - Commit them.

---

<img src="img/add-commit-staging.svg" />

from the [Git book](http://git-scm.com/about/staging-area).

---

Create a new repo:

``` bash
$ git init
Initialized empty Git repository in /home/nathan/devel/git-demo/.git/
```

Make a file:


``` bash
$ touch README.md
$ ls -a
. .. .git README.md
```

By default, this new file is untracked:

```
$ git ls-files
$ git status
On branch master

Initial commit

Untracked files:

    README.md
```

---

Files need to be added with `git add` before Git knows about them:

``` bash
$ git add README.md
```

Then they show up in the staging area:

```
$ git status
On branch master

Initial commit

Changes to be committed:

    new file:   README.md
```

```
$ git ls-files
README.md
```

---

```
$ git commit -m ‘initial commit’
[master (root-commit) 104ea88] initial commit
 1 file changed, 0 insertions(+), 0 deletions(-)
```

<img src="img/log-transition.svg" />

Commits move files from the staging area into the log.

---

## Commits

<!-- .slide: data-background="img/tracking-bg.svg" -->

- Identified by their [SHA1](http://en.wikipedia.org/wiki/SHA-1) hash.
  - e.g., `f3d19df9968f4260c6bfde8c1d71e0e00ef9f00e`
  - globally unique identifier.
- Commits contain changes to *file contents*.
  - History is preserved through renames.

---

## Trees

- Commits build on each other, so each one refers backwards to all the others.
- This forms a **tree**.

<img src="img/sha-hashes.svg" />

---

## Trees

<img src="img/sha-hashes.svg" />

- Their hashes are hashes of this entire history, not the individual changes.
- The same hash always refers to exactly the same history of the same tree.

