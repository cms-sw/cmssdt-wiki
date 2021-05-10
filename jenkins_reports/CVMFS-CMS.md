# [CVMFS-CMS](https://cmssdt.cern.ch/jenkins/view/CVMFS-CMS)

**View description:** None

**View type:** List View

---

# Projects:

## [cvmfs-cms-check-and-update-cmssw-git-mirror](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-cmssw-git-mirror)

**Description:** This job checks and updates the cmssw git mirror daily and monthly based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cvmfs_update_cmssw_git_mirror_v3.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
```

---

## [cvmfs-cms-check-and-update-gridpacks](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gridpacks)

**Description:** This job checks and updates gridpacks based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_rsync_generator_package_from_eos_individual.sh


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Sub-projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Triggers from:** []


**Periodic builds:**
```bash
54 * * * *
```

---

## [cvmfs-cms-check-and-update-lhapdf](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-lhapdf)

**Description:** This job checks and updates lhapdf based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_download_lhapdf.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
```

---

## [cvmfs-cms-check-and-update-report](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-report)

**Description:** This job reports status of upstream projects, siteconf and gridpacks.


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-and-update-gridpacks](#cvmfs-cms-check-and-update-gridpacks):
* [cvmfs-cms-check-and-update-siteconf](#cvmfs-cms-check-and-update-siteconf):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-check-and-update-siteconf](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-siteconf)

**Description:** This job checks and updates siteconf based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cvmfs_check_and_update_siteconf.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Sub-projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [cvmfs-cms-install-COMP-python](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-COMP-python)

**Description:** Job to install python whenever there is a new version pushed on cmsrep.cern.ch <br>
Install path is /cvmfs/${CVMFS_REPOSITORY} + COMP install dir (boostraped for comp)

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

**Downstream projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Sub-projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-install-rucio](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-rucio)

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

## [cvmfs-cms-stale-lock](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-stale-lock)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H */2 * * *
```

---

## [cvmfs-cms-test](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-test)

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

## [cvmfs-cms-update-ca-crl](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-update-ca-crl)

**Description:** This job updates CA/CRL under /cvmfs/cms.cern.ch/grid/etc/grid-security as in the following script:
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/update_ca_crl.sh

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H */6 * * *
```

---

## [cvmfs-cms-update-releases-map](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-update-releases-map)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [check-cvmfs-releases-map](#check-cvmfs-releases-map):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-create-directory-on-cvmfs](https://cmssdt.cern.ch/jenkins/job/cvmfs-create-directory-on-cvmfs)

**Description:** This is a copy of cvmfs-cms-install-package to create directories on /cvmfs/cms.cern.ch without login on the machine


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

## [cvmfs-cms-install-cms](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-cms)

**Description:** Job to install (test) releases (and IBs) once the upload is completed.
The job should be triggered by upstream job upload-release.
It's purpose is to only trigger cms-install-package with the same argument
it would get from upload-release job, but without using upload-release instance (it's just a trigger job for now)

**Project is `enabled`.**

**Upstream projects:**
* [cms-build-package](#cms-build-package):
* [cmsrep-webhook](#cmsrep-webhook):
* [update-release-map](#update-release-map):

**Downstream projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Sub-projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-install-common](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-common)

**Description:** Trigger the installation of new production architecture for CMS or reinstall cms-common new revision.<br/>
- Production architecture if obtained via <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">config.map</a><br/>
This job is triggered by <a href="https://cmssdt.cern.ch/jenkins/job/cmsrep-webhook">cmsrep-webhook</a> which should pass the cms-common revision and architecture.

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

**Downstream projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Sub-projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-install-package](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-package)

**Description:** This job installs packages using cmspkg tool
To be used for - CRAB3, PHEDEX, spacemon-client, python, releases(cmssw), cms-common
Triggered by webhook

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

