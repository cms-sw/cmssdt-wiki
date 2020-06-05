# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [ib-run-geometry](https://cmssdt.cern.ch/jenkins/job/ib-run-geometry)

**Description:** Runs geometry comparison tests for each IB

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [slc6](https://cmssdt.cern.ch/jenkins/job/slc6)

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

## [auto-forward-ports-old](https://cmssdt.cern.ch/jenkins/job/auto-forward-ports-old)

**Description:** This is triggered by github webhook for each cmssw/cmsdist branch merge event.
this forward port changes from source branch to target branch. Mapping between soruce and destination branches are available in cms-bot.

<ul>
  <li>
    <b>Q:</b> Job failed do to merge conflict.
  </li>
  <li>
    <b>A:</b> It comonly fails when merging diferences on `root.spec` files. 
    If we known that we want to keep our changes on merge conflict, we can a) manually run
    `auto-update-git-branches` with `-X ours` option and push changes, b) re-run job with 
    KEEP_OURS value set to True.<br>
    Due only when we are sure about changes. Otherwise, you have to resolve merge 
    conflict manually.
    
  </li>
</ul>

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [schedule-docker-build](https://cmssdt.cern.ch/jenkins/job/schedule-docker-build)

**Description:** A glue job to connect github-webhook with build-container. 
Should check only folder containing *EXECUTE_BUILD.sh  

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [build-container](#build-container):

**Sub-projects:**
* [build-container](#build-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [aarch64](https://cmssdt.cern.ch/jenkins/job/aarch64)

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

## [slc7](https://cmssdt.cern.ch/jenkins/job/slc7)

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

## [git-reference-cms-ib](https://cmssdt.cern.ch/jenkins/job/git-reference-cms-ib)

**Description:** Create GIT Reference for cms-sw/cmssw repository in /cvmfs/cms-ib.cern.ch/git/cms-sw.
This is automatically triggered by "git push" to cmssw repo.

**Project is `disabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

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

