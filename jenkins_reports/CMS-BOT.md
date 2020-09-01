# [CMS-BOT](https://cmssdt.cern.ch/jenkins/view/CMS-BOT)

**View description:** This view has all the projects involved for continuous integration testing (pull request testing, all issues processing in Github.com etc. ) 

**View type:** Build Pipeline View

---

# Projects:

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.

Will kill a scheduled/running job acording to comments.

<br><br>
<b>Q/A</b>

<ul>
  <li>
    <b>Q:</b> Job 'cms-sw/cmssw #****' failed. What to do?
  </li>
  <li>
    <b>A:</b> If cause of failure is fixed (bug in cms-bot, github servers issue), job should be restarted. Otherwise PR will not be procesed unless someone retrigers it by writing a comment.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Sub-projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [abort-pr-tests ](#abort-pr-tests ):
* [run-pr-code-checks](#run-pr-code-checks):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-pr-tests](https://cmssdt.cern.ch/jenkins/job/abort-pr-tests)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

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
* [ib-run-pr-tests](#ib-run-pr-tests):

**Sub-projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-tests](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-tests)

**Description:** Build mutiple  a pull requests. 
Same puprose as `ib-any-integration`, just different script is called.




**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [test-ib-schedule-pr-tests](#test-ib-schedule-pr-tests):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

**Sub-projects:**
* [abort-pr-tests](#abort-pr-tests):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-pr-tests](https://cmssdt.cern.ch/jenkins/job/abort-pr-tests)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

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
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-pr-code-checks](https://cmssdt.cern.ch/jenkins/job/run-pr-code-checks)

**Description:** This run "scram build code-checks" for a cmssw PR to find out if it comply with cmssw code checks.
In a CMSSW dev area, it runs 
  git cms-merge-topic -u PR
  scram build code-checks

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):
* [cms-prs-files](#cms-prs-files):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):
* [cms-prs-files](#cms-prs-files):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-prs-files](https://cmssdt.cern.ch/jenkins/job/cms-prs-files)

**Description:** On every CMSSW PR, this job dumps list of files that are going to be modified by open PRs to files_changed_by_prs.json .

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H/2 * * *
```

---

