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

## Conventional names

<img src="img/gitflow-master.svg" />

- First branch
- Created automatically by Git

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

```
demo$ git add helloworld.py
demo$ git commit -m 'initial commit'
[master (root-commit) 62b720a] initial commit
 1 file changed, 10 insertions(+)
 create mode 100644 helloworld.py
```

To show branches:

```
demo$ git branch
* master
```

---

```
$ vim helloworld.py
$ git diff
```

```
diff --git a/helloworld.py b/helloworld.py
index 328978e..b2c550a 100644
--- a/helloworld.py
+++ b/helloworld.py
@@ -1,10 +1,16 @@
 import sys
+from datetime import date
 
 def main():
+    today = datetime.today()
     if len(sys.argv) == 1:
         print('Hello, world')
     else:
         print(str.format('hello {}', ' '.join(sys.argv[1:])))
+    print(str.format('Today is {}-{}-{}',
+                     today.year,
+                     today.month,
+                     today.day()))
 
 if __name__ == '__main__':
     main()
```

---

```
demo$ git commit helloworld.py -m 'add date to helloworld'
[date 58fba34] add date to helloworld
 1 file changed, 6 insertions(+)
demo$ python3 helloworld.py Nathan
Traceback (most recent call last):
  File "helloworld.py", line 16, in <module>
    main()
  File "helloworld.py", line 5, in main
    today = datetime.today()
NameError: name 'datetime' is not defined
```

Darn! Should've tested before I committed that ...

Luckily, Git lets us **amend our work** before we send it anywhere.

---

```
$ vim helloworld.py
$ git diff
```

```
diff --git a/helloworld.py b/helloworld.py
index b2c550a..fd28150 100644
--- a/helloworld.py
+++ b/helloworld.py
@@ -2,7 +2,7 @@ import sys
 from datetime import date
 
 def main():
-    today = datetime.today()
+    today = date.today()
     if len(sys.argv) == 1:
         print('Hello, world')
     else:
@@ -10,7 +10,7 @@ def main():
     print(str.format('Today is {}-{}-{}',
                      today.year,
                      today.month,
-                     today.day()))
+                     today.day))
 
 if __name__ == '__main__':
     main()
```

---

```
demo$ python3 helloworld.py Nathan
hello Nathan
Today is 2014-7-14
demo$ git commit --amend helloworld.py
```

Great! It works. Let's amend that commit ...

```
add date to helloworld

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# Explicit paths specified without -i or -o; assuming --only paths...
# On branch date
# Changes to be committed:
#	modified:   helloworld.py
#
```

```
demo$ git commit --amend helloworld.py 
[date a497198] add date to helloworld
 1 file changed, 6 insertions(+)
```

---

```
demo$ git log
a497198 Nathan Typanski add date to helloworld
62b720a Nathan Typanski initial commit
```

This is safe, since every user basically has **their own local branch** by default.

#### Changes don't go anywhere unless you explicitly send them to a server.
