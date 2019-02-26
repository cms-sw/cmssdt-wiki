# [CMSSDT](https://cmssdt.cern.ch/jenkins/view/CMSSDT)

**View description:** None

**View type:** List View

---

# Projects:

## [abort-release](https://cmssdt.cern.ch/jenkins/job/abort-release)

**Description:** Aborts and kills a release building process.

**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**
* [kill-build-release](#kill-build-release):

**Sub-projects:**
* [kill-build-release](#kill-build-release):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [auto-forward-ports](https://cmssdt.cern.ch/jenkins/job/auto-forward-ports)

**Description:** This is triggered by github webhook for each cmssw/cmsdist branch merge event.
this forward port changes from source branch to target branch. Mapping between soruce and destination branches are available in cms-bot.

<ul>
  <li>
    <b>Q:</b> Job failed do to merge conflict.
  </li>
  <li>
    <b>A:</b> It comonly fails when merging diferences on `root.spec` files. 
    If we known that we want to keep our changes on merge conflict, we can a) manually run
    `auto-update-git-branches` with `-X ours` option and push changes, b) re-run job with 
    KEEP_OURS value set to True.<br>
    Due only when we are sure about changes. Otherwise, you have to resolve merge 
    conflict manually.
    
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [baseline-ib-results](https://cmssdt.cern.ch/jenkins/job/baseline-ib-results)

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
* [schedule-additional-tests](#schedule-additional-tests):

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

## [build-any-ib](https://cmssdt.cern.ch/jenkins/job/build-any-ib)

**Description:** This jobs starts an Integration Build(IB). Base on state of <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a>/<a href="https://github.com/cms-sw/cmssw">CMSSW</a> git repositories, it builds either a full release or patch release.
<br>Build Full IB if:

<ul>
  <li> There are changes in <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a></li>
  <li> There is no full IB available based on current <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a></li>
  <li> Previous full IB had build errors</li>
</ul>

Otherwise build a patch release.

<br><br>
<b>Q/A</b>

<ul>
  <li>
    <b>Q:</b> The job is scheduled with a clock simbol. Jenkins also complains that there are not agents with labels THIS and THIS.
  </li>
  <li>
    <b>A:</b> Jenkins should automaticly launch agents with specific labels for the job. However, for some reason it does not work for this job. For now, launch agent manually.
  </li>
</ul>

<ul>
  <li>
    <b>Q:</b> How to manually build an IB?
  </li>
  <li>
    <b>A:</b> Go to upstream job (ib-tag-and-schdule) and start a job.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [build-fwlite-ib](#build-fwlite-ib):
* [ib-build-logs](#ib-build-logs):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Sub-projects:**
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-build-logs](#ib-build-logs):
* [build-fwlite-ib](#build-fwlite-ib):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-container](https://cmssdt.cern.ch/jenkins/job/build-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [schedule-docker-build](#schedule-docker-build):

**Downstream projects:**
* [cvmfs-unpack-container](#cvmfs-unpack-container):
* [test-build-container](#test-build-container):

**Sub-projects:**
* [test-build-container](#test-build-container):
* [cvmfs-unpack-container](#cvmfs-unpack-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-fwlite](https://cmssdt.cern.ch/jenkins/job/build-fwlite)

**Description:** TO build a CMSSW_X_Y_Z_FWLITE release based on an existing CMSSW_X_Y_Z release. CMSSW_X_Y_Z should already be build/uploaded before building its FWLITE version.

**Project is `enabled`.**

**Upstream projects:**
* [update-release-map](#update-release-map):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-fwlite-ib](https://cmssdt.cern.ch/jenkins/job/build-fwlite-ib)

**Description:** This job is responsible for building FWLITE release for each Integration build(IB). 
Results of this build can be seen via <a href="https://cmssdt.cern.ch/SDT/">CMSSDT</a> 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a> 
<a href="https://cmssdt.cern.ch/SDT/html/showIB.html">(old page)</a>.

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):

**Downstream projects:**
* [ib-build-logs](#ib-build-logs):

**Sub-projects:**
* [ib-build-logs](#ib-build-logs):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-release](https://cmssdt.cern.ch/jenkins/job/build-release)

**Description:** This job actually builds a release.
It is triggered by cms-bot after the <a href="https://github.com/cms-sw/cmssw/issues?q=label%3Arelease-notes-requested">Release build Issue</a> is approved by release manager.

**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cleanup-auto-build](https://cmssdt.cern.ch/jenkins/job/cleanup-auto-build)

**Description:** This job deletes the relsease build areas after three days.

**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cleanup-cms-sw-io-history](https://cmssdt.cern.ch/jenkins/job/cleanup-cms-sw-io-history)

**Description:** This job cleanup the cms-sw/cms-sw.github.io repository history. Specially the data and _data directories history.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 1 * * 0
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

## [cms-dockerhub](https://cmssdt.cern.ch/jenkins/job/cms-dockerhub)

**Description:** This job creates docker image with CMSSW and push it to the dockerhub. It also uploads dockerfile to github.

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

## [cms-prs-cache](https://cmssdt.cern.ch/jenkins/job/cms-prs-cache)

**Description:** This job collects metadata for pull requests since reading github directly when necessary might become time consuming or rejected by github
on reached limit hits/hour grounds. 

**Project is `enabled`.**

**Upstream projects:**
* [cms-prs-cache](#cms-prs-cache):
* [github-webhook](#github-webhook):

**Downstream projects:**
* [cms-prs-cache](#cms-prs-cache):

**Sub-projects:**
* [cms-prs-cache](#cms-prs-cache):

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

**Sub-projects:**
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-crab3](#cvmfs-cms-install-crab3):
* [cvmfs-cms-install-phedex](#cvmfs-cms-install-phedex):
* [cvmfs-cms-install-spacemon-client](#cvmfs-cms-install-spacemon-client):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-COMP-xrootd](#cvmfs-cms-install-COMP-xrootd):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmssw-doxygen](https://cmssdt.cern.ch/jenkins/job/cmssw-doxygen)

**Description:** Generate doxygen documentation for CMSSW project

**Project is `enabled`.**

**Upstream projects:**
* [update-release-map](#update-release-map):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [comp-bot](https://cmssdt.cern.ch/jenkins/job/comp-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
This is to process bot commands for cmsdist comp branches

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Project is `enabled`.**

**Upstream projects:**
* [baseline-ib-results](#baseline-ib-results):

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
H 23  * *  4
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

## [cvmfs-unpack-container](https://cmssdt.cern.ch/jenkins/job/cvmfs-unpack-container)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Project is `enabled`.**

**Upstream projects:**
* [build-container](#build-container):

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

## [deploy-cms-repo](https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo)

**Description:** Updates cms-bot clone on Jenkins master

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [es-close-indexes](https://cmssdt.cern.ch/jenkins/job/es-close-indexes)

**Description:** This job keeps last 4 weeks of data in Elasticsearch open, and it closes older indexes (archive it).
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

## [forward-pull-requests](https://cmssdt.cern.ch/jenkins/job/forward-pull-requests)

**Description:** Given a branch, gets all of its pull requests and recreates them in a different branch.


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

## [git-mirror-repository](https://cmssdt.cern.ch/jenkins/job/git-mirror-repository)

**Description:** Mirror one git repository.
<br>
<b>Q/A:</b>

<ul>
  <li>Q: Failed due to `remote: GitLab: Failed to authorize your Git request: internal API unreachable`</li>
  <li>A: Problem with GitLab. Just file a ticket.</li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [git-reference-cms-ib](https://cmssdt.cern.ch/jenkins/job/git-reference-cms-ib)

**Description:** Create GIT Reference for cms-sw/cmssw repository in /cvmfs/cms-ib.cern.ch/git/cms-sw.
This is automatically triggered by "git push" to cmssw repo.

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

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

## [github-push-hook](https://cmssdt.cern.ch/jenkins/job/github-push-hook)

**Description:** Updates cms-bot clone on cmssdt.
This job is also triggered via github web hook. Please do not add/remove any parameters of this job otherwise github web hooks will not be able to triiger the job

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**
* [auto-forward-ports](#auto-forward-ports):
* [deploy-cms-repo](#deploy-cms-repo):
* [git-mirror-repository](#git-mirror-repository):
* [git-reference-cms-ib](#git-reference-cms-ib):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):

**Sub-projects:**
* [deploy-cms-repo](#deploy-cms-repo):
* [auto-forward-ports](#auto-forward-ports):
* [git-reference-cms-ib](#git-reference-cms-ib):
* [git-mirror-repository](#git-mirror-repository):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):

**Triggers from:** []


**Periodic builds:**
```bash
H */6 * * *
```

---

## [github-webhook](https://cmssdt.cern.ch/jenkins/job/github-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cms-bot](#cms-bot):
* [cms-prs-cache](#cms-prs-cache):
* [comp-bot](#comp-bot):
* [github-push-hook](#github-push-hook):
* [query-build-release-issues](#query-build-release-issues):
* [schedule-docker-build](#schedule-docker-build):

**Sub-projects:**
* [comp-bot](#comp-bot):
* [github-push-hook](#github-push-hook):
* [cms-prs-cache](#cms-prs-cache):
* [query-build-release-issues](#query-build-release-issues):
* [cms-bot](#cms-bot):
* [schedule-docker-build](#schedule-docker-build):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [HLT-Validation](https://cmssdt.cern.ch/jenkins/job/HLT-Validation)

**Description:** Appends job's time out information into jenkins.log file.

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** Build a pull request

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

## [ib-build-logs](https://cmssdt.cern.ch/jenkins/job/ib-build-logs)

**Description:** It is build periodically (H/30 * * * *). Runs on cmssdt. Projects to build: update-github-pages

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [build-fwlite-ib](#build-fwlite-ib):

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/30 * * * *
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

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [ib-validation](#ib-validation):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-addons](https://cmssdt.cern.ch/jenkins/job/ib-run-addons)

**Description:** Runs addons test on IB. Results are shown as "Other test" in the 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page</a> for the IB.  

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-cfipython](https://cmssdt.cern.ch/jenkins/job/ib-run-cfipython)

**Description:** This job gets the cfipython files for a cmssw release and push the changes to cms-sw/cmssw-cfipython repo.

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):
* [update-release-map](#update-release-map):

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
* [schedule-additional-tests](#schedule-additional-tests):

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
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-igprof-mp](https://cmssdt.cern.ch/jenkins/job/ib-run-igprof-mp)

**Description:** Runs <a href="https://igprof.org/">IgProf</a> on IB.
Results are available on <a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a>. 

<br>
run-ib-igprof is executed with `mp` flag for `performance profiling`.

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
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-igprof-pp](https://cmssdt.cern.ch/jenkins/job/ib-run-igprof-pp)

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
* [schedule-additional-tests](#schedule-additional-tests):

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
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-lizard](https://cmssdt.cern.ch/jenkins/job/ib-run-lizard)

**Description:** Runs <a href="https://github.com/terryyin/lizard">Lizard</a>, a Cyclomatic Complexity Analyzer, on IB.
Results are available on <a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a>. 


**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

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
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**
* [compare-material-budget](#compare-material-budget):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-python3](https://cmssdt.cern.ch/jenkins/job/ib-run-python3)

**Description:** Runs iwyu logs parsing for each IB

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-qa)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-relvals](https://cmssdt.cern.ch/jenkins/job/ib-run-relvals)

**Description:** The job runs release validations, as validations are separated on pieces (1of6 2of6 etc)

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):

**Downstream projects:**
* [process-relval-logs](#process-relval-logs):
* [update-das-queries](#update-das-queries):

**Sub-projects:**
* [update-das-queries](#update-das-queries):
* [process-relval-logs](#process-relval-logs):

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
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except no IB at 23h Sat & 11h Sun but a special IB at Sun 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
This was created to avoid the issue with <a href="https://wiki.jenkins.io/display/JENKINS/Dynamic+Parameter+Plug-in">Jenkins Dynamic Parameters</a>.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Sub-projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Triggers from:** []


**Periodic builds:**
```bash
#Special IB at 0h on Sunday
5  0   * *  0
#We skip Sunday 11h IB to leave resources for special Sunday's 0h IB
5 11  * * 1,2,3,4,5,6
#We do not run SAT 23H IB instead we start a special SUN 00h00 IB.
5 23  * *  0,1,2,3,4,5
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

## [ib-static-checks](https://cmssdt.cern.ch/jenkins/job/ib-static-checks)

**Description:** Runs a few tests only for the IB, for comparison with those ran by the pull request.

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-tag-and-schdule](https://cmssdt.cern.ch/jenkins/job/ib-tag-and-schdule)

**Description:** This job tags and schedules all the IBs.<br/>
It reads the <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a> to find all available CMSSW release cycles and tag them in github.
Once tags is done then it triggers 'build-any-ib' sub-job to actually build IBs for all possible architectures (mentioned in <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a>).
For Developement IB, it also triggers the generation of <a href="https://cmssdt.cern.ch/lxr">LXR indexes</a>

For Sunday's 00h IBs, it also resets the CMSREP weekly repositories by building a dummy package and uploading it to cms.weekN. It also 
then triggers 'ib-install-cvmfs' sub-job to get the new cms.weekN deployed on the /cvmfs/cms-ib.cern.ch

**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule](#ib-schedule):

**Downstream projects:**
* [build-any-ib](#build-any-ib):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [lxr-checkout-version](#lxr-checkout-version):

**Sub-projects:**
* [build-any-ib](#build-any-ib):
* [lxr-checkout-version](#lxr-checkout-version):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-validation](https://cmssdt.cern.ch/jenkins/job/ib-validation)

**Description:** Validates the integration builds.

**Project is `enabled`.**

**Upstream projects:**
* [ib-cvmfs-publish](#ib-cvmfs-publish):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Downstream projects:**
* [ib-run-addons](#ib-run-addons):
* [ib-run-qa](#ib-run-qa):
* [ib-run-relvals](#ib-run-relvals):
* [schedule-additional-tests](#schedule-additional-tests):

**Sub-projects:**
* [ib-run-addons](#ib-run-addons):
* [ib-run-qa ](#ib-run-qa ):
* [ib-run-relvals ](#ib-run-relvals ):
* [schedule-additional-tests](#schedule-additional-tests):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [import-stitched-tag](https://cmssdt.cern.ch/jenkins/job/import-stitched-tag)

**Description:** This tags a CMSSW release tag and upload the packages (https://github.com/cms-sw/Stitched/blob/master/packages.txt) needed by Stitched to Stitched repo.
CMSSW_* tag is rename to STITCHED_*

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

## [jenkins-download-rpm](https://cmssdt.cern.ch/jenkins/job/jenkins-download-rpm)

**Description:** This downloads a jenkins RPM from https://pkg.jenkins.io/redhat-stable/ and 
make it available via http://cmsrep.cern.ch/cmssw/download/jenkins
for faster access to CMs internal jenkns servers

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

## [kill-build-release](https://cmssdt.cern.ch/jenkins/job/kill-build-release)

**Description:** Aborts and kills a release building process. 

**Project is `enabled`.**

**Upstream projects:**
* [abort-release](#abort-release):

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

## [lxr-checkout-version](https://cmssdt.cern.ch/jenkins/job/lxr-checkout-version)

**Description:** This job sets modification timestamp of CMSSW source code according to commit history before 
indexing it using LXR.<br>


LXR index files based on modification timestamp. `<code>git clone</code>` ,however, sets files timestamps 
to command's execution time. Without it, LXR would index every file, increasing jobs execution duration 
and database size.

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [lxr-generate-index](#lxr-generate-index):

**Sub-projects:**
* [lxr-generate-index](#lxr-generate-index):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [lxr-generate-index](https://cmssdt.cern.ch/jenkins/job/lxr-generate-index)

**Description:** Generates CMSSW index using LXR tool. 

**Project is `enabled`.**

**Upstream projects:**
* [lxr-checkout-version](#lxr-checkout-version):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [mirror-cmsrep](https://cmssdt.cern.ch/jenkins/job/mirror-cmsrep)

**Description:** Create a live mirror of cmsrep.cern.ch

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

## [process-relval-logs](https://cmssdt.cern.ch/jenkins/job/process-relval-logs)

**Description:** This job process partial logs of Relvals and place files accordingly. 

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-relvals](#ib-run-relvals):

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
```

---

## [pySCRAM-develop](https://cmssdt.cern.ch/jenkins/job/pySCRAM-develop)

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

## [query-build-release-issues](https://cmssdt.cern.ch/jenkins/job/query-build-release-issues)

**Description:** Processes a github issue to check if it is requesting the build of a new release.
If the issue is not requesting any release, it ignores it. 

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**
* [abort-release](#abort-release):
* [build-release](#build-release):
* [cleanup-auto-build](#cleanup-auto-build):
* [release-produce-changelog](#release-produce-changelog):
* [upload-release-setup](#upload-release-setup):

**Sub-projects:**
* [build-release](#build-release):
* [upload-release-setup](#upload-release-setup):
* [cleanup-auto-build](#cleanup-auto-build):
* [release-produce-changelog](#release-produce-changelog):
* [abort-release](#abort-release):

**Triggers from:** []


**Periodic builds:**
```bash
H/15 * * * *
```

---

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Project is `enabled`.**

**Upstream projects:**
* [update-github-pages](#update-github-pages):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** [u'update-github-pages']


**Periodic builds:**
```bash
Not periodically build
```

---

## [release-produce-changelog](https://cmssdt.cern.ch/jenkins/job/release-produce-changelog)

**Description:** Posts a message in the github issue that triggered the build. Structure of the message depends on the option used.


**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**
* [update-release-notes-collection](#update-release-notes-collection):

**Sub-projects:**
* [update-release-notes-collection](#update-release-notes-collection):

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

## [run-repo-size-check](https://cmssdt.cern.ch/jenkins/job/run-repo-size-check)

**Description:** This job was supposed to tell how much repository size increases
if a pull request is merged. However, it is not properly working 
since:

<ul>
  <li> Not all information is available about pull request </li>
  <li> After merging, repo size is smaller do internal Github 
    optimization</li>
</ul> 

A solution would be to make a test branch, merge pul request there, 
push to Github and pull again to read the size. 


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

## [schedule-additional-tests](https://cmssdt.cern.ch/jenkins/job/schedule-additional-tests)

**Description:** Wrapper project to schedule aditonal test such as Flawfinder, Lizard, IgProf, etc.

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):

**Downstream projects:**
* [HLT-Validation](#HLT-Validation):
* [baseline-ib-results](#baseline-ib-results):
* [ib-run-cfipython](#ib-run-cfipython):
* [ib-run-check-headers](#ib-run-check-headers):
* [ib-run-flawfinder](#ib-run-flawfinder):
* [ib-run-geometry](#ib-run-geometry):
* [ib-run-igprof-mp](#ib-run-igprof-mp):
* [ib-run-igprof-pp](#ib-run-igprof-pp):
* [ib-run-iwyu](#ib-run-iwyu):
* [ib-run-lizard](#ib-run-lizard):
* [ib-run-material-budget](#ib-run-material-budget):
* [ib-run-python3](#ib-run-python3):
* [ib-run-qa](#ib-run-qa):
* [ib-run-valgrind](#ib-run-valgrind):
* [ib-static-checks](#ib-static-checks):

**Sub-projects:**
* [baseline-ib-results](#baseline-ib-results):
* [HLT-Validation](#HLT-Validation):
* [ib-static-checks](#ib-static-checks):
* [ib-run-valgrind ](#ib-run-valgrind ):
* [ib-run-igprof-mp,ib-run-igprof-pp](#ib-run-igprof-mp,ib-run-igprof-pp):
* [ib-run-geometry](#ib-run-geometry):
* [ib-run-iwyu](#ib-run-iwyu):
* [ib-run-material-budget](#ib-run-material-budget):
* [ib-run-lizard](#ib-run-lizard):
* [ib-run-flawfinder](#ib-run-flawfinder):
* [ib-run-check-headers](#ib-run-check-headers):
* [ib-run-cfipython](#ib-run-cfipython):
* [ib-run-qa](#ib-run-qa):
* [ib-run-python3](#ib-run-python3):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [schedule-docker-build](https://cmssdt.cern.ch/jenkins/job/schedule-docker-build)

**Description:** A glue job to connect github-webhook with build-container. 
Should check only folder containing *EXECUTE_BUILD.sh  

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

**Downstream projects:**
* [build-container](#build-container):

**Sub-projects:**
* [build-container](#build-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

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

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** Generates statistics for each IB ( merged pull request since last IB, test result summary, .etc)
as well as structure of release que and stores it in .json files. It then push it to <b>cms-sw.github.io</b> repo as well
as deploys on the web server. It is used to generate <a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a>.


<br><br>
<b>Q/A</b>

<ul>
  <li>
    <b>Q:</b> The job failed.
  </li>
  <li>
    <b>A:</b> Most likely Github rejected push request because other job pushed after `git pull --rebase`
	. Do not worry - job builds quite ofthen and next build shouls be succesful.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [update-github-pages](#update-github-pages):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** [u'update-github-pages']


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-build-container](https://cmssdt.cern.ch/jenkins/job/test-build-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [build-container](#build-container):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

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

## [test-cms-data](https://cmssdt.cern.ch/jenkins/job/test-cms-data)

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

## [test-dqm-upload](https://cmssdt.cern.ch/jenkins/job/test-dqm-upload)

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

## [test-kerberos-within-docker](https://cmssdt.cern.ch/jenkins/job/test-kerberos-within-docker)

**Description:** This job tests the the kerberos auth existence and its behaviour when ran from docker image. It first sets the env
var KRB5CC inside the image to point to the ticket within /tmp. Then adds few commands in a script
and runs the script with docker to check the behaviour

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

## [test-lxplus-future](https://cmssdt.cern.ch/jenkins/job/test-lxplus-future)

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

## [test-scram](https://cmssdt.cern.ch/jenkins/job/test-scram)

**Description:** ---need-description--- <br>
---need-check---

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

## [Test_get_source_flag](https://cmssdt.cern.ch/jenkins/job/Test_get_source_flag)

**Description:** <b>Test_get_source_flag</b> 

Test job

**Project is `enabled`.**

**Upstream projects:**

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

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-relvals](#ib-run-relvals):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [update-github-pages](https://cmssdt.cern.ch/jenkins/job/update-github-pages)

**Description:** This job update contents of the "data" directory in cms-sw.github.io

**Project is `enabled`.**

**Upstream projects:**
* [cleanup-cms-sw-io-history](#cleanup-cms-sw-io-history):
* [ib-build-logs](#ib-build-logs):
* [process-relval-logs](#process-relval-logs):

**Downstream projects:**
* [refresh-cmssdt](#refresh-cmssdt):
* [summary-of-merged-prs](#summary-of-merged-prs):

**Sub-projects:**

**Triggers from:** [u'cleanup-cms-sw-io-history', u'ib-build-logs']


**Periodic builds:**
```bash
Not periodically build
```

---

## [update-github-webhook-token](https://cmssdt.cern.ch/jenkins/job/update-github-webhook-token)

**Description:** Updates passphrase for git webhooks for selected repository.
More details <a href="https://github.com/cms-sw/cms-bot/tree/master/repos">here</a>.

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

## [update-release-map](https://cmssdt.cern.ch/jenkins/job/update-release-map)

**Description:** This project adds the release information in <a href="https://cmssdt.cern.ch/SDT/releases.map">cms-bot/releases.map</a> file.
CVMFS installation is started once a release is available in this file.

**Project is `enabled`.**

**Upstream projects:**
* [upload-release](#upload-release):

**Downstream projects:**
* [build-fwlite](#build-fwlite):
* [cmssw-doxygen](#cmssw-doxygen):
* [ib-run-cfipython](#ib-run-cfipython):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [update-release-notes-collection](https://cmssdt.cern.ch/jenkins/job/update-release-notes-collection)

**Description:** Generates <a href="https://cmssdt.cern.ch/SDT/ReleaseNotes/">CMSSW release notes</a> using Jekyll.

**Project is `enabled`.**

**Upstream projects:**
* [release-produce-changelog](#release-produce-changelog):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [upload-release](https://cmssdt.cern.ch/jenkins/job/upload-release)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Project is `enabled`.**

**Upstream projects:**
* [upload-release-setup](#upload-release-setup):

**Downstream projects:**
* [release-deploy-afs](#release-deploy-afs):
* [update-release-map](#update-release-map):

**Sub-projects:**
* [release-deploy-afs](#release-deploy-afs):
* [update-release-map](#update-release-map):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [upload-release-setup](https://cmssdt.cern.ch/jenkins/job/upload-release-setup)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**
* [upload-release](#upload-release):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [web-summary-data](https://cmssdt.cern.ch/jenkins/job/web-summary-data)

**Description:** Scans build summary (ib-report-generator/scan-build-summary)

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

## [web-update-cmssdt-ib](https://cmssdt.cern.ch/jenkins/job/web-update-cmssdt-ib)

**Description:** Job used to transpile cmssdt ib page from ECMAscript6 to regular javascript and push changes to github.

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [web-update-logReader](https://cmssdt.cern.ch/jenkins/job/web-update-logReader)

**Description:** Transpiles <a href="https://github.com/cms-sw/logreader">Logreader</a> to pure js/html/css and deploys to 
<a href="https://cmssdt.cern.ch/SDT/">cmssdt-web</a>.

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

## [web-update-SDT](https://cmssdt.cern.ch/jenkins/job/web-update-SDT)

**Description:** Copies releases.map to /data/sdt/SDT/jenkins-artifacts.<br>
<b>Depricated project</b>. Its tasks are taken by <a href="https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo">deploy-cms-repo</a> project.

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

