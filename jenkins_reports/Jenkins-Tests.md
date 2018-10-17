# [Jenkins Tests](https://cmssdt.cern.ch/jenkins/view/Jenkins Tests)

**View description:** None

**View type:** List View

---

# Projects:

## [jenkins-add-job-to-anthoer-server](https://cmssdt.cern.ch/jenkins/job/jenkins-add-job-to-anthoer-server)

**Description:** This is a helper job to copy a Jenkins Project from this Jenkins master to another Jenkins master.

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

## [jenkins-backup](https://cmssdt.cern.ch/jenkins/job/jenkins-backup)

**Description:** This job takes the backup of Jenkins master configuration (which includes projects, jenkins configuration, slaves, secrets etc.)
Backups jenkins scripts on https://github.com/cms-sw/jenkins-backup.git

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/5 * * * *
```

---

## [jenkins-disable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-jobs)

**Description:** Disable all nodes that started with the provided wildcard string,
example parameter
cmsbuild* 
would enable all cmsbuild machines found

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

## [jenkins-disable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-nodes)

**Description:** Disable all jenkins slaves based on the slave wildcard filter.

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

## [jenkins-elasticsearch-monitor](https://cmssdt.cern.ch/jenkins/job/jenkins-elasticsearch-monitor)

**Description:** This job runs a python script to push useful info from jenkins build logs to elasticsearch



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/5 * * * *
```

---

## [jenkins-enable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-jobs)

**Description:** Enable all Jenkins projects based on the wildcard filter.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-enable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-nodes)

**Description:** Enables all nodes that started with the provided wildcard string,
example parameter
cmsbuild* 
would enable all cmsbuild machines found

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

## [jenkins-env](https://cmssdt.cern.ch/jenkins/job/jenkins-env)

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

## [jenkins-initialize](https://cmssdt.cern.ch/jenkins/job/jenkins-initialize)

**Description:** This project is run once a new Jenkins instance is setup or upgrated to a new version.
This runs some sub-projects to check if basic functionality of jenkins is working.

**Project is `enabled`.**

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


**Periodic builds:**
```bash
H H * * *
```

---

## [jenkins-installation-cli-test](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-cli-test)

**Description:** This is Jenkins installation tests project. It tests if various Jenkins Command-line interface service are working.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-installation-trigger-cli](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-cli)

**Description:** Jenkins installaton test job to test the triggering of a sub-project via Command-line-interface.

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

## [jenkins-installation-trigger-test](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-test)

**Description:** This is Jenkins installation test project. This tests the triggering of a sub-project.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-projects-report](https://cmssdt.cern.ch/jenkins/job/jenkins-projects-report)

**Description:** This job runs a groovy script to dump jenkins
projects info , which is further read by python to 
display it in html form. The current page you are viewing is generated and updated by this job.



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

## [jenkins-projects-wiki-update](https://cmssdt.cern.ch/jenkins/job/jenkins-projects-wiki-update)

**Description:** This job runs a groovy script to dump jenkinsprojects info , which is further read by python to 
display it in markdown form. It is later imported to CMSSDT wiki.



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/5 * * * *
```

---

## [jenkins-restart-slaves](https://cmssdt.cern.ch/jenkins/job/jenkins-restart-slaves)

**Description:** This jobs looks for jenkins slaves which went offline due to job failures


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

## [jenkins-test-command-on-slave](https://cmssdt.cern.ch/jenkins/job/jenkins-test-command-on-slave)

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

## [jenkins-test-job1](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job1)

**Description:** Jenkins installation test job 1 to check for the parameters passed from a parent job.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-test-ws-trigger-job](#jenkins-test-ws-trigger-job):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-test-job2](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job2)

**Description:** Jenkins tests Project to test jenkins functionality.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-test-ws-trigger-job](#jenkins-test-ws-trigger-job):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-test-kerberos](https://cmssdt.cern.ch/jenkins/job/jenkins-test-kerberos)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-test-slaves](#jenkins-test-slaves):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-test-localcli](https://cmssdt.cern.ch/jenkins/job/jenkins-test-localcli)

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

## [jenkins-test-slave](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slave)

**Description:** This Jenkins project test various CMS Jenkins slaves and makes sure that various communication channels 
between Jenkins Master/slave  and slave and various services are working.

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-test-slaves](#jenkins-test-slaves):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-test-slaves](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slaves)

**Description:** Jenkins project to trigger the jenkins slave test job for each selected slave

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [jenkins-test-kerberos](#jenkins-test-kerberos):
* [jenkins-test-slave](#jenkins-test-slave):

**Sub-projects:**
* [jenkins-test-slave](#jenkins-test-slave):
* [jenkins-test-kerberos](#jenkins-test-kerberos):

**Triggers from:** []


**Periodic builds:**
```bash
H H/8 * * *
```

---

## [jenkins-test-workspace](https://cmssdt.cern.ch/jenkins/job/jenkins-test-workspace)

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

## [jenkins-test-ws-trigger-job](https://cmssdt.cern.ch/jenkins/job/jenkins-test-ws-trigger-job)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [jenkins-test-job1](#jenkins-test-job1):
* [jenkins-test-job2](#jenkins-test-job2):

**Sub-projects:**
* [jenkins-test-job1](#jenkins-test-job1):
* [jenkins-test-job2](#jenkins-test-job2):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

