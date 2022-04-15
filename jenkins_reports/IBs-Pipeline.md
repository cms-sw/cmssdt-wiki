# [IBs Pipeline](https://cmssdt.cern.ch/jenkins/view/IBs Pipeline)

**View description:** None

**View type:** Build Pipeline View

---

# Projects:

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except no IB at 23h Sat & 11h Sun but a special IB at Sun 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
This was created to avoid the issue with <a href="https://wiki.jenkins.io/display/JENKINS/Dynamic+Parameter+Plug-in">Jenkins Dynamic Parameters</a>.


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):
* [sync-patatrack-branch](#sync-patatrack-branch):

**Sub-projects:**
* [sync-patatrack-branch](#sync-patatrack-branch):
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

**Sub-projects:**
* [build-any-ib](#build-any-ib):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [cleanup-cmsrep,cleanup-cvmfs-ci](#cleanup-cmsrep,cleanup-cvmfs-ci):

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

<ul>
  <li>
    <b>Q:</b> What to do if it fails?
  </li>
  <li>
    <b>A:</b> If it fails due to network/github issues then just re-try it but if it fails to build then we need to understand the build issues before retry.
  </li>
</ul>

**Project is `enabled`.**

**Upstream projects:**
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**
* [build-fwlite-ib](#build-fwlite-ib):
* [ib-build-logs](#ib-build-logs):
* [ib-install-cvmfs](#ib-install-cvmfs):
* [process-external-elastic-stats](#process-external-elastic-stats):

**Sub-projects:**
* [ib-install-cvmfs](#ib-install-cvmfs):
* [ib-build-logs,process-external-elastic-stats](#ib-build-logs,process-external-elastic-stats):
* [build-fwlite-ib](#build-fwlite-ib):

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

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch. As this job runs on the CVMFS Stratum 0, so only one job can run at a time.
Sometimes ( specially IBs for non-86-64 archs) are stuck and do nothing. In that case better to kill the job and re-try it.
This gives chance to other IBs to get installed and at the end the re-tried job will re-run. 

There is no automatic re-try setup for this job. It rarely fails but in case it fails then just re-try the failed job and
either delete the failed job instance or update the "Build information" and mentioned that it has been re-tired. This allows others to not re-try it.


**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
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

## [ib-run-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-qa)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

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

## [process-external-elastic-stats](https://cmssdt.cern.ch/jenkins/job/process-external-elastic-stats)

**Description:** This job process resource metrics jsons for externals

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 22-23 * * *
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

## [cleanup-cvmfs-ci](https://cmssdt.cern.ch/jenkins/job/cleanup-cvmfs-ci)

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

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch. As this job runs on the CVMFS Stratum 0, so only one job can run at a time.
Sometimes ( specially IBs for non-86-64 archs) are stuck and do nothing. In that case better to kill the job and re-try it.
This gives chance to other IBs to get installed and at the end the re-tried job will re-run. 

There is no automatic re-try setup for this job. It rarely fails but in case it fails then just re-try the failed job and
either delete the failed job instance or update the "Build information" and mentioned that it has been re-tired. This allows others to not re-try it.


**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
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

## [ib-run-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-qa)

**Description:** Runs Quality Assurance (QA) test on IB. Rezulst are available at 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.

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
* [ib-schedule](#ib-schedule):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
55 * * * *
```

---

