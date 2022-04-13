# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [cvmfs-cleanup-containers](https://cmssdt.cern.ch/jenkins/job/cvmfs-cleanup-containers)

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

## [vtune-run-container](https://cmssdt.cern.ch/jenkins/job/vtune-run-container)

**Description:** This job stops and deletes old docker contaner of Vtune service and starts new one.

**Project is `disabled`.**

**Upstream projects:**
* [vtune-check](#vtune-check):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-ci-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-ci-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 23  * *  2
```

---

## [cvmfs-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 19  * *  2
```

---

## [ib-run-geometry](https://cmssdt.cern.ch/jenkins/job/ib-run-geometry)

**Description:** Runs geometry comparison tests for each IB

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-baseline-old](https://cmssdt.cern.ch/jenkins/job/ib-run-baseline-old)

**Description:** This job runs a few tests only for the IB, for comparison with those ran by the pull request.

<p><b> Latest failures.</b></p>
<ul>
  <li>
    Failed due to RelVal Error. The problem was that RelVal nr. 
    10224 was unable to download a randomly chosen sample file 
    (file is stored somewhere on the GRID and then must be fetched using a client). 
    The file is inaccessible, it should not appear on the list, but it does. 
    Restarting the job did the trick since another file, that actually exist was selected. 
  </li>
  <li>
    For 71X release cycles, couple of workflows are missing input data, that is why this job fails for 71X IBs.
    There is no need to re-try it for 71X if it fails due to those two workflows input data issues otherwise
    re-try is needed.
  </li>

</ul>

**Project is `disabled`.**

**Upstream projects:**

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

