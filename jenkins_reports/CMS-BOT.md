# [CMS-BOT](https://cmssdt.cern.ch/jenkins/view/CMS-BOT)

**View description:** None

**View type:** Build Pipeline View

---

# Projects:

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**

* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**

* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [stop-ib-any-integration](#stop-ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Triggers from:** []

## [ib-schedule-pr-tests](https://cmssdt.cern.ch/jenkins/job/ib-schedule-pr-tests)

**Description:** Build a pull request

**Upstream projects:**

* [cms-bot](#cms-bot):

**Downstream projects:**

* [ib-any-integration](#ib-any-integration):

**Sub-projects:**

* [ib-any-integration](#ib-any-integration):

**Triggers from:** []

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** Build a pull request

**Upstream projects:**

* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**

* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [run-igprof-pr](#run-igprof-pr):
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**

* [stop-ib-any-integration](#stop-ib-any-integration):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [run-igprof-pr](#run-igprof-pr):

**Triggers from:** []

## [compare-root-files-short-matrix](https://cmssdt.cern.ch/jenkins/job/compare-root-files-short-matrix)

**Description:** Download the files of the baseline IB and compare them with the results of the ones of a pull request

**Upstream projects:**

* [ib-any-integration](#ib-any-integration):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [run-igprof-pr](https://cmssdt.cern.ch/jenkins/job/run-igprof-pr)

**Description:** ---need-description---

**Upstream projects:**

* [ib-any-integration](#ib-any-integration):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Upstream projects:**

* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [run-pr-code-ckecks](https://cmssdt.cern.ch/jenkins/job/run-pr-code-ckecks)

**Description:** This run "scram build code-checks" for a cmssw PR to find out if it comply with cmssw code checks.
In a CMSSW dev area, it runs 
  git cms-merge-topic -u PR
  scram build code-checks

**Upstream projects:**

* [cms-bot](#cms-bot):

**Downstream projects:**

* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**

* [stop-ib-any-integration](#stop-ib-any-integration):

**Triggers from:** []

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Upstream projects:**

* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Upstream projects:**

* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []
