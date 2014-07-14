# Fixing mistakes

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
```

```
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

---

## Bigger mistakes

Fix bigger mistakes with `git rebase`.

- Commits out of order
- Forgot to add files 4 commits back
- etc.

---

## Bigger mistakes

Working on this repo, I forgot to add an image that was referenced in one of the
markdown files.

That was 3 commits ago. I can't just `--amend` it.

```
git-talk$ git rebase -i origin/master
```

`origin/master` is a remote branch.

It means I'm allowed to change things *up until* the history known on `origin`'s `master` branch.

---

```
git-talk$ git rebase -i origin/master
```

<img src="img/rebase-ci-01.png" />

Reorder and fixup (combine) the commits:

<img src="img/rebase-ci-02.png" />

---

```
[detached HEAD 4344a8d] add gitlab ci
 2 files changed, 9 insertions(+), 1 deletion(-)
 create mode 100644 img/gitlab-ci-preview.png
Successfully rebased and updated refs/heads/master.
```

Now my history looks like this:

```
2014-07-14 13:48 Unknown            o Unstaged changes
2014-07-14 13:32 Nathan Typanski    o [master] more branching
2014-07-14 13:32 Nathan Typanski    o expand tool descriptions
2014-07-14 13:31 Nathan Typanski    o add gitlab ci
2014-07-14 13:31 Nathan Typanski    o tweak formatting
2014-07-14 12:42 Nathan Typanski    o add link to gitbook
2014-07-14 12:37 Nathan Typanski    o [gh-pages] [origin/HEAD] [origin/gh-pages]
                                      [origin/master] remotes before merging
2014-07-14 12:36 Nathan Typanski    o add slides on cloning/forking repo
```

---

## But wait! That's rewriting history!

- No, it's rewriting **my** history.
- Commits are not "sacred" until someone **besides you** starts using them.
- This encourages good version control practices:
  - Commit early,
  - Commit often.
