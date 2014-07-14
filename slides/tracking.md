# Tracking changes
<!-- .slide: data-background="img/tracking-bg.svg" -->

``` bash
$ git log
```

``` bash
$ git blame
```

``` bash
$ git grep
```

``` bash
$ git bisect
```

---

### `git log`

```
git-talk$ git log --graph --pretty=format:'%h %an %s'
```

```
* bfd7061 Nathan Typanski remotes: change slide to use generic titlebg
* 5418ad7 Nathan Typanski concepts:shorten title
* 6e0aed4 Nathan Typanski whitespace nitpick fixup
* e169333 Nathan Typanski add readme
* 837fc50 Nathan Typanski rm extra slide
*   7b4245f Nathan Typanski Merge branch 'jkinney-what' of ...
|\
| *   524abf7 kinneyjb Merge branch 'jkinney-what' of ...
| |\
| | * 9975749 kinneyjb Split out the notes from what into ...
| * | 9f933af kinneyjb Split out the notes from what into ...
| |/
| * 40790cb kinneyjb Some notes for the what section, ...
* | 32330ac Nathan Typanski add section for remotes
|/
* 66f5fdd Nathan Typanski stop lying about fast-forward merges
```

---

> For these reasons, the "summary" must be no more than 70-75
> characters, and it must describe both what the patch changes, as well
> as why the patch might be necessary.  It is challenging to be both
> succinct and descriptive, but that is what a well-written summary
> should do.

[Linux kernel: Documentation/SubmittingPatches](http://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/tree/Documentation/SubmittingPatches?id=HEAD#l521)

---

### `git blame`

```
$ git blame slides/concepts.md
```

```
9f933af3 (kinneyjb        2014-07-10)  - (Client/Server)
9f933af3 (kinneyjb        2014-07-10) 
9f933af3 (kinneyjb        2014-07-10) ---
9f933af3 (kinneyjb        2014-07-10) 
9f933af3 (kinneyjb        2014-07-10) ### Centralized VCS
75f6b977 (Nathan Typanski 2014-07-10) <img src="img/centralized-vcs.svg" />
9f933af3 (kinneyjb        2014-07-10) 
9f933af3 (kinneyjb        2014-07-10) ---
9f933af3 (kinneyjb        2014-07-10) 
9f933af3 (kinneyjb        2014-07-10) ### Distributed Version Control
9f933af3 (kinneyjb        2014-07-10) 
9f933af3 (kinneyjb        2014-07-10) - Team members send changes to each
9f933af3 (kinneyjb        2014-07-10) - Everyone can work offline
```


---

### `git grep`

Use it with `--cached` to grep only files Git knows about:

```
git-flow$ git grep --cached --break --heading --line-number "Linux"
```

(the other arguments are just for pretty output)

```
slides/benchmarks.md
44:[Linux Kernel Wiki](https://git.wiki.kernel.org/index.php/GitBenchmarks)

slides/what.md
17:- Written by Linus Torvalds in 2005 to meet the needs of the Linux kernel
developers.

slides/workflows.md
29:- Linux kernel.
```

---

### `git bisect`

- Binary search of your commit history
- See also: [Debugging with Git](http://git-scm.com/book/en/Git-Tools-Debugging-with-Git)

---

<img src="img/binary-search.svg" />
