# [All](https://cmssdt.cern.ch/jenkins/view/All)

**View description:** This view contains all jobs.

**View type:** All

---

# Projects:

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

## [backport-pull-request](https://cmssdt.cern.ch/jenkins/job/backport-pull-request)

**Description:** Manually executed job for backporting pull requests given the repo name, the branch for which the PR should be created and the PR to be backported.

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

## [build-any-ib](https://cmssdt.cern.ch/jenkins/job/build-any-ib)

**Description:** This jobs starts an Integration Build (IB). Base on state of <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a>/<a href="https://github.com/cms-sw/cmssw">CMSSW</a> git repositories, it builds either a full release or patch release.
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

<ul>
  <li>
    <b>Q:</b> What to do if it fails?
  </li>
  <li>
    <b>A:</b> If it fails due to network/github issues then just re-try it, but if it fails to build then we need to understand the build issues before retry.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [build-fwlite-ib](#build-fwlite-ib):
* [ib-build-logs](#ib-build-logs):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):
* [process-external-elastic-stats](#process-external-elastic-stats):

**Sub-projects:**
* [ib-install-cvmfs,ib-install-cvmfs-gateway](#ib-install-cvmfs,ib-install-cvmfs-gateway):
* [ib-build-logs,process-external-elastic-stats](#ib-build-logs,process-external-elastic-stats):
* [build-fwlite-ib](#build-fwlite-ib):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-docker-container](https://cmssdt.cern.ch/jenkins/job/build-docker-container)

**Description:** This job builds container images and uploads them to dockerhub.<br/>
<br/>
Containers are built when either their base image is updated or if changes were made to dockerfile.<br/>
Failures may arise from the changes in the base image. In this case, the best approach is to log into the machine, reproduce the issue
and try to adapt the dokerfile accordingly (e.g., changing dependencies, ordering, etc).<br/>
<br/>
If the job fails due to a glitch in the infrastructure, retry should work. If the container image is changed, we need to retrigger this job from check-docker-container job (so that the correct checksum is passed to build-docker-container job).
<br/>
<br/>
<br/>
Since the built container images are left on the machine, this job can also fail due to disk full.<br/>
There is a separate jenkins job (clean-build-docker-machine) cleaning the images left on the device that runs once a week. In any case, one can always log into the machine and run the docker cleanup as follows:<br/>
<br/>
$ docker image prune<br/>
$ docker system prune --volumes<br/>
<br/>
If the ./singularity folder is big enough ($ du -hs /build/cmsbld/jenkins/workspace/.singularity), it can be also removed.<br/>




**Project is `enabled`.**

**Upstream projects:**
* [check-docker-container](#check-docker-container):

**Downstream projects:**
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [run-container-tests](#run-container-tests):
* [test-containter-singularity](#test-containter-singularity):

**Sub-projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [test-containter-singularity](#test-containter-singularity):
* [run-container-tests](#run-container-tests):
* [cms-containers-checks-tags](#cms-containers-checks-tags):

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

## [build-fwlite-ib](https://cmssdt.cern.ch/jenkins/job/build-fwlite-ib)

**Description:** This job is responsible for building FWLITE release for each Integration Build (IB). 
Results of this build can be seen via <a href="https://cmssdt.cern.ch/SDT/">CMSSDT</a> 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a> 
<a href="https://cmssdt.cern.ch/SDT/html/showIB.html">(old page)</a>.

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [cms-spack-ib](#cms-spack-ib):

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

## [check-cms-container-certificates](https://cmssdt.cern.ch/jenkins/job/check-cms-container-certificates)

**Description:** This job checks for HOST certificate in cmssw/cms:rhelX images, and fail if host certificate is going to expire in less than CERT_EXPIRY_DAYS days.<br/>
In such case, we need to check if there is already an updated osg-ca-certs package available and rebuild the container.

**Project is `enabled`.**

**Upstream projects:**
* [check-cms-container-certificates](#check-cms-container-certificates):

**Downstream projects:**
* [check-cms-container-certificates](#check-cms-container-certificates):

**Sub-projects:**
* [check-cms-container-certificates](#check-cms-container-certificates):

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
```

---

## [check-cmsdev-disk](https://cmssdt.cern.ch/jenkins/job/check-cmsdev-disk)

**Description:** This job cleans up disk space on cmsdev machines.

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

## [check-cvmfs-releases-map](https://cmssdt.cern.ch/jenkins/job/check-cvmfs-releases-map)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-update-releases-map](#cvmfs-cms-update-releases-map):

**Sub-projects:**
* [cvmfs-cms-update-releases-map](#cvmfs-cms-update-releases-map):

**Triggers from:** []


**Periodic builds:**
```bash
H H/4 * * *
```

---

## [check-docker](https://cmssdt.cern.ch/jenkins/job/check-docker)

**Description:** This job connects to the slave and checks if docker service is useable.<br/>
Job can fail for three reasons:<br/>
1. user is not in docker group<br/>
2. docker service is not running on the machine<br/>
3. docker daemon reports that there isn't space in the machine ("no space left on device").<br/>

If machine is in our control, we should take the appropriate action (e.g. login into the machine and manually run the ssh command), but if machine is in CERN IT control (e.g OpenLab machines), we should open a SNOW ticket.
<br>
In case of no space on the device, one can manually run the job clean-check-docker indicating the name of the machine as an input parameter.

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

## [check-docker-container](https://cmssdt.cern.ch/jenkins/job/check-docker-container)

**Description:** This job checks for changes in the parent image. If there are changes, it triggers the `build-docker-container` job so that our based image is updated and uploaded to the registry.

**Project is `enabled`.**

**Upstream projects:**
* [cms-auto-build-container](#cms-auto-build-container):

**Downstream projects:**
* [build-docker-container](#build-docker-container):

**Sub-projects:**
* [build-docker-container](#build-docker-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [check-pending-job](https://cmssdt.cern.ch/jenkins/job/check-pending-job)

**Description:** <pre>The project checks for a running job and shows the status of process running on a remote machine.
This can be useful to see if any process is handing and kill it. To run this job
- Copy the url of a running job e.g.
  - https://cmssdt.cern.ch/jenkins/job/ib-run-relvals/243936/
  - https://cmssdt.cern.ch/jenkins/job/ib-run-relvals/243936/console
- Start the job with JOB_URL=url-of-a-running-job
- Check the outout and see if any process is running for too long and should be killed?
- If a process should be killed then return the job with KILL_PID
</pre>

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

## [check-unused-cmsdist-packages](https://cmssdt.cern.ch/jenkins/job/check-unused-cmsdist-packages)

**Description:** This job check for unused cmsdist files so that one can do the cleanup.

**Project is `enabled`.**

**Upstream projects:**
* [check-unused-cmsdist-packages](#check-unused-cmsdist-packages):

**Downstream projects:**
* [check-unused-cmsdist-packages](#check-unused-cmsdist-packages):

**Sub-projects:**
* [check-unused-cmsdist-packages](#check-unused-cmsdist-packages):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [check-zombie](https://cmssdt.cern.ch/jenkins/job/check-zombie)

**Description:** Connects to the slave and look for runaway process. This job fails when it finds such processes.<br/>
In case of failure, we need to check the runaway process list (e.g. see the job log) and make sure that these processes are really runaway (e.g. cmsRun jobs running with parent PID 1).
If all looks good, then one can restart the job with KILL_HANGING_PROCESSES=true.
<br>
<br>
Note: A runaway process is a process that enters an infinite loop and spawns new processes.

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

## [clean-build-docker-container](https://cmssdt.cern.ch/jenkins/job/clean-build-docker-container)

**Description:** This job prevents running out of disk in the machines used to build container images (e.g., the ones used for running the build-docker-container job).

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 9 * * 1
```

---

## [clean-check-docker](https://cmssdt.cern.ch/jenkins/job/clean-check-docker)

**Description:** This job cleans the indicated machine when docker daemon reports errors of the type "no space left on device" in job check-docker.
<br>
It is necessay to indicate the machine name as an input parameter.

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

## [cleanup-cmsrep](https://cmssdt.cern.ch/jenkins/job/cleanup-cmsrep)

**Description:** This cleans up old cms.weekN.PR_* repositories from cmsrep.cern.ch server.

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cleanup-cmssdt](https://cmssdt.cern.ch/jenkins/job/cleanup-cmssdt)

**Description:** This job cleans up disk space on cmssdt.

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

## [cleanup-cvmfs-ci](https://cmssdt.cern.ch/jenkins/job/cleanup-cvmfs-ci)

**Description:** This job cleans up old cms.weekN.PR_* repositories from cmsrep.cern.ch server.

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cleanup-docker-tags](https://cmssdt.cern.ch/jenkins/job/cleanup-docker-tags)

**Description:** This job removes outdated tags from docker repository.

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

## [cleanup-release-build](https://cmssdt.cern.ch/jenkins/job/cleanup-release-build)

**Description:** Connect to selected slave and cleans the auto-builds directories

**Project is `enabled`.**

**Upstream projects:**
* [workspace-cleanup-slave](#workspace-cleanup-slave):

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

## [cms-auto-build-container](https://cmssdt.cern.ch/jenkins/job/cms-auto-build-container)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [check-docker-container](#check-docker-container):

**Sub-projects:**
* [check-docker-container](#check-docker-container):

**Triggers from:** []


**Periodic builds:**
```bash
H 10 * * *
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

## [cms-build-package](https://cmssdt.cern.ch/jenkins/job/cms-build-package)

**Description:** This job builds a cmssw external package ( e.g. crab , SCRAMV1 ) using the master cmsdist/pkgtools branches.
It then trigger the cvmfs installation job to install the newly build packages.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):

**Sub-projects:**
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):

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

## [cms-containers-run-cmssw-test](https://cmssdt.cern.ch/jenkins/job/cms-containers-run-cmssw-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):
* [cms-containers-schedule-cmssw-test](#cms-containers-schedule-cmssw-test):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-containers-schedule-cmssw-test](https://cmssdt.cern.ch/jenkins/job/cms-containers-schedule-cmssw-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):

**Sub-projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):

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

## [cms-spack-build-singularity](https://cmssdt.cern.ch/jenkins/job/cms-spack-build-singularity)

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

## [cms-spack-clean](https://cmssdt.cern.ch/jenkins/job/cms-spack-clean)

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

## [cms-spack-ib](https://cmssdt.cern.ch/jenkins/job/cms-spack-ib)

**Description:** This jobs starts an Integration Build (IB). Base on state of <a href="https://github.com/cms-sw/cmsdist">CMSDIST</a>/<a href="https://github.com/cms-sw/cmssw">CMSSW</a> git repositories, it builds either a full release or patch release.
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

<ul>
  <li>
    <b>Q:</b> What to do if it fails?
  </li>
  <li>
    <b>A:</b> If it fails due to network/github issues then just re-try it, but if it fails to build then we need to understand the build issues before retry.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [build-fwlite-ib](#build-fwlite-ib):
* [ib-build-logs](#ib-build-logs):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):
* [process-external-elastic-stats](#process-external-elastic-stats):

**Sub-projects:**
* [ib-install-cvmfs,ib-install-cvmfs-gateway](#ib-install-cvmfs,ib-install-cvmfs-gateway):
* [ib-build-logs,process-external-elastic-stats](#ib-build-logs,process-external-elastic-stats):
* [build-fwlite-ib](#build-fwlite-ib):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cms-spack-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/cms-spack-install-cvmfs)

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

## [cmsbuild-access](https://cmssdt.cern.ch/jenkins/job/cmsbuild-access)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 14 * * *
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

## [cmsrep-webhook](https://cmssdt.cern.ch/jenkins/job/cmsrep-webhook)

**Description:** This is cms bot job which is triggered by github webhooks ( https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook ) for every valid comment added to github PRs.
Also it runsevery 30mins to make sure any webhooks were not missed. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cvmfs-install-pr](#cvmfs-install-pr):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Sub-projects:**
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [ib-install-cvmfs,ib-install-cvmfs-gateway](#ib-install-cvmfs,ib-install-cvmfs-gateway):
* [cvmfs-install-pr](#cvmfs-install-pr):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmssw-afs-eos-comparison](https://cmssdt.cern.ch/jenkins/job/cmssw-afs-eos-comparison)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-additional-tests](#ib-schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cmssw-container](https://cmssdt.cern.ch/jenkins/job/cmssw-container)

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

**Description:** Download the files of the baseline IB and compare them with the results of the ones of a pull request.
Rate of failure of this job is very low and when failed then just re-try it and either delete the failed job or update the build information that it has been re-tried.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-pr-relvals](#ib-run-pr-relvals):

**Downstream projects:**
* [cms-bot](#cms-bot):

**Sub-projects:**
* [cms-bot](#cms-bot):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [crab-cleanup](https://cmssdt.cern.ch/jenkins/job/crab-cleanup)

**Description:** This job runs once a day to clean up the /eos/cms/store/user/cmsbot/CRAB_PrivateMC directory e.g. delete every thing older than X days.<br/>
In case of failure , just re-run it.

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

## [cvmfs-check-cuda-compatible-runtime](https://cmssdt.cern.ch/jenkins/job/cvmfs-check-cuda-compatible-runtime)

**Description:** This job checks and updates cuda-compatible-runtime. This is used by CMS pilot jobs to find available gpu on the worker node.<br/>

Requestsed by marco.mascheroni@cern.ch and andrea.bocci@cern.ch


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-deploy-cuda-compatible-runtime](#cvmfs-cms-deploy-cuda-compatible-runtime):

**Sub-projects:**
* [cvmfs-cms-deploy-cuda-compatible-runtime](#cvmfs-cms-deploy-cuda-compatible-runtime):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-ci-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-ci-gc)

**Description:** This runs CVMFS GC (once a week)

**Project is `disabled`.**

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

## [cvmfs-cms-check-and-update-cmssw-git-mirror](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-cmssw-git-mirror)

**Description:** This job checks and updates the cmssw git mirror daily and monthly based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cvmfs_update_cmssw_git_mirror_v3.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
```

---

## [cvmfs-cms-check-and-update-gridpacks](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gridpacks)

**Description:** This job checks and updates gridpacks based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_rsync_generator_package_from_eos_individual.sh


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Sub-projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [cvmfs-cms-check-and-update-lhapdf](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-lhapdf)

**Description:** This job checks and updates lhapdf based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_download_lhapdf.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
```

---

## [cvmfs-cms-check-and-update-report](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-report)

**Description:** This job reports status of upstream projects, siteconf and gridpacks.


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-and-update-gridpacks](#cvmfs-cms-check-and-update-gridpacks):
* [cvmfs-cms-check-and-update-siteconf](#cvmfs-cms-check-and-update-siteconf):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-check-and-update-siteconf](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-siteconf)

**Description:** This job checks and updates siteconf based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cvmfs_check_and_update_siteconf.sh



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Sub-projects:**
* [cvmfs-cms-check-and-update-report](#cvmfs-cms-check-and-update-report):

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [cvmfs-cms-crab-symlink](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-crab-symlink)

**Description:** This changes the /cvmfs/cms.cern.ch/common/crab symlink to point to either crab-pre, crab-prod or crab-dev.<br/>

<b>Note any cmssw release which installs a different crab version will revert the symlink back to crab-prod</b><br/>

Note that this only changes the /cvmfs/cms.cern.ch/common/crab symlink. For crab python api, one still needs to source /cvmfs/cms.cern.ch/common/crab-setup.sh prod|pre|dev


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

## [cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration)

**Description:** This deploys a gitlab repository under /cvmfs/cms.cern.ch/rsync/repository/name<br/>
- POG scale factors on CVMFS: Requested by XPOG silvio.donato@cern.ch

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-rsync-gitlab-repo](#cvmfs-cms-rsync-gitlab-repo):

**Sub-projects:**
* [cvmfs-cms-rsync-gitlab-repo](#cvmfs-cms-rsync-gitlab-repo):

**Triggers from:** []


**Periodic builds:**
```bash
5 5 * * *
```

---

## [cvmfs-cms-deploy-cuda-compatible-runtime](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-cuda-compatible-runtime)

**Description:** This job checks and updates cuda-compatible-runtime. This is used by CMS pilot jobs to find available gpu on the worker node.<br/>

Requestsed by marco.mascheroni@cern.ch and andrea.bocci@cern.ch


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-check-cuda-compatible-runtime](#cvmfs-check-cuda-compatible-runtime):

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

## [cvmfs-cms-install-common](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-common)

**Description:** Trigger the installation of new production architecture for CMS or reinstall cms-common new revision.<br/>
- Production architecture if obtained via <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">config.map</a><br/>
This job is triggered by <a href="https://cmssdt.cern.ch/jenkins/job/cmsrep-webhook">cmsrep-webhook</a> which should pass the cms-common revision and architecture.

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

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

## [cvmfs-cms-install-COMP-python](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-COMP-python)

**Description:** Job to install python whenever there is a new version pushed on cmsrep.cern.ch <br>
Install path is /cvmfs/${CVMFS_REPOSITORY} + COMP install dir (boostraped for comp)

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

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

## [cvmfs-cms-install-rucio](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-install-rucio)

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

## [cvmfs-cms-rsync-gitlab-repo](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-rsync-gitlab-repo)

**Description:** This deploys a gitlab repository under /cvmfs/cms.cern.ch/rsync/repository/name<br/>


**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration](#cvmfs-cms-deploy-cms-nanoAOD-jsonpog-integration):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-stale-lock](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-stale-lock)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H */2 * * *
```

---

## [cvmfs-cms-test](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-test)

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

## [cvmfs-cms-update-ca-crl](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-update-ca-crl)

**Description:** This job updates CA/CRL under /cvmfs/cms.cern.ch/grid/etc/grid-security as in the following script:
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/update_ca_crl.sh

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H */6 * * *
```

---

## [cvmfs-cms-update-releases-map](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-update-releases-map)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [check-cvmfs-releases-map](#check-cvmfs-releases-map):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-deploy-artifacts](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-artifacts)

**Description:** Copy baseline results from cmssdt for an IB

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-baseline](#ib-run-baseline):
* [ib-run-pr-baseline](#ib-run-pr-baseline):

**Downstream projects:**
* [cvmfs-publish-artifacts](#cvmfs-publish-artifacts):

**Sub-projects:**
* [cvmfs-publish-artifacts](#cvmfs-publish-artifacts):

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
* [cvmfs-run-gc](#cvmfs-run-gc):

**Sub-projects:**
* [cvmfs-run-gc](#cvmfs-run-gc):

**Triggers from:** []


**Periodic builds:**
```bash
#Run once on Thursday at 23h05
H 19  * *  2
```

---

## [cvmfs-install-pr](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-pr)

**Description:** To install PR externals

**Project is `enabled`.**

**Upstream projects:**
* [cmsrep-webhook](#cmsrep-webhook):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-install-shared-pip-package](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-shared-pip-package)

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

## [cvmfs-list-catelogs](https://cmssdt.cern.ch/jenkins/job/cvmfs-list-catelogs)

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

## [cvmfs-publish-artifacts](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-artifacts)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-run-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-run-gc)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-gc](#cvmfs-gc):

**Downstream projects:**
* [cvmfs-run-gw-gc](#cvmfs-run-gw-gc):

**Sub-projects:**
* [cvmfs-run-gw-gc](#cvmfs-run-gw-gc):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-run-gw-gc](https://cmssdt.cern.ch/jenkins/job/cvmfs-run-gw-gc)

**Description:** This runs CVMFS GC on the Gateway, make sure that top level path "/" has a lease.

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-run-gc](#cvmfs-run-gc):

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

## [das-query](https://cmssdt.cern.ch/jenkins/job/das-query)

**Description:** Job to run das client and cache the results in github to be used by IBs.
Ignore any failed job if a newer job has succeeded.
Retry if last run is failed.

**Project is `enabled`.**

**Upstream projects:**
* [das-query](#das-query):

**Downstream projects:**
* [das-query](#das-query):

**Sub-projects:**
* [das-query](#das-query):

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

## [dxr-cmssw-cleanup](https://cmssdt.cern.ch/jenkins/job/dxr-cmssw-cleanup)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 7 * * *
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

## [es-close-indexes](https://cmssdt.cern.ch/jenkins/job/es-close-indexes)

**Description:** This job keeps last 6 weeks (1.5 months) of data in Elasticsearch open, and it closes older indexes (archive it).
We do not care about older data. By doing it we make Elasticsearch faster. 

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 0  * *  0
```

---

## [es-cmssw-afs-eos](https://cmssdt.cern.ch/jenkins/job/es-cmssw-afs-eos)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
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

## [gh-teams](https://cmssdt.cern.ch/jenkins/job/gh-teams)

**Description:** printing some python file	

**Project is `enabled`.**

**Upstream projects:**
* [gh-teams](#gh-teams):

**Downstream projects:**
* [gh-teams](#gh-teams):

**Sub-projects:**
* [gh-teams](#gh-teams):

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

## [github-hooks](https://cmssdt.cern.ch/jenkins/job/github-hooks)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Project is `enabled`.**

**Upstream projects:**
* [github-hooks](#github-hooks):

**Downstream projects:**
* [github-hooks](#github-hooks):

**Sub-projects:**
* [github-hooks](#github-hooks):

**Triggers from:** []


**Periodic builds:**
```bash
H 0 * * *
```

---

## [github-labels](https://cmssdt.cern.ch/jenkins/job/github-labels)

**Description:** Adds and configures web hooks in github repositories. The web hooks are then used to send some events to a specified url
and then a jenkins job is triggered based on the information passed from the web hook , as jenkins parameters. 

**Project is `enabled`.**

**Upstream projects:**
* [github-labels](#github-labels):

**Downstream projects:**
* [github-labels](#github-labels):

**Sub-projects:**
* [github-labels](#github-labels):

**Triggers from:** []


**Periodic builds:**
```bash
H 1 * * *
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
* [grid-webhook](#grid-webhook):

**Sub-projects:**
* [grid-webhook](#grid-webhook):

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
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

## [ib-build-logs](https://cmssdt.cern.ch/jenkins/job/ib-build-logs)

**Description:** It is build periodically (H/30 * * * *). Runs on cmssdt. Projects to build: update-github-pages

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [build-fwlite-ib](#build-fwlite-ib):
* [cms-spack-ib](#cms-spack-ib):

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

## [ib-check-baseline-requests](https://cmssdt.cern.ch/jenkins/job/ib-check-baseline-requests)

**Description:** This jobs look for on demand baseline generation requests (made by ib-run-pr-tests job) and start the baseline generation job ( if not already started).

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-run-baseline](#ib-run-baseline):

**Sub-projects:**
* [ib-run-baseline](#ib-run-baseline):

**Triggers from:** []


**Periodic builds:**
```bash
H/3 * * * *
```

---

## [ib-check-siteconf](https://cmssdt.cern.ch/jenkins/job/ib-check-siteconf)

**Description:** This check for /cvmfs/REPO/SITECONF contents and triggers ib-install-siteconf (for each repo) if https://github.com/cms-sw/siteconf has updates.
Thsi jobs runs every hour

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-install-siteconf](#ib-install-siteconf):

**Sub-projects:**
* [ib-install-siteconf](#ib-install-siteconf):

**Triggers from:** []


**Periodic builds:**
```bash
H * * * *
```

---

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch. As this job runs on the CVMFS Stratum 0, so only one job can run at a time.
Sometimes ( specially IBs for non-86-64 archs) are stuck and do nothing. In that case better to kill the job and re-try it.
This gives chance to other IBs to get installed and at the end the re-tried job will re-run. 

There is no automatic re-try setup for this job. It rarely fails but in case it fails then just re-try the failed job and
either delete the failed job instance or update the "Build information" and mentioned that it has been re-tired. This allows others to not re-try it.


**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [cms-spack-ib](#cms-spack-ib):
* [cmsrep-webhook](#cmsrep-webhook):
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

## [ib-install-cvmfs-gateway](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs-gateway)

**Description:** Test job to install IBs in parallel (cvmfs gateway).

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [cms-spack-ib](#cms-spack-ib):
* [cmsrep-webhook](#cmsrep-webhook):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Sub-projects:**
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-install-siteconf](https://cmssdt.cern.ch/jenkins/job/ib-install-siteconf)

**Description:** Update the contents of/cvmfs/REPO/SITECONF from https://github.com/cms-sw/siteconf

**Project is `enabled`.**

**Upstream projects:**
* [ib-check-siteconf](#ib-check-siteconf):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-monitor-crab](https://cmssdt.cern.ch/jenkins/job/ib-monitor-crab)

**Description:** This job is triggered by `ib-run-crab` or `ib-run-pr-crab` once a test analysis is submitted to CRAB. It monitors the status of the CRAB job by using curl calls until the job finishes.
<br>
Finally, it generates a status file that is visible in the IB page (https://cmssdt.cern.ch/SDT/jenkins-artifacts/ib-run-crab).

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-crab](#ib-run-crab):
* [ib-run-pr-crab](#ib-run-pr-crab):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-additional-tests](https://cmssdt.cern.ch/jenkins/job/ib-run-additional-tests)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule-additional-tests](#ib-schedule-additional-tests):

**Downstream projects:**

**Sub-projects:**
* [ib-run-${ADDITIONAL_TEST_NAME}](#ib-run-${ADDITIONAL_TEST_NAME}):

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

## [ib-run-baseline](https://cmssdt.cern.ch/jenkins/job/ib-run-baseline)

**Description:** This job generates the IB baseline. It is two phase job<br/>
- First it runs on any suitable node and look for workflows for which the baseline should be generated. It then re-run itself with the list of workflows and build an upload the actual baseline.<br/>
- In case of failure, just retry this job (Unless there are network/github issues)

**Project is `enabled`.**

**Upstream projects:**
* [ib-check-baseline-requests](#ib-check-baseline-requests):
* [ib-run-baseline](#ib-run-baseline):

**Downstream projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):
* [ib-run-baseline](#ib-run-baseline):

**Sub-projects:**
* [cvmfs-deploy-artifacts](#cvmfs-deploy-artifacts):
* [ib-run-baseline](#ib-run-baseline):

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

## [ib-run-crab](https://cmssdt.cern.ch/jenkins/job/ib-run-crab)

**Description:** This job integrates CRAB into the CI system.
<br>
<br>
Note: CRAB is the CMS Computing tool to submit CMSSW users' analysis jobs to distributed computing resources (https://twiki.cern.ch/twiki/bin/view/CMSPublic/SWGuideCrab).

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-crab](#ib-run-crab):

**Downstream projects:**
* [ib-monitor-crab](#ib-monitor-crab):
* [ib-run-crab](#ib-run-crab):

**Sub-projects:**
* [ib-monitor-crab](#ib-monitor-crab):
* [ib-run-crab](#ib-run-crab):

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

## [ib-run-gpu](https://cmssdt.cern.ch/jenkins/job/ib-run-gpu)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-run-qa](#ib-run-qa):

**Sub-projects:**
* [ib-run-qa](#ib-run-qa):

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
* [sync-profile-data](#sync-profile-data):

**Sub-projects:**

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

## [ib-run-pr-addon](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-addon)

**Description:** Build mutiple pull requests. 
Run cmssw addON (HLT tests)

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

## [ib-run-pr-baseline](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-baseline)

**Description:** None

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

## [ib-run-pr-crab](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-crab)

**Description:** PR Unit Test for CRAB updates.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-monitor-crab](#ib-monitor-crab):

**Sub-projects:**
* [ib-monitor-crab](#ib-monitor-crab):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-dasgoclient](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-dasgoclient)

**Description:** Job to run das client and cache the results in github to be used by IBs.
Ignore any failed job if a newer job has succeeded.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [lfn-to-ibeos](#lfn-to-ibeos):

**Sub-projects:**
* [lfn-to-ibeos](#lfn-to-ibeos):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-pr-external_checks](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-external_checks)

**Description:** Build mutiple pull requests. 
test cmssw externals packages static checks e.g. hardcoded build paths etc.




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

## [ib-run-pr-profiling](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-profiling)

**Description:** Build mutiple  a pull requests. 
Same puprose as `ib-any-integration`, just different script is called.




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

## [ib-run-pr-relvals](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-relvals)

**Description:** Build mutiple  a pull requests. 
Same puprose as `ib-any-integration`, just different script is called.




**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [lfn-to-ibeos](#lfn-to-ibeos):

**Sub-projects:**
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [lfn-to-ibeos](#lfn-to-ibeos):

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

## [ib-run-profiling](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling)

**Description:** Runs FastTimerService and Igprof on the RECO and PAT steps for high pileup workflow.

<ul>
  <li>
    If it fails, we should normally retry since IT used to kill this job.
  </li>  
</ul>



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [sync-profile-data](#sync-profile-data):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-profiling-gpu](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling-gpu)

**Description:** Runs FastTimerService and Igprof on the RECO and PAT steps for high pileup workflow.



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [sync-profile-data](#sync-profile-data):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-profiling-mem](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling-mem)

**Description:** Runs Igprof memory profiling on the RECO and PAT steps for high pileup workflow.

<ul>
  <li>
    If it fails, we should normally retry since IT used to kill this job.
  </li>  
</ul>



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [sync-profile-data](#sync-profile-data):

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

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-qa)

**Description:** Runs Quality Assurance (QA) test on IB. Results are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.<br>

Sometimes it can hang during scp copy / ssh. This failure can be found by looking for a gap of several hours in the log file during scp / ssh.<br>
If the job runs for more than several hours, the procedure is to login to build node, check which job is hanging and take the appropiate action, if necessary.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-gpu](#ib-run-gpu):
* [ib-validation](#ib-validation):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-relvals](https://cmssdt.cern.ch/jenkins/job/ib-run-relvals)

**Description:** The job runs release validations, as validations are separated on pieces (1of6 2of6 etc).<br>
It can fail due to connection issues (e.g. Remote call on machine-XYZ failed).<br>

Sometimes it can also hang during scp copy / ssh (which is usually the last job).
This failure can be found by looking for a gap of several hours in the log file where the Jenkins job is trying to finish the last test job.

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

## [ib-schedule-additional-tests](https://cmssdt.cern.ch/jenkins/job/ib-schedule-additional-tests)

**Description:** Wrapper project to schedule aditonal test such as Flawfinder, Lizard, IgProf, etc.

**Project is `enabled`.**

**Upstream projects:**
* [ib-validation](#ib-validation):

**Downstream projects:**
* [cmssw-afs-eos-comparison](#cmssw-afs-eos-comparison):
* [ib-run-additional-tests](#ib-run-additional-tests):

**Sub-projects:**
* [ib-run-additional-tests](#ib-run-additional-tests):
* [cmssw-afs-eos-comparison](#cmssw-afs-eos-comparison):

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

## [ib-tag-and-schdule](https://cmssdt.cern.ch/jenkins/job/ib-tag-and-schdule)

**Description:** This job tags and schedules all the IBs.<br/>
It reads the <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a> to find all available CMSSW release cycles and tag them in github.
Once tags is done then it triggers 'build-any-ib' sub-job to actually build IBs for all possible architectures (mentioned in <a href="https://raw.githubusercontent.com/cms-sw/cms-bot/master/config.map">cms-bot/config.map</a>).
For Developement IB, it also triggers the generation of <a href="https://cmssdt.cern.ch/lxr">LXR indexes</a>

For Sunday's 00h IBs, it also resets the CMSREP weekly repositories by building a dummy package and uploading it to cms.weekN. It also 
then triggers 'ib-install-cvmfs' sub-job to get the new cms.weekN deployed on the /cvmfs/cms-ib.cern.ch

This job re-tries itself on failure. So there is no need to re-try it manually (unless all re-tries failed).

**Project is `enabled`.**

**Upstream projects:**
* [ib-schedule](#ib-schedule):

**Downstream projects:**
* [build-any-ib](#build-any-ib):
* [cleanup-cmsrep](#cleanup-cmsrep):
* [cleanup-cvmfs-ci](#cleanup-cvmfs-ci):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-install-cvmfs-gateway](#ib-install-cvmfs-gateway):

**Sub-projects:**
* [build-any-ib](#build-any-ib):
* [ib-install-cvmfs,ib-install-cvmfs-gateway](#ib-install-cvmfs,ib-install-cvmfs-gateway):
* [cleanup-cmsrep,cleanup-cvmfs-ci](#cleanup-cmsrep,cleanup-cvmfs-ci):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-validation](https://cmssdt.cern.ch/jenkins/job/ib-validation)

**Description:** This job waits for the recently installed IB on CVMFS to be visible on CERN Stratum 1.
Once the IB is available on Stratum 1 then it triggers various validation jobs.
If this job fails or timeout then just re-run it. Failure rate is very low but on 
Wednesday CERN IT runs CVMFS Stratum 1 garbage collection which can add extra few hours
delay and may cause this job to timeout.

**Project is `enabled`.**

**Upstream projects:**
* [ib-install-cvmfs](#ib-install-cvmfs):

**Downstream projects:**
* [ib-run-addons](#ib-run-addons):
* [ib-run-qa](#ib-run-qa):
* [ib-run-relvals](#ib-run-relvals):
* [ib-schedule-additional-tests](#ib-schedule-additional-tests):
* [summary-of-merged-prs](#summary-of-merged-prs):

**Sub-projects:**
* [ib-run-addons](#ib-run-addons):
* [ib-run-qa ](#ib-run-qa ):
* [ib-run-relvals ](#ib-run-relvals ):
* [ib-schedule-additional-tests](#ib-schedule-additional-tests):
* [summary-of-merged-prs](#summary-of-merged-prs):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-add-job](https://cmssdt.cern.ch/jenkins/job/jenkins-add-job)

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

## [jenkins-auto-label-nodes](https://cmssdt.cern.ch/jenkins/job/jenkins-auto-label-nodes)

**Description:** This job is to start those nodes which only has LABEL set to auto-label.<br/>
This happens when jenkins is restart and labels are read from nodes/config.xml.<br/>
We need to make a initial connection to the slave to get its labels assigned.


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

## [jenkins-delete-node](https://cmssdt.cern.ch/jenkins/job/jenkins-delete-node)

**Description:** Deletes nodes from jenkins and then deletes it on openstack.

**Project is `enabled`.**

**Upstream projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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
H * * * *
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
* [jenkins-webhook](#jenkins-webhook):

**Sub-projects:**
* [jenkins-enable-jobs](#jenkins-enable-jobs):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):
* [jenkins-installation-trigger-test](#jenkins-installation-trigger-test):
* [jenkins-webhook](#jenkins-webhook):

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

## [jenkins-job-frequency](https://cmssdt.cern.ch/jenkins/job/jenkins-job-frequency)

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

## [jenkins-kill-job](https://cmssdt.cern.ch/jenkins/job/jenkins-kill-job)

**Description:** Kill a <b>specific</b> running job.

**Project is `enabled`.**

**Upstream projects:**
* [grid-make-node-available](#grid-make-node-available):

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

## [jenkins-search-release-build](https://cmssdt.cern.ch/jenkins/job/jenkins-search-release-build)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-search-release-build](#jenkins-search-release-build):

**Downstream projects:**
* [jenkins-search-release-build](#jenkins-search-release-build):

**Sub-projects:**
* [jenkins-search-release-build](#jenkins-search-release-build):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-test-bootstrap](https://cmssdt.cern.ch/jenkins/job/jenkins-test-bootstrap)

**Description:** Test new bootstrap for cmssw

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

## [jenkins-test-buggy-node](https://cmssdt.cern.ch/jenkins/job/jenkins-test-buggy-node)

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

## [jenkins-test-cmssw-bootstrap](https://cmssdt.cern.ch/jenkins/job/jenkins-test-cmssw-bootstrap)

**Description:** Test new bootstrap for cmssw

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

## [jenkins-test-code-format](https://cmssdt.cern.ch/jenkins/job/jenkins-test-code-format)

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

## [jenkins-test-container](https://cmssdt.cern.ch/jenkins/job/jenkins-test-container)

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

## [jenkins-test-docker_launcher](https://cmssdt.cern.ch/jenkins/job/jenkins-test-docker_launcher)

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

## [jenkins-test-dummyjob](https://cmssdt.cern.ch/jenkins/job/jenkins-test-dummyjob)

**Description:** Dummy job for testing purposes (@avalenzu)

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

## [jenkins-test-gpu](https://cmssdt.cern.ch/jenkins/job/jenkins-test-gpu)

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

## [jenkins-test-groovy-labels](https://cmssdt.cern.ch/jenkins/job/jenkins-test-groovy-labels)

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

## [jenkins-test-indirect-slave](https://cmssdt.cern.ch/jenkins/job/jenkins-test-indirect-slave)

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

## [jenkins-test-install-rucio](https://cmssdt.cern.ch/jenkins/job/jenkins-test-install-rucio)

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

## [jenkins-test-lxplus-future](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lxplus-future)

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

## [jenkins-test-parser](https://cmssdt.cern.ch/jenkins/job/jenkins-test-parser)

**Description:** avalenzu: debug

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-test-parser](#jenkins-test-parser):

**Downstream projects:**
* [jenkins-test-parser](#jenkins-test-parser):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash

```

---

## [jenkins-test-parser-monitor](https://cmssdt.cern.ch/jenkins/job/jenkins-test-parser-monitor)

**Description:** This job monitors parser retries.

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

## [jenkins-test-patch-checkout](https://cmssdt.cern.ch/jenkins/job/jenkins-test-patch-checkout)

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

## [jenkins-test-retry](https://cmssdt.cern.ch/jenkins/job/jenkins-test-retry)

**Description:** This job retries a build given the job name and the build number to retry.<br>
It copies the build parameters from the given build and adds a retry counter as an environmental variable to keep track of the number of retries (a maximum of 3 retries per build has been set). <br>
This job is automatically triggered by the job "jenkins-test-parser" when a build fails due to a known issue and a retry action is needed.<br>
This job is expected to fail if the same build has been retried more than 3 times. If it fails due to another issue, we need to take the appropiate action.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**
* [${JOB_TO_RETRY}](#${JOB_TO_RETRY}):

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
* [jenkins-test-slave](#jenkins-test-slave):

**Sub-projects:**
* [jenkins-test-slave](#jenkins-test-slave):

**Triggers from:** []


**Periodic builds:**
```bash
H H/8 * * *
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

## [jenkins-trigger-dynamic-job](https://cmssdt.cern.ch/jenkins/job/jenkins-trigger-dynamic-job)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [grid-make-node-available](#grid-make-node-available):

**Downstream projects:**

**Sub-projects:**
* [${JENKINS_DYNAMIC_JOB_NAME}](#${JENKINS_DYNAMIC_JOB_NAME}):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [jenkins-webhook](https://cmssdt.cern.ch/jenkins/job/jenkins-webhook)

**Description:** None

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
* [ib-run-pr-dasgoclient](#ib-run-pr-dasgoclient):
* [ib-run-pr-relvals](#ib-run-pr-relvals):
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

## [lxr-repair-table](https://cmssdt.cern.ch/jenkins/job/lxr-repair-table)

**Description:** Run this if there is any MySQL table to repair e.g. if lxr-remove-idex fails with error <br/>
ERROR 144 (HY000) at line 3: Table './lxr/lxr_usages' is marked as crashed and last (automatic?) repair failed<br/>
then run it with LXR_TABLE=lxr_usages

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
Not periodically build
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

## [nodes-sanity-check](https://cmssdt.cern.ch/jenkins/job/nodes-sanity-check)

**Description:** 

This job runs a check that makes sure /afs, /cvmfs, /cvmfs/cms.cern.ch, /cvmfs/cms-ci.cern.ch, /cvmfs/cms-ib.cern.ch, /cvmfs/grid.cern.ch and /cvmfs/unpacked.cern.ch are mounted and that singularity can start a container in the node. It runs on lxplus7, lxplus8 and lxplus9 considering the available hosts at the time of running and both aarch64 and ppc64le machines.<br>
<br>
If any of the checks fails, it sends an email notification and writes the node name into a blacklist. For lxplus nodes, this blacklist is checked before connecting any node to make sure Jenkins does not connect to a blacklisted node. For aarch64 and ppc64le machines, it takes the corresponding nodes offline.<br>
<br>
The blacklist is cleaned up for lxplus nodes if the tests run again successfully in any of the nodes or if the host is not in the list of available hosts anymore. The aarch64 and ppc64le nodes must be taken online manually after receiving the email notification and fixing the issue.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/30 * * * *
```

---

## [nodes-status-summary](https://cmssdt.cern.ch/jenkins/job/nodes-status-summary)

**Description:** This job checks the status of the Jenkins nodes every day to verify that none of them has been manually disconnected/or disconnected by CLI and not bring back online.<br>
It also notifies about the blacklisted nodes.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 16 * * *
```

---

## [openstack-add-jenkins-slave](https://cmssdt.cern.ch/jenkins/job/openstack-add-jenkins-slave)

**Description:** Find all hosts in an hostgroup and add them to jenkins

**Project is `enabled`.**

**Upstream projects:**
* [openstack-check-jenkins-slaves](#openstack-check-jenkins-slaves):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [openstack-check-jenkins-slaves](https://cmssdt.cern.ch/jenkins/job/openstack-check-jenkins-slaves)

**Description:** Find all hosts in an hostgroup and add then to jenkins

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [openstack-add-jenkins-slave](#openstack-add-jenkins-slave):

**Sub-projects:**
* [openstack-add-jenkins-slave](#openstack-add-jenkins-slave):

**Triggers from:** []


**Periodic builds:**
```bash
H * * * * 
```

---

## [openstack-create-vms](https://cmssdt.cern.ch/jenkins/job/openstack-create-vms)

**Description:** Create Openstack VMs for a selected hostgroup.
Node configuration is obtained from  https://github.com/cms-sw/cms-bot/tree/master/openstack/hg/<host/group/name>.
In order to create a new VM please do
- provide the name of VM
- select the Forman Host group for the node.
  If for any reason, you have to change any parameters e.g different VM size, or attach extra volume then just set those in the job parameters.

**Project is `enabled`.**

**Upstream projects:**
* [openstack-create-vms](#openstack-create-vms):

**Downstream projects:**
* [openstack-create-vms](#openstack-create-vms):
* [openstack-delete-vms](#openstack-delete-vms):
* [openstack-delete-volume](#openstack-delete-volume):

**Sub-projects:**
* [openstack-create-vms](#openstack-create-vms):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [openstack-delete-vm-foreman](https://cmssdt.cern.ch/jenkins/job/openstack-delete-vm-foreman)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [openstack-delete-vms](https://cmssdt.cern.ch/jenkins/job/openstack-delete-vms)

**Description:** Job to delete openstack instances providing only the name.
<b>Only kills builder nodes (cmsbuild)</b>

**Project is `enabled`.**

**Upstream projects:**
* [openstack-create-vms](#openstack-create-vms):
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**
* [jenkins-delete-node](#jenkins-delete-node):
* [openstack-delete-vm-foreman](#openstack-delete-vm-foreman):
* [openstack-delete-vms](#openstack-delete-vms):
* [openstack-delete-volume](#openstack-delete-volume):

**Sub-projects:**
* [openstack-delete-vms](#openstack-delete-vms):
* [openstack-delete-vm-foreman ](#openstack-delete-vm-foreman ):
* [openstack-delete-volume](#openstack-delete-volume):
* [jenkins-delete-node](#jenkins-delete-node):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [openstack-delete-volume](https://cmssdt.cern.ch/jenkins/job/openstack-delete-volume)

**Description:** Job to delete openstack instances providing only the name

**Project is `enabled`.**

**Upstream projects:**
* [openstack-create-vms](#openstack-create-vms):
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [openstack-set-property](https://cmssdt.cern.ch/jenkins/job/openstack-set-property)

**Description:** Job to delete openstack instances providing only the name

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

## [openstack-show-flavor](https://cmssdt.cern.ch/jenkins/job/openstack-show-flavor)

**Description:** Job to delete openstack instances providing only the name

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

## [process-external-elastic-stats](https://cmssdt.cern.ch/jenkins/job/process-external-elastic-stats)

**Description:** This job process resource metrics jsons for externals

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [cms-spack-ib](#cms-spack-ib):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 22-23 * * *
```

---

## [process-relval-logs](https://cmssdt.cern.ch/jenkins/job/process-relval-logs)

**Description:** This job process partial logs of Relvals and place files accordingly.<br/>
There is no need to re-try newer run is successful or running. If it keeps on failing then one need 
to check the logs and find out the reason of failure. In that case some manual work is needed to cleanup
cmssdt.cern.ch logs.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-relvals](#ib-run-relvals):

**Downstream projects:**
* [process-relval-logs-cleanup](#process-relval-logs-cleanup):
* [update-github-pages](#update-github-pages):

**Sub-projects:**
* [update-github-pages](#update-github-pages):
* [process-relval-logs-cleanup](#process-relval-logs-cleanup):

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
```

---

## [process-relval-logs-cleanup](https://cmssdt.cern.ch/jenkins/job/process-relval-logs-cleanup)

**Description:** This job process partial logs of Relvals and place files accordingly.<br/>
There is no need to re-try this is a newer run is successful. If it keeps on failing then one need 
to check the logs and find out the reason of failure. In that case some manual work is needed to cleanup
cmssdt.cern.ch logs.

**Project is `enabled`.**

**Upstream projects:**
* [process-relval-logs](#process-relval-logs):

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

## [reco-profiling-eos-cleanup](https://cmssdt.cern.ch/jenkins/job/reco-profiling-eos-cleanup)

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

## [release-analyze-reco-profiling](https://cmssdt.cern.ch/jenkins/job/release-analyze-reco-profiling)

**Description:** This job processes data from release-run-reco-profiling and prepares https://cms-reco-profiling.web.cern.ch/cms-reco-profiling/

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

## [release-run-reco-profiling](https://cmssdt.cern.ch/jenkins/job/release-run-reco-profiling)

**Description:** Profiling jobs that are submitted manually for each CMSSW release. The performance is summarized on https://cms-reco-profiling.web.cern.ch/. Managed by cms-offline-conveners-reco@cern.ch.

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

## [run-container-stageout](https://cmssdt.cern.ch/jenkins/job/run-container-stageout)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [run-container-stageout](#run-container-stageout):

**Downstream projects:**
* [run-container-stageout](#run-container-stageout):

**Sub-projects:**
* [run-container-stageout](#run-container-stageout):

**Triggers from:** []


**Periodic builds:**
```bash
H 0,12 * * *

```

---

## [run-container-tests](https://cmssdt.cern.ch/jenkins/job/run-container-tests)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):

**Downstream projects:**

**Sub-projects:**
* [run-container-${CI_TEST}](#run-container-${CI_TEST}):

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

## [run-vtune-profiling](https://cmssdt.cern.ch/jenkins/job/run-vtune-profiling)

**Description:** Profiling jobs that are submitted manually for each CMSSW release. The performance is summarized on https://cms-reco-profiling.web.cern.ch/. Managed by cms-offline-conveners-reco@cern.ch.

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

## [slaves-checks](https://cmssdt.cern.ch/jenkins/job/slaves-checks)

**Description:** A wrapper project that starts a 
<a href="https://cmssdt.cern.ch/jenkins/job/workspace-cleanup-slave/">workspace-cleanup-slave</a>
and <a href="https://cmssdt.cern.ch/jenkins/job/test-docker">test-docker</a> jobs on selected slaves. 

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [check-docker](#check-docker):
* [check-zombie](#check-zombie):
* [workspace-cleanup-slave](#workspace-cleanup-slave):

**Sub-projects:**
* [workspace-cleanup-slave](#workspace-cleanup-slave):
* [check-docker ](#check-docker ):
* [check-zombie ](#check-zombie ):

**Triggers from:** []


**Periodic builds:**
```bash
H 07 * * *
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

## [sync-patatrack-branch](https://cmssdt.cern.ch/jenkins/job/sync-patatrack-branch)

**Description:** - this is to sync patatrack branches <br/>
- Currently this job does not do any thing (kind of disabled)


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
55 * * * *
```

---

## [sync-profile-data](https://cmssdt.cern.ch/jenkins/job/sync-profile-data)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-igprof](#ib-run-igprof):
* [ib-run-profiling](#ib-run-profiling):
* [ib-run-profiling-gpu](#ib-run-profiling-gpu):
* [ib-run-profiling-mem](#ib-run-profiling-mem):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** [u'ib-run-igprof', u'ib-run-profiling', u'ib-run-profiling-gpu', u'ib-run-profiling-mem']


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

## [test-containter-singularity](https://cmssdt.cern.ch/jenkins/job/test-containter-singularity)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-new-cvmfs-publisher](https://cmssdt.cern.ch/jenkins/job/test-new-cvmfs-publisher)

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

## [test-os](https://cmssdt.cern.ch/jenkins/job/test-os)

**Description:** This job generates property files for triggering os test jobs (e.g., test-os-cs8, test-os-alma8, etc) for any  os_arch_compiler combination.
<br>
The operating systems tested are rhel8, rocky8, ubi8, el8, cs8, alma8 and lxplus8 os.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [test-os-alma8](#test-os-alma8):
* [test-os-cs8](#test-os-cs8):
* [test-os-el8](#test-os-el8):
* [test-os-lxplus8](#test-os-lxplus8):
* [test-os-rhel8](#test-os-rhel8):
* [test-os-rocky8](#test-os-rocky8):
* [test-os-ubi8](#test-os-ubi8):

**Sub-projects:**
* [test-os-cs8](#test-os-cs8):
* [test-os-ubi8](#test-os-ubi8):
* [test-os-alma8](#test-os-alma8):
* [test-os-lxplus8](#test-os-lxplus8):
* [test-os-rhel8](#test-os-rhel8):
* [test-os-el8](#test-os-el8):
* [test-os-rocky8](#test-os-rocky8):

**Triggers from:** []


**Periodic builds:**
```bash
H 20 * * *
```

---

## [test-os-alma8](https://cmssdt.cern.ch/jenkins/job/test-os-alma8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-cs8](https://cmssdt.cern.ch/jenkins/job/test-os-cs8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-el8](https://cmssdt.cern.ch/jenkins/job/test-os-el8)

**Description:** [11/11 - avalenzu]: Failures when getting latest bootstrap driver file from cmsrep (file not found):
<br><br>

-bash-4.2$ wget --no-check-certificate '--header=Cache-Control: max-age=0' --user-agent=CMSPKG/1.0 --timeout=600 -O /tmp/tmpuBC1G/el8_amd64_gcc10-driver.txt.tmp 'cmsrep.cern.ch/cgi-bin/cmspkg/driver/cms.sw/el8_amd64_gcc10?repo_uri=cmssw'
<br><br>
--2022-11-11 11:19:47--  http://cmsrep.cern.ch/cgi-bin/cmspkg/driver/cms.sw/el8_amd64_gcc10?repo_uri=cmssw
<br>
Resolving cmsrep.cern.ch (cmsrep.cern.ch)... 188.184.102.160
<br>
Connecting to cmsrep.cern.ch (cmsrep.cern.ch)|188.184.102.160|:80... connected.
<br>
HTTP request sent, awaiting response... 404 Not Found
<br>
2022-11-11 11:19:47 ERROR 404: Not Found.
<br><br>
Workspace for #634 at cmsbuild70.

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-lxplus8](https://cmssdt.cern.ch/jenkins/job/test-os-lxplus8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-rhel8](https://cmssdt.cern.ch/jenkins/job/test-os-rhel8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-rocky8](https://cmssdt.cern.ch/jenkins/job/test-os-rocky8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [test-os-ubi8](https://cmssdt.cern.ch/jenkins/job/test-os-ubi8)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [test-os](#test-os):

**Downstream projects:**

**Sub-projects:**

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

## [update-circles-cmssdt](https://cmssdt.cern.ch/jenkins/job/update-circles-cmssdt)

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

## [update-circles-eos](https://cmssdt.cern.ch/jenkins/job/update-circles-eos)

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

## [update-pr-status](https://cmssdt.cern.ch/jenkins/job/update-pr-status)

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
* [update-release-map](#update-release-map):

**Sub-projects:**
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
* [upload-release](#upload-release):

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

## [workspace-cleanup-slave](https://cmssdt.cern.ch/jenkins/job/workspace-cleanup-slave)

**Description:** Connect to selected slave and cleans (deletes) workspace.

**Project is `enabled`.**

**Upstream projects:**
* [slaves-checks](#slaves-checks):

**Downstream projects:**
* [cleanup-release-build](#cleanup-release-build):

**Sub-projects:**
* [cleanup-release-build](#cleanup-release-build):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

