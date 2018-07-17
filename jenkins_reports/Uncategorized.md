# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [web-update-SDT](https://cmssdt.cern.ch/jenkins/job/web-update-SDT)

**Description:** Copies releases.map to /data/sdt/SDT/jenkins-artifacts.<br>
<b>Depricated project</b>. Its tasks are taken by <a href="https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo">deploy-cms-repo</a> project.

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

## [cmssw-to-stitched](https://cmssdt.cern.ch/jenkins/job/cmssw-to-stitched)

**Description:** This looks for the Framework changes in cmssw and port them to stitched repo
This is automatically triggered by auto-forward-port job

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

## [test](https://cmssdt.cern.ch/jenkins/job/test)

**Description:** None

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

## [ib-cache-to-eos](https://cmssdt.cern.ch/jenkins/job/ib-cache-to-eos)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**
* [update-ibeos-cache](#update-ibeos-cache):

**Triggers from:** []


**Periodic builds:**
```bash
H 10,22 * * *
```

---

