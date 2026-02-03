# [Containers](https://cmssdt.cern.ch/jenkins/view/Containers)

**View description:** None

**View type:** List View

---

# Projects:

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

## [cms-auto-build-container](https://cmssdt.cern.ch/jenkins/job/cms-auto-build-container)

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🔧 cms-auto-build-container</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Orchestration job that coordinates automated Docker container builds across multiple repository types. Generates configuration files and triggers parallel container checking jobs for different operating system repositories.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Coordinates and initiates automated Docker container build workflows for different Linux distributions (EL8, EL9, EL10). Acts as a scheduler and orchestrator that distributes container checking tasks across parallel executions.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>Multi-repository orchestration</strong> - manages builds for el8, el9, el10 repositories</li>
  <li>🔹 <strong>Property file generation</strong> - creates configuration files for downstream jobs</li>
  <li>🔹 <strong>Parallel triggering</strong> - initiates multiple check-docker-container jobs simultaneously</li>
  <li>🔹 <strong>Daily scheduling</strong> - runs automatically every day at 10:00 AM</li>
  <li>🔹 <strong>Result aggregation</strong> - monitors and reports on all triggered builds</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 30</li>
    <li><strong>Max Builds to Keep:</strong> 200</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Default Value</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>REPOSITORIES</code></td>
      <td style="border:1px solid #ddd; padding:8px;">el8 el9 el10</td>
      <td style="border:1px solid #ddd; padding:8td;">Space-separated list of repository types to process</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Daily at 10:00 AM (H 10 * * *)</li>
    <li><strong>Execution Nodes:</strong> Jenkins master only</li>
    <li><strong>Trigger:</strong> Build periodically</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Three-Phase Orchestration:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Configuration Generation</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      rm -f *.txt
      for r in $REPOSITORIES ; do
        echo "REPOSITORY=$r" > $r.txt
      done
    </div>
    <p style="margin:5px 0; font-size:13px;">Creates property files (el8.txt, el9.txt, el10.txt) for each repository</p>
  </li>
  
  <li><strong>Parallel Job Triggering</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Triggers <code>check-docker-container</code> job for each property file</li>
      <li>Executes jobs in parallel using Jenkins property file triggering</li>
      <li>Each job receives <code>REPOSITORY=elX</code> parameter from corresponding .txt file</li>
    </ul>
  </li>
  
  <li><strong>Result Monitoring</strong>:
    <ul style="margin:5px 0 5px 20px;">
      <li>Blocks until all triggered jobs complete</li>
      <li>Aggregates results from all parallel executions</li>
      <li>Sets overall build status based on worst-performing downstream job</li>
    </ul>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 Trigger Configuration:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>Job Triggering Logic:</strong><br>
    1. <strong>Target Job</strong>: check-docker-container<br>
    2. <strong>File Pattern</strong>: *.txt (matches el8.txt, el9.txt, el10.txt)<br>
    3. <strong>Blocking</strong>: Waits for all triggered jobs to complete<br>
    4. <strong>Status Mapping</strong>:<br>
       • Failure if any downstream job fails<br>
       • Unstable if any downstream job is unstable<br>
       • Success only if all downstream jobs succeed<br>
    5. <strong>Empty Handling</strong>: No trigger if no .txt files exist
  </p>
</div>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>Orchestrator Only</strong>: This job doesn't build containers directly, it coordinates other jobs</li>
  <li>⚠️ <strong>Master Node Requirement</strong>: Must run on Jenkins master for triggering capabilities</li>
  <li>🔗 <strong>Downstream Dependency</strong>: Requires check-docker-container job to exist and function</li>
  <li>⚡ <strong>Parallel Execution</strong>: Multiple check-docker-container jobs run simultaneously</li>
  <li>📅 <strong>Fixed Schedule</strong>: Daily execution may need adjustment based on workload</li>
</ul>

<h3 style="color:#27ae60;">🛠️ Repository Management</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>Supported Repositories:</strong><br>
    • <strong>el8</strong>: Enterprise Linux 8 based containers<br>
    • <strong>el9</strong>: Enterprise Linux 9 based containers<br>
    • <strong>el10</strong>: Enterprise Linux 10 based containers<br><br>
    <strong>Customization:</strong><br>
    • Modify <code>REPOSITORIES</code> parameter to change which repos are checked<br>
    • Add new repository types by extending the parameter list<br>
    • Remove repositories by editing the default value or providing custom parameter
  </p>
</div>

<h3 style="color:#e67e22;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Centralized coordination</strong> - single point for container build scheduling</li>
  <li>✅ <strong>Parallel efficiency</strong> - multiple repository checks run simultaneously</li>
  <li>✅ <strong>Flexible configuration</strong> - easily adjust which repositories are processed</li>
  <li>✅ <strong>Automated scheduling</strong> - daily execution ensures regular checks</li>
  <li>✅ <strong>Result aggregation</strong> - unified status from multiple downstream jobs</li>
</ul>

<h3 style="color:#c0392b;">🔗 Downstream Impact</h3>
<div style="background-color:#ffe6e6; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #c0392b;">
  <p style="margin:0; font-size:13px;">
    <strong>Effect on check-docker-container Jobs:</strong><br>
    1. <strong>Trigger</strong>: Each repository triggers one check-docker-container job<br>
    2. <strong>Parameters</strong>: REPOSITORY parameter set to el8/el9/el10<br>
    3. <strong>Timing</strong>: All jobs start approximately simultaneously<br>
    4. <strong>Resource Usage</strong>: May cause concurrent load on Docker build infrastructure<br>
    5. <strong>Monitoring</strong>: All downstream jobs appear as triggered builds in Jenkins
  </p>
</div>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Container build orchestrator that schedules and coordinates Docker container checks across multiple Linux distribution repositories. Acts as a daily scheduler that initiates parallel container inspection workflows.</i>
</p>

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

## [cms-containers-checks-tags](https://cmssdt.cern.ch/jenkins/job/cms-containers-checks-tags)

**Description:** <h2 style="color:#c0392b; font-weight:bold;">🏷️ cms-containers-checks-tags</h2>

<p style="font-size:14px; color:#2c3e50;">
<b>Description:</b> Automated Docker image tag management job that processes tags.yaml files from the cms-sw/cms-docker repository. Creates new image tags by applying tag inheritance rules and triggers container retagging jobs when needed.
</p>

<h3 style="color:#8e44ad;">🎯 Purpose</h3>
<p style="font-size:14px; line-height:1.6;">
Manages Docker image tag inheritance and propagation by reading tag definitions from YAML files. Automatically creates new image tags based on source→destination mappings and coordinates downstream container retagging operations.
</p>

<h3 style="color:#27ae60;">📌 Key Features</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>🔹 <strong>YAML-based tag definitions</strong> - Processes tags.yaml files for tag inheritance rules</li>
  <li>🔹 <strong>Selective container processing</strong> - Can target specific containers or process all</li>
  <li>🔹 <strong>Automated tag generation</strong> - Creates new tags based on source→destination mappings</li>
  <li>🔹 <strong>Property file generation</strong> - Creates configuration files for downstream retagging jobs</li>
  <li>🔹 <strong>Daily scheduling</strong> - Runs automatically every day at 2:00 AM</li>
</ul>

<h3 style="color:#3498db;">⚙️ Configuration Settings</h3>

<div style="background-color:#f8f9fa; padding:15px; border-radius:5px; border-left:4px solid #3498db; margin:10px 0;">
  <h4 style="margin-top:0; color:#2c3e50;">📊 Build Retention</h4>
  <ul style="margin:5px 0;">
    <li><strong>Strategy:</strong> Log Rotation</li>
    <li><strong>Days to Keep Builds:</strong> 7</li>
    <li><strong>Max Builds to Keep:</strong> 30</li>
  </ul>

  <h4 style="color:#2c3e50;">🎛️ Job Parameters</h4>
  <table style="width:100%; font-size:13px; border-collapse: collapse;">
    <tr style="background-color:#e9ecef;">
      <th style="border:1px solid #ddd; padding:8px;">Parameter</th>
      <th style="border:1px solid #ddd; padding:8px;">Description</th>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>CONTAINER</code></td>
      <td style="border:1px solid #ddd; padding:8td;">Specific container to process (e.g., cc7, slc6, cc8) or all containers</td>
    </tr>
  </table>

  <h4 style="color:#2c3e50;">⚡ Execution Settings</h4>
  <ul style="margin:5px 0;">
    <li><strong>Schedule:</strong> Daily at 2:00 AM (H 2 * * *)</li>
    <li><strong>Execution Nodes:</strong> cmssdt machines</li>
    <li><strong>Build Name:</strong> #${BUILD_NUMBER} ${CONTAINER}</li>
    <li><strong>Workspace:</strong> Delete before build starts</li>
    <li><strong>Trigger:</strong> Build periodically</li>
  </ul>
