# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Project is `disabled`.**

**Upstream projects:**
* [update-github-pages](#update-github-pages):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** [u'update-github-pages']


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

## [test-os-el8](https://cmssdt.cern.ch/jenkins/job/test-os-el8)

**Description:** [11/11 - avalenzu]: Failures when getting latest bootstrap driver file from cmsrep (file not found):
<br><br>

-bash-4.2$ wget --no-check-certificate '--header=Cache-Control: max-age=0' --user-agent=CMSPKG/1.0 --timeout=600 -O /tmp/tmpuBC1G/el8_amd64_gcc10-driver.txt.tmp 'cmsrep.cern.ch/cgi-bin/cmspkg/driver/cms.sw/el8_amd64_gcc10?repo_uri=cmssw'
<br><br>
--2022-11-11 11:19:47--  http://cmsrep.cern.ch/cgi-bin/cmspkg/driver/cms.sw/el8_amd64_gcc10?repo_uri=cmssw
<br>
Resolving cmsrep.cern.ch (cmsrep.cern.ch)... 188.184.102.160
<br>
Connecting to cmsrep.cern.ch (cmsrep.cern.ch)|188.184.102.160|:80... connected.
<br>
HTTP request sent, awaiting response... 404 Not Found
<br>
2022-11-11 11:19:47 ERROR 404: Not Found.
<br><br>
Workspace for #634 at cmsbuild70.

**Project is `disabled`.**

**Upstream projects:**
* [test-os](#test-os):

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

