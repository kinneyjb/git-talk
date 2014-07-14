<!-- .slide: data-background="img/background.svg" -->
# Remotes

<img src="img/remotes-defn.svg" />

---

### Remotes can be anywhere.

##### Folder on the same machine

```
$ git clone /opt/git/project.git
```

##### Server somewhere

```
$ git clone user@server:project.git
```

---

## Conventional names

- `origin` The first remote that you add.
  - "Where your code came from."

---

Clone this repo!

<img src="img/clone-this-repo.png" />

---

```
$ git clone git@github.com:nathantypanski/git-talk.git
Cloning into 'git-talk'...
remote: Counting objects: 312, done.
remote: Compressing objects: 100% (205/205), done.
remote: Total 312 (delta 136), reused 270 (delta 94)
Receiving objects: 100% (312/312), 1.69 MiB | 0 bytes/s, done.
Resolving deltas: 100% (136/136), done.
Checking connectivity... done.
```

If you have an account: [**fork**](https://help.github.com/articles/fork-a-repo) this repo, then clone your fork:

<img src="img/fork-this-repo.png" />

<img src="img/fork-kinneyjb.png" />

---

```
$ git remote add kjb https://github.com/kinneyjb/git-talk.git
git-talk$ git fetch kjb
remote: Counting objects: 9, done.
remote: Compressing objects: 100% (1/1), done.
remote: Total 4 (delta 3), reused 3 (delta 3)
Unpacking objects: 100% (4/4), done.
From https://github.com/kinneyjb/git-talk
 * [new branch]      gh-pages   -> kjb/gh-pages
 * [new branch]      jkinney-what -> kjb/jkinney-what
 * [new branch]      master     -> kjb/master
```

- You want to [**add a remote**](http://git-scm.com/book/en/Git-Basics-Working-with-Remotes) for your own code, and any code you might wish to download.
- **Push code to your own fork**, then send a **pull request**.

<img src="img/github-pull-request.png" />

