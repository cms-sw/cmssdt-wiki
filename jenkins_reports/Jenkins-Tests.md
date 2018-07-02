# [Jenkins Tests](https://cmssdt.cern.ch/jenkins/view/Jenkins Tests)

**View description:** None

**View type:** List View

---

# Projects:

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

