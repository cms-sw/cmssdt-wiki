# [All](https://cmssdt.cern.ch/jenkins/view/All)

**View description:** This view has listed all CMSSDT jobs.

**View type:** All

---

# Projects:

## [abort-release](https://cmssdt.cern.ch/jenkins/job/abort-release)

**Description:** Aborts and kills a release building process.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [kill-build-release](#kill-build-release):

**Sub-projects:**

* [kill-build-release](#kill-build-release):

**Triggers from:** []

## [auto-forward-ports](https://cmssdt.cern.ch/jenkins/job/auto-forward-ports)

**Description:** This is triggered by github webhook for each cmssw/cmsdist branch merge event.
this forward port changes from source branch to target branch. Mapping between soruce and destination branches are available in cms-bot.

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [backport-pull-request](https://cmssdt.cern.ch/jenkins/job/backport-pull-request)

**Description:** Manually executed job for backporting pull requests given the repo name, the branch for which the PR should be created and the PR to be backported

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [baseline-ib-results](https://cmssdt.cern.ch/jenkins/job/baseline-ib-results)

**Description:** This job runs a few tests only for the IB, for comparison with those ran by the pull request.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

**Sub-projects:**


**Triggers from:** []

## [build-any-ib](https://cmssdt.cern.ch/jenkins/job/build-any-ib)

**Description:** This jobs starts an Integration Build(IB). Base on state of <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a>/<a href="https://github.com/cms-sw/cmssw">CMSSW</a> git repositories, it builds either a full release or patch release.
<br>Build Full IB if:

<ul>
  <li> There are changes in <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a></li>
  <li> There is no full IB available based on current <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a></li>
  <li> Previous full IB had build errors</li>
</ul>

Otherwise build a patch release


**Upstream projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

* [build-fwlite-ib](#build-fwlite-ib):
* [cmspkg-clone](#cmspkg-clone):
* [ib-build-logs](#ib-build-logs):
* [ib-install-cvmfs](#ib-install-cvmfs):

**Sub-projects:**

* [ib-install-cvmfs,cmspkg-clone](#ib-install-cvmfs,cmspkg-clone):
* [ib-build-logs](#ib-build-logs):
* [build-fwlite-ib](#build-fwlite-ib):

**Triggers from:** []

## [build-container](https://cmssdt.cern.ch/jenkins/job/build-container)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [build-fwlite](https://cmssdt.cern.ch/jenkins/job/build-fwlite)

**Description:** TO build a CMSSW_X_Y_Z_FWLITE release based on an existing CMSSW_X_Y_Z release. CMSSW_X_Y_Z should already be build/uploaded before building its FWLITE version.

**Upstream projects:**

* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [build-fwlite-ib](https://cmssdt.cern.ch/jenkins/job/build-fwlite-ib)

**Description:** This job is responsible for building FWLITE release for each Integration build(IB). 
Results of this build can be seen via <a href="https://cmssdt.cern.ch/SDT/">CMSSDT</a> <a href="https://cmssdt.cern.ch/SDT/html/showIB.html">IB page</a>.

**Upstream projects:**

* [build-any-ib](#build-any-ib):

**Downstream projects:**

* [ib-build-logs](#ib-build-logs):

**Sub-projects:**


**Triggers from:** []

## [build-release](https://cmssdt.cern.ch/jenkins/job/build-release)

**Description:** This job actually builds a release.
It is triggered by cms-bot after the <a href="https://github.com/cms-sw/cmssw/issues?q=label%3Arelease-notes-requested">Release build Issue</a> is approved by release manager.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-auto-build](https://cmssdt.cern.ch/jenkins/job/cleanup-auto-build)

**Description:** This job deletes the relsease build areas after three days.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-cms-sw-io-history](https://cmssdt.cern.ch/jenkins/job/cleanup-cms-sw-io-history)

**Description:** This job cleanup the cms-sw/cms-sw.github.io repository history. Specially the data and _data directories history.


**Upstream projects:**


**Downstream projects:**

* [update-github-pages](#update-github-pages):

**Sub-projects:**


**Triggers from:** []

## [cleanup-cmssdt](https://cmssdt.cern.ch/jenkins/job/cleanup-cmssdt)

**Description:** Clean up disk space on cmssdt

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cleanup-tags](https://cmssdt.cern.ch/jenkins/job/cleanup-tags)

**Description:** Cleanup IB tags from the official CMSSW repository.


**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

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

## [cms-dockerhub](https://cmssdt.cern.ch/jenkins/job/cms-dockerhub)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cms-prs-cache](https://cmssdt.cern.ch/jenkins/job/cms-prs-cache)

**Description:** None

**Upstream projects:**

* [cms-prs-cache](#cms-prs-cache):
* [github-webhook](#github-webhook):

**Downstream projects:**

* [cms-prs-cache](#cms-prs-cache):

**Sub-projects:**

* [cms-prs-cache](#cms-prs-cache):

**Triggers from:** []

## [cmspkg-clone](https://cmssdt.cern.ch/jenkins/job/cmspkg-clone)

**Description:** None

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [upload-release](#upload-release):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cmssw-doxygen](https://cmssdt.cern.ch/jenkins/job/cmssw-doxygen)

**Description:** Generate doxygen documentation for CMSSW project

**Upstream projects:**

* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cmssw-to-stitched](https://cmssdt.cern.ch/jenkins/job/cmssw-to-stitched)

**Description:** This looks for the Framework changes in cmssw and port them to stitched repo
This is automatically triggered by auto-forward-port job

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [comp-bot](https://cmssdt.cern.ch/jenkins/job/comp-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
This is to process bot commands for cmsdist comp branches

**Upstream projects:**

* [github-webhook](#github-webhook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [compare-material-budget](https://cmssdt.cern.ch/jenkins/job/compare-material-budget)

**Description:** Comopare results of material budget of two releases using Validation/Geometry/test/TrackerMaterialBudgetComparison.C macro


**Upstream projects:**

* [ib-run-material-budget](#ib-run-material-budget):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [compare-root-files-short-matrix](https://cmssdt.cern.ch/jenkins/job/compare-root-files-short-matrix)

**Description:** Download the files of the baseline IB and compare them with the results of the ones of a pull request

**Upstream projects:**

* [ib-any-integration](#ib-any-integration):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Upstream projects:**

* [baseline-ib-results](#baseline-ib-results):

**Downstream projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Sub-projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Triggers from:** []

## [cvmfs-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-gc)

**Description:** This runs CVMFS GC (once a week)

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [cvmfs-publish-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-baseline)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Upstream projects:**

* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [das-query](https://cmssdt.cern.ch/jenkins/job/das-query)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [dataset-to-ibeos](https://cmssdt.cern.ch/jenkins/job/dataset-to-ibeos)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**


**Triggers from:** []

## [deploy-cms-repo](https://cmssdt.cern.ch/jenkins/job/deploy-cms-repo)

**Description:** Updates cms-bot clone on Jenkins master

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [deploy-cmsdoxygen](https://cmssdt.cern.ch/jenkins/job/deploy-cmsdoxygen)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [dxr-cmssw-index](https://cmssdt.cern.ch/jenkins/job/dxr-cmssw-index)

**Description:** ---need-description---

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [es-close-indexes](https://cmssdt.cern.ch/jenkins/job/es-close-indexes)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [external-deploy-afs](https://cmssdt.cern.ch/jenkins/job/external-deploy-afs)

**Description:** This job deployes any external tool on afs that is required. 

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [fix-backport-prs](https://cmssdt.cern.ch/jenkins/job/fix-backport-prs)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [forward-pull-requests](https://cmssdt.cern.ch/jenkins/job/forward-pull-requests)

**Description:** Given a branch, gets all of its pull requests and recreates them in a different branch.


**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [gh-teams](https://cmssdt.cern.ch/jenkins/job/gh-teams)

**Description:** printing some python file	

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [git-mirror-repository](https://cmssdt.cern.ch/jenkins/job/git-mirror-repository)

**Description:** mirror one git repository

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [git-reference-cms-ib](https://cmssdt.cern.ch/jenkins/job/git-reference-cms-ib)

**Description:** Create GIT Reference for cms-sw/cmssw repository in /cvmfs/cms-ib.cern.ch/git/cms-sw.
This is automatically triggered by "git push" to cmssw repo.

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [github-hooks](https://cmssdt.cern.ch/jenkins/job/github-hooks)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [github-push-hook](https://cmssdt.cern.ch/jenkins/job/github-push-hook)

**Description:** Updates cms-bot clone on cmssdt.
This job is also triggered via github web hook. Please do not add/remove any parameters of this job otherwise github web hooks will not be able to triiger the job

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

## [github-webhook](https://cmssdt.cern.ch/jenkins/job/github-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Upstream projects:**


**Downstream projects:**

* [cms-bot](#cms-bot):
* [cms-prs-cache](#cms-prs-cache):
* [comp-bot](#comp-bot):
* [github-push-hook](#github-push-hook):
* [query-build-release-issues](#query-build-release-issues):

**Sub-projects:**

* [comp-bot](#comp-bot):
* [github-push-hook](#github-push-hook):
* [cms-prs-cache](#cms-prs-cache):
* [query-build-release-issues](#query-build-release-issues):
* [cms-bot](#cms-bot):

**Triggers from:** []

## [HLT-Validation](https://cmssdt.cern.ch/jenkins/job/HLT-Validation)

**Description:** Appends job's time out information into jenkins.log file.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-any-integration](https://cmssdt.cern.ch/jenkins/job/ib-any-integration)

**Description:** Build a pull request

**Upstream projects:**

* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**

* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [run-igprof-pr](#run-igprof-pr):
* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**

* [stop-ib-any-integration](#stop-ib-any-integration):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [run-igprof-pr](#run-igprof-pr):

**Triggers from:** []

## [ib-build-logs](https://cmssdt.cern.ch/jenkins/job/ib-build-logs)

**Description:** It is build periodically (H/30 * * * *). Runs on cmssdt. Projects to build: update-github-pages

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [build-fwlite-ib](#build-fwlite-ib):

**Downstream projects:**

* [update-github-pages](#update-github-pages):

**Sub-projects:**


**Triggers from:** [u'build-fwlite-ib']

## [ib-cache-to-eos](https://cmssdt.cern.ch/jenkins/job/ib-cache-to-eos)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**


**Downstream projects:**

* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**

* [update-ibeos-cache](#update-ibeos-cache):

**Triggers from:** []

## [ib-cleanup-installers](https://cmssdt.cern.ch/jenkins/job/ib-cleanup-installers)

**Description:** Cron job for log rotation on installer nodes. (clean up obsolete weeks)

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-cvmfs-publish](https://cmssdt.cern.ch/jenkins/job/ib-cvmfs-publish)

**Description:** This jobs copies IBs installation for a arch from another machine and publish it to cvmfs

**Upstream projects:**


**Downstream projects:**

* [ib-validation](#ib-validation):

**Sub-projects:**


**Triggers from:** []

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

* [ib-validation](#ib-validation):

**Sub-projects:**


**Triggers from:** []

## [ib-run-addons](https://cmssdt.cern.ch/jenkins/job/ib-run-addons)

**Description:** ---need-description---

**Upstream projects:**

* [ib-validation](#ib-validation):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-cfipython](https://cmssdt.cern.ch/jenkins/job/ib-run-cfipython)

**Description:** This job gets the cfipython files for a cmssw release and push the changes to cms-sw/cmssw-cfipython repo.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):
* [update-release-map](#update-release-map):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-check-headers](https://cmssdt.cern.ch/jenkins/job/ib-run-check-headers)

**Description:** Check for missing headers and parse the log for all errors (clang modules)

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-flawfinder](https://cmssdt.cern.ch/jenkins/job/ib-run-flawfinder)

**Description:** ---need-description---

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-geometry](https://cmssdt.cern.ch/jenkins/job/ib-run-geometry)

**Description:** Runs geometry comparison tests for each IB

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-igprof-mp](https://cmssdt.cern.ch/jenkins/job/ib-run-igprof-mp)

**Description:** ---need-description---

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-igprof-pp](https://cmssdt.cern.ch/jenkins/job/ib-run-igprof-pp)

**Description:** ---need-description---

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-iwyu](https://cmssdt.cern.ch/jenkins/job/ib-run-iwyu)

**Description:** Runs iwyu logs parsing for each IB

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-lizard](https://cmssdt.cern.ch/jenkins/job/ib-run-lizard)

**Description:** ---need-description---

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-material-budget](https://cmssdt.cern.ch/jenkins/job/ib-run-material-budget)

**Description:** Runs Validation/Geometry/test/runP_Tracker_cfg.py and MaterialBudget.C for an IB

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**

* [compare-material-budget](#compare-material-budget):

**Sub-projects:**


**Triggers from:** []

## [ib-run-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-qa)

**Description:** ---need-description---

**Upstream projects:**

* [ib-validation](#ib-validation):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-relvals](https://cmssdt.cern.ch/jenkins/job/ib-run-relvals)

**Description:** The job runs release validations, as validations are separated on pieces (1of6 2of6 etc)

**Upstream projects:**

* [ib-validation](#ib-validation):

**Downstream projects:**

* [process-relval-logs](#process-relval-logs):
* [update-das-queries](#update-das-queries):

**Sub-projects:**


**Triggers from:** []

## [ib-run-valgrind](https://cmssdt.cern.ch/jenkins/job/ib-run-valgrind)

**Description:** This job runs valgrind tool for selected IBs when build IB job is complete.   

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except Sunday at 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
This was created to avoid the issue with <a href="https://wiki.jenkins.io/display/JENKINS/Dynamic+Parameter+Plug-in">Jenkins Dynamic Parameters</a>.


**Upstream projects:**


**Downstream projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Sub-projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

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

## [ib-static-checks](https://cmssdt.cern.ch/jenkins/job/ib-static-checks)

**Description:** Runs a few tests only for the IB, for comparison with those ran by the pull request.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-tag-and-schdule](https://cmssdt.cern.ch/jenkins/job/ib-tag-and-schdule)

**Description:** This job tags and schedules all the IBs.<br/>
It reads the <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a> to find all available CMSSW release cycles and tag them in github.
Once tags is done then it triggers 'build-any-ib' sub-job to actually build IBs for all possible architectures (mentioned in <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a>).
For Developement IB, it also triggers the generation of <a href="https://cmssdt.cern.ch/lxr">LXR indexes</a>

For Sunday's 00h IBs, it also resets the CMSREP weekly repositories by building a dummy package and uploading it to cms.weekN. It also 
then triggers 'ib-install-cvmfs' sub-job to get the new cms.weekN deployed on the /cvmfs/cms-ib.cern.ch

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

## [ib-validation](https://cmssdt.cern.ch/jenkins/job/ib-validation)

**Description:** Validates the integration builds.

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

## [import-stitched-tag](https://cmssdt.cern.ch/jenkins/job/import-stitched-tag)

**Description:** This tags a CMSSW release tag and upload the packages (https://github.com/cms-sw/Stitched/blob/master/packages.txt) needed by Stitched to Stitched repo.
CMSSW_* tag is rename to STITCHED_*

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-add-job-to-anthoer-server](https://cmssdt.cern.ch/jenkins/job/jenkins-add-job-to-anthoer-server)

**Description:** This is a helper job to copy a Jenkins Project from this Jenkins master to another Jenkins master.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-backup](https://cmssdt.cern.ch/jenkins/job/jenkins-backup)

**Description:** This job takes the backup of Jenkins master configuration (which includes projects, jenkins configuration, slaves, secrets etc.)
Backups jenkins scripts on https://github.com/cms-sw/jenkins-backup.git

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-disable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-jobs)

**Description:** Disable all nodes that started with the provided wildcard string,
example parameter
cmsbuild* 
would enable all cmsbuild machines found

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-disable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-disable-nodes)

**Description:** Disable all jenkins slaves based on the slave wildcard filter.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-elasticsearch-monitor](https://cmssdt.cern.ch/jenkins/job/jenkins-elasticsearch-monitor)

**Description:** This job runs a python script to push useful info from jenkins build logs to elasticsearch



**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-enable-jobs](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-jobs)

**Description:** Enable all Jenkins projects based on the wildcard filter.

**Upstream projects:**

* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-enable-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-enable-nodes)

**Description:** Enables all nodes that started with the provided wildcard string,
example parameter
cmsbuild* 
would enable all cmsbuild machines found

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-initialize](https://cmssdt.cern.ch/jenkins/job/jenkins-initialize)

**Description:** This project is run once a new Jenkins instance is setup or upgrated to a new version.
This runs some sub-projects to check if basic functionality of jenkins is working.

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

**Description:** This is Jenkins installation tests project. It tests if various Jenkins Command-line interface service are working.

**Upstream projects:**

* [jenkins-initialize](#jenkins-initialize):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-installation-trigger-cli](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-cli)

**Description:** Jenkins installaton test job to test the triggering of a sub-project via Command-line-interface.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-installation-trigger-test](https://cmssdt.cern.ch/jenkins/job/jenkins-installation-trigger-test)

**Description:** This is Jenkins installation test project. This tests the triggering of a sub-project.

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

## [jenkins-projects-wiki-update](https://cmssdt.cern.ch/jenkins/job/jenkins-projects-wiki-update)

**Description:** This job runs a groovy script to dump jenkinsprojects info , which is further read by python to 
display it in markdown form. It is later imported to CMSSDT wiki.



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

## [jenkins-test-job1](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job1)

**Description:** Jenkins installation test job 1 to check for the parameters passed from a parent job.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-job2](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job2)

**Description:** Jenkins tests Project to test jenkins functionality.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-slave](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slave)

**Description:** This Jenkins project test various CMS Jenkins slaves and makes sure that various communication channels 
between Jenkins Master/slave  and slave and various services are working.

**Upstream projects:**

* [jenkins-test-slaves](#jenkins-test-slaves):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [jenkins-test-slaves](https://cmssdt.cern.ch/jenkins/job/jenkins-test-slaves)

**Description:** Jenkins project to trigger the jenkins slave test job for each selected slave

**Upstream projects:**


**Downstream projects:**

* [jenkins-test-slave](#jenkins-test-slave):

**Sub-projects:**

* [jenkins-test-slave](#jenkins-test-slave):

**Triggers from:** []

## [kill-build-release](https://cmssdt.cern.ch/jenkins/job/kill-build-release)

**Description:** Aborts and kills a release building process. 

**Upstream projects:**

* [abort-release](#abort-release):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [kill-hanging-jobs](https://cmssdt.cern.ch/jenkins/job/kill-hanging-jobs)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [lfn-to-ibeos](https://cmssdt.cern.ch/jenkins/job/lfn-to-ibeos)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**


**Downstream projects:**

* [update-ibeos-cache](#update-ibeos-cache):

**Sub-projects:**

* [update-ibeos-cache](#update-ibeos-cache):

**Triggers from:** []

## [lxr-check](https://cmssdt.cern.ch/jenkins/job/lxr-check)

**Description:** None

**Upstream projects:**


**Downstream projects:**

* [lxr-run-container](#lxr-run-container):

**Sub-projects:**

* [lxr-run-container](#lxr-run-container):

**Triggers from:** []

## [lxr-checkout-version](https://cmssdt.cern.ch/jenkins/job/lxr-checkout-version)

**Description:** None

**Upstream projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

* [lxr-generate-index](#lxr-generate-index):

**Sub-projects:**

* [lxr-generate-index](#lxr-generate-index):

**Triggers from:** []

## [lxr-generate-index](https://cmssdt.cern.ch/jenkins/job/lxr-generate-index)

**Description:** None

**Upstream projects:**

* [lxr-checkout-version](#lxr-checkout-version):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [lxr-remove-index](https://cmssdt.cern.ch/jenkins/job/lxr-remove-index)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [lxr-run-container](https://cmssdt.cern.ch/jenkins/job/lxr-run-container)

**Description:** None

**Upstream projects:**

* [lxr-check](#lxr-check):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [material-budget-ref](https://cmssdt.cern.ch/jenkins/job/material-budget-ref)

**Description:** Runs Validation/Geometry/test/runP_Tracker_cfg.py and MaterialBudget.C for an IB

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [mirror-cmsrep](https://cmssdt.cern.ch/jenkins/job/mirror-cmsrep)

**Description:** Create a live mirror of cmsrep.cern.ch

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [monitor-openstack-vms](https://cmssdt.cern.ch/jenkins/job/monitor-openstack-vms)

**Description:** This job run periodically to monitor the running state of vms in openstack , if stopped , creates an email alert.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [openstack-add-jenkins-slave](https://cmssdt.cern.ch/jenkins/job/openstack-add-jenkins-slave)

**Description:** Find all hosts in an hostgroup and add them to jenkins

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

## [openstack-create-vms](https://cmssdt.cern.ch/jenkins/job/openstack-create-vms)

**Description:** Create Openstack VMs for a selected hostgroup.

**Upstream projects:**

* [openstack-create-vms](#openstack-create-vms):

**Downstream projects:**

* [openstack-create-vms](#openstack-create-vms):
* [openstack-delete-vms](#openstack-delete-vms):

**Sub-projects:**

* [openstack-create-vms](#openstack-create-vms):

**Triggers from:** []

## [openstack-create-volume](https://cmssdt.cern.ch/jenkins/job/openstack-create-volume)

**Description:** Job to delete openstack instances providing only the name

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [openstack-delete-vms](https://cmssdt.cern.ch/jenkins/job/openstack-delete-vms)

**Description:** Job to delete openstack instances providing only the name

**Upstream projects:**

* [openstack-create-vms](#openstack-create-vms):
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**

* [openstack-delete-vms](#openstack-delete-vms):
* [openstack-delete-volume](#openstack-delete-volume):

**Sub-projects:**

* [openstack-delete-vms](#openstack-delete-vms):
* [openstack-delete-volume](#openstack-delete-volume):

**Triggers from:** []

## [openstack-delete-volume](https://cmssdt.cern.ch/jenkins/job/openstack-delete-volume)

**Description:** Job to delete openstack instances providing only the name

**Upstream projects:**

* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [process-deprecate-releases](https://cmssdt.cern.ch/jenkins/job/process-deprecate-releases)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [process-relval-logs](https://cmssdt.cern.ch/jenkins/job/process-relval-logs)

**Description:** This job process partial logs of Relvals and place files accordingly. 

**Upstream projects:**

* [ib-run-relvals](#ib-run-relvals):
* [test-kerberos-within-docker](#test-kerberos-within-docker):
* [test-relvals-with-krb](#test-relvals-with-krb):

**Downstream projects:**

* [update-github-pages](#update-github-pages):

**Sub-projects:**


**Triggers from:** []

## [query-build-release-issues](https://cmssdt.cern.ch/jenkins/job/query-build-release-issues)

**Description:** ---need-description---

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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [release-deploy-afs](https://cmssdt.cern.ch/jenkins/job/release-deploy-afs)

**Description:** ---need-description---

**Upstream projects:**

* [upload-release](#upload-release):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [release-produce-changelog](https://cmssdt.cern.ch/jenkins/job/release-produce-changelog)

**Description:** ---need-description---

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [update-release-notes-collection](#update-release-notes-collection):

**Sub-projects:**

* [update-release-notes-collection](#update-release-notes-collection):

**Triggers from:** []

## [rpm-repository-backup](https://cmssdt.cern.ch/jenkins/job/rpm-repository-backup)

**Description:** Backs-up cmsrep

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [run-igprof-pr](https://cmssdt.cern.ch/jenkins/job/run-igprof-pr)

**Description:** ---need-description---

**Upstream projects:**

* [ib-any-integration](#ib-any-integration):

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

* [stop-ib-any-integration](#stop-ib-any-integration):

**Sub-projects:**

* [stop-ib-any-integration](#stop-ib-any-integration):

**Triggers from:** []

## [run-repo-size-check](https://cmssdt.cern.ch/jenkins/job/run-repo-size-check)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [schedule-additional-tests](https://cmssdt.cern.ch/jenkins/job/schedule-additional-tests)

**Description:** ---need-description---

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

## [stop-ib-any-integration](https://cmssdt.cern.ch/jenkins/job/stop-ib-any-integration)

**Description:** Kill a running 

**Upstream projects:**

* [cms-bot](#cms-bot):
* [ib-any-integration](#ib-any-integration):
* [run-pr-code-ckecks](#run-pr-code-ckecks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** ---need-description---

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [test](https://cmssdt.cern.ch/jenkins/job/test)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [test-build-periodic](https://cmssdt.cern.ch/jenkins/job/test-build-periodic)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [test-docker](https://cmssdt.cern.ch/jenkins/job/test-docker)

**Description:** None

**Upstream projects:**

* [slaves-checks](#slaves-checks):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [test-kerberos-within-docker](https://cmssdt.cern.ch/jenkins/job/test-kerberos-within-docker)

**Description:** The job runs release validations, as validations are separated on pieces (1of6 2of6 etc)

**Upstream projects:**


**Downstream projects:**

* [process-relval-logs](#process-relval-logs):
* [update-das-queries](#update-das-queries):

**Sub-projects:**


**Triggers from:** []

## [test-relvals-with-krb](https://cmssdt.cern.ch/jenkins/job/test-relvals-with-krb)

**Description:** The job runs release validations, as validations are separated on pieces (1of6 2of6 etc)

**Upstream projects:**


**Downstream projects:**

* [process-relval-logs](#process-relval-logs):
* [update-das-queries](#update-das-queries):

**Sub-projects:**


**Triggers from:** []

## [test-scram](https://cmssdt.cern.ch/jenkins/job/test-scram)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [tutorial-jenkins](https://cmssdt.cern.ch/jenkins/job/tutorial-jenkins)

**Description:** This is job used to learn jenkins.

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-categories-page](https://cmssdt.cern.ch/jenkins/job/update-categories-page)

**Description:** ---need-description---

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**

* [ib-run-relvals](#ib-run-relvals):
* [test-kerberos-within-docker](#test-kerberos-within-docker):
* [test-relvals-with-krb](#test-relvals-with-krb):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-externals-mirrors](https://cmssdt.cern.ch/jenkins/job/update-externals-mirrors)

**Description:** Update some of the externals mirror and setup a cms specific branch so that updates can be proposed there. 

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-github-pages](https://cmssdt.cern.ch/jenkins/job/update-github-pages)

**Description:** This job update contents of the "data" directory in cms-sw.github.io

**Upstream projects:**

* [cleanup-cms-sw-io-history](#cleanup-cms-sw-io-history):
* [ib-build-logs](#ib-build-logs):
* [process-relval-logs](#process-relval-logs):

**Downstream projects:**

* [refresh-cmssdt](#refresh-cmssdt):
* [summary-of-merged-prs](#summary-of-merged-prs):

**Sub-projects:**


**Triggers from:** [u'cleanup-cms-sw-io-history', u'ib-build-logs']

## [update-github-webhook-token](https://cmssdt.cern.ch/jenkins/job/update-github-webhook-token)

**Description:** None

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-ibeos-cache](https://cmssdt.cern.ch/jenkins/job/update-ibeos-cache)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**

* [dataset-to-ibeos](#dataset-to-ibeos):
* [ib-cache-to-eos](#ib-cache-to-eos):
* [lfn-to-ibeos](#lfn-to-ibeos):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [update-release-map](https://cmssdt.cern.ch/jenkins/job/update-release-map)

**Description:** This project adds the release information in <a href="https://cmssdt.cern.ch/SDT/releases.map">cms-bot/releases.map</a> file.
CVMFS installation is started once a release is available in this file.

**Upstream projects:**

* [upload-release](#upload-release):

**Downstream projects:**

* [build-fwlite](#build-fwlite):
* [cmssw-doxygen](#cmssw-doxygen):
* [ib-run-cfipython](#ib-run-cfipython):

**Sub-projects:**


**Triggers from:** []

## [update-release-notes-collection](https://cmssdt.cern.ch/jenkins/job/update-release-notes-collection)

**Description:** None

**Upstream projects:**

* [release-produce-changelog](#release-produce-changelog):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [upload-release](https://cmssdt.cern.ch/jenkins/job/upload-release)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Upstream projects:**

* [upload-release-setup](#upload-release-setup):

**Downstream projects:**

* [cmspkg-clone](#cmspkg-clone):
* [release-deploy-afs](#release-deploy-afs):
* [update-release-map](#update-release-map):

**Sub-projects:**


**Triggers from:** []

## [upload-release-setup](https://cmssdt.cern.ch/jenkins/job/upload-release-setup)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Upstream projects:**

* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**

* [upload-release](#upload-release):

**Sub-projects:**


**Triggers from:** []

## [web-summary-data](https://cmssdt.cern.ch/jenkins/job/web-summary-data)

**Description:** Scans build summary (ib-report-generator/scan-build-summary)

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [web-update-cmssdt-ib](https://cmssdt.cern.ch/jenkins/job/web-update-cmssdt-ib)

**Description:** Job used to transpile cmssdt ib page from ECMAscript6 to regular javascript and bush changes to github.

**Upstream projects:**

* [github-push-hook](#github-push-hook):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [web-update-logReader](https://cmssdt.cern.ch/jenkins/job/web-update-logReader)

**Description:** ---need-description---

**Upstream projects:**


**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [web-update-SDT](https://cmssdt.cern.ch/jenkins/job/web-update-SDT)

**Description:** ---need-description---

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

