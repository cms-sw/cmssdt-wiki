# [Services](https://cmssdt.cern.ch/jenkins/view/Services)

**View description:** None

**View type:** List View

---

# Projects:

## [cleanup-auto-build](https://cmssdt.cern.ch/jenkins/job/cleanup-auto-build)

**Description:** This job deletes the relsease build areas after three days.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-cms-sw-io-history](https://cmssdt.cern.ch/jenkins/job/cleanup-cms-sw-io-history)

**Description:** This job cleanup the cms-sw/cms-sw.github.io repository history. Specially the data and _data directories history.


**Upstream projects:**


**Downstream projects:**

* [update-github-pages](#update-github-pages):

**Sub-projects:**


**Triggers from:** []

## [cleanup-cmssdt](https://cmssdt.cern.ch/jenkins/job/cleanup-cmssdt)

**Description:** Clean up disk space on cmssdt

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-tags](https://cmssdt.cern.ch/jenkins/job/cleanup-tags)

**Description:** Cleanup IB tags from the official CMSSW repository.


**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cmspkg-clone](https://cmssdt.cern.ch/jenkins/job/cmspkg-clone)

**Description:** None

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [upload-release](#upload-release):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [deploy-cms-repo](https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo)

**Description:** Updates cms-bot clone on Jenkins master

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [deploy-cmsdoxygen](https://cmssdt.cern.ch/jenkins/job/deploy-cmsdoxygen)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [gh-teams](https://cmssdt.cern.ch/jenkins/job/gh-teams)

**Description:** printing some python file	

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [git-mirror-repository](https://cmssdt.cern.ch/jenkins/job/git-mirror-repository)

**Description:** mirror one git repository

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [git-reference-cms-ib](https://cmssdt.cern.ch/jenkins/job/git-reference-cms-ib)

**Description:** Create GIT Reference for cms-sw/cmssw repository in /cvmfs/cms-ib.cern.ch/git/cms-sw.
This is automatically triggered by "git push" to cmssw repo.

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [github-hooks](https://cmssdt.cern.ch/jenkins/job/github-hooks)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [github-push-hook](https://cmssdt.cern.ch/jenkins/job/github-push-hook)

**Description:** Updates cms-bot clone on cmssdt.
This job is also triggered via github web hook. Please do not add/remove any parameters of this job otherwise github web hooks will not be able to triiger the job

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**

* [auto-forward-ports](#auto-forward-ports):
* [deploy-cms-repo](#deploy-cms-repo):
* [git-mirror-repository](#git-mirror-repository):
* [git-reference-cms-ib](#git-reference-cms-ib):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):

**Sub-projects:**

* [deploy-cms-repo](#deploy-cms-repo):
* [auto-forward-ports](#auto-forward-ports):
* [git-reference-cms-ib](#git-reference-cms-ib):
* [git-mirror-repository](#git-mirror-repository):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):

**Triggers from:** []

## [mirror-cmsrep](https://cmssdt.cern.ch/jenkins/job/mirror-cmsrep)

**Description:** Create a live mirror of cmsrep.cern.ch

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [monitor-openstack-vms](https://cmssdt.cern.ch/jenkins/job/monitor-openstack-vms)

**Description:** This job run periodically to monitor the running state of vms in openstack , if stopped , creates an email alert.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [slaves-checks](https://cmssdt.cern.ch/jenkins/job/slaves-checks)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [test-docker](#test-docker):
* [workspace-cleanup-slave](#workspace-cleanup-slave):

**Sub-projects:**

* [workspace-cleanup-slave](#workspace-cleanup-slave):
* [test-docker ](#test-docker ):

**Triggers from:** []

## [test-build-periodic](https://cmssdt.cern.ch/jenkins/job/test-build-periodic)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [test-docker](https://cmssdt.cern.ch/jenkins/job/test-docker)

**Description:** None

**Upstream projects:**

* [slaves-checks](#slaves-checks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-categories-page](https://cmssdt.cern.ch/jenkins/job/update-categories-page)

**Description:** ---need-description---

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-release-map](https://cmssdt.cern.ch/jenkins/job/update-release-map)

**Description:** This project adds the release information in <a href="https://cmssdt.cern.ch/SDT/releases.map">cms-bot/releases.map</a> file.
CVMFS installation is started once a release is available in this file.

**Upstream projects:**

* [upload-release](#upload-release):

**Downstream projects:**

* [build-fwlite](#build-fwlite):
* [cmssw-doxygen](#cmssw-doxygen):
* [ib-run-cfipython](#ib-run-cfipython):

**Sub-projects:**


**Triggers from:** []

## [web-summary-data](https://cmssdt.cern.ch/jenkins/job/web-summary-data)

**Description:** Scans build summary (ib-report-generator/scan-build-summary)

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [web-update-SDT](https://cmssdt.cern.ch/jenkins/job/web-update-SDT)

**Description:** ---need-description---

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [workspace-cleanup-slave](https://cmssdt.cern.ch/jenkins/job/workspace-cleanup-slave)

**Description:** None

**Upstream projects:**

* [slaves-checks](#slaves-checks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

