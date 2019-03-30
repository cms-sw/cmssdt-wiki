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
Not periodically build
```

---

## [grid-check-nodes](https://cmssdt.cern.ch/jenkins/job/grid-check-nodes)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [grid-keep-node-busy](#grid-keep-node-busy):
* [grid-webhook](#grid-webhook):

**Sub-projects:**
* [grid-webhook](#grid-webhook):
* [grid-keep-node-busy](#grid-keep-node-busy):

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

## [grid-keep-node-busy](https://cmssdt.cern.ch/jenkins/job/grid-keep-node-busy)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [grid-check-nodes](#grid-check-nodes):

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

**Sub-projects:**
* [jenkins-kill-job](#jenkins-kill-job):

**Triggers from:** []


**Periodic builds:**
```bash
H/2 * * * *
```

---

## [grid-shutdown-node](https://cmssdt.cern.ch/jenkins/job/grid-shutdown-node)

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

## [grid-webhook](https://cmssdt.cern.ch/jenkins/job/grid-webhook)

**Description:** None

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

