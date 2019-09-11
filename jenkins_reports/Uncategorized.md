# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [ib-cleanup-installers](https://cmssdt.cern.ch/jenkins/job/ib-cleanup-installers)

**Description:** Cron job for log rotation on installer nodes. (clean up obsolete weeks)

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 22 * * *
```

---

## [ib-cvmfs-publish](https://cmssdt.cern.ch/jenkins/job/ib-cvmfs-publish)

**Description:** This jobs copies IBs installation for an arch from another machine and publish it to cvmfs

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-validation](#ib-validation):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [auto-forward-ports](https://cmssdt.cern.ch/jenkins/job/auto-forward-ports)

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
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

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

## [rpm-repository-backup](https://cmssdt.cern.ch/jenkins/job/rpm-repository-backup)

**Description:** Backs-up cmsrep

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [external-deploy-afs](https://cmssdt.cern.ch/jenkins/job/external-deploy-afs)

**Description:** This job deployes any external tool on afs that is required. 

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

## [update-externals-mirrors](https://cmssdt.cern.ch/jenkins/job/update-externals-mirrors)

**Description:** Update some of the externals mirror and setup a cms specific branch so that updates can be proposed there. 

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
0 0 * * *
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

## [lxr-check](https://cmssdt.cern.ch/jenkins/job/lxr-check)

**Description:** This job checks if https://cmssdt.cern.ch/lxr/ is acessable and if not, starts <a href="https://cmssdt.cern.ch/jenkins/view/All/job/lxr-run-container/">lxr-run-container<a/> job to restart the service.

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [lxr-run-container](#lxr-run-container):

**Sub-projects:**
* [lxr-run-container](#lxr-run-container):

**Triggers from:** []


**Periodic builds:**
```bash
H/5 * * * *
```

---

