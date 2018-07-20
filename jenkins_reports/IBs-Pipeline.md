# [IBs Pipeline](https://cmssdt.cern.ch/jenkins/view/IBs Pipeline)

**View description:** None

**View type:** Build Pipeline View

---

# Projects:

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except Sunday at 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
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
#We do not run SAT 23H IB instead we start a special SUN 00h00 IB.
5 11  * * *
5 23  * *  0,1,2,3,4,5
5  0   * *  0

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

**Project is `enabled`.**

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

**Triggers from:** [u'build-fwlite-ib']


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

## [cmspkg-clone](https://cmssdt.cern.ch/jenkins/job/cmspkg-clone)

**Description:** Periodically (at 21 every day) backs up rpm repos from one place to another.

**Project is `enabled`.**

**Upstream projects:**
* [build-any-ib](#build-any-ib):
* [upload-release](#upload-release):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 21 * * *
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

**Triggers from:** [u'build-fwlite-ib']


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
* [test-relvals-with-krb](#test-relvals-with-krb):

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
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

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-relvals](#ib-run-relvals):
* [test-relvals-with-krb](#test-relvals-with-krb):

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

## [baseline-ib-results](https://cmssdt.cern.ch/jenkins/job/baseline-ib-results)

**Description:** This job runs a few tests only for the IB, for comparison with those ran by the pull request.

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

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

## [ib-run-geometry](https://cmssdt.cern.ch/jenkins/job/ib-run-geometry)

**Description:** Runs geometry comparison tests for each IB

**Project is `disabled`.**

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
run-ib-igprof is executed with `mp` flag for `memory profiling`.
<br>

<b>Q/a</b>

<ul>
  <li>
    Q: Error: near line 63: unrecognized token: "" 
  </li>  
  <li>
    A: Igprof has a bug that from time to time it returns unrecognizable character which fails the job. There is no easy fix, so we glance over it.
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
* [test-relvals-with-krb](#test-relvals-with-krb):

**Downstream projects:**
* [update-github-pages](#update-github-pages):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
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

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-relvals](#ib-run-relvals):
* [test-relvals-with-krb](#test-relvals-with-krb):

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

## [baseline-ib-results](https://cmssdt.cern.ch/jenkins/job/baseline-ib-results)

**Description:** This job runs a few tests only for the IB, for comparison with those ran by the pull request.

**Project is `enabled`.**

**Upstream projects:**
* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**
* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

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

## [ib-run-geometry](https://cmssdt.cern.ch/jenkins/job/ib-run-geometry)

**Description:** Runs geometry comparison tests for each IB

**Project is `disabled`.**

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
run-ib-igprof is executed with `mp` flag for `memory profiling`.
<br>

<b>Q/a</b>

<ul>
  <li>
    Q: Error: near line 63: unrecognized token: "" 
  </li>  
  <li>
    A: Igprof has a bug that from time to time it returns unrecognizable character which fails the job. There is no easy fix, so we glance over it.
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

