# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

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

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except no IB at 23h Sat & 11h Sun but a special IB at Sun 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
This was created to avoid the issue with <a href="https://wiki.jenkins.io/display/JENKINS/Dynamic+Parameter+Plug-in">Jenkins Dynamic Parameters</a>.


**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Sub-projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Triggers from:** []


**Periodic builds:**
```bash
#Special IB at 0h on Sunday
5  0   * *  0
#We skip Sunday 11h IB to leave resources for special Sunday's 0h IB
5 11  * * 1,2,3,4,5,6
#We do not run SAT 23H IB instead we start a special SUN 00h00 IB.
5 23  * *  0,1,2,3,4,5
```

---

## [ib-tag-and-schdule](https://cmssdt.cern.ch/jenkins/job/ib-tag-and-schdule)

**Description:** This job tags and schedules all the IBs.<br/>
It reads the <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a> to find all available CMSSW release cycles and tag them in github.
Once tags is done then it triggers 'build-any-ib' sub-job to actually build IBs for all possible architectures (mentioned in <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a>).
For Developement IB, it also triggers the generation of <a href="https://cmssdt.cern.ch/lxr">LXR indexes</a>

For Sunday's 00h IBs, it also resets the CMSREP weekly repositories by building a dummy package and uploading it to cms.weekN. It also 
then triggers 'ib-install-cvmfs' sub-job to get the new cms.weekN deployed on the /cvmfs/cms-ib.cern.ch

This job re-tries itself on failure. So there is no need to re-try it manually (unless all re-tries failed).

**Project is `disabled`.**

**Upstream projects:**
* [ib-schedule](#ib-schedule):

**Downstream projects:**
* [build-any-ib](#build-any-ib):
* [cleanup-cmsrep](#cleanup-cmsrep):
* [cleanup-cvmfs-ci](#cleanup-cvmfs-ci):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Sub-projects:**
* [build-any-ib](#build-any-ib):
* [ib-install-cvmfs,ib-install-cvmfs-gateway](#ib-install-cvmfs,ib-install-cvmfs-gateway):
* [cleanup-cmsrep,cleanup-cvmfs-ci](#cleanup-cmsrep,cleanup-cvmfs-ci):

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

