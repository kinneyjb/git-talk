<!-- .slide: data-background="img/background.svg" -->
# Benchmarks

---

[torial](http://stackoverflow.com/questions/136650/long-compile-times-and-lost-productivity) @ StackOverflow:
> "anything greater than a 1 second delay broke people out of the zone"

- That was about compile times.
- I'm pretty sure it applies to version control.

---

# Git is fast.

---

<img src="img/bench-01.png" />

[oak.homeunix.org/~marcel](http://www.oak.homeunix.org/~marcel/blog/2009/12/18/version-control-comparison-for-large-repositories)

---

<img src="img/bench-02.png" />

[oak.homeunix.org/~marcel](http://www.oak.homeunix.org/~marcel/blog/2009/12/18/version-control-comparison-for-large-repositories)

---

<img src="img/bench-03.png" />

[oak.homeunix.org/~marcel](http://www.oak.homeunix.org/~marcel/blog/2009/12/18/version-control-comparison-for-large-repositories)

---

<img src="img/bench-04.png" />

[oak.homeunix.org/~marcel](http://www.oak.homeunix.org/~marcel/blog/2009/12/18/version-control-comparison-for-large-repositories)

---

<img src="img/bench-lkml.png" />

[Linux Kernel Wiki](https://git.wiki.kernel.org/index.php/GitBenchmarks)

---

## Storage

- Git repos are tiny.
- Storage is cheap.
- Just clone the whole history!

---

### Mozilla repo

- **CVS**: 2.7 GiB
- **SVN**: 8.2 GiB
- **Git**: 450 MiB

[keithp](http://keithp.com/blog/Repository_Formats_Matter/)

---

### Mozilla repo

- **SVN**:
  - partial history
  - **350 MiB**
- **Git**
  - entire history
  - **450**.

[keithp](http://keithp.com/blog/Repository_Formats_Matter/)

---

## Django

- **SVN**: 61 MiB
- **bzr**: 64 MiB
- **Hg**: 53 MiB
- **Git**: 43 Mib

[why git is better](http://thkoch2001.github.io/whygitisbetter/#git-is-small)

---

## KDE

- **SVN**: 34 GiB
- **Git**: 6.7 GiB

[KDE mailing list](http://lists.kde.org/?l=kde-scm-interest&m=120193241832235&w=2)