</div>

<h3 style="color:#e67e22;">🔍 How It Works</h3>

<h4 style="color:#d35400; font-size:15px;">🔄 Three-Phase Tag Processing:</h4>

<ol style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li><strong>Repository & Container Selection</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      if [ "${CONTAINER}" = "" ] ; then
        CONTAINER="cms-docker"
      else
        CONTAINER="cms-docker/${CONTAINER}"
      fi
      git clone --depth 1 git@github.com:cms-sw/cms-docker
    </div>
    <p style="margin:5px 0; font-size:13px;">Determines target path and clones cms-docker repository</p>
  </li>
  
  <li><strong>YAML File Processing</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      for tag in $(find ${CONTAINER} -name 'tags.yaml' -type f) ; do
        repo=$(echo $tag | cut -d/ -f2)
        grep '^\s*[a-zA-Z]' $tag | while IFS= read -r line ; do
          # Parse source→destination mappings
    </div>
    <p style="margin:5px 0; font-size:13px;">Finds and processes all tags.yaml files, extracts tag mappings</p>
  </li>
  
  <li><strong>Tag Generation & File Creation</strong>:
    <div style="background-color:#f0f0f0; padding:8px; border-radius:3px; margin:5px 0; font-family:monospace; font-size:12px;">
      pfile=$(echo cmssw-${repo}-${des} | tr '/:' '--').txt
      PYTHONPATH="" ./cms-docker/bin/retag-image.py -r cmssw/${repo} \
         -s ${src} -d ${des} > ${pfile}
    </div>
    <p style="margin:5px 0; font-size:13px;">Generates property files for each tag mapping using retag-image.py</p>
  </li>
</ol>

<h4 style="color:#d35400; font-size:15px;">📋 YAML Processing Logic:</h4>
<div style="background-color:#fff8e1; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #ffc107;">
  <p style="margin:0; font-size:13px;">
    <strong>tags.yaml Format Example:</strong><br>
    <code>destination_tag: source_tag</code><br>
    <code>latest: 1.0.0</code><br>
    <code>stable: latest</code><br><br>
    <strong>Processing Steps:</strong><br>
    1. <strong>Find files</strong>: Locates tags.yaml in container directories<br>
    2. <strong>Extract repo</strong>: Gets container name from path (2nd component)<br>
    3. <strong>Parse mappings</strong>: Reads each source→destination line<br>
    4. <strong>Generate files</strong>: Creates cmssw-repo-dest.txt property files<br>
    5. <strong>File naming</strong>: Converts special chars (/, :) to double dashes (--)<br>
    6. <strong>Validation</strong>: Only keeps files with SOURCE_IMAGE= content
  </p>
</div>

<h3 style="color:#c0392b;">⚠️ Critical Notes</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px; color:#7f8c8d;">
  <li>❗ <strong>GitHub SSH Access</strong>: Uses git@github.com URLs requiring SSH keys</li>
  <li>⚠️ <strong>File Validation</strong>: Only property files with SOURCE_IMAGE= are kept</li>
  <li>🔒 <strong>Error Handling</strong>: Creates err.log on failures and exits with code 1</li>
  <li>🐍 <strong>Python Script Dependency</strong>: Relies on cms-docker/bin/retag-image.py</li>
  <li>📁 <strong>Special Character Handling</strong>: Converts / and : to -- in filenames</li>
