# Branches
<!-- .slide: data-background="img/branch-bg.svg" -->

``` bash
$ git checkout -b hotfix
```

---

## Branches

- A **branch** is a pointer to a commit.
- No, really:

``` shell
filer$ cd .git/refs/heads
heads$ ll
total 12
drwxr-xr-x 1 nathan nathan 28 Jun 16 09:06 cleanup
-rw-r--r-- 1 nathan nathan 41 May 30 14:56 cython
-rw-r--r-- 1 nathan nathan 41 Jul  8 11:43 develop
drwxr-xr-x 1 nathan nathan 40 Jun  3 09:27 feature
drwxr-xr-x 1 nathan nathan 28 May 27 10:30 hotfix
-rw-r--r-- 1 nathan nathan 41 Jul  7 10:21 master
heads$ cat master
9326780e3cde95034a6a402ee39a47e66e9c2398
```

---

```
$ mkdir demo
$ cd demo
demo$ git init
Initialized empty Git repository in ~/demo/.git/
demo$ la
.  ..  .git
demo$ vim helloworld.py
```

``` python
import sys

def main():
    if len(sys.argv) == 1:
        print('Hello, world')
    else:
        print(str.format('hello {}', ' '.join(sys.argv[1:])))

if __name__ == '__main__':
    main()
```

```
demo$ python3 helloworld.py
Hello, world
demo$ python3 helloworld.py nathan
hello nathan
```

---

## Conventional names

<img src="img/gitflow-master.svg" />

- First branch
- Created automatically by Git


