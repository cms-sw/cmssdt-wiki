# [CMS-BOT](https://cmssdt.cern.ch/jenkins/view/CMS-BOT)

**View description:** This view has all the projects involved for continuous integration testing (pull request testing, all issues processing in Github.com etc. ) 

**View type:** Build Pipeline View

---

# Projects:

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.

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
* [run-pr-tests](#run-pr-tests):

**Sub-projects:**
* [ib-any-integration](#ib-any-integration):
* [run-pr-tests](#run-pr-tests):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** This job will take pull request and merged it to branch, then build an IB and run selected tests.
It will upload results online and comment back to PR the tests results. 


<br>
<br>

<b>Q/a:</b>

<ul>
  <li>
    Q: git error - "error: switch `b' requires a value" 
  </li>  
  <li>
    A: It happened to a job in  a form of `PR cmssw#24237 cmsdist#4249` when `cmssw#24237` was a back port 
    to 10_2 from 10_3, but there was no related pull request on cmsdist 10_2 branch (cmssw#24237 was 
    a pull request on branch 10_3). Solved creating back port on cmsdist manually. 
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**
* [stop-ib-any-integration](#stop-ib-any-integration):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

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
* [run-pr-tests](#run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [Test_get_source_flag](#Test_get_source_flag):
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [run-pr-tests](#run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-pr-tests](https://cmssdt.cern.ch/jenkins/job/run-pr-tests)

**Description:** Build mutiple  a pull requests

<br>
<br>



**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**
* [stop-ib-any-integration](#stop-ib-any-integration):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

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
* [run-pr-tests](#run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [Test_get_source_flag](#Test_get_source_flag):
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [run-pr-tests](#run-pr-tests):

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

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [Test_get_source_flag](#Test_get_source_flag):
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [run-pr-tests](#run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running job (by default it is 'ib-any-integration'). 

The idea is that if pull reguest was updated, all the test should be restarted. This job will kill all the running jobs for that
PR and matching parameters. It will ignore given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [Test_get_source_flag](#Test_get_source_flag):
* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [run-pr-tests](#run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

