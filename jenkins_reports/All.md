# [All](https://cmssdt.cern.ch/jenkins/view/All)

**View description:** None

**View type:** All

---

# Projects:

## [abort-tests](https://cmssdt.cern.ch/jenkins/job/abort-tests)

**Description:** None

**Upstream projects:**

* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-EcalLaserValidation-HLT_EcalLaserValidation-tests](#run-EcalLaserValidation-HLT_EcalLaserValidation-tests):
* [run-cms_patatrack-cmssw-tests](#run-cms_patatrack-cmssw-tests):
* [run-smuzaffar-int-build-tests](#run-smuzaffar-int-build-tests):
* [run-user-test-template](#run-user-test-template):

**Downstream projects:**

* [jenkins-stop-job](#jenkins-stop-job):

**Sub-projects:**

* [jenkins-stop-job](#jenkins-stop-job):

**Triggers from:** []

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**

* [abort-tests](#abort-tests):
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [schedule-user-tests](#schedule-user-tests):

**Sub-projects:**

* [run-pr-code-ckecks](#run-pr-code-ckecks):
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [schedule-user-tests](#schedule-user-tests):
* [abort-tests](#abort-tests):

**Triggers from:** []

## [compare-root-files-short-matrix](https://cmssdt.cern.ch/jenkins/job/compare-root-files-short-matrix)

**Description:** Download the files of the baseline IB and compare them with the results of the ones of a pull request

**Upstream projects:**

* [ib-any-integration](#ib-any-integration):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [deploy-cms-repo](https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo)

**Description:** Updates cms-bot clone on Jenkins master

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [github-webhook](https://cmssdt.cern.ch/jenkins/job/github-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Upstream projects:**


**Downstream projects:**

* [cms-bot](#cms-bot):
* [schedule-user-push-tests](#schedule-user-push-tests):

**Sub-projects:**

* [cms-bot](#cms-bot):
* [schedule-user-push-tests](#schedule-user-push-tests):

**Triggers from:** []

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** Build a pull request

**Upstream projects:**

* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**

* [abort-tests](#abort-tests):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

**Sub-projects:**

* [abort-tests](#abort-tests):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):

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

## [jenkins-backup](https://cmssdt.cern.ch/jenkins/job/jenkins-backup)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-disable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-jobs)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-disable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-nodes)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-elasticsearch-monitor](https://cmssdt.cern.ch/jenkins/job/jenkins-elasticsearch-monitor)

**Description:** This job runs a pthon script to push useful info from jenkins build logs to elasticsearch and kibana viewing



**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-enable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-jobs)

**Description:** None

**Upstream projects:**

* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-enable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-nodes)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-initialize](https://cmssdt.cern.ch/jenkins/job/jenkins-initialize)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [jenkins-enable-jobs](#jenkins-enable-jobs):
* [jenkins-installation-cli-test](#jenkins-installation-cli-test):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):

**Sub-projects:**

* [jenkins-enable-jobs](#jenkins-enable-jobs):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):

**Triggers from:** []

## [jenkins-installation-cli-test](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-cli-test)

**Description:** None

**Upstream projects:**

* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-installation-trigger-cli](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-cli)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-installation-trigger-test](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-test)

**Description:** None

**Upstream projects:**

* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-projects-report](https://cmssdt.cern.ch/jenkins/job/jenkins-projects-report)

**Description:** This job runs a groovy script to dump jenkins
projects info , which is further read by python to 
display it in html form. The current page you are viewing is generated and updated by this job.



**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-restart-slaves](https://cmssdt.cern.ch/jenkins/job/jenkins-restart-slaves)

**Description:** This jobs looks for jenkins slaves which went offline due to job failures


**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-stop-job](https://cmssdt.cern.ch/jenkins/job/jenkins-stop-job)

**Description:** Kill a running 

**Upstream projects:**

* [abort-tests](#abort-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-job1](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job1)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**

* [${SUB_JOB}](#${SUB_JOB}):

**Triggers from:** []

## [jenkins-test-job2](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job2)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-job3](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job3)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-slave](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slave)

**Description:** None

**Upstream projects:**

* [jenkins-test-slaves](#jenkins-test-slaves):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-slaves](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slaves)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [jenkins-test-slave](#jenkins-test-slave):

**Sub-projects:**

* [jenkins-test-slave](#jenkins-test-slave):

**Triggers from:** []

## [openstack-add-jenkins-slave](https://cmssdt.cern.ch/jenkins/job/openstack-add-jenkins-slave)

**Description:** Find all hosts in an hostgroup and add then to jenkins

**Upstream projects:**

* [openstack-check-jenkins-slaves](#openstack-check-jenkins-slaves):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [openstack-check-jenkins-slaves](https://cmssdt.cern.ch/jenkins/job/openstack-check-jenkins-slaves)

**Description:** Find all hosts in an hostgroup and add then to jenkins

**Upstream projects:**


**Downstream projects:**

* [openstack-add-jenkins-slave](#openstack-add-jenkins-slave):

**Sub-projects:**

* [openstack-add-jenkins-slave](#openstack-add-jenkins-slave):

**Triggers from:** []

## [run-cms_patatrack-cmssw-tests](https://cmssdt.cern.ch/jenkins/job/run-cms_patatrack-cmssw-tests)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [abort-tests](#abort-tests):

**Sub-projects:**

* [abort-tests](#abort-tests):

**Triggers from:** []

## [run-EcalLaserValidation-HLT_EcalLaserValidation-push-tests](https://cmssdt.cern.ch/jenkins/job/run-EcalLaserValidation-HLT_EcalLaserValidation-push-tests)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [run-EcalLaserValidation-HLT_EcalLaserValidation-tests](https://cmssdt.cern.ch/jenkins/job/run-EcalLaserValidation-HLT_EcalLaserValidation-tests)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [abort-tests](#abort-tests):

**Sub-projects:**

* [abort-tests](#abort-tests):

**Triggers from:** []

## [run-EcalLaserValidation-L1T_EcalLaserValidation-push-tests](https://cmssdt.cern.ch/jenkins/job/run-EcalLaserValidation-L1T_EcalLaserValidation-push-tests)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [run-EcalLaserValidation-TPG_EcalLaserValidation-push-tests](https://cmssdt.cern.ch/jenkins/job/run-EcalLaserValidation-TPG_EcalLaserValidation-push-tests)

**Description:** None

**Upstream projects:**


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


**Sub-projects:**


**Triggers from:** []

## [run-smuzaffar-int-build-tests](https://cmssdt.cern.ch/jenkins/job/run-smuzaffar-int-build-tests)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [abort-tests](#abort-tests):

**Sub-projects:**

* [abort-tests](#abort-tests):

**Triggers from:** []

## [run-user-test-template](https://cmssdt.cern.ch/jenkins/job/run-user-test-template)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [abort-tests](#abort-tests):

**Sub-projects:**

* [abort-tests](#abort-tests):

**Triggers from:** []

## [schedule-user-push-tests](https://cmssdt.cern.ch/jenkins/job/schedule-user-push-tests)

**Description:** None

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**


**Sub-projects:**

* [run-${REPO_STRING}-push-tests](#run-${REPO_STRING}-push-tests):

**Triggers from:** []

## [schedule-user-tests](https://cmssdt.cern.ch/jenkins/job/schedule-user-tests)

**Description:** None

**Upstream projects:**

* [cms-bot](#cms-bot):

**Downstream projects:**


**Sub-projects:**

* [run-${REPO_STRING}-tests](#run-${REPO_STRING}-tests):

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

## [test-docker](https://cmssdt.cern.ch/jenkins/job/test-docker)

**Description:** None

**Upstream projects:**

* [slaves-checks](#slaves-checks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [test-remote-triggerred](https://cmssdt.cern.ch/jenkins/job/test-remote-triggerred)

**Description:** None

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