</ul>

<h3 style="color:#27ae60;">🛠️ Container Targeting Options</h3>
<div style="background-color:#e8f4fd; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #3498db;">
  <p style="margin:0; font-size:13px;">
    <strong>CONTAINER Parameter Usage:</strong><br>
    • <strong>Empty</strong>: Processes all containers in cms-docker repository<br>
    • <strong>Specific container</strong> (e.g., <code>cc7</code>): Processes only cms-docker/cc7/<br>
    • <strong>Path structure</strong>: Converts to cms-docker/${CONTAINER}/ for find command<br><br>
    <strong>Example Container Types:</strong><br>
    • cc7 (CentOS 7 based containers)<br>
    • slc6 (Scientific Linux CERN 6)<br>
    • cc8 (CentOS 8 based containers)<br>
    • Other CMS Docker container configurations
  </p>
</div>

<h3 style="color:#e67e22;">🔗 Downstream Triggering</h3>

<h4 style="color:#d35400; font-size:15px;">📋 Generated Property Files:</h4>
<table style="width:100%; font-size:13px; border-collapse: collapse; margin:10px 0;">
  <thead style="background-color:#f1f2f6;">
    <tr>
      <th style="border:1px solid #ddd; padding:8px;">Generated File</th>
      <th style="border:1px solid #ddd; padding:8px;">Example Content</th>
      <th style="border:1px solid #ddd; padding:8px;">Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>cmssw-cc7-latest.txt</code></td>
      <td style="border:1px solid #ddd; padding:8px; font-family:monospace; font-size:11px;">SOURCE_IMAGE=cmssw/cc7:1.0.0<br>TARGET_IMAGE=cmssw/cc7:latest</td>
      <td style="border:1px solid #ddd; padding:8px;">Tags cc7:1.0.0 as cc7:latest</td>
    </tr>
    <tr>
      <td style="border:1px solid #ddd; padding:8px;"><code>cmssw-slc6-stable.txt</code></td>
      <td style="border:1px solid #ddd; padding:8px; font-family:monospace; font-size:11px;">SOURCE_IMAGE=cmssw/slc6:latest<br>TARGET_IMAGE=cmssw/slc6:stable</td>
      <td style="border:1px solid #ddd; padding:8px;">Tags slc6:latest as slc6:stable</td>
    </tr>
  </tbody>
</table>

<h4 style="color:#d35400; font-size:15px;">🎯 Downstream Job Trigger:</h4>
<div style="background-color:#ffe6e6; padding:12px; border-radius:5px; margin:10px 0; border-left:4px solid #c0392b;">
  <p style="margin:0; font-size:13px;">
    <strong>cms-tag-container Triggering:</strong><br>
    1. <strong>Target Job</strong>: cms-tag-container<br>
    2. <strong>File Pattern</strong>: cmssw-*.txt (matches all generated property files)<br>
    3. <strong>Trigger Logic</strong>: One build per property file<br>
    4. <strong>Empty Handling</strong>: No trigger if no .txt files generated<br>
    5. <strong>Purpose</strong>: Each triggered job performs the actual Docker retagging operation
  </p>
</div>

<h3 style="color:#27ae60;">🎯 Benefits</h3>
<ul style="font-size:14px; line-height:1.6; padding-left:20px;">
  <li>✅ <strong>Declarative tag management</strong> - YAML files define tag relationships</li>
  <li>✅ <strong>Automated propagation</strong> - New tags automatically created from sources</li>
  <li>✅ <strong>Selective processing</strong> - Can target specific containers or process all</li>
  <li>✅ <strong>Parallel execution</strong> - Triggers multiple retagging jobs simultaneously</li>
  <li>✅ <strong>Daily maintenance</strong> - Ensures tag consistency with regular execution</li>
</ul>

<hr style="border:1px solid #bdc3c7;"/>

<p style="color:#34495e; font-size:13px;">
💡 <i>Automated Docker tag management system that processes YAML-based tag definitions and coordinates container retagging operations. Maintains tag inheritance and consistency across CMS Docker containers through declarative configuration.</i>
</p>

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

