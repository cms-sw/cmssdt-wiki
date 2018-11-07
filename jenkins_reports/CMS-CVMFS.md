# [CMS-CVMFS](https://cmssdt.cern.ch/jenkins/view/CMS-CVMFS)

**View description:** None

**View type:** Dashboard

---

# Projects:

## [install-cms-common-devjob](https://cmssdt.cern.ch/jenkins/job/install-cms-common-devjob)

**Description:** Install cms-common for any new architecture listed as production arch ('PROD_ARCH=1')
found here: https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map
The job tries to bootstrap (if not) and install cms+cms-common+1.0 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [install-cms-package-cmsbot-devjob](#install-cms-package-cmsbot-devjob):

**Sub-projects:**
* [install-cms-package-cmsbot-devjob](#install-cms-package-cmsbot-devjob):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [install-cms-package-cmsbot-devjob](https://cmssdt.cern.ch/jenkins/job/install-cms-package-cmsbot-devjob)

**Description:** This job installs packages using cmspkg tool

**Project is `enabled`.**

**Upstream projects:**
* [install-cms-common-devjob](#install-cms-common-devjob):
* [install-release-devjob](#install-release-devjob):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [install-release-devjob](https://cmssdt.cern.ch/jenkins/job/install-release-devjob)

**Description:** This is a test job to install releases and IBs once the upload is completed.
The job should be triggered by upstream job upload-release.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [install-cms-package-cmsbot-devjob](#install-cms-package-cmsbot-devjob):

**Sub-projects:**
* [install-cms-package-cmsbot-devjob](#install-cms-package-cmsbot-devjob):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

