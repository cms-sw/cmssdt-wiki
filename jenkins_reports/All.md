# [All](https://cmssdt.cern.ch/jenkins/view/All)

**View description:** This view contains all jobs.

**View type:** All

---

# Projects:

## [abort-jenkins-job](https://cmssdt.cern.ch/jenkins/job/abort-jenkins-job)

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🚨 abort-jenkins-job</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Kill a running Jenkins job (default: <i>ib-run-pr-tests</i>) and any jobs started by it.  
The purpose is to ensure that when a pull request (PR) is updated, all related tests restart cleanly.  
This job terminates all matching running jobs for that PR, while ignoring the job ID of the upstream job that triggered it.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Kills running Jenkins jobs for a given pull request, except the upstream job that initiated this job.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Kills matching Jenkins jobs</strong> based on <i>JENKINS_PROJECT_TO_KILL</i> and parameters (<i>JENKINS_PROJECT_PARAMS</i>).</li>
  <li>🔹 <strong>Ignores upstream job</strong> identified by <i>IGNORE_JOB_BUILD_NUMBER</i> to prevent killing its own parent.</li>
  <li>🔹 <strong>Supports extra filtering</strong> via <i>EXTRA_PARAMS</i> to refine which jobs should be terminated.</li>
  <li>🔹 <strong>Auto-stops stuck jobs</strong> after 5 minutes to prevent unnecessary resource usage.</li>
  <li>🔹 <strong>Automatically cleans old builds</strong> (keeps builds for 3 days or a maximum of 50).</li>
  <li>🔹 <strong>Optimized for speed</strong> so PR test jobs can restart quickly without delays.</li>
</ul>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures killing a running Jenkin job with its children processes. </i>
</p>


**Project is `enabled`.**

**Upstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [kill-stuck-pr-test](#kill-stuck-pr-test):
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

**Description:** <h2 style="color:#d35400; font-weight:bold;">🚨 abort-pr-tests</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> This job triggers the <i>abort-jenkins-jobs</i> job for all Jenkins jobs related to PR tests.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
This job aborts all Jenkins PR test jobs associated with a specific PR.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Generates kill-job parameter files</strong> for each PR test job and triggers the <i>abort-jenkins-jobs</i> job to terminate them.</li>
  <li>🔹 <strong>Protects the upstream job</strong> by excluding the parent job that matches <i>IGNORE_JOB_BUILD_NUMBER</i> from termination.</li>
  <li>🔹 <strong>Automatically triggers abort-jenkins-job</strong> to kill all running processes for any project starting with <strong>ib-run-pr</strong>.</li>
</ul>

<h4 style="color:#c0392b;">📝 Note</h4>
<p style="font-size:13px; color:#34495e;">
In the future, if additional jobs need to be included, they must be added under the <strong>ib-run-pr</strong> naming prefix.
</p>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures killing all Jenkins jobs related to PR.</i>
</p>


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
<h2 style="color:#e74c3c; font-weight:bold;">🛑 abort-release</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Aborts and kills a release building process.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
This job detects, aborts, and cleans up any running or stuck CMSSW release build.  
It terminates active build processes and removes leftover workspace files to ensure a clean, stable environment for new release builds.
</p>

<h3 style="color:#27ae60;">📌 How It Works</h3>
<p style="font-size:14px;">Internally, the job executes two Groovy scripts via the Jenkins CLI:</p>

<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>kill-jenkins-job.groovy</strong> — Aborts active Jenkins build jobs that match the specified CMSSW release version.</li>
  <li>🔹 <strong>kill-build-release.groovy</strong> — Cleans up stale or incomplete build directories and artifacts, with optional <i>dry-run</i> support.</li>
</ul>

<p style="font-size:14px; line-height:1.6;">
Together, these scripts ensure that no leftover processes or files interfere with new CMSSW release builds.
</p>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures clean, conflict-free CMSSW release builds.</i>
</p>


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

**Description:** <h2 style="color:#2980b9; font-weight:bold;">🔄 auto-forward-port</h2>

<p style="font-size:14px; color:#2c3e50;">
This is triggered by github webhook for each cmssw/cmsdist branch merge event. This is just a place holder job to trigger one sub-job per destionation branch for which the forward porting should be done. If this fails then this means that one of its sub-job failed. There is no need to re-try this job. Retry the failed sub-jobs only.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
The auto-forward-port job is automatically triggered by GitHub webhook events whenever a branch in a repository (e.g., cms-sw/cmssw or cms-sw/cmsdist) is merged. Its primary role is not to perform the forward porting itself, but to spawn sub-jobs—one per destination branch that requires forward porting.
</p>

<h3 style="color:#27ae60;">📌 Behavior</h3>

<p style="font-size:14px;"><strong>Receives two parameters:</strong></p>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>REPOSITORY – the GitHub repository name (e.g., cms-sw/cmssw)</li>
  <li>BRANCH – the source branch to forward-port (e.g., CMSSW_7_6_X)</li>
</ul>

<p style="font-size:14px; line-height:1.6;">
Reads the mapping of destination branches from forward_ports_map.GIT_REPO_FWPORTS.
</p>

<p style="font-size:14px;"><strong>For each destination branch:</strong></p>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Creates a parameter file containing REPOSITORY, SOURCE_BRANCH, and DESTINATION_BRANCH.</li>
  <li>Triggers the corresponding forward-port sub-job.</li>
</ul>

<h3 style="color:#c0392b;">⚠️ Failure Handling</h3>
<p style="font-size:14px; line-height:1.6;">
If this job fails, it only indicates a sub-job failure.  
Only retry the failed sub-jobs, not this placeholder job.
</p>

<h3 style="color:#16a085;">🛠 Job Configuration Highlights</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Maximum 5 total builds; 1 per node; prevents duplicate builds for the same REPOSITORY and BRANCH.</li>
  <li>30 minutes to prevent stuck builds.</li>
  <li>Keep builds for 7 days or up to 100 builds.</li>
  <li>Runs on nodes labeled cmssdt or lxplus-scripts.</li>
</ul>


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

**Description:** <h2 style="color:#9b59b6; font-weight:bold;">🔀 auto-forward-port-branch</h2>

<p style="font-size:14px; color:#2c3e50;">
This job forward ports git changes from one branch to another. If it fails due to network of github related issues then just re-try it. Most of the times this job fails due to merge conflicts e.g. cmsdist master branch has different version of root as compare of rootmaster rootnext branch. If merge conflicts are just the version differences, then re-build the job with "STRATEGY=ours" as parameter, but if there are complex conflicts then better to resolve the issue by hand and directly push changes to github
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
This job forward ports git changes from one branch to another. If it fails due to a network of github related issues then just re-try it. Most of the times this job fails due to merge conflicts e.g. cmsdist master branch has different version of root as compare of rootmaster rootnext branch. If merge conflicts are just the version differences, then re-build the job with "STRATEGY=ours" as parameter, but if there are complex conflicts then better to resolve the issue by hand and directly push changes to github
</p>

<h3 style="color:#27ae60;">📌 Behavior & Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Automatically moves changes from a source branch to a destination branch.</li>
  <li>Runs on nodes labeled cmsdev, cmssdt, or lxplus-scripts.</li>
  <li>Resolves simple version conflicts automatically (<strong>STRATEGY=ours</strong>).</li>
  <li>Supports alternative merge strategy (<strong>STRATEGY=theirs</strong>).</li>
  <li>For complex conflicts, manual resolution and GitHub push are required.</li>
  <li>Retry only if the job fails due to network or GitHub issues.</li>
  <li>Can push changes immediately if <strong>FORCE_PUSH</strong> is enabled.</li>
  <li>Prevents multiple jobs from running on the same destination branch at the same time.</li>
  <li>Stops jobs that run too long (35 minutes) and keeps build history for 7 days or up to 100 builds.</li>
</ul>

<h3 style="color:#c0392b;">📝 Note</h3>
<p style="font-size:14px; color:#34495e;">
In case of Root master use "ours" strategy to port forward.
</p>


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

**Description:** <h2 style="color:#1abc9c; font-weight:bold;">🔁 backport-pull-request</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Manually executed job for backporting pull requests given the repository name, the branch for which the PR should be created, and the pull request to be backported.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Manual Backporting: Manually backports an existing GitHub pull request to a specified branch.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Simple Inputs:</strong> Requires the repository name, target branch, and pull request number to backport.</li>
  <li><strong>Automated Process:</strong> Uses the <i>backport-pr.py</i> script to apply the pull request changes automatically.</li>
  <li><strong>Clean Environment:</strong> Deletes the workspace before starting to avoid conflicts from previous runs.</li>
  <li><strong>Controlled Execution:</strong> Runs only on <strong>cmssdt</strong> nodes to ensure a stable execution environment.</li>
  <li><strong>Timeout Protection:</strong> Stops the job automatically if it runs longer than <strong>30 minutes</strong>.</li>
  <li><strong>Build History Management:</strong> Keeps build logs for <strong>30 days</strong> or up to <strong>100 builds</strong> for tracking and auditing.</li>
</ul>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job provides a safe and controlled way to backport changes while maintaining clean build environments.</i>
</p>


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

**Description:** <h2 style="color:#2c3e50; font-weight:bold;">🧱 Integration Build (IB)</h2>

<p style="font-size:14px; color:#2c3e50;">
This job starts an <strong>Integration Build (IB)</strong>. Based on the state of the <strong>CMSDIST</strong> and <strong>CMSSW</strong> Git repositories, it builds either a <strong>full release</strong> or a <strong>patch release</strong>.
</p>

<h3 style="color:#8e44ad;">🏗 Build Decision Logic</h3>
<p style="font-size:14px;">A <strong>Full IB</strong> is built if:</p>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>There are changes in <strong>CMSDIST</strong></li>
  <li>There is no full IB available based on the current <strong>CMSDIST</strong></li>
  <li>The previous full IB had build errors</li>
</ul>

<p style="font-size:14px; line-height:1.6;">
If none of the above conditions are met, the job builds a <strong>patch release</strong>.
</p>

<h3 style="color:#27ae60;">❓ Q / A</h3>

<p style="font-size:14px;"><strong>Q:</strong> The job is scheduled with a clock symbol. Jenkins also complains that there are no agents with labels <i>THIS</i> and <i>THIS</i>.</p>
<p style="font-size:14px; line-height:1.6;">
<strong>A:</strong> Jenkins should automatically launch agents with the required labels for this job. However, for some reason this does not work for this job. For now, launch the agent manually.
</p>

<p style="font-size:14px;"><strong>Q:</strong> How to manually build an IB?</p>
<p style="font-size:14px; line-height:1.6;">
<strong>A:</strong> Go to the upstream job <strong>ib-tag-and-schdule</strong> and start the job.
</p>

<p style="font-size:14px;"><strong>Q:</strong> What to do if it fails?</p>
<p style="font-size:14px; line-height:1.6;">
<strong>A:</strong> If it fails due to network or GitHub issues, simply retry the job.  
If it fails during the build, the build issues must be understood and resolved before retrying.
</p>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures consistent and reliable Integration Builds by selecting the correct build strategy based on repository state.</i>
</p>


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

## [build-docker-container](https://cmssdt.cern.ch/jenkins/job/build-docker-container)

**Description:** <h2 style="color:#3498db; font-weight:bold;">🐳 Build Docker Containers</h2>

<p style="font-size:14px; color:#2c3e50;">
This job builds container images and uploads them to <strong>DockerHub</strong>.
</p>

<h3 style="color:#8e44ad;">🏗 Build Triggers</h3>
<p style="font-size:14px; line-height:1.6;">
Containers are built when either their <strong>base image</strong> is updated or when changes are made to the <strong>Dockerfile</strong>.
</p>

<h3 style="color:#27ae60;">⚠️ Failure Scenarios & Handling</h3>

<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>
    <strong>Base image changes:</strong> Failures may arise due to updates in the base image.  
    In this case, log into the machine, reproduce the issue, and adapt the Dockerfile accordingly (e.g., adjusting dependencies or build order).
  </li>

  <li>
    <strong>Infrastructure glitches:</strong> If the failure is caused by transient infrastructure issues, a simple retry should resolve the problem.
  </li>

  <li>
    <strong>Checksum mismatch:</strong> If the container image definition changes, retrigger this job from the
    <strong>check-docker-container</strong> job to ensure the correct checksum is passed to the
    <strong>build-docker-container</strong> job.
  </li>

  <li>
    <strong>Disk space issues:</strong> Since built container images remain on the machine, the job may fail due to insufficient disk space.
  </li>
</ul>

<h3 style="color:#e67e22;">🧹 Cleanup & Maintenance</h3>

<p style="font-size:14px; line-height:1.6;">
A separate Jenkins job, <strong>clean-build-docker-machine</strong>, runs once a week to clean up unused images on the build machine.
</p>

<p style="font-size:14px; line-height:1.6;">
If immediate cleanup is required, log into the machine and run:
</p>

<pre style="background:#f4f6f7; padding:10px; border-radius:5px; font-size:13px;">
docker image prune
docker system prune --volumes
</pre>

<p style="font-size:14px; line-height:1.6;">
If the <code>./singularity</code> folder is large
(<code>du -hs /build/cmsbld/jenkins/workspace/.singularity</code>),
it can also be safely removed.
</p>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures container images are rebuilt, validated, and published while providing clear recovery paths for common failure scenarios.</i>
</p>




**Project is `enabled`.**

**Upstream projects:**
* [check-docker-container](#check-docker-container):

**Downstream projects:**
* [check-docker-container](#check-docker-container):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [docker-issue-comment](#docker-issue-comment):
* [docker-packages-info](#docker-packages-info):
* [run-container-tests](#run-container-tests):
* [test-containter-singularity](#test-containter-singularity):

**Sub-projects:**
* [docker-packages-info](#docker-packages-info):
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [test-containter-singularity](#test-containter-singularity):
* [run-container-tests](#run-container-tests):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [docker-packages-info](#docker-packages-info):
* [check-docker-container](#check-docker-container):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [build-fwlite](https://cmssdt.cern.ch/jenkins/job/build-fwlite)

**Description:** <h2 style="color:#16a085; font-weight:bold;">🧩 build-fwlite</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> This job builds a <strong>CMSSW_X_Y_Z_FWLITE</strong> release based on an existing
<strong>CMSSW_X_Y_Z</strong> release. The base CMSSW release must already be built and uploaded
before running this job.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
FWLite Release Build: Builds a <strong>CMSSW_X_Y_Z_FWLITE</strong> release from an already built and
uploaded <strong>CMSSW_X_Y_Z</strong> release.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Prerequisite Required:</strong> The base <strong>CMSSW_X_Y_Z</strong> release must already exist before running this job.</li>
  <li><strong>Architecture-Aware:</strong> Builds the FWLite release for the specified architecture and execution environment (native or container-based).</li>
  <li><strong>Patch Release Handling:</strong> By default, FWLite is not built for patch releases unless <strong>FORCE_PATCH_BUILD</strong> is enabled.</li>
  <li><strong>Version Safeguards:</strong> Automatically skips builds for unsupported CMSSW versions (FWLite is built only for <strong>CMSSW_8_1</strong> and above).</li>
  <li><strong>Clean & Controlled Build:</strong> Starts from a clean workspace and runs with a <strong>120-minute timeout</strong> to prevent stuck builds.</li>
  <li><strong>Automated Upload & Logging:</strong> Uploads the FWLite build and stores build logs for later inspection.</li>
</ul>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job extends existing CMSSW releases with FWLite builds while enforcing version compatibility and build safety.</i>
</p>


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

**Description:** <h2 style="color:#8e44ad; font-weight:bold;">🧩 build-fwlite-ib</h2>

<p style="font-size:14px; color:#2c3e50;">
This job is responsible for building <strong>FWLite releases</strong> for each Integration Build (IB).  
Results of this build can be seen via:  
<a href="https://cmssdt.cern.ch/SDT/">CMSSDT</a> | 
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib">IB page</a> | 
<a href="https://cmssdt.cern.ch/SDT/html/showIB.html">(old page)</a>
</p>

<h3 style="color:#27ae60;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Builds FWLite releases for every Integration Build (IB) while ensuring controlled execution, clean workspaces, and reproducible results.
</p>

<h3 style="color:#2980b9;">📌 Parameters</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Release format</li>
  <li>Repository</li>
  <li>Architecture</li>
  <li>Release queue</li>
  <li>Docker image</li>
  <li>Specific commit hashes: <strong>CMSDIST_HASH</strong>, <strong>PKGTOOLS_HASH</strong></li>
</ul>

<h3 style="color:#27ae60;">🛠 Controlled Execution</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Runs only on nodes appropriate for the specified architecture and environment labels.</li>
  <li>Concurrency limited to <strong>10 total builds</strong> and <strong>1 per node</strong>.</li>
  <li>Deletes workspace before starting to avoid conflicts from previous builds.</li>
  <li>Stops builds longer than <strong>180 minutes</strong> to avoid stuck processes.</li>
</ul>

<h3 style="color:#e67e22;">⚙️ Build Process</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Clones the CMS bot repository.</li>
  <li>Sets up the environment architecture.</li>
  <li>Launches the FWLite IB build using <strong>docker_launcher.sh</strong>.</li>
</ul>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures FWLite builds for Integration Builds are performed reliably, reproducibly, and within controlled execution limits.</i>
</p>


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

**Description:** 
<h2 style="color:#c0392b; font-weight:bold;">🏗 build-release</h2>

<p style="font-size:14px; color:#2c3e50;">
This job actually builds a release. It is triggered by <strong>cms-bot</strong> after the Release Build Issue is approved by the release manager.
</p>

<h3 style="color:#27ae60;">⚠️ Failure Handling</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>
    <strong>Retryable failures:</strong> Depending on the type of failure, most of the time simply retrying the job works.
  </li>
  <li>
    <strong>Disk quota issues (aarch64 builds):</strong> Some aarch64 machines may run out of disk space. In this case, log into the affected machine, clean up old or unused files, and then retry the job.
  </li>
  <li>
    <strong>Build errors in release:</strong> Sometimes the job may succeed but build errors are reported by the bot in the corresponding issue. Use the <strong>Rebuild</strong> button to re-trigger the build. The bot will automatically remove build-error labels and inform that a new build has started.
  </li>
</ul>

<hr/>


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

**Description:** <h2 style="color:#2980b9; font-weight:bold;">🐳 check-cms-container-certificates</h2>

<p style="font-size:14px; color:#2c3e50;">
This job checks for <strong>HOST certificates</strong> in <strong>cmssw/cms:rhelX</strong> Docker images and fails if the host certificate is going to expire in less than <strong>CERT_EXPIRY_DAYS</strong> days.
</p>

<h3 style="color:#27ae60;">⚠️ Action on Expiring Certificates</h3>
<p style="font-size:14px; line-height:1.6;">
If the job fails due to an expiring certificate, check if there is an updated <strong>osg-ca-certs</strong> package available and rebuild the container.
</p>

<h3 style="color:#8e44ad;">🔄 Rerun Options</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Rerun the job with:
    <ul>
      <li><strong>LOCAL_CERTIFICATE=/cvmfs/grid.cern.ch/etc/grid-security/certificates</strong></li>
      <li><strong>CHECK_LOCAL_CERTIFICATE=true</strong></li>
    </ul>
    to check if new certificates are already available.
  </li>
  <li>If the job still fails, this indicates that new root certificates are not yet available.</li>
</ul>

<h3 style="color:#e67e22;">ℹ️ Notes</h3>
<p style="font-size:14px; line-height:1.6;">
The job fails some days before the actual expiration (<strong>CERT_EXPIRY_DAYS</strong>) to allow time for updates.
</p>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures that Docker container certificates are valid and proactively triggers rebuilds to avoid certificate expiration issues.</i>
</p>


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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">💾 check-cmsdev-disk</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Monitors and manages disk space on CMS development (cmsdev) machines. Automatically identifies users consuming excessive disk space and sends cleanup notifications when thresholds are exceeded.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Proactively prevents disk space exhaustion on shared CMS development infrastructure by identifying heavy disk usage and notifying responsible users for cleanup actions.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Automated disk monitoring</strong> across all active cmsdev machines</li>
  <li>🔹 <strong>Threshold-based notifications</strong> with configurable limits</li>
  <li>🔹 <strong>Parallel execution</strong> (4 concurrent processes) for efficient scanning</li>
  <li>🔹 <strong>Intelligent user identification</strong> via CERN phonebook integration</li>
  <li>🔹 <strong>Personalized email notifications</strong> with specific cleanup instructions</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 2</li>
    <li><strong>Max Builds to Keep:</strong> 10</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Default Value</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>DISK_SPACE_USED_IN_PERCENT</code></td>
      <td style="border:1px solid #ddd; padding:8px;">85%</td>
      <td style="border:1px solid #ddd; padding:8px;">Disk space threshold (with % sign) triggering email notifications</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>SIZE_THRESHOLD</code></td>
      <td style="border:1px solid #ddd; padding:8px;">50</td>
      <td style="border:1px solid #ddd; padding:8px;">Size threshold in GB for individual user data triggering notifications</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⏱️ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Timeout Strategy:</strong> Absolute</li>
    <li><strong>Timeout Duration:</strong> 180 minutes</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Execution Flow:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Machine Discovery</strong>: Identifies all active cmsdev machines (excluding temporarily offline nodes)</li>
  <li><strong>Parallel Disk Check</strong>: Simultaneously checks disk usage on 4 machines at a time</li>
  <li><strong>Threshold Evaluation</strong>: Compares usage against <code>DISK_SPACE_USED_IN_PERCENT</code></li>
  <li><strong>User Data Analysis</strong>: Collects detailed usage statistics for machines exceeding threshold</li>
  <li><strong>User Identification</strong>: Looks up user details via CERN phonebook for personalized notifications</li>
  <li><strong>Notification Dispatch</strong>: Sends cleanup emails to users exceeding <code>SIZE_THRESHOLD</code></li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📧 Notification Logic:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Triggers email when:</strong><br>
    1. Machine disk usage > <code>85%</code><br>
    2. User has > <code>50</code> GB of data on that machine<br>
    3. User contact information is available in CERN phonebook
  </p>
</div>

<h3 style="color:#27ae60;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Prevents service disruption</strong> due to disk space exhaustion</li>
  <li>✅ <strong>Proactive maintenance</strong> rather than reactive firefighting</li>
  <li>✅ <strong>Fair usage enforcement</strong> across all developers</li>
  <li>✅ <strong>Reduced administrative overhead</strong> through automation</li>
  <li>✅ <strong>Educational approach</strong> with polite, informative notifications</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This maintenance job ensures sustainable disk usage across shared CMS development resources, promoting responsible data management through automated monitoring and user-friendly notifications.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🗺️ check-cvmfs-releases-map</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Monitors and detects changes between the CVMFS releases.map file and its authoritative source in the cms-bot GitHub repository. This job performs periodic synchronization checks to ensure the distributed file system version matches the source control version.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Maintains version consistency between the CVMFS releases.map file and its source in GitHub. Acts as a change detection mechanism that triggers downstream update processes when discrepancies are identified.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Automated periodic checking</strong> - runs every 4 hours</li>
  <li>🔹 <strong>Intelligent comparison</strong> - detects actual content differences, not just timestamp changes</li>
  <li>🔹 <strong>Efficient execution</strong> - exits immediately if files are identical</li>
  <li>🔹 <strong>Change flag creation</strong> - creates an update marker file when differences are detected</li>
  <li>🔹 <strong>GitHub integration</strong> - fetches the latest authoritative version for comparison</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 7</li>
    <li><strong>Max Builds to Keep:</strong> 30</li>
  </ul>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Rebuild Options:</strong> Enabled</li>
    <li><strong>Execution Nodes:</strong> Restricted to lxplus-scripts, lxplus, or cmsdev machines</li>
    <li><strong>Schedule:</strong> Runs every 4 hours (H H/4 * * *)</li>
    <li><strong>Trigger:</strong> Build periodically (scheduled)</li>
  </ul>

  <h4 style="color:#2c3e50;">📁 File Locations</h4>
  <ul style="margin:5px 0;">
    <li><strong>CVMFS Location:</strong> <code>/cvmfs/cms.cern.ch/releases.map</code></li>
    <li><strong>GitHub Source:</strong> cms-sw/cms-bot repository master branch</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Execution Logic:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Scheduled Execution</strong>: Automatically triggers every 4 hours</li>
  <li><strong>Source Retrieval</strong>: Downloads the latest releases.map file from the cms-bot GitHub repository</li>
  <li><strong>File Comparison</strong>: Compares the downloaded file with the existing CVMFS version using content-based diff</li>
  <li><strong>Conditional Processing</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>If files are identical → Job completes successfully (exit code 0)</li>
      <li>If differences exist → Creates an <code>update-releases-map</code> flag file</li>
    </ul>
  </li>
  <li><strong>Update Signaling</strong>: The flag file serves as a trigger for downstream update processes</li>
</ol>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This change detection job ensures the CVMFS releases.map is monitored for synchronization with its GitHub source. It serves as the first step in a pipeline that maintains consistency across distributed CMS infrastructure.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🔧 check-docker</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Connects to Jenkins slave nodes and verifies Docker service functionality.  
Performs health checks to ensure Docker is properly configured and operational for build/test execution.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Validates Docker service availability and configuration on Jenkins slave nodes. Ensures Docker environment is ready for containerized builds and tests.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Docker service validation</strong> - checks if Docker daemon is running and accessible</li>
  <li>🔹 <strong>Permission verification</strong> - confirms user has proper Docker group membership</li>
  <li>🔹 <strong>Disk space monitoring</strong> - detects and reports insufficient disk space for Docker operations</li>
  <li>🔹 <strong>Targeted execution</strong> - can be manually run against specific machines using machine name parameter</li>
</ul>

<h3 style="color:#e67e22;">🔍 Troubleshooting & Failure Resolution</h3>

<h4 style="color:#d35400; font-size:15px; margin-top:15px;">🔴 Common Failure Scenarios:</h4>

<table style="width:100%; font-size:14px; border-collapse: collapse; margin:15px 0;">
  <thead style="background-color:#f1f2f6;">
    <tr>
      <th style="border:1px solid #ddd; padding:10px; text-align:left;">Failure Reason</th>
      <th style="border:1px solid #ddd; padding:10px; text-align:left;">Symptoms</th>
      <th style="border:1px solid #ddd; padding:10px; text-align:left;">Resolution Action</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border:1px solid #ddd; padding:10px;"><strong>1. User not in Docker group</strong></td>
      <td style="border:1px solid #ddd; padding:10px;">Permission denied errors when running Docker commands</td>
      <td style="border:1px solid #ddd; padding:10px;">
        <strong>For machines under our control:</strong><br>
        • Login to machine and add user to Docker group<br>
        • Run: <code>sudo usermod -aG docker &lt;username&gt;</code>
      </td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:10px;"><strong>2. Docker service not running</strong></td>
      <td style="border:1px solid #ddd; padding:10px;">Cannot connect to Docker daemon; service unavailable</td>
      <td style="border:1px solid #ddd; padding:10px;">
        <strong>For machines under our control:</strong><br>
        • Start Docker service manually<br>
        • Run: <code>sudo systemctl start docker</code><br><br>
        <strong>For CERN IT controlled machines (e.g., OpenLab):</strong><br>
        • Open a SNOW ticket for service restoration
      </td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:10px;"><strong>3. Insufficient disk space</strong></td>
      <td style="border:1px solid #ddd; padding:10px;">"No space left on device" errors from Docker daemon</td>
      <td style="border:1px solid #ddd; padding:10px;">
        • Manually trigger this job with machine name as parameter<br>
        • Or run cleanup commands on affected machine:<br>
        <code>docker system prune -a --volumes</code><br>
        <code>docker image prune -a</code>
      </td>
    </tr>
  </tbody>
</table>

<h4 style="color:#d35400; font-size:15px; margin-top:20px;">🛠️ Resolution Workflow:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Identify affected machine</strong> from job console output</li>
  <li><strong>Determine machine ownership</strong> (our control vs. CERN IT control)</li>
  <li><strong>For our machines</strong>: SSH into machine and execute appropriate remediation commands</li>
  <li><strong>For CERN IT machines</strong>: Open SNOW ticket with detailed error information</li>
  <li><strong>For disk space issues</strong>: Run <code>clean-check-docker</code> job with machine name parameter or execute manual cleanup</li>
</ol>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>Build blockage</strong>: Failure prevents Docker-based builds/tests on affected nodes</li>
  <li>⚠️ <strong>Ownership awareness</strong>: Critical to distinguish between self-managed and CERN IT-managed machines</li>
  <li>💾 <strong>Space monitoring</strong>: Disk space issues are common and require regular cleanup</li>
  <li>🎯 <strong>Quick resolution</strong>: Prompt action required to minimize impact on build pipelines</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This diagnostic job ensures Docker readiness across Jenkins infrastructure. Regular execution helps prevent build failures due to Docker environment issues.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🐳 check-docker-container</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Monitors upstream Docker base images for changes and triggers rebuilds when updates are detected. Specifically checks for changes in parent images and orchestrates the update process by creating GitHub issues and triggering downstream build jobs.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Ensures CMS Docker containers remain up-to-date with their base images by automatically detecting upstream changes and initiating rebuild processes through GitHub issue creation and job triggering.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Upstream change detection</strong> - monitors base image checksums for modifications</li>
  <li>🔹 <strong>Multi-architecture support</strong> - handles x86_64, aarch64, and ppc64le architectures</li>
  <li>🔹 <strong>GitHub integration</strong> - creates issues in cms-sw/cms-docker repository for tracking</li>
  <li>🔹 <strong>Selective processing</strong> - can target specific tags or force rebuilds via parameters</li>
  <li>🔹 <strong>Build state management</strong> - labels and tracks which images are queued for building</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 15</li>
    <li><strong>Max Builds to Keep:</strong> 50</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Type</th>
      <th style="border:1px solid #ddd; padding:8px;">Default Value</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>REPOSITORY</code></td>
      <td style="border:1px solid #ddd; padding:8px;">String</td>
      <td style="border:1px solid #ddd; padding:8px;">cms</td>
      <td style="border:1px solid #ddd; padding:8px;">Target Docker repository to check</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>FORCE_BUILD</code></td>
      <td style="border:1px solid #ddd; padding:8px;">Boolean</td>
      <td style="border:1px solid #ddd; padding:8px;">false</td>
      <td style="border:1px solid #ddd; padding:8px;">Force rebuild regardless of changes</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>TAGS</code></td>
      <td style="border:1px solid #ddd; padding:8px;">String</td>
      <td style="border:1px solid #ddd; padding:8px;">(empty)</td>
      <td style="border:1px solid #ddd; padding:8px;">Specific tags to process (default: all)</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Concurrency Control:</strong> Prevent multiple jobs with identical REPOSITORY parameter</li>
    <li><strong>Execution Nodes:</strong> Restricted to cmsdist machines</li>
    <li><strong>Build Name Format:</strong> #${BUILD_NUMBER} ${REPOSITORY} ${TAGS}</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Detection & Notification Logic:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Base Image Comparison</strong>: Compares current base image checksums against stored values</li>
  <li><strong>Architecture-Specific Processing</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li><strong>el8/el9 repositories</strong>: Check for AlmaLinux base image changes</li>
      <li><strong>Other repositories</strong>: Check Dockerfile-based image changes</li>
    </ul>
  </li>
  <li><strong>GitHub Issue Creation</strong>: When changes detected, creates issues in cms-sw/cms-docker with specific labels</li>
  <li><strong>Build State Management</strong>: Updates issue labels to track queued/building states</li>
  <li><strong>Duplicate Prevention</strong>: Checks for already-building architectures to avoid conflicts</li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Key Detection Logic:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Change Detection Criteria:</strong><br>
    1. <strong>For el8/el9</strong>: Detects changes in <code>library/almalinux</code> base images<br>
    2. <strong>For other repos</strong>: Detects changes in Dockerfile-based images (excluding bootstrap files)<br>
    3. <strong>Identifies by</strong>: Architecture + checksum (first 10 chars) combination<br>
    4. <strong>Creates GitHub issue</strong> with format: <code>[REPOSITORY][ARCH-checksum]</code>
  </p>
</div>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>GitHub Dependency</strong>: Requires GitHub API access for issue creation and labeling</li>
  <li>⚠️ <strong>Concurrency Control</strong>: Only one job per repository can run simultaneously</li>
  <li>🔧 <strong>Manual Override</strong>: Use <code>FORCE_BUILD=true</code> to bypass change detection</li>
  <li>🏷️ <strong>Label Management</strong>: Uses GitHub labels for build state tracking (queued/building)</li>
  <li>🔄 <strong>Downstream Trigger</strong>: Detection triggers <code>build-docker-container</code> job for actual rebuilds</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This monitoring job ensures CMS Docker containers stay synchronized with upstream base images through automated change detection and issue-based workflow orchestration.</i>
</p>

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):
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

## [check-future-commit-prs](https://cmssdt.cern.ch/jenkins/job/check-future-commit-prs)

**Description:** <h2 style="color:#2980b9; font-weight:bold;">🔍 check-future-commit-prs</h2>

<p style="font-size:14px; color:#2c3e50;">
Periodically runs the script
<a href="https://github.com/cms-sw/cms-bot/blob/master/fix-backport-labels.py">fix-backport-labels.py</a>
to check whether a pull request on <strong>master</strong>, for which a backport has been requested, has been merged.
If the original PR is merged, the job updates all related open backport PRs from
  <strong>backport</strong> <strong style="color:blue"> (blue) </strong> 🔵 to <strong>backport-ok</strong> <strong style="color:green"> (green)</strong> 🟢.
</p>

<h3 style="color:#27ae60;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Automatically monitors pull requests on the master branch that have requested backports and keeps their status up to date.
</p>

<h3 style="color:#8e44ad;">⏱ Periodic Execution</h3>
<p style="font-size:14px; line-height:1.6;">
Runs every <strong>15 minutes</strong> to ensure backport statuses are refreshed in a timely manner.
</p>

<h3 style="color:#27ae60;">🔄 Backport Status Update</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Checks whether the original PR on <strong>master</strong> has been merged.</li>
  <li>If merged, updates all associated open backport PRs from
      <strong>backport</strong> 🔵 to <strong>backport-ok</strong> 🟢</li>
</ul>

<h3 style="color:#2980b9;">⚙️ Implementation Details</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Uses the <strong>check-future-commits-prs.py</strong> script from <strong>cms-bot</strong>.</li>
  <li>Designed to be fast and lightweight with a <strong>2-minute timeout</strong>.</li>
  <li>Runs only on <strong>cmssdt</strong> nodes with elevated job priority.</li>
  <li>Keeps build history for <strong>2 days</strong> or up to <strong>50 builds</strong> to reduce clutter.</li>
</ul>

<hr/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This job ensures that backport pull requests accurately reflect the merge status of their original changes.</i>
</p>


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cms-bot](#cms-bot):

**Sub-projects:**
* [cms-bot](#cms-bot):

**Triggers from:** []


**Periodic builds:**
```bash
H/15 * * * *
```

---

## [check-pending-job](https://cmssdt.cern.ch/jenkins/job/check-pending-job)

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🔍 Process Status & Killer</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Monitors and manages processes on remote Jenkins slave machines for running jobs. This diagnostic tool allows administrators to inspect long-running or potentially stuck processes and terminate them if necessary, providing visibility and control over remote execution environments.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Provides remote process monitoring and intervention capabilities for Jenkins jobs. Enables administrators to diagnose hanging processes, view execution trees, and safely terminate problematic processes on remote build machines.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Remote process inspection</strong> - displays process trees with PID, start time, and command details</li>
  <li>🔹 <strong>Targeted process termination</strong> - allows killing specific processes by PID</li>
  <li>🔹 <strong>Job context awareness</strong> - automatically identifies the remote machine where a job is running</li>
  <li>🔹 <strong>Safety checks</strong> - verifies process ownership before allowing termination</li>
  <li>🔹 <strong>Forest view display</h> - shows parent-child process relationships for better debugging</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 10</li>
    <li><strong>Max Builds to Keep:</strong> 10</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Type</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>JOB_URL</code></td>
      <td style="border:1px solid #ddd; padding:8px;">String</td>
      <td style="border:1px solid #ddd; padding:8td;">URL of the running Jenkins job to inspect (e.g., https://cmssdt.cern.ch/jenkins/job/ib-run-relvals/243936/)</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>KILL_PID</code></td>
      <td style="border:1px solid #ddd; padding:8px;">String</td>
      <td style="border:1px solid #ddd; padding:8td;">Optional: Process ID to terminate (must match a process owned by the job user)</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Build Name Format:</strong> #${BUILD_NUMBER} ${KILL_PID} ${JOB_URL}</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Execution Workflow:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Job URL Processing</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Accepts Jenkins job URLs (with or without /console suffix)</li>
      <li>Extracts job path and locates build configuration files</li>
    </ul>
  </li>
  <li><strong>Remote Machine Identification</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Parses build.xml to determine which slave machine is executing the job</li>
      <li>Extracts SSH connection string from node configuration</li>
    </ul>
  </li>
  <li><strong>Process Inspection</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>SSHes to remote machine and runs: <code>ps -u ${USER} -o pid,start_time,cmd --forest</code></li>
      <li>Displays hierarchical process tree with timestamps</li>
    </ul>
  </li>
  <li><strong>Conditional Termination</strong> (if KILL_PID provided):
    <ul style="margin:5px 0 5px 20px;">
      <li>Verifies the PID belongs to the job user</li>
      <li>Executes <code>kill -9 ${PID}</code> on the remote machine</li>
      <li>Re-displays process tree to confirm termination</li>
    </ul>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Usage Instructions:</h4>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Step-by-Step Usage:</strong><br>
    1. <strong>Copy URL</strong> of a running job (e.g., https://cmssdt.cern.ch/jenkins/job/ib-run-relvals/243936/)<br>
    2. <strong>Start this job</strong> with <code>JOB_URL=</code> parameter set to the copied URL<br>
    3. <strong>Analyze output</strong> - look for processes running unusually long<br>
    4. <strong>Optional kill</strong> - if a process should be terminated, restart with <code>KILL_PID=</code> parameter<br>
    5. <strong>Verify</strong> - check that the process was successfully terminated
  </p>
</div>
<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This diagnostic and intervention tool provides controlled access to remote process management, enabling administrators to resolve hanging jobs while maintaining system stability and security boundaries.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🧹 check-unused-cmsdist-packages</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Identifies unused files across cmsdist branches to facilitate repository cleanup. Uses a three-phase parallel architecture to analyze all active configurations.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Analyzes cmsdist repository to detect orphaned files (.patch, .file, .spec) that are no longer referenced by any active build configuration, enabling systematic repository maintenance.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li> <strong>Three-phase parallel architecture</strong> for efficient multi-architecture analysis</li>
  <li> <strong>Cross-branch scanning</strong> of all active cmsdist release branches</li>
  <li> <strong>Intelligent filtering</strong> - excludes archives, vectorization, and validates pip dependencies</li>
  <li> <strong>Artifact sharing</strong> via UPLOAD_ID for coordinated parallel execution</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep:</strong> 30</li>
    <li><strong>Max Builds:</strong> 100</li>
   </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
       <th style="border:1px solid #ddd; padding:8px;">Purpose</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>ARCHITECTURE</code></td>
      <td style="border:1px solid #ddd; padding:8px;">Target architecture (determines execution node)</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>RELEASE_QUEUE</code></td>
      <td style="border:1px solid #ddd; padding:8px;">Specific release queue to analyze</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>UPLOAD_ID</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Reuse previous analysis artifacts</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Build Name:</strong> #${BUILD_NUMBER} ${RELEASE_QUEUE} ${ARCHITECTURE} ${UPLOAD_ID}</li>
    <li><strong>Node Selection:</strong> Dynamic via Groovy script based on ARCHITECTURE</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 Three-Phase Execution Architecture</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Phase 1: Orchestrator (Manual Trigger)</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Parses cms-bot/config.map for active release configurations</li>
  <li>Generates CMSSW_*.prop files for each architecture/release combination</li>
  <li>Sets UPLOAD_ID = ${BUILD_ID} for artifact coordination</li>
  <li>Triggers parallel sub-builds for each architecture</li>
</ol>

<h4 style="color:#d35400; font-size:15px;">🔄 Phase 2: Parallel Workers (Auto-Triggered)</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Each worker processes specific architecture via docker_launcher.sh</li>
  <li>Clones and analyzes cmsdist branches for unused files</li>
  <li>Uploads results using shared UPLOAD_ID for coordination</li>
  <li>Creates skip.txt to prevent duplicate processing</li>
</ol>

<h4 style="color:#d35400; font-size:15px;">🔄 Phase 3: Result Aggregation</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>Collects all worker artifacts using shared UPLOAD_ID</li>
  <li>Compiles unified unused.txt and unused_uniq.txt reports</li>
  <li>Generates final cleanup recommendations</li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Analysis Logic:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>File Detection Rules:</strong><br>
    1. <strong>Scanned:</strong> .patch, .file, .spec, spec files<br>
    2. <strong>Excluded:</strong> /.git/, vectorization/, archive/<br>
    3. <strong>Pip Validation:</strong> .file packages must be in requirements.txt<br>
    4. <strong>Unused:</strong> Files not referenced in any build configuration
  </p>
</div>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Parallel analysis system for cmsdist repository cleanup, identifying orphaned files across all active branches and architectures through coordinated three-phase execution.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🧟 check-zombie</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Detects and terminates runaway/zombie processes on Jenkins slave machines. Identifies processes orphaned from their parent (PPID=1) running for more than 4 hours and provides automated cleanup capabilities.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Monitors slave machines for orphaned processes consuming resources indefinitely. Automatically kills processes that have lost their parent and been running for excessive durations, preventing resource exhaustion on build nodes.If all looks good, then one can restart the job with KILL_HANGING_PROCESSES=true. 
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Orphaned process detection</strong> - identifies processes with parent PID=1</li>
  <li>🔹 <strong>Duration-based filtering</strong> - only targets processes running >4 hours (14400 seconds)</li>
  <li>🔹 <strong>Process group termination</strong> - kills entire process groups using kill -- '-PGID'</li>
  <li>🔹 <strong>Verification cycle</strong> - checks again after cleanup to confirm resolution</li>
  <li>🔹 <strong>Email notifications</strong> - alerts cms-sdt-logs@cern.ch on failures</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 2</li>
    <li><strong>Max Builds to Keep:</strong> 100</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>SLAVE_CONNECTION</code></td>
      <td style="border:1px solid #ddd; padding:8td;">SSH connection string (ex. cmsbld@cmsbuild58.cern.ch)</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>KILL_HANGING_PROCESSES</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Set to true to enable automatic termination</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Build Name:</strong> #${BUILD_NUMBER} ${SLAVE_CONNECTION}</li>
    <li><strong>Concurrency:</strong> Max 15 builds total, 15 per node</li>
    <li><strong>Execution Nodes:</strong> lxplus-scripts, lxplus7, lxplus6, master</li>
    <li><strong>Timeout:</strong> 3 minutes absolute timeout</li>
    <li><strong>Email Notification:</strong> cms-sdt-logs@cern.ch on failure</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Detection & Cleanup Logic:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>SSH Connection</strong>: Connects to specified slave machine with optimized SSH options</li>
  <li><strong>Process Detection</strong>: Finds processes where:
    <ul style="margin:5px 0 5px 20px;">
      <li>Parent PID (PPID) = 1 (orphaned from init/systemd)</li>
      <li>Running time > 4 hours (14400 seconds)</li>
      <li>Owned by slave user (default: cmsbld)</li>
    </ul>
  </li>
  <li><strong>Automatic Termination</strong>: Kills entire process groups using PGID</li>
  <li><strong>Verification</strong>: Waits 3 seconds, re-checks for remaining orphaned processes</li>
  <li><strong>Failure Condition</strong>: Job fails if orphaned processes remain after cleanup</li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Detection Command:</h4>
<div style="background-color:#f0f0f0; padding:10px; border-radius:5px; margin:10px 0; font-family:monospace; font-size:12px;">
ps -u ${USER} -o ppid,pgid,pid,etimes,start_time,cmd --forest |<br>
grep '^\s*1\s' | awk '\$4>14400'
</div>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>Orphaned Process Definition</strong>: PPID=1 indicates process lost its parent</li>
  <li>⚠️ <strong>4-Hour Threshold</strong>: Only kills processes running >4 hours to avoid false positives</li>
  <li>🔒 <strong>Process Group Termination</strong>: Kills entire process group to prevent orphaned children</li>
  <li>⏱️ <strong>Short Timeout</strong>: 3-minute timeout ensures job doesn't hang on unresponsive slaves</li>
  <li>📧 <strong>Failure Notification</strong>: Email sent to cms-sdt-logs@cern.ch for manual intervention</li>
</ul>

<h3 style="color:#27ae60;">🛠️ Troubleshooting</h3>

<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>If Job Fails:</strong><br>
    1. <strong>Check job logs</strong> for detected orphaned process details<br>
    2. <strong>Verify</strong> if processes are truly runaway (PPID=1, etimes>14400)<br>
    3. <strong>If legitimate orphaned processes</strong>: Restart job with <code>KILL_HANGING_PROCESSES=true</code><br>
    4. <strong>If uncertain</strong>: Investigate process manually before killing<br>
    5. <strong>Note</strong>: Some cmsRun jobs legitimately run with PPID=1
  </p>
</div>
<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Automated orphaned process cleanup for Jenkins slave nodes. Prevents resource exhaustion by identifying and terminating processes that have lost parent connections and run for excessive durations. Requires manual verification before enabling automatic termination.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🧹 clean-build-docker-container</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Weekly cleanup job that prevents disk space exhaustion on Docker build machines. Systematically removes unused Docker images, volumes, and Singularity cache files to maintain sufficient disk capacity for container image building operations.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Proactively manages disk space on Docker build infrastructure by removing accumulated temporary files, unused images, and cached data. Prevents build failures due to insufficient disk space on machines used for container image construction.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Scheduled weekly cleanup</strong> - runs every Monday at 9:00 AM</li>
  <li>🔹 <strong>Three-layer cleanup</strong> - targets Docker images, volumes, and Singularity cache</li>
  <li>🔹 <strong>Automated confirmation</strong> - uses 'yes' command for non-interactive operation</li>
  <li>🔹 <strong>Resource optimization</strong> - recovers disk space without manual intervention</li>
  <li>🔹 <strong>Build prevention</strong> - maintains capacity for build-docker-container job operations</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 15</li>
    <li><strong>Max Builds to Keep:</strong> 100</li>
  </ul>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Every Monday at 9:00 AM (H 9 * * 1)</li>
    <li><strong>Execution Nodes:</strong> docker-build && amd64 machines</li>
    <li><strong>Rebuild Options:</strong> Enabled</li>
    <li><strong>Trigger:</strong> Build periodically</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Three-Phase Cleanup Process:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Docker Image Cleanup</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      yes | docker image prune -a
    </div>
    <p style="margin:5px 0; font-size:13px;">Removes all unused Docker images (dangling and unreferenced)</p>
  </li>
  
  <li><strong>Docker System & Volume Cleanup</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      yes | docker system prune --volumes
    </div>
    <p style="margin:5px 0; font-size:13px;">Removes stopped containers, unused networks, build cache, and volumes</p>
  </li>
  
  <li><strong>Singularity Cache Cleanup</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      yes | rm -rf /build/cmsbld/jenkins/workspace/.singularity
    </div>
    <p style="margin:5px 0; font-size:13px;">Deletes Singularity container cache directory</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Cleanup Scope:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Targeted Cleanup Items:</strong><br>
    1. <strong>Docker Images</strong>: All unused images (including those not tagged)<br>
    2. <strong>Docker Volumes</strong>: Unused named volumes<br>
    3. <strong>Docker System</strong>: Containers, networks, build cache<br>
    4. <strong>Singularity</strong>: Complete cache directory removal<br>
    5. <strong>Scope</strong>: Only affects unused resources; active containers remain
  </p>
</div>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>Forceful Cleanup</strong>: Uses 'yes |' to auto-confirm all removal prompts</li>
  <li>⚠️ <strong>Permanent Deletion</strong>: Removed images/volumes cannot be recovered</li>
  <li>🔒 <strong>Active Resource Protection</strong>: Only removes unused resources; running containers unaffected</li>
  <li>⏰ <strong>Weekly Schedule</strong>: Monday morning timing minimizes impact on active builds</li>
  <li>💾 <strong>Significant Space Recovery</strong>: Can free gigabytes of disk space from accumulated caches</li>
</ul>
<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Scheduled disk maintenance job for Docker build infrastructure. Prevents resource exhaustion by systematically removing unused container images, volumes, and cache files on a weekly basis, ensuring reliable container build operations.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🗑️ cleanup-auto-build</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Manages automated cleanup of release build areas after 3 days. Removes workspace directories from remote build machines to prevent disk space accumulation from completed auto-build jobs.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Systematically cleans up build directories from remote machines after the standard 3-day retention period. Ensures efficient disk space utilization across build infrastructure while maintaining traceability through artifact preservation.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Time-based cleanup</strong> - targets build areas older than 3 days</li>
  <li>🔹 <strong>Remote execution</strong> - runs cleanup scripts on target build machines</li>
  <li>🔹 <strong>Status reporting</strong> - updates GitHub issue status with cleanup results</li>
  <li>🔹 <strong>Artifact preservation</strong> - uploads logs before directory deletion</li>
  <li>🔹 <strong>Email notifications</strong> - alerts cms-sdt-logs@cern.ch on failures</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 30</li>
    <li><strong>Max Builds to Keep:</strong> 20</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>CMSSW_X_Y_Z</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Release version to cleanup (e.g., CMSSW_16_0_0)</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>ARCHITECTURE</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Target architecture (e.g., el8_amd64_gcc14)</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>ISSUE_NUMBER</code></td>
      <td style="border:1px solid #ddd; padding:8td;">GitHub issue number for status reporting</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>MACHINE_NAME</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Remote build machine hostname</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>DRY_RUN_PARAM</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Optional dry-run flag</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Build Name:</strong> #${CMSSW_X_Y_Z} - ${ARCHITECTURE} Issue ${ISSUE_NUMBER}</li>
    <li><strong>Concurrency:</strong> Max 4 total builds, 0 per node</li>
    <li><strong>Execution Nodes:</strong> cmssdt or lxplus-scripts machines</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Email:</strong> cms-sdt-logs@cern.ch for unstable builds</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Cleanup Workflow:</h4>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Environment Setup</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Clones cms-bot repository with cleanup scripts</li>
      <li>Defines remote workspace path: <code>/build/cmsbld/jenkins/workspace/auto-builds/CMSSW_X_Y_Z-ARCHITECTURE/</code></li>
    </ul>
  </li>
  <li><strong>Directory Verification</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Checks if build directory exists on remote machine</li>
      <li>If missing → logs "Build directory already deleted"</li>
      <li>If present → proceeds with cleanup</li>
    </ul>
  </li>
  <li><strong>Remote Execution</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Transfers cleanup script to remote machine via rsync</li>
      <li>Executes cleanup-auto-build script on target machine</li>
      <li>Passes release, architecture, and build directory parameters</li>
    </ul>
  </li>
  <li><strong>Status Reporting</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Checks for "ALL_OK" in cleanup log</li>
      <li>Reports status to GitHub issue via report-build-release-status</li>
      <li>Uploads cleanup log as Jenkins artifact</li>
    </ul>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Key Operations:</h4>
<div style="background-color:#f0f0f0; padding:10px; border-radius:5px; margin:10px 0; font-family:monospace; font-size:12px;">
# Check if directory exists<br>
ssh $SSH_OPTS $BLD_USER@$MACHINE_NAME ls -d $REMOTE_WORKSPACE<br><br>
# Execute remote cleanup<br>
ssh $BLD_USER@$MACHINE_NAME $REMOTE_WORKSPACE/cleanup-auto-build $CMSSW_X_Y_Z $ARCHITECTURE $BUILD_DIR
</div>

<h3 style="color:#27ae60;">🛠️ Status Reporting</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Success Scenario:</strong><br>
    • Log contains "ALL_OK"<br>
    • GitHub issue marked with CLEANUP_OK<br>
    • Email notification: None (unless configured otherwise)<br><br>
    <strong>Failure Scenario:</strong><br>
    • Log contains errors<br>
    • GitHub issue marked with CLEANUP_ERROR<br>
    • Email sent to cms-sdt-logs@cern.ch<br>
    • Cleanup log preserved as Jenkins artifact
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Disk space management</strong> - prevents accumulation of old build artifacts</li>
  <li>✅ <strong>Automated scheduling</strong> - integrates with auto-build lifecycle</li>
  <li>✅ <strong>Audit trail</strong> - logs preserved even after directory deletion</li>
  <li>✅ <strong>Status transparency</strong> - GitHub issue updates for tracking</li>
  <li>✅ <strong>Safe execution</strong> - verifies directory existence before attempting cleanup</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Post-build cleanup job that removes release build directories from remote machines after 3 days. Maintains disk space efficiency while preserving logs and providing status updates through GitHub issue integration.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🗑️ cleanup-cms-sw-io-history</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Maintains the CMS GitHub Pages repository by resetting history for data directories while preserving current content. Specifically cleans the `data` and `_data` directories' Git history to manage repository size and optimize performance.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Performs controlled Git history rewriting for data-heavy directories in the cms-sw.github.io repository. Reduces repository bloat by resetting history while keeping current data intact, then triggers GitHub Pages regeneration.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Scheduled weekly cleanup</strong> - runs every Sunday at 1:00 AM</li>
  <li>🔹 <strong>Dual-branch strategy</strong> - uses 'code' branch as source, 'master' as target</li>
  <li>🔹 <strong>History reset</strong> - completely replaces data directory history with fresh state</li>
  <li>🔹 <strong>Force-push workflow</strong> - uses git push -f to rewrite branch history</li>
  <li>🔹 <strong>Downstream triggering</strong> - automatically updates GitHub Pages after cleanup</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 30</li>
    <li><strong>Max Builds to Keep:</strong> 20</li>
  </ul>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Every Sunday at 1:00 AM (H 1 * * 0)</li>
    <li><strong>Execution Nodes:</strong> lxplus, lxplus-scripts, or cmsdev machines</li>
    <li><strong>Trigger:</strong> Build periodically</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Downstream Job:</strong> Triggers update-github-pages on success</li>
    <li><strong>Email:</strong> cms-sdt-logs@cern.ch for unstable builds</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Four-Phase Cleanup Process:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Repository Cloning</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Shallow clone of 'code' branch (source data)</li>
      <li>Shallow clone of 'master' branch (target for cleanup)</li>
      <li>Uses depth=1 to minimize transfer size</li>
    </ul>
  </li>
  
  <li><strong>Marker File Management</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      if [ ! -f data/history_cleanup ] ; then
        touch data/history_cleanup
        git add data/history_cleanup
        git commit -a -m 'history cleanup file added'
    </div>
    <p style="margin:5px 0; font-size:13px;">Ensures clean working state by adding/removing marker file</p>
  </li>
  
  <li><strong>Directory Synchronization</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      rm -rf GITHUB_IO_MASTER/.git
      rsync -a GITHUB_IO_CODE/ GITHUB_IO_MASTER/
    </div>
    <p style="margin:5px 0; font-size:13px;">Replaces master content with code branch while preserving .git separately</p>
  </li>
  
  <li><strong>History Rewriting</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      git add .
      git commit -m "Hisory of data directories was reset at $(date)"
      git push -f origin HEAD:master
    </div>
    <p style="margin:5px 0; font-size:13px;">Force-pushes rewritten history to master branch</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Branch Strategy:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Two-Branch Architecture:</strong><br>
    1. <strong>code branch</strong>: Contains current data files (source)<br>
    2. <strong>master branch</strong>: GitHub Pages branch (target for cleanup)<br>
    3. <strong>Workflow</strong>: Master gets fresh data from code, resetting its history<br>
    4. <strong>Result</strong>: Master has clean history with current data files<br>
    5. <strong>Benefit</strong>: Reduces repository size while maintaining content
  </p>
</div>

<h3 style="color:#27ae60;">🔄 Downstream Integration</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Automatic Triggering:</strong><br>
    • <strong>Success</strong>: Triggers <code>update-github-pages</code> job<br>
    • <strong>Condition</strong>: Only if build is stable<br>
    • <strong>Purpose</strong>: Ensures GitHub Pages are regenerated with cleaned repository<br>
    • <strong>Timing</strong>: Immediate sequential execution<br>
    • <strong>Monitoring</strong>: Both jobs can be tracked in Jenkins build chain
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Repository optimization</strong> - reduces Git history bloat from data files</li>
  <li>✅ <strong>Performance improvement</strong> - faster clones and operations</li>
  <li>✅ <strong>Automated maintenance</strong> - weekly schedule prevents accumulation</li>
  <li>✅ <strong>Content preservation</strong> - keeps current data while removing history</li>
  <li>✅ <strong>Integrated workflow</strong> - automatically triggers pages regeneration</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Scheduled Git history maintenance for CMS GitHub Pages repository. Resets history of data directories to manage repository size while preserving current content, followed by automatic GitHub Pages regeneration.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🗑️ cleanup-cmsrep</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Cleans up obsolete pull request repositories from the CMS RPM repository server. Removes old <code>cms.weekN.PR_*</code> directories to manage disk space on the cmsrep.cern.ch server.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Systematically removes temporary pull request repositories associated with specific CMS weekly builds. Prevents disk space accumulation by deleting PR repositories that are no longer needed after pull request testing or merging.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li> <strong>Targeted cleanup</strong> - removes specific PR repository patterns</li>
  <li> <strong>Validation safety</strong> - verifies parameter format before execution</li>
  <li> <strong>Direct filesystem operation</strong> - executes on cmsrep server itself</li>
  <li> <strong>Pattern-based matching</strong> - uses wildcards to match multiple repositories</li>
  <li> <strong>Single-purpose design</strong> - focused cleanup for PR repositories only</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 30</li>
    <li><strong>Max Builds to Keep:</strong> 50</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>CMS_WEEK</code></td>
      <td style="border:1px solid #ddd; padding:8td;">CMS weekly repository name (e.g., week0, week1, week2, etc.)</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Execution Nodes:</strong> cmsrep server only</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Two-Step Cleanup Process:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Parameter Validation</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      if [ $(echo ${CMS_WEEK} | grep '^week[0-9]$' | wc -l) -eq 0 ] ; then exit 1; fi
    </div>
    <p style="margin:5px 0; font-size:13px;">Ensures <code>CMS_WEEK</code> parameter matches pattern <code>week[0-9]</code></p>
  </li>
  
  <li><strong>Repository Cleanup</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      cd /data/cmssw/repos
      for repo in $(ls -d cms.${CMS_WEEK}.PR_*) ; do
        rm -rf $repo
      done
    </div>
    <p style="margin:5px 0; font-size:13px;">Recursively deletes all matching PR repositories in the target week</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Target Directory Structure:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Directory Layout:</strong><br>
    <code>/data/cmssw/repos/</code> - Base repository directory<br>
    <code>cms.week0.PR_12345/</code> - Example PR repository<br>
    <code>cms.week0.PR_67890/</code> - Another PR repository<br>
    <code>cms.week1.PR_12345/</code> - PR repository in different week<br><br>
    <strong>Cleanup Scope:</strong> All <code>cms.${CMS_WEEK}.PR_*</code> directories<br>
    <strong>Preserved:</strong> Other repository types and different weeks
  </p>
</div>

<h3 style="color:#27ae60;">🛠️ Usage Guidelines</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Typical Use Cases:</strong><br>
    1. <strong>Weekly maintenance</strong>: Clean up old PR repositories after week rotation<br>
    2. <strong>Disk space recovery</strong>: Free space when server approaches capacity<br>
    3. <strong>Repository management</strong>: Remove completed/abandoned PR repositories<br><br>
    <strong>Parameter Examples:</strong><br>
    • <code>CMS_WEEK=week0</code> - Cleans PR repos from week0<br>
    • <code>CMS_WEEK=week1</code> - Cleans PR repos from week1<br>
    • <code>CMS_WEEK=week2</code> - Cleans PR repos from week2
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Disk space management</strong> - prevents accumulation of obsolete PR repositories</li>
  <li>✅ <strong>Targeted cleanup</strong> - only affects specific weekly PR directories</li>
  <li>✅ <strong>Safety mechanisms</strong> - parameter validation prevents accidental deletions</li>
  <li>✅ <strong>Simple operation</strong> - minimal logic for reliable execution</li>
  <li>✅ <strong>Repository hygiene</strong> - maintains clean server filesystem</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Targeted cleanup job for CMS RPM repository server. Removes pull request repositories from specific weekly directories to manage disk space and maintain repository hygiene on cmsrep.cern.ch.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🗑️ cleanup-cmssdt</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Daily disk space maintenance job for the CMSSDT server. Executes automated cleanup routines and monitors disk usage, sending alerts when space utilization exceeds critical thresholds.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Performs regular disk cleanup and monitoring on the cmssdt server to prevent space exhaustion. Combines automated cleanup operations with proactive alerting to ensure system reliability and availability.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Daily scheduled execution</strong> - runs every day at midnight</li>
  <li>🔹 <strong>Dual functionality</strong> - cleanup operations + disk monitoring</li>
  <li>🔹 <strong>Dry-run capability</strong> - optional simulation mode for testing</li>
  <li>🔹 <strong>Proactive alerting</strong> - emails when disk usage exceeds 80%</li>
  <li>🔹 <strong>Built-in reporting</strong> - includes disk usage statistics before and after</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 15</li>
    <li><strong>Max Builds to Keep:</strong> 10</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>DRY_RUN</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Optional parameter to simulate cleanup without actual deletion</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Daily at midnight (H 0 * * *)</li>
    <li><strong>Execution Nodes:</strong> cmssdt server only</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Trigger:</strong> Build periodically</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Three-Phase Execution:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Initial Disk Status</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      df -h
    </div>
    <p style="margin:5px 0; font-size:13px;">Captures disk usage statistics before cleanup for comparison</p>
  </li>
  
  <li><strong>Cleanup Execution</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      ${CMS_BOT_DIR}/cleanup-cmssdt $DRY_RUN
    </div>
    <p style="margin:5px 0; font-size:13px;">Executes the main cleanup script from cms-bot directory</p>
  </li>
  
  <li><strong>Monitoring & Alerting</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      if [ `df -h | grep ' /data$' | awk '{print $5}' | sed 's|%||'` -gt 80 ] ; then
        echo -e "${BUILD_URL}\n$(df -h)" | mail -s '[CMSSDT] Disk getting full' cms-sdt-logs@cern.ch
      fi
    </div>
    <p style="margin:5px 0; font-size:13px;">Monitors /data partition and sends email alert if usage >80%</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Alerting Logic:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Monitoring Target:</strong> <code>/data</code> partition specifically<br>
    <strong>Threshold:</strong> 80% disk usage<br>
    <strong>Alert Content:</strong><br>
    • Jenkins build URL for reference<br>
    • Current disk usage statistics (df -h output)<br>
    <strong>Recipient:</strong> cms-sdt-logs@cern.ch<br>
    <strong>Subject:</strong> [CMSSDT] Disk getting full<br>
    <strong>Trigger:</strong> Post-cleanup usage check
  </p>
</div>

<h3 style="color:#27ae60;">🛠️ Dry Run Mode</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Testing Without Risk:</strong><br>
    • <strong>Purpose:</strong> Simulate cleanup operations without actual deletion<br>
    • <strong>Usage:</strong> Provide <code>DRY_RUN</code> parameter value<br>
    • <strong>Benefit:</strong> Review what would be cleaned before execution<br>
    • <strong>Monitoring:</strong> Alert logic still functions in dry-run mode<br>
    • <strong>Typical Use:</strong> Testing cleanup scripts or evaluating impact
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Preventative maintenance</strong> - regular cleanup prevents space crises</li>
  <li>✅ <strong>Proactive alerting</strong> - notification before critical levels reached</li>
  <li>✅ <strong>Audit trail</strong> - disk usage captured before and after cleanup</li>
  <li>✅ <strong>Safe testing</strong> - dry-run mode allows risk-free evaluation</li>
  <li>✅ <strong>Automated scheduling</strong> - daily execution ensures consistent maintenance</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Daily disk maintenance and monitoring job for CMSSDT server. Combines automated cleanup operations with proactive alerting to prevent disk space exhaustion and ensure system reliability.</i>
</p>

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

**Description:** 
<h2 style="color:#c0392b; font-weight:bold;">🗑️ cleanup-cvmfs-ci</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> This job cleans up old cms.weekN.PR_* repositories from cmsrep.cern.ch server. Manages CVMFS (CernVM File System) cleanup for CMS continuous integration repositories. Removes specified weekly directories from the CVMFS repository while handling transaction safety, publishing, and garbage collection operations.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Performs controlled removal of weekly CI repositories from CVMFS with proper transaction management and garbage collection. Ensures safe filesystem operations while freeing space in the CVMFS repository used for CMS continuous integration.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>CVMFS transaction management</strong> - handles publishing and rollback safely</li>
  <li>🔹 <strong>Weekly directory cleanup</strong> - removes specified week directories</li>
  <li>🔹 <strong>Garbage collection</strong> - recovers space after directory removal</li>
  <li>🔹 <strong>Lock recovery</strong> - handles stuck publishing locks automatically</li>
  <li>🔹 <strong>Parameter validation</strong> - ensures proper week format before execution</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Days to Keep Builds:</strong> 30</li>
    <li><strong>Max Builds to Keep:</strong> 50</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>CMS_WEEK</code></td>
      <td style="border:1px solid #ddd; padding:8td;">CMS weekly repository name (e.g., week0, week1, week2, etc.)</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Execution Nodes:</strong> cvmfs-server && publish && cms-ci nodes</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Timeout:</strong> 240 minutes (4 hours) absolute timeout</li>
    <li><strong>Environment:</strong> Uses CVMFS_REPOSITORY environment variable</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Four-Phase CVMFS Cleanup:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Parameter Validation</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      if [ $(echo ${CMS_WEEK} | grep '^week[0-9]$' | wc -l) -eq 0 ] ; then exit 1; fi
    </div>
    <p style="margin:5px 0; font-size:13px;">Validates week parameter format (week0-week9)</p>
  </li>
  
  <li><strong>CVMFS Transaction Start</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      cvmfs_server transaction $CVMFS_REPOSITORY || ((cvmfs_server abort -f $CVMFS_REPOSITORY || rm -fR /var/spool/cvmfs/$CVMFS_REPOSITORY/is_publishing.lock) && cvmfs_server transaction $CVMFS_REPOSITORY)
    </div>
    <p style="margin:5px 0; font-size:13px;">Initiates transaction with lock recovery fallback</p>
  </li>
  
  <li><strong>Directory Removal</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      rm -rf /cvmfs/$CVMFS_REPOSITORY/${CMS_WEEK}
    </div>
    <p style="margin:5px 0; font-size:13px;">Deletes specified weekly directory from CVMFS</p>
  </li>
  
  <li><strong>Publish & Garbage Collection</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      time cvmfs_server publish $CVMFS_REPOSITORY
      time cvmfs_server gc -f $CVMFS_REPOSITORY
    </div>
    <p style="margin:5px 0; font-size:13px;">Commits changes and performs garbage collection</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 CVMFS Operations Detail:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Transaction Safety:</strong><br>
    1. <strong>Initial attempt</strong>: <code>cvmfs_server transaction</code><br>
    2. <strong>Failure recovery</strong>: Abort any existing transaction<br>
    3. <strong>Lock cleanup</strong>: Remove stuck publishing lock if needed<br>
    4. <strong>Retry</strong>: Attempt transaction again after cleanup<br><br>
    <strong>Directory Structure:</strong><br>
    • <code>/cvmfs/$CVMFS_REPOSITORY/week0/</code> - Target for deletion<br>
    • <code>/cvmfs/$CVMFS_REPOSITORY/week1/</code> - Another example<br>
    • <code>/var/spool/cvmfs/$CVMFS_REPOSITORY/is_publishing.lock</code> - Lock file
  </p>
</div>

<h3 style="color:#27ae60;">🛠️ CVMFS Command Flow</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Command Sequence:</strong><br>
    1. <strong>Transaction</strong>: Begin CVMFS write transaction<br>
    2. <strong>Cleanup</strong>: Delete target week directory<br>
    3. <strong>Publish</strong>: Commit changes to repository (timed)<br>
    4. <strong>Garbage Collection</strong>: Reclaim freed space (timed)<br><br>
    <strong>Timing Information:</strong><br>
    • <code>time</code> command tracks publish and GC duration<br>
    • Useful for performance monitoring and debugging<br>
    • Helps identify slow operations requiring optimization
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Space recovery</strong> - frees CVMFS repository space efficiently</li>
  <li>✅ <strong>Transaction safety</strong> - ensures atomic operations with rollback</li>
  <li>✅ <strong>Automated lock recovery</strong> - handles stuck transactions automatically</li>
  <li>✅ <strong>Performance monitoring</strong> - times critical operations</li>
  <li>✅ <strong>CVMFS integration</strong> - uses native CVMFS tools for reliable cleanup</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>CVMFS repository maintenance job for CMS CI infrastructure. Safely removes weekly directories with proper transaction management, publishing, and garbage collection to maintain repository performance and availability.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🏷️ cleanup-docker-tags</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Daily maintenance job that removes outdated Docker image tags from container registries. Manages tag lifecycle by deleting old or unused tags to maintain registry efficiency and prevent tag proliferation.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Prevents Docker registry bloat by systematically removing obsolete image tags. Ensures registry performance and manageability by applying tag retention policies and freeing storage space from unused Docker images.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Daily scheduled execution</strong> - runs every day at midnight</li>
  <li>🔹 <strong>Dry-run capability</strong> - preview deletion operations without execution</li>
  <li>🔹 <strong>Python-based logic</strong> - uses dedicated docker_tag_delete.py script</li>
  <li>🔹 <strong>CMS Docker integration</strong> - leverages cms-docker repository tools</li>
  <li>🔹 <strong>Safe operation</strong> - configurable dry-run mode for testing</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 7</li>
    <li><strong>Max Builds to Keep:</strong> 50</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>DRY_RUN</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Boolean flag to simulate deletions without actual removal</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Daily at midnight (H 0 * * *)</li>
    <li><strong>Execution Nodes:</strong> cmsdist machines</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Trigger:</strong> Build periodically</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Two-Phase Execution:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Repository Preparation</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      git clone --depth 1 https://github.com/cms-sw/cms-docker
    </div>
    <p style="margin:5px 0; font-size:13px;">Clones the latest CMS Docker utilities with minimal history</p>
  </li>
  
  <li><strong>Tag Cleanup Execution</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      PYTHONPATH= ./cms-docker/bin/docker_tag_delete.py ${ARGS}
    </div>
    <p style="margin:5px 0; font-size:13px;">Executes the Python tag deletion script with appropriate arguments</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Argument Handling:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Argument Logic:</strong><br>
    1. <strong>Default mode</strong>: <code>ARGS=""</code> - performs actual deletion<br>
    2. <strong>Dry-run mode</strong>: <code>ARGS="-n"</code> when <code>DRY_RUN=true</code><br>
    3. <strong>Environment</strong>: <code>PYTHONPATH=</code> ensures clean Python environment<br>
    4. <strong>Script location</strong>: <code>cms-docker/bin/docker_tag_delete.py</code><br>
    5. <strong>Execution</strong>: Direct script execution without Python path modifications
  </p>
</div>
<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Registry optimization</strong> - prevents tag proliferation and registry bloat</li>
  <li>✅ <strong>Storage efficiency</strong> - frees space from obsolete image tags</li>
  <li>✅ <strong>Automated maintenance</strong> - daily execution ensures consistent cleanup</li>
  <li>✅ <strong>Safe testing</strong> - dry-run mode allows risk-free evaluation</li>
  <li>✅ <strong>Integration ready</strong> - uses established CMS Docker tooling</li>
</ul>

<h3 style="color:#c0392b;">🔧 Underlying Script Details</h3>
<div style="background-color:#ffe6e6; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #c0392b;">
  <p style="margin:0; font-size:13px;">
    <strong>docker_tag_delete.py Script (Expected Behavior):</strong><br>
    1. <strong>Registry Analysis</strong>: Scans Docker registries for CMS images<br>
    2. <strong>Tag Evaluation</strong>: Identifies tags meeting deletion criteria<br>
    3. <strong>Policy Application</strong>: Applies retention rules (age, count, etc.)<br>
    4. <strong>Deletion Execution</strong>: Removes selected tags from registry<br>
    5. <strong>Logging</strong>: Records all operations for audit purposes
  </p>
</div>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Daily Docker registry maintenance job that removes outdated image tags using CMS Docker tooling. Features dry-run capability for safe testing and regular execution to maintain registry efficiency.</i>
</p>

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

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🤖 cms-bot</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Triggered by GitHub webhooks (<a href="https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook" target="_blank">https://cmssdt.cern.ch/SDT/cgi-bin/github_webhook</a>) for every valid comment added to GitHub pull requests.
Processes GitHub comments (e.g., "please test") and manages scheduled/running Jenkins jobs accordingly.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Monitors GitHub PR comments and triggers appropriate Jenkins job actions. Acts as the bridge between GitHub PR interactions and Jenkins test execution.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li> <strong>Real-time GitHub webhook processing</strong> for PR comments</li>
  <li> <strong>Automated job scheduling/killing</strong> based on comment commands (e.g., "please test")</li>
  <li> <strong>Built-in retry mechanism</strong> (3 retries) for transient failures</li>
</ul>

<h3 style="color:#e67e22;">🔍 Troubleshooting if this job fails:</h3>
<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>📋 <strong>Check the console output</strong> for specific error messages - most failures are GitHub API or network connectivity issues</li>
  <li>🔄 <strong>Verify automatic retries</strong> - job is configured with 3 retries for transient failures</li>
  <li>⏳ <strong>For persistent SSH timeout failures</strong>, wait 1-2 hours as the job may recover when network connectivity is restored</li>
  <li>⚙️ <strong>If failures persist beyond 3 hours</strong>, consider temporarily disabling and re-enabling the job</li>
  <li>🔗 <strong>Check GitHub webhook configuration</strong> at the webhook URL if multiple PRs are affected</li>
</ol>
<br>
<h3 style="color:#3498db;">❓ Frequently Asked Questions</h3>
<div style="font-size:14px; line-height:1.6; background-color:#f8f9fa; padding:15px; border-left:4px solid #3498db; border-radius:5px;">
  <p><b>Q:</b> Job 'cms-sw/cmssw #****' failed. What should I do?</p>
  <p><b>A:</b> The job is configured with multiple retries. In case of GitHub or network glitches, it will automatically recover. If it continues failing, check the logs. Most failures are due to GitHub/SSH connection issues and will resolve automatically.</p>
  
  <p style="margin-top:15px;"><b>Q:</b> Job failed with SSH timeout. How should I proceed?</p>
  <p><b>A:</b> The job will retry 3 times to recover. If it keeps failing for several hours, it's better to disable it temporarily and re-enable once the underlying issue is resolved (e.g., when GitHub is back online or CERN network is working again).</p>
</div>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>This bot processes GitHub comments and manages Jenkins test execution. Most failures are transient and resolve automatically through built-in retry mechanisms.</i>
</p>

**Project is `enabled`.**

**Upstream projects:**
* [check-future-commit-prs](#check-future-commit-prs):
* [cms-bot](#cms-bot):
* [compare-root-files-short-matrix](#compare-root-files-short-matrix):
* [github-webhook](#github-webhook):

**Downstream projects:**
* [abort-pr-tests](#abort-pr-tests):
* [cms-bot](#cms-bot):
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [query-new-data-repo-issues](#query-new-data-repo-issues):
* [run-pr-code-checks](#run-pr-code-checks):

**Sub-projects:**
* [ib-schedule-pr-tests](#ib-schedule-pr-tests):
* [abort-pr-tests ](#abort-pr-tests ):
* [run-pr-code-checks](#run-pr-code-checks):
* [query-new-data-repo-issues](#query-new-data-repo-issues):
* [cms-bot](#cms-bot):

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
H 2 * * *
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

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [cmsrep-eos-backup](https://cmssdt.cern.ch/jenkins/job/cmsrep-eos-backup)

**Description:** Copy unused Os/archs RPMs to EOS

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 10,22  * *  *
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

**Sub-projects:**
* [cvmfs-cms-install-common](#cvmfs-cms-install-common):
* [cmspkg-clone](#cmspkg-clone):
* [cvmfs-cms-install-cms](#cvmfs-cms-install-cms):
* [cvmfs-cms-install-COMP-python](#cvmfs-cms-install-COMP-python):
* [ib-install-cvmfs](#ib-install-cvmfs):
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

## [cvmfs-cms-check-and-update-gen-model_config](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gen-model_config)

**Description:** This job checks and updates generators model configurations



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
```

---

## [cvmfs-cms-check-and-update-gen-tar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gen-tar)

**Description:** This job checks and updates generators model configurations



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
```

---

## [cvmfs-cms-check-and-update-gridpacks](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gridpacks)

**Description:** This job checks and updates gridpacks based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_rsync_generator_package_from_eos_individual.sh


**Project is `disabled`.**

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

## [cvmfs-cms-check-and-update-gridpacks-new-generation](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-gridpacks-new-generation)

**Description:** This job checks and updates gridpacks based on 
<br> https://github.com/bockjoo/cvmfs-cms-install-scripts/blob/master/cron_rsync_generator_package_from_eos_individual.sh


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

## [cvmfs-cms-check-and-update-metadata](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-metadata)

**Description:** Job to deploy the contents of https://gitlab.cern.ch/cms-analysis-corrections to /cvmfs/cms-griddata.cern.ch/cat

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

## [cvmfs-cms-check-and-update-premixPUlist](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-and-update-premixPUlist)

**Description:** This job checks and updates premixPUlist
<br>https://its.cern.ch/jira/browse/CMSVOC-616</br>



**Project is `enabled`.**

**Upstream projects:**
* [eos-premixPUlist-list](#eos-premixPUlist-list):

**Downstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Sub-projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

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

## [cvmfs-cms-check-eos-dir](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-eos-dir)

**Description:** This job checks/compares EOS directory with cvmfs nd trigger the sync if there are changes



**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-and-update-gen-model_config](#cvmfs-cms-check-and-update-gen-model_config):
* [cvmfs-cms-check-and-update-gen-tar](#cvmfs-cms-check-and-update-gen-tar):
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Downstream projects:**
* [cvmfs-cms-sync-eos-dir](#cvmfs-cms-sync-eos-dir):

**Sub-projects:**
* [cvmfs-cms-sync-eos-dir](#cvmfs-cms-sync-eos-dir):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-cms-check-gridpacks-untar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-check-gridpacks-untar)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-deploy-gridpacks-untar](#cvmfs-cms-deploy-gridpacks-untar):

**Sub-projects:**
* [cvmfs-cms-deploy-gridpacks-untar](#cvmfs-cms-deploy-gridpacks-untar):

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
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

## [cvmfs-cms-deploy-gridpacks-untar](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-deploy-gridpacks-untar)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-gridpacks-untar](#cvmfs-cms-check-gridpacks-untar):

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

## [cvmfs-cms-reseed](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-reseed)

**Description:** This rebuild the RPM DB on cvmfs by re-seeding the system packages. This is needed in order to get the newer features provides by new versions of system packages.<br/>
For exmaple, sometime an expternal builds and installs fine for IBs but when build and uploaded for Release then we might get install errors like<br/>
<pre>
  error: Failed dependencies:
    libcrypto.so.3(OPENSSL_3.2.0)(64bit) is needed by external+py3-cryptography+45.0.4-bbe4987a111798bac173b7ad286acc92-1-1.x86_64
</pre>

this is because we might have updated our cmssw-elX image and it might have a newer feature of OpenSSL. As RPM database was generated using old image so that is why it does not contain the new feature. Running this job will use the new image and re-seed the OpenSSL.


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

## [cvmfs-cms-reseed-architecture](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-reseed-architecture)

**Description:** This job is to reseed a already installed architecture.
This is needed when we have updated the packages to be seeded from the system installation.


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

## [cvmfs-cms-sync-eos-dir](https://cmssdt.cern.ch/jenkins/job/cvmfs-cms-sync-eos-dir)

**Description:** This job syncs an EOS directory on to CVMFS



**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-cms-check-eos-dir](#cvmfs-cms-check-eos-dir):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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
* [update-release-map](#update-release-map):

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

## [cvmfs-deploy-py23](https://cmssdt.cern.ch/jenkins/job/cvmfs-deploy-py23)

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

## [cvmfs-install-cuda](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-cuda)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [cvmfs-project-install-cuda](#cvmfs-project-install-cuda):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [cvmfs-install-fix-cuda](https://cmssdt.cern.ch/jenkins/job/cvmfs-install-fix-cuda)

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

## [cvmfs-list-catalogs](https://cmssdt.cern.ch/jenkins/job/cvmfs-list-catalogs)

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

## [cvmfs-project-install-cuda](https://cmssdt.cern.ch/jenkins/job/cvmfs-project-install-cuda)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-install-cuda](#cvmfs-install-cuda):

**Sub-projects:**
* [cvmfs-install-cuda](#cvmfs-install-cuda):

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

## [cvmfs-update-proot](https://cmssdt.cern.ch/jenkins/job/cvmfs-update-proot)

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

## [cvmfs-update-qemu](https://cmssdt.cern.ch/jenkins/job/cvmfs-update-qemu)

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

## [cvmfs_publish_remote_dir](https://cmssdt.cern.ch/jenkins/job/cvmfs_publish_remote_dir)

**Description:** This jobs install an IB on /cvmfs/cms-ib.cern.ch.

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

## [docker-images-to-github](https://cmssdt.cern.ch/jenkins/job/docker-images-to-github)

**Description:** This job migrates exisiting images in dockerhub to the github registry.<br/>
<br/>


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

## [docker-issue-comment](https://cmssdt.cern.ch/jenkins/job/docker-issue-comment)

**Description:** avalenzu: reporting back on existing issues

**Project is `enabled`.**

**Upstream projects:**
* [build-docker-container](#build-docker-container):
* [docker-watch-pkgs](#docker-watch-pkgs):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [docker-packages-info](https://cmssdt.cern.ch/jenkins/job/docker-packages-info)

**Description:** avalenzu: testing docker image comparison

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

## [docker-watch-pkgs](https://cmssdt.cern.ch/jenkins/job/docker-watch-pkgs)

**Description:** avalenzu: testing watching concrete pkgs

**Project is `enabled`.**

**Upstream projects:**
* [docker-watch-pkgs](#docker-watch-pkgs):

**Downstream projects:**
* [docker-issue-comment](#docker-issue-comment):
* [docker-watch-pkgs](#docker-watch-pkgs):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 15 * * 0
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

## [doxygen-zip-to-squashFS](https://cmssdt.cern.ch/jenkins/job/doxygen-zip-to-squashFS)

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

## [eos-premixPUlist-list](https://cmssdt.cern.ch/jenkins/job/eos-premixPUlist-list)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Sub-projects:**
* [cvmfs-cms-check-and-update-premixPUlist](#cvmfs-cms-check-and-update-premixPUlist):

**Triggers from:** []


**Periodic builds:**
```bash
H H * * *
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
Not periodically build
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

## [es-insert-failure-data](https://cmssdt.cern.ch/jenkins/job/es-insert-failure-data)

**Description:** Insert record into ES linking Issue/PR and error in IB

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

## [es-push-pkginfo](https://cmssdt.cern.ch/jenkins/job/es-push-pkginfo)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H 3 * * *
H 15 * * *
```

---

## [es_send_cached_payload](https://cmssdt.cern.ch/jenkins/job/es_send_cached_payload)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/10 * * * *
```

---

## [find-cmssw-build-packages](https://cmssdt.cern.ch/jenkins/job/find-cmssw-build-packages)

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

## [find-cmssw-install-packages](https://cmssdt.cern.ch/jenkins/job/find-cmssw-install-packages)

**Description:** avalenzu(testing): dummy job for builid cmssw images.

**Project is `enabled`.**

**Upstream projects:**
* [trigger-docker-packages-check](#trigger-docker-packages-check):

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

## [fix-rpm-db](https://cmssdt.cern.ch/jenkins/job/fix-rpm-db)

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

## [git-notify-build-results](https://cmssdt.cern.ch/jenkins/job/git-notify-build-results)

**Description:** Triggered when new IB results are available and send a Mattermost notification if there are new failures

**Project is `disabled`.**

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
* [query-new-data-repo-issues](#query-new-data-repo-issues):

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
* [query-new-data-repo-issues](#query-new-data-repo-issues):

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

## [github-monitor-api](https://cmssdt.cern.ch/jenkins/job/github-monitor-api)

**Description:** PyGitHub API at: https://pygithub.readthedocs.io/en/latest/github.html

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
* * * * *
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
* [git-notify-build-results](#git-notify-build-results):
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
* [git-notify-build-results](#git-notify-build-results):

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
H * * * *
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

## [hlt-p2-timing-data-sync](https://cmssdt.cern.ch/jenkins/job/hlt-p2-timing-data-sync)

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

## [ib-inject-profiling-data](https://cmssdt.cern.ch/jenkins/job/ib-inject-profiling-data)

**Description:** Inject the FastTimerService files to CMSMonit


**Project is `enabled`.**

**Upstream projects:**
* [ib-run-profiling-gpu](#ib-run-profiling-gpu):

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

## [ib-reproduce-unittests](https://cmssdt.cern.ch/jenkins/job/ib-reproduce-unittests)

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

## [ib-run-allocmon-profiling](https://cmssdt.cern.ch/jenkins/job/ib-run-allocmon-profiling)

**Description:** Runs FastTimerService and Igprof on the RECO and PAT steps for high pileup workflow.



**Project is `enabled`.**

**Upstream projects:**
* [ib-run-profiling](#ib-run-profiling):

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

## [ib-run-class-versions](https://cmssdt.cern.ch/jenkins/job/ib-run-class-versions)

**Description:** Runs edm class version checks for IB

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

## [ib-run-gpu-qa](https://cmssdt.cern.ch/jenkins/job/ib-run-gpu-qa)

**Description:** None

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

## [ib-run-gpu-relvals](https://cmssdt.cern.ch/jenkins/job/ib-run-gpu-relvals)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-run-relvals](#ib-run-relvals):

**Sub-projects:**
* [ib-run-relvals](#ib-run-relvals):

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

## [ib-run-hlt-p2-timing](https://cmssdt.cern.ch/jenkins/job/ib-run-hlt-p2-timing)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-circle-dataset](#update-circle-dataset):

**Sub-projects:**
* [update-circle-dataset](#update-circle-dataset):

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

## [ib-run-pr-hlt_p2_integration](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-hlt_p2_integration)

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

## [ib-run-pr-hlt_p2_timing](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-hlt_p2_timing)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [update-circle-dataset](#update-circle-dataset):

**Sub-projects:**
* [update-circle-dataset](#update-circle-dataset):

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
* [update-circle-dataset](#update-circle-dataset):

**Sub-projects:**
* [update-circle-dataset](#update-circle-dataset):

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

## [ib-run-pr-unittests](https://cmssdt.cern.ch/jenkins/job/ib-run-pr-unittests)

**Description:** Build mutiple pull requests. 
Run cmssw GPU unit tests

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



**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-run-allocmon-profiling](#ib-run-allocmon-profiling):
* [run-vtune-profiling](#run-vtune-profiling):
* [sync-profile-data](#sync-profile-data):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-profiling-gpu](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling-gpu)

**Description:** Runs NSYS on the RECO and PAT steps for high pileup workflow.



**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [ib-inject-profiling-data](#ib-inject-profiling-data):
* [sync-profile-data](#sync-profile-data):

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ib-run-profiling-mem](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling-mem)

**Description:** Runs Jemalloc memory profiling on the RECO and PAT steps for high pileup workflow.



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

## [ib-run-profiling-mem-GC](https://cmssdt.cern.ch/jenkins/job/ib-run-profiling-mem-GC)

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
<a href="https://cmssdt.cern.ch/SDT/html/cmssdt-ib/">IB page's</a> Q/A section.<br> If this job fails, logs can be found under 
<a href=https://cmssdt.cern.ch/buildlogs/>https://cmssdt.cern.ch/buildlogs//os_arch_compiler/www/week_day/...</a><br>
<br>
Sometimes it can hang during scp copy / ssh. This failure can be found by looking for a gap of several hours in the log file during scp / ssh.<br>
If the job runs for more than several hours, the procedure is to login to build node, check which job is hanging and take the appropiate action, if necessary.

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-gpu-qa](#ib-run-gpu-qa):
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
* [ib-run-gpu-relvals](#ib-run-gpu-relvals):
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

## [ib-test-lto](https://cmssdt.cern.ch/jenkins/job/ib-test-lto)

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

## [ib-test-lto-openstack](https://cmssdt.cern.ch/jenkins/job/ib-test-lto-openstack)

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

## [ib-test-lto-openstack-hlt](https://cmssdt.cern.ch/jenkins/job/ib-test-lto-openstack-hlt)

**Description:** avalenzu: To be removed soon. HLT test can run as part of https://cmssdt.cern.ch/jenkins/job/ib-test-lto-openstack/

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

## [install-qemu](https://cmssdt.cern.ch/jenkins/job/install-qemu)

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

## [jenkins-build-externals-for-testing](https://cmssdt.cern.ch/jenkins/job/jenkins-build-externals-for-testing)

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
* [jenkins-infrastructure-sanity-check](#jenkins-infrastructure-sanity-check):

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
* [kill-stuck-pr-test](#kill-stuck-pr-test):

**Sub-projects:**
* [kill-stuck-pr-test](#kill-stuck-pr-test):

**Triggers from:** []


**Periodic builds:**
```bash
H/30 * * * * 
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

## [jenkins-infrastructure-sanity-check](https://cmssdt.cern.ch/jenkins/job/jenkins-infrastructure-sanity-check)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-infrastructure-sanity-check](#jenkins-infrastructure-sanity-check):

**Downstream projects:**
* [jenkins-disable-nodes](#jenkins-disable-nodes):
* [jenkins-infrastructure-sanity-check](#jenkins-infrastructure-sanity-check):

**Sub-projects:**
* [jenkins-infrastructure-sanity-check](#jenkins-infrastructure-sanity-check):
* [jenkins-disable-nodes](#jenkins-disable-nodes):

**Triggers from:** []


**Periodic builds:**
```bash
H 11 * * *
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

## [jenkins-monitor-queue](https://cmssdt.cern.ch/jenkins/job/jenkins-monitor-queue)

**Description:** None

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

## [jenkins-process](https://cmssdt.cern.ch/jenkins/job/jenkins-process)

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

## [jenkins-s3-test](https://cmssdt.cern.ch/jenkins/job/jenkins-s3-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-s3-test](#jenkins-s3-test):

**Downstream projects:**
* [jenkins-s3-test](#jenkins-s3-test):

**Sub-projects:**
* [jenkins-s3-test](#jenkins-s3-test):

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

## [jenkins-test-condor](https://cmssdt.cern.ch/jenkins/job/jenkins-test-condor)

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

## [jenkins-test-full-pgo](https://cmssdt.cern.ch/jenkins/job/jenkins-test-full-pgo)

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

## [jenkins-test-java-version](https://cmssdt.cern.ch/jenkins/job/jenkins-test-java-version)

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

## [jenkins-test-job3](https://cmssdt.cern.ch/jenkins/job/jenkins-test-job3)

**Description:** Jenkins tests Project to test jenkins functionality.

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

## [jenkins-test-lto](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lto)

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

## [jenkins-test-lumi](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lumi)

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

## [jenkins-test-lumi-connection](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lumi-connection)

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

## [jenkins-test-lumi-xrootd](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lumi-xrootd)

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

## [jenkins-test-lxplus-env](https://cmssdt.cern.ch/jenkins/job/jenkins-test-lxplus-env)

**Description:** testing lxplus env.
Delete me as soon as possible

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

## [jenkins-test-ngt-amd](https://cmssdt.cern.ch/jenkins/job/jenkins-test-ngt-amd)

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
H/30 * * * *
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

## [jenkins-test-pgo](https://cmssdt.cern.ch/jenkins/job/jenkins-test-pgo)

**Description:** avalenzu: Doing some cleanup (06-12-2024) - Possibly to be deleted.

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

## [kill-stuck-pr-test](https://cmssdt.cern.ch/jenkins/job/kill-stuck-pr-test)

**Description:** Kill stuck PR testing job and update PR accordingly

**Project is `enabled`.**

**Upstream projects:**
* [jenkins-elasticsearch-monitor](#jenkins-elasticsearch-monitor):

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

## [lumi-image-update](https://cmssdt.cern.ch/jenkins/job/lumi-image-update)

**Description:** Update sif image for LUMI HPC

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

## [ngt-create-session](https://cmssdt.cern.ch/jenkins/job/ngt-create-session)

**Description:** Job to create NGT Session and add it a jenkins agent

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

**Description:** Find all hosts in an hostgroup and add them to jenkins. This job needs to run `ai-*` commands
to be run on aiadm nodes. As due to 2FA we can not do a batch login to aiadm nodes so `ai-*`
commands are run via a acrontab job <br/>
~cmsbuild/private/jenkins/scripts/process.sh ~/private/jenkins


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

## [query-new-data-repo-issues](https://cmssdt.cern.ch/jenkins/job/query-new-data-repo-issues)

**Description:** Processes a github issue to check if it is requesting the creation of a new data repository.
If the issue is not requesting any release, it ignores it. 

**Project is `enabled`.**

**Upstream projects:**
* [cms-bot](#cms-bot):

**Downstream projects:**
* [github-hooks](#github-hooks):
* [github-labels](#github-labels):

**Sub-projects:**
* [github-labels,github-hooks](#github-labels,github-hooks):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
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

## [release-rsync-reco-profiling](https://cmssdt.cern.ch/jenkins/job/release-rsync-reco-profiling)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [release-run-reco-profiling](#release-run-reco-profiling):

**Downstream projects:**

**Sub-projects:**

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
* [release-rsync-reco-profiling](#release-rsync-reco-profiling):

**Sub-projects:**
* [release-rsync-reco-profiling](#release-rsync-reco-profiling):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [run-container-stageout](https://cmssdt.cern.ch/jenkins/job/run-container-stageout)

**Description:** This job tests submission to multiple sites. Some of them are expected to fail.

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
* [ib-run-profiling](#ib-run-profiling):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [s3-run-speed-test](https://cmssdt.cern.ch/jenkins/job/s3-run-speed-test)

**Description:** None

**Project is `disabled`.**

**Upstream projects:**

**Downstream projects:**
* [s3-speet-test](#s3-speet-test):

**Sub-projects:**
* [s3-speet-test](#s3-speet-test):

**Triggers from:** []


**Periodic builds:**
```bash
H 22 * * *
```

---

## [s3-speet-test](https://cmssdt.cern.ch/jenkins/job/s3-speet-test)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [s3-run-speed-test](#s3-run-speed-test):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [set-shifter](https://cmssdt.cern.ch/jenkins/job/set-shifter)

**Description:** Run this job at the start of your shift to receive MM pings from failed builds/tests

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

**Triggers from:** ['update-github-pages']


**Periodic builds:**
```bash
Not periodically build
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
* [ib-run-profiling-mem-GC](#ib-run-profiling-mem-GC):

**Downstream projects:**
* [update-circle-dataset](#update-circle-dataset):

**Sub-projects:**
* [update-circle-dataset](#update-circle-dataset):

**Triggers from:** ['ib-run-igprof', 'ib-run-profiling', 'ib-run-profiling-mem', 'ib-run-profiling-mem-GC']


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

## [test-build-release](https://cmssdt.cern.ch/jenkins/job/test-build-release)

**Description:** avalenzu: Testing build error in release https://github.com/cms-sw/cmssw/issues/41976 for el8_amd64_gcc12

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

## [tmp-node-get-config](https://cmssdt.cern.ch/jenkins/job/tmp-node-get-config)

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

## [trigger-docker-packages-check](https://cmssdt.cern.ch/jenkins/job/trigger-docker-packages-check)

**Description:** This job checks for changes in the parent image. If there are changes, it triggers the `build-docker-container` job so that our based image is updated and uploaded to the registry.

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [find-cmssw-install-packages](#find-cmssw-install-packages):

**Sub-projects:**
* [find-cmssw-install-packages](#find-cmssw-install-packages):

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

## [update-circle-dataset](https://cmssdt.cern.ch/jenkins/job/update-circle-dataset)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ib-run-hlt-p2-timing](#ib-run-hlt-p2-timing):
* [ib-run-pr-hlt_p2_timing](#ib-run-pr-hlt_p2_timing):
* [ib-run-pr-profiling](#ib-run-pr-profiling):
* [sync-profile-data](#sync-profile-data):

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

## [update-cmssdt-circles](https://cmssdt.cern.ch/jenkins/job/update-cmssdt-circles)

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

## [update-external-elastic-stats](https://cmssdt.cern.ch/jenkins/job/update-external-elastic-stats)

**Description:** This job process resource metrics jsons for externals

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
* [summary-of-merged-prs](#summary-of-merged-prs):

**Sub-projects:**

**Triggers from:** ['cleanup-cms-sw-io-history', 'ib-build-logs']


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
* [cvmfs-cms-update-releases-map](#cvmfs-cms-update-releases-map):
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

## [vtune-check](https://cmssdt.cern.ch/jenkins/job/vtune-check)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
H/20 * * * *
```

---

## [vtune-cmssw-cleanup](https://cmssdt.cern.ch/jenkins/job/vtune-cmssw-cleanup)

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

