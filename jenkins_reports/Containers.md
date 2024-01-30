# [Containers](https://cmssdt.cern.ch/jenkins/view/Containers)

**View description:** None

**View type:** List View

---

# Projects:

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
* [check-docker-container](#check-docker-container):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [compare-docker-images](#compare-docker-images):
* [docker-issue-comment](#docker-issue-comment):
* [run-container-tests](#run-container-tests):
* [test-containter-singularity](#test-containter-singularity):

**Sub-projects:**
* [cms-containers-run-cmssw-test](#cms-containers-run-cmssw-test):
* [test-containter-singularity](#test-containter-singularity):
* [run-container-tests](#run-container-tests):
* [compare-docker-images](#compare-docker-images):
* [cms-containers-checks-tags](#cms-containers-checks-tags):
* [check-docker-container](#check-docker-container):
* [docker-issue-comment](#docker-issue-comment):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [check-docker-container](https://cmssdt.cern.ch/jenkins/job/check-docker-container)

**Description:** This job checks for changes in the parent image. If there are changes, it triggers the `build-docker-container` job so that our based image is updated and uploaded to the registry.

**Project is `disabled`.**

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

