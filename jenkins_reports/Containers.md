# [Containers](https://cmssdt.cern.ch/jenkins/view/Containers)

**View description:** None

**View type:** List View

---

# Projects:

## [build-container](https://cmssdt.cern.ch/jenkins/job/build-container)

**Description:** None

**Project is `disabled`.**

**Upstream projects:**
* [schedule-docker-build](#schedule-docker-build):

**Downstream projects:**
* [cvmfs-unpack-container](#cvmfs-unpack-container):
* [test-build-container](#test-build-container):

**Sub-projects:**
* [test-build-container](#test-build-container):
* [cvmfs-unpack-container](#cvmfs-unpack-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-docker-container](https://cmssdt.cern.ch/jenkins/job/build-docker-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [check-docker-container](#check-docker-container):

**Downstream projects:**
* [cvmfs-unpack-container](#cvmfs-unpack-container):
* [test-image-build](#test-image-build):

**Sub-projects:**
* [test-image-build](#test-image-build):
* [cvmfs-unpack-container](#cvmfs-unpack-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [check-docker-container](https://cmssdt.cern.ch/jenkins/job/check-docker-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cms-auto-build-container](#cms-auto-build-container):

**Downstream projects:**
* [build-docker-container](#build-docker-container):

**Sub-projects:**
* [build-docker-container](#build-docker-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-auto-build-container](https://cmssdt.cern.ch/jenkins/job/cms-auto-build-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [check-docker-container](#check-docker-container):

**Sub-projects:**
* [check-docker-container](#check-docker-container):

**Triggers from:** []


**Periodic builds:**
```bash
H 10 * * *
```

---

## [cms-containers-checks-tags](https://cmssdt.cern.ch/jenkins/job/cms-containers-checks-tags)

**Description:** This project search for tags.yaml files in cms-sw/cms-docker repostory and create new image tags if needed

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**
* [cms-grid-tag-container](#cms-grid-tag-container):

**Sub-projects:**
* [cms-grid-tag-container](#cms-grid-tag-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-grid-tag-container](https://cmssdt.cern.ch/jenkins/job/cms-grid-tag-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cms-containers-checks-tags](#cms-containers-checks-tags):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmssw-container](https://cmssdt.cern.ch/jenkins/job/cmssw-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---
