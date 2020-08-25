# [Containers](https://cmssdt.cern.ch/jenkins/view/Containers)

**View description:** None

**View type:** List View

---

# Projects:

## [build-docker-container](https://cmssdt.cern.ch/jenkins/job/build-docker-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [check-docker-container](#check-docker-container):

**Downstream projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [cvmfs-unpack-container](#cvmfs-unpack-container):

**Sub-projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
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

## [cleanup-docker-tags](https://cmssdt.cern.ch/jenkins/job/cleanup-docker-tags)

**Description:** Removes outdated tags from docker repository.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [cms-auto-build-container](https://cmssdt.cern.ch/jenkins/job/cms-auto-build-container)

**Description:** None

**Project is `disabled`.**

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
* [cms-tag-container](#cms-tag-container):

**Sub-projects:**
* [cms-tag-container](#cms-tag-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-containers-run-cmssw-test](https://cmssdt.cern.ch/jenkins/job/cms-containers-run-cmssw-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):
* [cms-containers-schedule-cmssw-test](#cms-containers-schedule-cmssw-test):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-containers-schedule-cmssw-test](https://cmssdt.cern.ch/jenkins/job/cms-containers-schedule-cmssw-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):

**Sub-projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-tag-container](https://cmssdt.cern.ch/jenkins/job/cms-tag-container)

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

## [dockerhub_synchronization](https://cmssdt.cern.ch/jenkins/job/dockerhub_synchronization)

**Description:** Synchronizes Docker Hub Organization's setup (repositories/teams/members/permissions) with docker configuration yaml file.

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

