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
    <b>A:</b>
    Job is configured to do few re-tries, so in case of github or network glitches the job will recover. If it keeps on failing then one need to check the logs. 
    Mostly it fails due to github/ssh connection, so it will automatically recover.
  </li>
  <li>
    <b>Q:</b> Job failed with ssh timeout?
  </li>
  <li>
    <b>A:</b>
    Nothing to do, job will re-try 3 time to recover. If it keeps on failing for few hours then better to disable it an re-enable once issue is solved e.g. github is back or CERN network is working again.
  </li>
  
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
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

**Description:** This basically triiger abort-jenkins-jobs for all the jobs related to PR tests

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

**Description:** Kill a running job (by default it is 'ib-run-pr-tests and jobs started by it'). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore given job ID - the ID of upstream job that started this job.

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

**Description:** This is CMSSw CI Job which runs the build and unit tests part of CI. 
It first kills any other job whcih is running for same PullRequests/Architecture. and then starts the build process.
Once the build process if done then it trigger other jobs to start the deployment of the build artifects on CVMFS and
start the tests. at the end it run the unit tests. Unit tests are run here as it needs the CMSSW/tmp directory which
is not deployed on CVMFS.

<b>Q/A:</b>
In case this job fails then in most cases just re-try it. In case it is failed due to network/github issues then it is
better to wait for the service to get healthy.




**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [ib-run-pr-baseline](#ib-run-pr-baseline):
* [ib-run-pr-wait-deployment](#ib-run-pr-wait-deployment):
* [pr-publish-cmssw](#pr-publish-cmssw):
* [update-das-queries](#update-das-queries):

**Sub-projects:**
* [abort-pr-tests](#abort-pr-tests):
* [pr-publish-cmssw](#pr-publish-cmssw):
* [ib-run-pr-wait-deployment](#ib-run-pr-wait-deployment):
* [ib-run-pr-baseline ](#ib-run-pr-baseline ):
* [update-das-queries ](#update-das-queries ):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-pr-tests](https://cmssdt.cern.ch/jenkins/job/abort-pr-tests)

**Description:** This basically triiger abort-jenkins-jobs for all the jobs related to PR tests

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

**Description:** Kill a running job (by default it is 'ib-run-pr-tests and jobs started by it'). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore given job ID - the ID of upstream job that started this job.

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

## [ib-run-pr-baseline](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-baseline)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):

**Sub-projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-deploy-artifacts](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-artifacts)

**Description:** Copy baseline results from cmssdt for an IB

**Project is `enabled`.**

**Upstream projects:**
* [cms-run-baseline](#cms-run-baseline):
* [ib-run-baseline](#ib-run-baseline):
* [ib-run-pr-baseline](#ib-run-pr-baseline):

**Downstream projects:**
* [cvmfs-publish-artifacts](#cvmfs-publish-artifacts):

**Sub-projects:**
* [cvmfs-publish-artifacts](#cvmfs-publish-artifacts):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-publish-artifacts](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-artifacts)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-wait-deployment](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-wait-deployment)

**Description:** Build mutiple  a pull requests. 
Same puprose as `ib-any-integration`, just different script is called.




**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**

**Sub-projects:**
* [ib-run-pr-${TEST_TYPE}](#ib-run-pr-${TEST_TYPE}):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [pr-publish-cmssw](https://cmssdt.cern.ch/jenkins/job/pr-publish-cmssw)

**Description:** None

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

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):
* [ib-run-relvals](#ib-run-relvals):

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

This job re-tries twice to recover. If it still fails after two retires then try to understand the failure and re-try again.

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

**Description:** Kill a running job (by default it is 'ib-run-pr-tests and jobs started by it'). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore given job ID - the ID of upstream job that started this job.

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

