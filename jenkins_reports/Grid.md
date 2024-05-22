# [Grid](https://cmssdt.cern.ch/jenkins/view/Grid)

**View description:** None

**View type:** List View

---

# Projects:

## [grid-check-jobs](https://cmssdt.cern.ch/jenkins/job/grid-check-jobs)

**Description:** None

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

## [grid-create-gpu-node](https://cmssdt.cern.ch/jenkins/job/grid-create-gpu-node)

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

## [grid-make-node-available](https://cmssdt.cern.ch/jenkins/job/grid-make-node-available)

**Description:** Check if there are jobs queued for condor nodes, and if so kill placeholder job.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [jenkins-kill-job](#jenkins-kill-job):
* [jenkins-trigger-dynamic-job](#jenkins-trigger-dynamic-job):

**Sub-projects:**
* [jenkins-kill-job](#jenkins-kill-job):
* [jenkins-trigger-dynamic-job](#jenkins-trigger-dynamic-job):

**Triggers from:** []


**Periodic builds:**
```bash
H/2 * * * *
```

---

## [grid-shutdown-node](https://cmssdt.cern.ch/jenkins/job/grid-shutdown-node)

**Description:** shutdowns condor job.

TODO: needs to check if manuall deletion is working.

**Project is `enabled`.**

**Upstream projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [grid-webhook](#grid-webhook):

**Downstream projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [jenkins-delete-node](#jenkins-delete-node):

**Sub-projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [jenkins-delete-node](#jenkins-delete-node):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [grid-test-gpu](https://cmssdt.cern.ch/jenkins/job/grid-test-gpu)

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

## [grid-test-submit](https://cmssdt.cern.ch/jenkins/job/grid-test-submit)

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

## [lumi-create-node](https://cmssdt.cern.ch/jenkins/job/lumi-create-node)

**Description:** Connect to a lumi slot

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

## [lumi-shutdown-node](https://cmssdt.cern.ch/jenkins/job/lumi-shutdown-node)

**Description:** Cancel lumi slot

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [jenkins-delete-node](#jenkins-delete-node):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [lumi-webhook](https://cmssdt.cern.ch/jenkins/job/lumi-webhook)

**Description:** Asking for an allocation to lumi


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

## [grid-check-nodes](https://cmssdt.cern.ch/jenkins/job/grid-check-nodes)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [grid-webhook](#grid-webhook):

**Sub-projects:**
* [grid-webhook](#grid-webhook):

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
```

---

## [grid-create-node](https://cmssdt.cern.ch/jenkins/job/grid-create-node)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [grid-webhook](#grid-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [grid-webhook](https://cmssdt.cern.ch/jenkins/job/grid-webhook)

**Description:** This job is triggered by HTCondor pilot jobs. When we submit a request to get a HTCondor node then first pilot runs and triggers this job at various stages with different "STATUS"<br/>

- STATUS=online<br/>
  - When pilot script first runs on the HTCondor node then it sends an "online" event along with CONDOR_JOB_ID. In this case, this job tried to add the new HTCondor node as jenkins agent. 
In case a job with "online" status fails:<br/>
1. First check if the new HTCondor node has been successfully added as a Jenkins agent (https://cmssdt.cern.ch/jenkins/computer/). It can happen that the agent is created, 
but the connection failed. In this case, just re-starting
the agent should work.<br/>
2. If the node has not been successfully added, then please first run https://cmssdt.cern.ch/jenkins/job/grid-check-jobs/ job and see if HTCondor job with 
CONDOR_JOB_ID is still running. For example look for messages like:<br/>
OWNER        BATCH_NAME       SUBMITTED     DONE   RUN    IDLE   HOLD  TOTAL JOB_IDS<br/>
cmsbuild ID: CONDOR_JOB_ID    DATE TIME      _      1      _      _      1 CONDOR_JOB_ID"<br/>
If it is still in "RUN" state, then just re-try this job. If it is in "IDLE" state then do not do anything and if it is in "DONE" state then better 
to run https://cmssdt.cern.ch/jenkins/view/Grid/job/grid-shutdown-node/ to kill it.<br/><br/>

- STATUS=offline<br/>
  - This event is sent when HTCondor pilot has run 90% of its max allocated time. When this event is received then this jobs marks the grid${CONDOR_JOB_ID} jenkins agent as offline
so that no new job can be run on this agent. When grid${CONDOR_JOB_ID} is offline, and it is not running any job then this agent is automatically 
deleted by https://cmssdt.cern.ch/jenkins/view/Grid/job/grid-check-nodes/. Depending on the agent "LABELS" (e.g. auto-recreate) , this job can request a new HTCondor node to replace it.<br/><br/>

- STATUS=shutdown<br/>
  - This event is sent when a pilot has reached its max life and going to shutdown. In this case this job tried to delete the agent from the jenkins.





**Project is `enabled`.**

**Upstream projects:**
* [grid-check-nodes](#grid-check-nodes):

**Downstream projects:**
* [grid-create-node](#grid-create-node):
* [grid-shutdown-node](#grid-shutdown-node):

**Sub-projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [grid-create-node](#grid-create-node):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

