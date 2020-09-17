# [Uncategorized](https://cmssdt.cern.ch/jenkins/view/Uncategorized)

**View description:** This view contains all projects that were not categorized.

**View type:** Custom

---

# Projects:

## [test-build-periodic](https://cmssdt.cern.ch/jenkins/job/test-build-periodic)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/15 * * * *
```

---

## [ib-run-igprof](https://cmssdt.cern.ch/jenkins/job/ib-run-igprof)

**Description:** Runs <a href="https://igprof.org/">IgProf</a> on IB.
Results are available on <a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a>. 

<br>
run-ib-igprof is executed with `pp` flag for `performance profiling`.

<br><br>

<b>Q/a:</b>

<ul>
  <li>
    Q: Error: near line 63: unrecognized token: "" 
  </li>  
  <li>
    A: Igprof has a bug that from time to time it returns unrecognizable character which fails the job. There is no easy fix, so we glance over it.
  	However, job will execute all steps and then fail.
  </li>
</ul>


<ul>
  <li>
    Q: `IOError: [Errno 2] No such file or directory: 'runall-report-step123-.log'`
  </li>  
  <li>
    A: No idea... Yet.
  </li>
</ul>




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

## [ib-run-check-headers](https://cmssdt.cern.ch/jenkins/job/ib-run-check-headers)

**Description:** Check for missing headers and parse the log for all errors (clang modules)

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

## [run-cvmfs-commands](https://cmssdt.cern.ch/jenkins/job/run-cvmfs-commands)

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

## [update-ibeos-cache](https://cmssdt.cern.ch/jenkins/job/update-ibeos-cache)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [dataset-to-ibeos](#dataset-to-ibeos):
* [ib-cache-to-eos](#ib-cache-to-eos):
* [lfn-to-ibeos](#lfn-to-ibeos):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H */6 * * *
```

---

## [lxr-remove-index](https://cmssdt.cern.ch/jenkins/job/lxr-remove-index)

**Description:** Deletes index of of IB's older then treshold on LXR ( default 14 days).
If specified, it also deletes Release index.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 5  * * *

```

---

## [compare-material-budget](https://cmssdt.cern.ch/jenkins/job/compare-material-budget)

**Description:** Comopare results of material budget of two releases using Validation/Geometry/test/TrackerMaterialBudgetComparison.C macro


**Project is `enabled`.**

**Upstream projects:**
* [ib-run-material-budget](#ib-run-material-budget):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-new-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-new-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 23  * *  4
```

---

## [ib-run-python3](https://cmssdt.cern.ch/jenkins/job/ib-run-python3)

**Description:** Runs iwyu logs parsing for each IB

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

## [github-labels](https://cmssdt.cern.ch/jenkins/job/github-labels)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 1 * * *
```

---

## [test-docker](https://cmssdt.cern.ch/jenkins/job/test-docker)

**Description:** Connects to the slave and checks if docker service is runable.

**Project is `enabled`.**

**Upstream projects:**
* [slaves-checks](#slaves-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmssw-to-stitched](https://cmssdt.cern.ch/jenkins/job/cmssw-to-stitched)

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

## [ib-run-HLT](https://cmssdt.cern.ch/jenkins/job/ib-run-HLT)

**Description:** Appends job's time out information into jenkins.log file.

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

## [kill-hanging-jobs](https://cmssdt.cern.ch/jenkins/job/kill-hanging-jobs)

**Description:** This project checks all selected host for process running longer then set treshold (default 2 days) and kill them. 
<br><br>
<b>Q/A:</b>

<ul>
  <li>
    <b>Q:</b> The job is taken more time then is supposed to (status bar becomes red).
  </li>
  <li>
    <b>A:</b> Most likely one of the machine is in a weird state (last time it was issues with CMSFS) and job hangs when connecting to it.
    IF it is a cmsbuildXX machine, just delete it and restart the job.
  </li>
</ul>


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H/8 * * *
```

---

## [update-categories-page](https://cmssdt.cern.ch/jenkins/job/update-categories-page)

