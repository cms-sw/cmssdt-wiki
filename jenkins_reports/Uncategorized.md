# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [cvmfs-new-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-new-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 23  * *  4
```

---

## [cvmfs-install-pr](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-pr)

**Description:** To install PR externals

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cleanup-containers](https://cmssdt.cern.ch/jenkins/job/cvmfs-cleanup-containers)

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

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-baseline](#ib-run-baseline):

**Downstream projects:**
* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Sub-projects:**
* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 19  * *  4
```

---

## [cvmfs-publish-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-baseline)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

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

## [ib-install-new-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-new-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

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

## [cvmfs-unpack-container](https://cmssdt.cern.ch/jenkins/job/cvmfs-unpack-container)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):

**Downstream projects:**
* [cvmfs_publish_remote_dir](#cvmfs_publish_remote_dir):

**Sub-projects:**
* [cvmfs_publish_remote_dir](#cvmfs_publish_remote_dir):

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

## [schedule-docker-build](https://cmssdt.cern.ch/jenkins/job/schedule-docker-build)

**Description:** A glue job to connect github-webhook with build-container. 
Should check only folder containing *EXECUTE_BUILD.sh  

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

