# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [compare-docker-images](https://cmssdt.cern.ch/jenkins/job/compare-docker-images)

**Description:** avalenzu: testing docker image comparison

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

## [cvmfs-ci-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-ci-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 23  * *  2
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

## [es-close-indexes](https://cmssdt.cern.ch/jenkins/job/es-close-indexes)

**Description:** This job keeps last 6 weeks (1.5 months) of data in Elasticsearch open, and it closes older indexes (archive it).
We do not care about older data. By doing it we make Elasticsearch faster. 

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0  * *  0
```

---

## [es-insert-failure-data](https://cmssdt.cern.ch/jenkins/job/es-insert-failure-data)

**Description:** Insert record into ES linking Issue/PR and error in IB

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

## [ib-install-cvmfs-gateway](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs-gateway)

**Description:** Test job to install IBs in parallel (cvmfs gateway).

**Project is `disabled`.**

**Upstream projects:**
* [cms-spack-ib](#cms-spack-ib):
* [cmsrep-webhook](#cmsrep-webhook):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Sub-projects:**
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

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

## [ib-run-gpu](https://cmssdt.cern.ch/jenkins/job/ib-run-gpu)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-run-qa](#ib-run-qa):

**Sub-projects:**
* [ib-run-qa](#ib-run-qa):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Project is `disabled`.**

**Upstream projects:**
* [update-github-pages](#update-github-pages):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** ['update-github-pages']


**Periodic builds:**
```bash
Not periodically build
```

---

## [s3-run-speed-test](https://cmssdt.cern.ch/jenkins/job/s3-run-speed-test)

**Description:** None

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [s3-speet-test](#s3-speet-test):

**Sub-projects:**
* [s3-speet-test](#s3-speet-test):

**Triggers from:** []


**Periodic builds:**
```bash
H 22 * * *
```

---

## [sync-patatrack-branch](https://cmssdt.cern.ch/jenkins/job/sync-patatrack-branch)

**Description:** - this is to sync patatrack branches <br/>
- Currently this job does not do any thing (kind of disabled)


**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
55 * * * *
```

---

## [test-cmssw-images](https://cmssdt.cern.ch/jenkins/job/test-cmssw-images)

**Description:** avalenzu: Jenkins job to test the new runtime and buildtime images. I will delete this job after the tests.

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

