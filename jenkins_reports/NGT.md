# [NGT](https://cmssdt.cern.ch/jenkins/view/NGT)

**View description:** None

**View type:** List View

---

# Projects:

## [ngt-check-pods](https://cmssdt.cern.ch/jenkins/job/ngt-check-pods)

**Description:** Check pending jobs for each GPU flavor and <br/>
- Delete all pods except the required min number of pod of GPU flavor if there are no pending jobs <br/>
- Create a new pod (not exceeding max number of pods for a GPU flavor) if there are JOB_BACKLOG_THRESHOLD pending jobs  


**Project is `enabled`.**

**Upstream projects:**

**Downstream projects:**
* [jenkins-delete-node](#jenkins-delete-node):
* [ngt-create-pod](#ngt-create-pod):
* [ngt-delete-pod](#ngt-delete-pod):

**Sub-projects:**
* [jenkins-delete-node](#jenkins-delete-node):
* [ngt-delete-pod](#ngt-delete-pod):
* [ngt-create-pod](#ngt-create-pod):

**Triggers from:** []


**Periodic builds:**
```bash
H/5 * * * *
```

---

## [ngt-check-token](https://cmssdt.cern.ch/jenkins/job/ngt-check-token)

**Description:** This job checks the life of the k8s token. If token expiry days are less then a threshold then this job fails and we need to create a new token for cmsbuild user <br/>
To create a new token (see detail doc at https://ngt.docs.cern.ch/getting-started/#long-lived-tokens ), login to cmsbuild@lxplus and then run <br/>
<pre>
  TOKEN=$(kubectl --context ngt-prod create token --duration=8760h default-editor)
  # This will ask for 2FA, so you need to open the provided URL and browser ( using cmsbuild account and 2FA) and copy the token and paste on the terminal
  kubectl config set-credentials token --token "${TOKEN}"
  kubectl config set-context ngt-token --cluster ngt-prod --user token --namespace ${USER}
</pre>

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

## [ngt-create-jenkins-node](https://cmssdt.cern.ch/jenkins/job/ngt-create-jenkins-node)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ngt-create-pod](#ngt-create-pod):

**Downstream projects:**

**Sub-projects:**

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ngt-create-pod](https://cmssdt.cern.ch/jenkins/job/ngt-create-pod)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ngt-check-pods](#ngt-check-pods):

**Downstream projects:**
* [ngt-create-jenkins-node](#ngt-create-jenkins-node):
* [ngt-delete-pod](#ngt-delete-pod):

**Sub-projects:**
* [ngt-create-jenkins-node](#ngt-create-jenkins-node):
* [ngt-delete-pod](#ngt-delete-pod):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ngt-delete-pod](https://cmssdt.cern.ch/jenkins/job/ngt-delete-pod)

**Description:** None

**Project is `enabled`.**

**Upstream projects:**
* [ngt-check-pods](#ngt-check-pods):
* [ngt-create-pod](#ngt-create-pod):

**Downstream projects:**
* [jenkins-delete-node](#jenkins-delete-node):

**Sub-projects:**
* [jenkins-delete-node](#jenkins-delete-node):

**Triggers from:** []


**Periodic builds:**
```bash
Not periodically build
```

---

## [ngt-list-pods](https://cmssdt.cern.ch/jenkins/job/ngt-list-pods)

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

