# [Grid](https://cmssdt.cern.ch/jenkins/view/Grid)

**View description:** None

**View type:** List View

---

# Projects:

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
* [grid-keep-node-busy](#grid-keep-node-busy):

**Downstream projects:**
* [grid-keep-node-busy](#grid-keep-node-busy):
* [grid-webhook](#grid-webhook):

**Sub-projects:**
* [grid-keep-node-busy](#grid-keep-node-busy):
* [grid-webhook](#grid-webhook):

**Triggers from:** []


**Periodic builds:**
```bash
H/30 * * * *
```

---

## [grid-webhook](https://cmssdt.cern.ch/jenkins/job/grid-webhook)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [grid-keep-node-busy](#grid-keep-node-busy):

**Downstream projects:**
* [grid-create-node](#grid-create-node):

**Sub-projects:**
* [grid-create-node](#grid-create-node):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

