# [CMSSW Releases](https://cmssdt.cern.ch/jenkins/view/CMSSW Releases)

**View description:** All jobs triggered/used for CMSSW Release Build

**View type:** Build Pipeline View

---

# Projects:

## [query-build-release-issues](https://cmssdt.cern.ch/jenkins/job/query-build-release-issues)

**Description:** ---need-description---

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**

* [abort-release](#abort-release):
* [build-release](#build-release):
* [cleanup-auto-build](#cleanup-auto-build):
* [release-produce-changelog](#release-produce-changelog):
* [upload-release-setup](#upload-release-setup):

**Sub-projects:**

* [build-release](#build-release):
* [upload-release-setup](#upload-release-setup):
* [cleanup-auto-build](#cleanup-auto-build):
* [release-produce-changelog](#release-produce-changelog):
* [abort-release](#abort-release):

**Triggers from:** []

## [abort-release](https://cmssdt.cern.ch/jenkins/job/abort-release)

**Description:** Aborts and kills a release building process.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [kill-build-release](#kill-build-release):

**Sub-projects:**

* [kill-build-release](#kill-build-release):

**Triggers from:** []

## [kill-build-release](https://cmssdt.cern.ch/jenkins/job/kill-build-release)

**Description:** Aborts and kills a release building process. 

**Upstream projects:**

* [abort-release](#abort-release):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [build-release](https://cmssdt.cern.ch/jenkins/job/build-release)

**Description:** This job actually builds a release.
It is triggered by cms-bot after the <a href="https://github.com/cms-sw/cmssw/issues?q=label%3Arelease-notes-requested">Release build Issue</a> is approved by release manager.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-auto-build](https://cmssdt.cern.ch/jenkins/job/cleanup-auto-build)

**Description:** This job deletes the relsease build areas after three days.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [release-produce-changelog](https://cmssdt.cern.ch/jenkins/job/release-produce-changelog)

**Description:** ---need-description---

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [update-release-notes-collection](#update-release-notes-collection):

**Sub-projects:**

* [update-release-notes-collection](#update-release-notes-collection):

**Triggers from:** []

## [update-release-notes-collection](https://cmssdt.cern.ch/jenkins/job/update-release-notes-collection)

**Description:** None

**Upstream projects:**

* [release-produce-changelog](#release-produce-changelog):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [upload-release-setup](https://cmssdt.cern.ch/jenkins/job/upload-release-setup)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [upload-release](#upload-release):

**Sub-projects:**


**Triggers from:** []

## [upload-release](https://cmssdt.cern.ch/jenkins/job/upload-release)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Upstream projects:**

* [upload-release-setup](#upload-release-setup):

**Downstream projects:**

* [cmspkg-clone](#cmspkg-clone):
* [release-deploy-afs](#release-deploy-afs):
* [update-release-map](#update-release-map):

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

## [release-deploy-afs](https://cmssdt.cern.ch/jenkins/job/release-deploy-afs)

**Description:** ---need-description---

**Upstream projects:**

* [upload-release](#upload-release):

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

## [build-fwlite](https://cmssdt.cern.ch/jenkins/job/build-fwlite)

**Description:** TO build a CMSSW_X_Y_Z_FWLITE release based on an existing CMSSW_X_Y_Z release. CMSSW_X_Y_Z should already be build/uploaded before building its FWLITE version.

**Upstream projects:**

* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cmssw-doxygen](https://cmssdt.cern.ch/jenkins/job/cmssw-doxygen)

**Description:** Generate doxygen documentation for CMSSW project

**Upstream projects:**

* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-cfipython](https://cmssdt.cern.ch/jenkins/job/ib-run-cfipython)

**Description:** This job gets the cfipython files for a cmssw release and push the changes to cms-sw/cmssw-cfipython repo.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):
* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []
