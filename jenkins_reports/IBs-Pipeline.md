# [IBs Pipeline](https://cmssdt.cern.ch/jenkins/view/IBs Pipeline)

**View description:** None

**View type:** Build Pipeline View

---

# Projects:

## [ib-schedule](https://cmssdt.cern.ch/jenkins/job/ib-schedule)

**Description:** This is a warpper job which runs daily at 11h and 23h (except Sunday at 00h) to triger 'ib-tag-and-schdule' sub-project.<br/>
This was created to avoid the issue with <a href="https://wiki.jenkins.io/display/JENKINS/Dynamic+Parameter+Plug-in">Jenkins Dynamic Parameters</a>.


**Upstream projects:**


**Downstream projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Sub-projects:**

* [ib-tag-and-schdule](#ib-tag-and-schdule):

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

## [build-fwlite-ib](https://cmssdt.cern.ch/jenkins/job/build-fwlite-ib)

**Description:** This job is responsible for building FWLITE release for each Integration build(IB). 
Results of this build can be seen via <a href="https://cmssdt.cern.ch/SDT/">CMSSDT</a> <a href="https://cmssdt.cern.ch/SDT/html/showIB.html">IB page</a>.

**Upstream projects:**

* [build-any-ib](#build-any-ib):

**Downstream projects:**

* [ib-build-logs](#ib-build-logs):

**Sub-projects:**


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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** ---need-description---

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [cmspkg-clone](https://cmssdt.cern.ch/jenkins/job/cmspkg-clone)

**Description:** None

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [upload-release](#upload-release):

**Downstream projects:**


**Sub-projects:**


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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** ---need-description---

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [ib-install-cvmfs](https://cmssdt.cern.ch/jenkins/job/ib-install-cvmfs)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

**Upstream projects:**

* [build-any-ib](#build-any-ib):
* [ib-tag-and-schdule](#ib-tag-and-schdule):

**Downstream projects:**

* [ib-validation](#ib-validation):

**Sub-projects:**


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

## [ib-run-addons](https://cmssdt.cern.ch/jenkins/job/ib-run-addons)

**Description:** ---need-description---

**Upstream projects:**

* [ib-validation](#ib-validation):

**Downstream projects:**


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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** ---need-description---

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**

* [ib-run-relvals](#ib-run-relvals):
* [test-kerberos-within-docker](#test-kerberos-within-docker):
* [test-relvals-with-krb](#test-relvals-with-krb):

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

## [HLT-Validation](https://cmssdt.cern.ch/jenkins/job/HLT-Validation)

**Description:** Appends job's time out information into jenkins.log file.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

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

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Upstream projects:**

* [baseline-ib-results](#baseline-ib-results):

**Downstream projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Sub-projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Triggers from:** []

## [cvmfs-publish-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-baseline)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Upstream projects:**

* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

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

## [compare-material-budget](https://cmssdt.cern.ch/jenkins/job/compare-material-budget)

**Description:** Comopare results of material budget of two releases using Validation/Geometry/test/TrackerMaterialBudgetComparison.C macro


**Upstream projects:**

* [ib-run-material-budget](#ib-run-material-budget):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-valgrind](https://cmssdt.cern.ch/jenkins/job/ib-run-valgrind)

**Description:** This job runs valgrind tool for selected IBs when build IB job is complete.   

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-static-checks](https://cmssdt.cern.ch/jenkins/job/ib-static-checks)

**Description:** Runs a few tests only for the IB, for comparison with those ran by the pull request.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


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

## [ib-run-addons](https://cmssdt.cern.ch/jenkins/job/ib-run-addons)

**Description:** ---need-description---

**Upstream projects:**

* [ib-validation](#ib-validation):

**Downstream projects:**


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

## [refresh-cmssdt](https://cmssdt.cern.ch/jenkins/job/refresh-cmssdt)

**Description:** This job updates the cmssw IB page on cmssdt.

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [summary-of-merged-prs](https://cmssdt.cern.ch/jenkins/job/summary-of-merged-prs)

**Description:** ---need-description---

**Upstream projects:**

* [update-github-pages](#update-github-pages):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** [u'update-github-pages']

## [update-das-queries](https://cmssdt.cern.ch/jenkins/job/update-das-queries)

**Description:** Job to run das client and cache the results in github to be used by IBs.

**Upstream projects:**

* [ib-run-relvals](#ib-run-relvals):
* [test-kerberos-within-docker](#test-kerberos-within-docker):
* [test-relvals-with-krb](#test-relvals-with-krb):

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

## [HLT-Validation](https://cmssdt.cern.ch/jenkins/job/HLT-Validation)

**Description:** Appends job's time out information into jenkins.log file.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

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

## [cvmfs-deploy-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-baseline)

**Description:** Copy baseline results from cmssdt for an IB

**Upstream projects:**

* [baseline-ib-results](#baseline-ib-results):

**Downstream projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Sub-projects:**

* [cvmfs-publish-baseline](#cvmfs-publish-baseline):

**Triggers from:** []

## [cvmfs-publish-baseline](https://cmssdt.cern.ch/jenkins/job/cvmfs-publish-baseline)

**Description:** Copy baseline results from cmssdt for an IB and deploy them on cvmfs

**Upstream projects:**

* [cvmfs-deploy-baseline](#cvmfs-deploy-baseline):

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

## [compare-material-budget](https://cmssdt.cern.ch/jenkins/job/compare-material-budget)

**Description:** Comopare results of material budget of two releases using Validation/Geometry/test/TrackerMaterialBudgetComparison.C macro


**Upstream projects:**

* [ib-run-material-budget](#ib-run-material-budget):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-run-valgrind](https://cmssdt.cern.ch/jenkins/job/ib-run-valgrind)

**Description:** This job runs valgrind tool for selected IBs when build IB job is complete.   

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


**Triggers from:** []

## [ib-static-checks](https://cmssdt.cern.ch/jenkins/job/ib-static-checks)

**Description:** Runs a few tests only for the IB, for comparison with those ran by the pull request.

**Upstream projects:**

* [schedule-additional-tests](#schedule-additional-tests):

**Downstream projects:**


**Sub-projects:**


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