**Description:** Generates categories.json file and uploads it to this <a href="https://github.com/cms-sw/cms-sw.github.io">github repo</a>. 
<br>
The date is later used to generate <a href="http://cms-sw.github.io/categories.html">this page</a>.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [slaves-checks](https://cmssdt.cern.ch/jenkins/job/slaves-checks)

**Description:** A wrapper project that starts a 
<a href="https://cmssdt.cern.ch/jenkins/job/workspace-cleanup-slave/">workspace-cleanup-slave</a>
and <a href="https://cmssdt.cern.ch/jenkins/job/test-docker">test-docker</a> jobs on selected slaves. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [test-docker](#test-docker):
* [workspace-cleanup-slave](#workspace-cleanup-slave):

**Sub-projects:**
* [workspace-cleanup-slave](#workspace-cleanup-slave):
* [test-docker ](#test-docker ):

**Triggers from:** []


**Periodic builds:**
```bash
H 7,19 * * *
```

---

## [cmspkg-test](https://cmssdt.cern.ch/jenkins/job/cmspkg-test)

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

## [create-json](https://cmssdt.cern.ch/jenkins/job/create-json)

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

## [update-config-guess](https://cmssdt.cern.ch/jenkins/job/update-config-guess)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 10,22 * * *
```

---

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

## [das-query](https://cmssdt.cern.ch/jenkins/job/das-query)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 9,21 * * *
```

---

## [dataset-to-ibeos](https://cmssdt.cern.ch/jenkins/job/dataset-to-ibeos)

**Description:** Copies root files for a given dataset localy on eos to be used from local cache (eos) if they diasappear from the site where they resided. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmsrep-webhook](https://cmssdt.cern.ch/jenkins/job/cmsrep-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-COMP-xrootd](#cvmfs-cms-install-COMP-xrootd):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cvmfs-cms-install-crab3](#cvmfs-cms-install-crab3):
* [cvmfs-cms-install-phedex](#cvmfs-cms-install-phedex):
* [cvmfs-cms-install-spacemon-client](#cvmfs-cms-install-spacemon-client):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Sub-projects:**
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-crab3](#cvmfs-cms-install-crab3):
* [cvmfs-cms-install-phedex](#cvmfs-cms-install-phedex):
* [cvmfs-cms-install-spacemon-client](#cvmfs-cms-install-spacemon-client):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-COMP-xrootd](#cvmfs-cms-install-COMP-xrootd):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [monitor-openstack-vms](https://cmssdt.cern.ch/jenkins/job/monitor-openstack-vms)

**Description:** This job run periodically to monitor the running state of vms in openstack , if stopped , creates an email alert.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
@hourly
```

---

## [GitHub-refactor-cmssw-module](https://cmssdt.cern.ch/jenkins/job/GitHub-refactor-cmssw-module)

**Description:** Refactors one module of CMSSW and makes an PR.

**Project is `enabled`.**

**Upstream projects:**
* [GitHub-refactor-cmssw](#GitHub-refactor-cmssw):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [github-hooks](https://cmssdt.cern.ch/jenkins/job/github-hooks)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-baseline](#ib-run-baseline):

**Downstream projects:**
* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Sub-projects:**
* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-static-checks](https://cmssdt.cern.ch/jenkins/job/ib-run-static-checks)

**Description:** Runs a few tests only for the IB, for comparison with those ran by the pull request.

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

## [lxr-run-container](https://cmssdt.cern.ch/jenkins/job/lxr-run-container)

**Description:** This job stops and deletes old docker contaner of LXR service and starts new one.

**Project is `enabled`.**

**Upstream projects:**
* [lxr-check](#lxr-check):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [backport-pull-request](https://cmssdt.cern.ch/jenkins/job/backport-pull-request)

**Description:** Manually executed job for backporting pull requests given the repo name, the branch for which the PR should be created and the PR to be backported

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

## [cmspkg-clone](https://cmssdt.cern.ch/jenkins/job/cmspkg-clone)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
#Run on Monday at 2h to do the cleanup
H 2 * * 1
```

---

## [deploy-cmsdoxygen](https://cmssdt.cern.ch/jenkins/job/deploy-cmsdoxygen)

**Description:** This job deploys <a href="http://doxygen.org">doxygen</a> scripts to web server. 
It is later used to serve <a href="http://cmsdoxygen.web.cern.ch/cmsdoxygen/">CMSSW documentation</a><br>
<b>Could be automated by github hooks.<b>

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
H 19  * *  4
```

---

## [material-budget-ref](https://cmssdt.cern.ch/jenkins/job/material-budget-ref)

**Description:** Runs Validation/Geometry/test/runP_Tracker_cfg.py and MaterialBudget.C for an IB

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

## [ib-run-iwyu](https://cmssdt.cern.ch/jenkins/job/ib-run-iwyu)

**Description:** Runs iwyu logs parsing for each IB

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

## [es-close-indexes](https://cmssdt.cern.ch/jenkins/job/es-close-indexes)

**Description:** This job keeps last 6 weeks (1.5 months) of data in Elasticsearch open, and it closes older indexes (archive it).
We do not care about older data. By doing it we make Elasticsearch faster. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0  * *  0
```

---

## [cvmfs-publish-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-baseline)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-material-budget](https://cmssdt.cern.ch/jenkins/job/ib-run-material-budget)

**Description:** Runs Validation/Geometry/test/runP_Tracker_cfg.py and MaterialBudget.C for an IB

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [compare-material-budget](#compare-material-budget):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [ib-run-baseline](https://cmssdt.cern.ch/jenkins/job/ib-run-baseline)

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
</ul>

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

**Sub-projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-invalid-includes](https://cmssdt.cern.ch/jenkins/job/ib-run-invalid-includes)

**Description:** Runs iwyu logs parsing for each IB

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

## [cvmfs-unpack-container](https://cmssdt.cern.ch/jenkins/job/cvmfs-unpack-container)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):

**Downstream projects:**
* [cvmfs_publish_remote_dir](#cvmfs_publish_remote_dir):

**Sub-projects:**
* [cvmfs_publish_remote_dir](#cvmfs_publish_remote_dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [slc6](https://cmssdt.cern.ch/jenkins/job/slc6)

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

## [lfn-to-ibeos](https://cmssdt.cern.ch/jenkins/job/lfn-to-ibeos)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [lfn-to-ibeos](#lfn-to-ibeos):

**Downstream projects:**
* [lfn-to-ibeos](#lfn-to-ibeos):
* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**
* [update-ibeos-cache](#update-ibeos-cache):
* [lfn-to-ibeos](#lfn-to-ibeos):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [process-deprecate-releases](https://cmssdt.cern.ch/jenkins/job/process-deprecate-releases)

**Description:** This job marks selected realeases depricated in realease map. Grid jobs will not use depricated release and posibly uninstall it.
This is useful if a specific release contains and needs to be removed.



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

## [gh-teams](https://cmssdt.cern.ch/jenkins/job/gh-teams)

**Description:** printing some python file	

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 22 * * *
```

---

## [schedule-docker-build](https://cmssdt.cern.ch/jenkins/job/schedule-docker-build)

**Description:** A glue job to connect github-webhook with build-container. 
Should check only folder containing *EXECUTE_BUILD.sh  

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

## [aarch64](https://cmssdt.cern.ch/jenkins/job/aarch64)

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

## [GitHub-refactor-cmssw](https://cmssdt.cern.ch/jenkins/job/GitHub-refactor-cmssw)

**Description:** Refactors the CMSSW repo.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [GitHub-refactor-cmssw-module](#GitHub-refactor-cmssw-module):

**Sub-projects:**
* [GitHub-refactor-cmssw-module](#GitHub-refactor-cmssw-module):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [es-open-indexes](https://cmssdt.cern.ch/jenkins/job/es-open-indexes)

**Description:** This job keeps last 4 weeks of data in Elasticsearch open, and it closes older indexes (archive it).
We do not care about older data. By doing it we make Elasticsearch faster. 

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

## [cleanup-tags](https://cmssdt.cern.ch/jenkins/job/cleanup-tags)

**Description:** Cleanup IB tags from the official CMSSW repository.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [ib-run-lizard](https://cmssdt.cern.ch/jenkins/job/ib-run-lizard)

**Description:** Runs <a href="https://github.com/terryyin/lizard">Lizard</a>, a Cyclomatic Complexity Analyzer, on IB.
Results are available on <a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a>. 


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

## [cvmfs_publish_remote_dir](https://cmssdt.cern.ch/jenkins/job/cvmfs_publish_remote_dir)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-unpack-container](#cvmfs-unpack-container):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [fix-backport-prs](https://cmssdt.cern.ch/jenkins/job/fix-backport-prs)

**Description:** Periodicaly runs https://github.com/cms-sw/cms-bot/blob/master/fix-backport-labels.py to check if the PR on master, which backport has been requested, is merged.
If the original PR has been merged, it changes all opened backport PRs of it from backport(blue) to backport-ok(green)

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

## [ib-run-profiling](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling)

**Description:** Runs FastTimerService and Igprof on the RECO and PAT steps for high pileup workflow.





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

## [cleanup-cmssdt](https://cmssdt.cern.ch/jenkins/job/cleanup-cmssdt)

**Description:** Clean up disk space on cmssdt

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [slc7](https://cmssdt.cern.ch/jenkins/job/slc7)

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

## [test](https://cmssdt.cern.ch/jenkins/job/test)

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

## [ib-run-flawfinder](https://cmssdt.cern.ch/jenkins/job/ib-run-flawfinder)

**Description:** Runs <a href="https://www.dwheeler.com/flawfinder/"> Flawfinder</a> test on IB.

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

## [ib-run-gpu](https://cmssdt.cern.ch/jenkins/job/ib-run-gpu)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

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

## [ib-run-valgrind](https://cmssdt.cern.ch/jenkins/job/ib-run-valgrind)

**Description:** This job runs valgrind tool for selected IBs when build IB job is complete.   

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

## [reindex-elasticsearch-indexes](https://cmssdt.cern.ch/jenkins/job/reindex-elasticsearch-indexes)

**Description:** Job to reindex existing indexes whenever the template schema is changed or for whatever other reason


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

## [workspace-cleanup-slave](https://cmssdt.cern.ch/jenkins/job/workspace-cleanup-slave)

**Description:** Connect to selected slave and cleans (deletes) workspace.

**Project is `enabled`.**

**Upstream projects:**
* [slaves-checks](#slaves-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [lxr-check](https://cmssdt.cern.ch/jenkins/job/lxr-check)

**Description:** This job checks if https://cmssdt.cern.ch/lxr/ is acessable and if not, starts <a href="https://cmssdt.cern.ch/jenkins/view/All/job/lxr-run-container/">lxr-run-container<a/> job to restart the service.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [lxr-run-container](#lxr-run-container):

**Sub-projects:**
* [lxr-run-container](#lxr-run-container):

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
```

---

## [git-repo-size](https://cmssdt.cern.ch/jenkins/job/git-repo-size)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
5 11,23 * * *
```

---

## [docker-monitor-repos](https://cmssdt.cern.ch/jenkins/job/docker-monitor-repos)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H/4 * * *
```

---

## [dxr-cmssw-index](https://cmssdt.cern.ch/jenkins/job/dxr-cmssw-index)

**Description:** Index <a href="https://cmssdt.cern.ch/dxr">CMSSW</a> documentation using DXR. 

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

## [ib-cache-to-eos](https://cmssdt.cern.ch/jenkins/job/ib-cache-to-eos)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**
* [update-ibeos-cache](#update-ibeos-cache):

**Triggers from:** []


**Periodic builds:**
```bash
H 10,22 * * *
```

---

