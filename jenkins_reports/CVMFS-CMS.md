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

## [cvmfs-cms-check-and-update-gen-model_config](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gen-model_config)

**Description:** This job checks and updates generators model configurations



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-check-and-update-gen-tar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gen-tar)

**Description:** This job checks and updates generators model configurations



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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
H * * * *
```

---

## [cvmfs-cms-check-and-update-gridpacks-new-generation](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gridpacks-new-generation)

**Description:** This job checks and updates gridpacks based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_rsync_generator_package_from_eos_individual.sh


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

## [cvmfs-cms-check-and-update-metadata](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-metadata)

**Description:** Job to deploy the contents of https://gitlab.cern.ch/cms-analysis-metadata to /cvmfs/cms-griddata.cern.ch/cat

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [cvmfs-cms-check-and-update-premixPUlist](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-premixPUlist)

**Description:** This job checks and updates premixPUlist
<br>https://its.cern.ch/jira/browse/CMSVOC-616</br>



**Project is `enabled`.**

**Upstream projects:**
* [eos-premixPUlist-list](#eos-premixPUlist-list):

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [cvmfs-cms-check-eos-dir](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-eos-dir)

**Description:** This job checks/compares EOS directory with cvmfs nd trigger the sync if there are changes



**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-and-update-gen-model_config](#cvmfs-cms-check-and-update-gen-model_config):
* [cvmfs-cms-check-and-update-gen-tar](#cvmfs-cms-check-and-update-gen-tar):
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Downstream projects:**
* [cvmfs-cms-sync-eos-dir](#cvmfs-cms-sync-eos-dir):

**Sub-projects:**
* [cvmfs-cms-sync-eos-dir](#cvmfs-cms-sync-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-check-gridpacks-untar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-gridpacks-untar)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-deploy-gridpacks-untar](#cvmfs-cms-deploy-gridpacks-untar):

**Sub-projects:**
* [cvmfs-cms-deploy-gridpacks-untar](#cvmfs-cms-deploy-gridpacks-untar):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-crab-symlink](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-crab-symlink)

**Description:** This changes the /cvmfs/cms.cern.ch/common/crab symlink to point to either crab-pre, crab-prod or crab-dev.<br/>

<b>Note any cmssw release which installs a different crab version will revert the symlink back to crab-prod</b><br/>

Note that this only changes the /cvmfs/cms.cern.ch/common/crab symlink. For crab python api, one still needs to source /cvmfs/cms.cern.ch/common/crab-setup.sh prod|pre|dev


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

## [cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration)

**Description:** This deploys a gitlab repository under /cvmfs/cms.cern.ch/rsync/repository/name<br/>
- POG scale factors on CVMFS: Requested by XPOG silvio.donato@cern.ch

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-rsync-gitlab-repo](#cvmfs-cms-rsync-gitlab-repo):

**Sub-projects:**
* [cvmfs-cms-rsync-gitlab-repo](#cvmfs-cms-rsync-gitlab-repo):

**Triggers from:** []


**Periodic builds:**
```bash
5 5 * * *
```

---

## [cvmfs-cms-deploy-cuda-compatible-runtime](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-cuda-compatible-runtime)

**Description:** This job checks and updates cuda-compatible-runtime. This is used by CMS pilot jobs to find available gpu on the worker node.<br/>

Requestsed by marco.mascheroni@cern.ch and andrea.bocci@cern.ch


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-check-cuda-compatible-runtime](#cvmfs-check-cuda-compatible-runtime):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-deploy-gridpacks-untar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-gridpacks-untar)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-gridpacks-untar](#cvmfs-cms-check-gridpacks-untar):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [cvmfs-cms-reseed](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-reseed)

**Description:** This job installs packages using cmspkg tool
To be used for - CRAB3, PHEDEX, spacemon-client, python, releases(cmssw), cms-common
Triggered by webhook

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

## [cvmfs-cms-reseed-architecture](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-reseed-architecture)

**Description:** This job is to reseed a already installed architecture.
This is needed when we have updated the packages to be seeded from the system installation.


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

## [cvmfs-cms-rsync-gitlab-repo](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-rsync-gitlab-repo)

**Description:** This deploys a gitlab repository under /cvmfs/cms.cern.ch/rsync/repository/name<br/>


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration](#cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration):

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

## [cvmfs-cms-sync-eos-dir](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-sync-eos-dir)

**Description:** This job syncs an EOS directory on to CVMFS



**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [cvmfs-deploy-py23](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-py23)

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

## [cvmfs-install-cuda](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-cuda)

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

## [cvmfs-install-fix-cuda](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-fix-cuda)

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

## [cvmfs-install-shared-pip-package](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-shared-pip-package)

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

## [eos-premixPUlist-list](https://cmssdt.cern.ch/jenkins/job/eos-premixPUlist-list)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Sub-projects:**
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
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

