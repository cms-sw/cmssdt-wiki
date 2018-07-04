# [CMS-BOT](https://cmssdt.cern.ch/jenkins/view/CMS-BOT)

**View description:** This view has all the projects involved for continuous integration testing (pull request testing, all issues processing in Github.com etc. ) 

**View type:** Build Pipeline View

---

# Projects:

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Project is `enabled`.**

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


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-schedule-pr-tests](https://cmssdt.cern.ch/jenkins/job/ib-schedule-pr-tests)

**Description:** Build a pull request

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [ib-any-integration](#ib-any-integration):

**Sub-projects:**
* [ib-any-integration](#ib-any-integration):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** Build a pull request

**Project is `enabled`.**

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


**Periodic builds:**
```bash
Not periodically build
```

---

## [compare-root-files-short-matrix](https://cmssdt.cern.ch/jenkins/job/compare-root-files-short-matrix)

**Description:** Download the files of the baseline IB and compare them with the results of the ones of a pull request

**Project is `enabled`.**

**Upstream projects:**
* [ib-any-integration](#ib-any-integration):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-igprof-pr](https://cmssdt.cern.ch/jenkins/job/run-igprof-pr)

**Description:** ---need-description---

**Project is `enabled`.**

**Upstream projects:**
* [ib-any-integration](#ib-any-integration):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-pr-code-ckecks](https://cmssdt.cern.ch/jenkins/job/run-pr-code-ckecks)

**Description:** This run "scram build code-checks" for a cmssw PR to find out if it comply with cmssw code checks.
In a CMSSW dev area, it runs 
  git cms-merge-topic -u PR
  scram build code-checks

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**
* [stop-ib-any-integration](#stop-ib-any-integration):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

