<!-- .slide: data-background="img/background.svg" -->
# What?
 - [Configuration Management (CM)](http://en.wikipedia.org/wiki/Configuration_management)
  - Practice of handling changes systematically so that a system maintains its integrity over time.
  - CM implements the policies, procedures, techniques, and tools that are required to manage, evaluate proposed changes, track the status of changes, and to maintain an inventory of system and support documents as the system changes. 
 - [Software CM (SCM)](http://en.wikipedia.org/wiki/Software_configuration_management)
  - Track and controll changes in the software
  - Revision Control and the establishment of baselines.
 - [Version Control System (VCS)](http://en.wikipedia.org/wiki/Version_Control_System)
  - Tracks and provides control over changes to source code
  - Baseline -or- Branch -or- Tag ... i.e. Version
  - Centralized, with a single authoritative data store, the repository. (Client/Server)
 - [Distributed VCS (DVCS)](http://en.wikipedia.org/wiki/Distributed_version_control_system)
  - Decentralized, each working copy functions as remote backup (Peer-To-Peer)

---

### Git is revision control software.

- History tracking
- Automatic merging
- Bisecting bugs

---

### History

- Written by Linus Torvalds in 2005 to meet the needs of the Linux kernel developers.

- Now maintained by [Junio Hamano](http://git-blame.blogspot.com/).

---

### Centralized VCS

- Everyone stores history on a central repository
- Only the central repo gets a full copy of the history

---

<!-- .slide: data-background="img/centralized-vcs.svg" -->

---

### Distributed Version Control

- Team members send changes to each other
- Everyone can work offline

---

<!-- .slide: data-background="img/dvcs.svg" -->
