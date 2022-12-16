# [Github-WebHook](https://cmssdt.cern.ch/jenkins/view/Github-WebHook)

**View description:** None

**View type:** Build Pipeline View

---

# Projects:

## [github-webhook](https://cmssdt.cern.ch/jenkins/job/github-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cleanup-cms-sw-io-history](#cleanup-cms-sw-io-history):
* [cms-bot](#cms-bot):
* [cms-prs-cache](#cms-prs-cache):
* [cms-prs-files](#cms-prs-files):
* [comp-bot](#comp-bot):
* [docker-dmwm-CMSKubernetes](#docker-dmwm-CMSKubernetes):
* [dockerhub_synchronization](#dockerhub_synchronization):
* [github-push-hook](#github-push-hook):
* [query-build-release-issues](#query-build-release-issues):
* [update-data-tag-on-pr-merge](#update-data-tag-on-pr-merge):

**Sub-projects:**
* [comp-bot](#comp-bot):
* [github-push-hook](#github-push-hook):
* [cms-prs-cache](#cms-prs-cache):
* [query-build-release-issues](#query-build-release-issues):
* [cms-bot](#cms-bot):
* [dockerhub_synchronization](#dockerhub_synchronization):
* [docker-dmwm-CMSKubernetes](#docker-dmwm-CMSKubernetes):
* [cms-prs-files](#cms-prs-files):
* [update-data-tag-on-pr-merge](#update-data-tag-on-pr-merge):
* [cleanup-cms-sw-io-history](#cleanup-cms-sw-io-history):

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
* [github-webhook](#github-webhook):

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 1 * * 0
```

---

## [update-github-pages](https://cmssdt.cern.ch/jenkins/job/update-github-pages)

**Description:** This job update contents of the "data" directory in cms-sw.github.io. 
It downloads our github pages, parses the log files, updates the documentation accordingly, and uploads the pages again.
In this case, the job is automatically triggered after some minutes. 
If it fails, one just needs to check that the next build was successful so that pages are updated correctly.

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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Project is `disabled`.**

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
	. Do not worry - job builds quite often and next build shouls be succesful. But if it keeps on failing (over 3 times) then try to re-run the job with "RESET" enabled.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):
* [update-github-pages](#update-github-pages):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** [u'update-github-pages']


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-bot](https://cmssdt.cern.ch/jenkins/job/cms-bot)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.

Will kill a scheduled/running job acording to comments.

<br><br>
<b>Q/A</b>

<ul>
  <li>
    <b>Q:</b> Job 'cms-sw/cmssw #****' failed. What to do?
  </li>
  <li>
    <b>A:</b>
    Job is configured to do few re-tries, so in case of github or network glitches the job will recover. If it keeps on failing then one need to check the logs. 
    Mostly it fails due to github/ssh connection, so it will automatically recover.
  </li>
  <li>
    <b>Q:</b> Job failed with ssh timeout?
  </li>
  <li>
    <b>A:</b>
    Nothing to do, job will re-try 3 time to recover. If it keeps on failing for few hours then better to disable it an re-enable once issue is solved e.g. github is back or CERN network is working again.
  </li>
  
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [github-webhook](#github-webhook):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Sub-projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [abort-pr-tests ](#abort-pr-tests ):
* [run-pr-code-checks](#run-pr-code-checks):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-pr-tests](https://cmssdt.cern.ch/jenkins/job/abort-pr-tests)

**Description:** This job basically triggers the `abort-jenkins-jobs` job for all the jobs related to PR tests.

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-run-pr-tests' and jobs started by it). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore the given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-schedule-pr-tests](https://cmssdt.cern.ch/jenkins/job/ib-schedule-pr-tests)

**Description:** Build a pull request

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Sub-projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-tests](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-tests)

**Description:** This is CMSSw CI Job which runs the build and unit tests part of CI. 
It first kills any other job whcih is running for same PullRequests/Architecture. and then starts the build process.
Once the build process if done then it trigger other jobs to start the deployment of the build artifects on CVMFS and
start the tests. at the end it run the unit tests. Unit tests are run here as it needs the CMSSW/tmp directory which
is not deployed on CVMFS.

<b>Q/A:</b>
In case this job fails then in most cases just re-try it. In case it is failed due to network/github issues then it is
better to wait for the service to get healthy.




**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [ib-run-pr-wait-deployment](#ib-run-pr-wait-deployment):
* [pr-publish-cmssw](#pr-publish-cmssw):
* [update-das-queries](#update-das-queries):

**Sub-projects:**
* [abort-pr-tests](#abort-pr-tests):
* [pr-publish-cmssw](#pr-publish-cmssw):
* [ib-run-pr-wait-deployment](#ib-run-pr-wait-deployment):
* [update-das-queries ](#update-das-queries ):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-pr-tests](https://cmssdt.cern.ch/jenkins/job/abort-pr-tests)

**Description:** This job basically triggers the `abort-jenkins-jobs` job for all the jobs related to PR tests.

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-run-pr-tests' and jobs started by it). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore the given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-wait-deployment](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-wait-deployment)

**Description:** Same puprose as `ib-any-integration`, just different script is called.<br>
This job waits until the build has been deployed into cvmfs (cms-ci.cern.ch repository).<br>
If the job fails, it could be because of a failure in the previous job (cvmfs-install-pr) that produces and uploads the build. Therefore, the current job will time out.<br>
The way to proceed in case of failure is to look for the PR number present in the build name and trace back what has happened. It could be that the PR test were stuck and the build was never produced or uploaded.




**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**

**Sub-projects:**
* [ib-run-pr-${TEST_TYPE}](#ib-run-pr-${TEST_TYPE}):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [pr-publish-cmssw](https://cmssdt.cern.ch/jenkins/job/pr-publish-cmssw)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.<br/>
Job could fail due to github issues or disk related issue. Normally it is safe to just retry it once github/disk issues are resolved.<br/>
There is no need to retry if it has been rerun successfully after the last failure.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-tests](#ib-run-pr-tests):
* [ib-run-relvals](#ib-run-relvals):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-pr-code-checks](https://cmssdt.cern.ch/jenkins/job/run-pr-code-checks)

**Description:** This run "scram build code-checks" for a cmssw PR to find out if it comply with cmssw code checks.
In a CMSSW dev area, it runs 
  git cms-merge-topic -u PR
  scram build code-checks

This job re-tries twice to recover. If it still fails after two retires then try to understand the failure and re-try again.

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [abort-jenkins-job](#abort-jenkins-job):
* [cms-prs-files](#cms-prs-files):

**Sub-projects:**
* [abort-jenkins-job](#abort-jenkins-job):
* [cms-prs-files](#cms-prs-files):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** Kill a running job (by default it is 'ib-run-pr-tests' and jobs started by it). 

The idea is that if pull request was updated, all the test should be restarted. This job will kill all the running jobs for that
PR (with matching parameters). It will ignore the given job ID - the ID of upstream job that started this job.

**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-prs-files](https://cmssdt.cern.ch/jenkins/job/cms-prs-files)

**Description:** On every CMSSW PR, this job dumps list of files that are going to be modified by open PRs to files_changed_by_prs.json .

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H/2 * * *
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
* [cms-prs-cache](#cms-prs-cache):

**Triggers from:** []


**Periodic builds:**
```bash
H 20 * * *
```

---

## [cms-prs-files](https://cmssdt.cern.ch/jenkins/job/cms-prs-files)

**Description:** On every CMSSW PR, this job dumps list of files that are going to be modified by open PRs to files_changed_by_prs.json .

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):
* [run-pr-code-checks](#run-pr-code-checks):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H/2 * * *
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

## [docker-dmwm-CMSKubernetes](https://cmssdt.cern.ch/jenkins/job/docker-dmwm-CMSKubernetes)

**Description:** None

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

## [dockerhub_synchronization](https://cmssdt.cern.ch/jenkins/job/dockerhub_synchronization)

**Description:** Synchronizes Docker Hub Organization's setup (repositories/teams/members/permissions) with docker configuration yaml file.

**Project is `enabled`.**

**Upstream projects:**
* [github-webhook](#github-webhook):

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
* [auto-forward-port](#auto-forward-port):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [deploy-cms-repo](#deploy-cms-repo):
* [git-mirror-repository](#git-mirror-repository):
* [git-reference-cvmfs](#git-reference-cvmfs):
* [update-cmssw-l2-histroy](#update-cmssw-l2-histroy):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):
* [web-update-logReader](#web-update-logReader):

**Sub-projects:**
* [deploy-cms-repo](#deploy-cms-repo):
* [git-reference-cvmfs](#git-reference-cvmfs):
* [git-mirror-repository](#git-mirror-repository):
* [web-update-cmssdt-ib](#web-update-cmssdt-ib):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [web-update-logReader](#web-update-logReader):
* [auto-forward-port](#auto-forward-port):
* [update-cmssw-l2-histroy](#update-cmssw-l2-histroy):

**Triggers from:** []


**Periodic builds:**
```bash
H */6 * * *
```

---

## [auto-forward-port](https://cmssdt.cern.ch/jenkins/job/auto-forward-port)

**Description:** This is triggered by github webhook for each cmssw/cmsdist branch merge event.
This is just a place holder job to trigger one sub-job per destionation branch for which the forward porting should be done.
If this fails then this means that one of its sub-job failed. There is no need to re-try this job. Retry the failed sub-jobs only.

**Project is `enabled`.**

**Upstream projects:**
* [github-push-hook](#github-push-hook):

**Downstream projects:**
* [auto-forward-port-branch](#auto-forward-port-branch):

**Sub-projects:**
* [auto-forward-port-branch](#auto-forward-port-branch):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [auto-forward-port-branch](https://cmssdt.cern.ch/jenkins/job/auto-forward-port-branch)

**Description:** This job forward ports git changes from one branch to another. If it fails due to network of github related issues then just re-try it.
Most of the times this job fails due to merge conflicts e.g. cmsdist master branch has different version of root as compare of rootmaster
rootnext branch. If merge conflicts are just the version differences, then re-build the job with "STRATEGY=ours" as parameter, but if there
are complex conflicts then better to resolve the issue by hand and directly push changes to github

**Project is `enabled`.**

**Upstream projects:**
* [auto-forward-port](#auto-forward-port):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-containers-checks-tags](https://cmssdt.cern.ch/jenkins/job/cms-containers-checks-tags)

**Description:** This project search for tags.yaml files in cms-sw/cms-docker repostory and create new image tags if needed

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):
* [github-push-hook](#github-push-hook):

**Downstream projects:**
* [cms-tag-container](#cms-tag-container):

**Sub-projects:**
* [cms-tag-container](#cms-tag-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-tag-container](https://cmssdt.cern.ch/jenkins/job/cms-tag-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cms-containers-checks-tags](#cms-containers-checks-tags):

**Downstream projects:**

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

## [git-reference-cvmfs](https://cmssdt.cern.ch/jenkins/job/git-reference-cvmfs)

**Description:** Create GIT Reference for cms-sw/cmssw repository in /cvmfs/cms-ci.cern.ch/git/cms-sw.
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

## [update-cmssw-l2-histroy](https://cmssdt.cern.ch/jenkins/job/update-cmssw-l2-histroy)

**Description:** None

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
* [github-push-hook](#github-push-hook):

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

## [build-release](https://cmssdt.cern.ch/jenkins/job/build-release)

**Description:** This job actually builds a release.
It is triggered by cms-bot after the <a href="https://github.com/cms-sw/cmssw/issues?q=label%3Arelease-notes-requested">Release build Issue</a> is approved by the release manager.
<br/>
<ul>
  <li> In case the job fails:<br/>
Depending on the type of failure, most of the time re-try works. In some cases (specially for aarch64 builds), it fails due to disk quota issues 
as one of the aarch64 machine does not have enought disk. In that case, one needs to login to the corresponding aarch64 machine and cleanup old/unused stuff and then re-try this job.
  <li> In case there is a build error in a release:<br/>
It can happen that the job succeed, but there have been build errors that the bot reports in the corresponding issue.
    In this case, the <it>Rebuild</it> button can be used to re-trigger the build. The bot will automatically remove the build-error labels and inform that a new build has been started.
</ul>

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

**Description:** This job deletes the release build areas after three days.

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

## [upload-release-setup](https://cmssdt.cern.ch/jenkins/job/upload-release-setup)

**Description:** This job uploads a release on cmsrep server once approved by release manager.

**Project is `enabled`.**

**Upstream projects:**
* [query-build-release-issues](#query-build-release-issues):

**Downstream projects:**
* [upload-release](#upload-release):

**Sub-projects:**
* [upload-release](#upload-release):

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
* [update-release-map](#update-release-map):

**Sub-projects:**
* [update-release-map](#update-release-map):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [ib-run-cfipython](#ib-run-cfipython):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-fwlite](https://cmssdt.cern.ch/jenkins/job/build-fwlite)

**Description:** This job builds a CMSSW_X_Y_Z_FWLITE release based on an existing CMSSW_X_Y_Z release. CMSSW_X_Y_Z should be already build/uploaded before building its FWLITE version.

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

## [cvmfs-cms-install-cms](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-cms)

**Description:** Job to install (test) releases (and IBs) once the upload is completed.
The job should be triggered by upstream job upload-release.
It's purpose is to only trigger cms-install-package with the same argument
it would get from upload-release job, but without using upload-release instance (it's just a trigger job for now)

**Project is `enabled`.**

**Upstream projects:**
* [cms-build-package](#cms-build-package):
* [cmsrep-webhook](#cmsrep-webhook):
* [update-release-map](#update-release-map):

**Downstream projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Sub-projects:**
* [cvmfs-cms-install-package](#cvmfs-cms-install-package):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-install-package](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-package)

**Description:** This job installs packages using cmspkg tool
To be used for - CRAB3, PHEDEX, spacemon-client, python, releases(cmssw), cms-common
Triggered by webhook

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):

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
* [update-release-map](#update-release-map):

**Downstream projects:**
* [dxr-cmssw-index](#dxr-cmssw-index):
* [lxr-generate-index](#lxr-generate-index):

**Sub-projects:**
* [lxr-generate-index](#lxr-generate-index):
* [dxr-cmssw-index](#dxr-cmssw-index):

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
* [ib-run-cfipython](#ib-run-cfipython):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [lxr-generate-index](https://cmssdt.cern.ch/jenkins/job/lxr-generate-index)

**Description:** This job sets modification timestamp of CMSSW source code according to commit history before 
indexing it using LXR.<br>


LXR index files based on modification timestamp. `<code>git clone</code>` ,however, sets files timestamps 
to command's execution time. Without it, LXR would index every file, increasing jobs execution duration 
and database size.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-cfipython](#ib-run-cfipython):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [update-data-tag-on-pr-merge](https://cmssdt.cern.ch/jenkins/job/update-data-tag-on-pr-merge)

**Description:** This job creates new release and tag it on cms-data PR merge.
It also creates cmsdist PR with the new release tag 

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

