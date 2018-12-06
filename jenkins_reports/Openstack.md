# [Openstack](https://cmssdt.cern.ch/jenkins/view/Openstack)

**View description:** This view contains jobs responsible working with <a href="http://openstack.cern.ch">CERN Openstack</a> (creating, deleting VMs, etc.)

**View type:** List View

---

# Projects:

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

## [openstack-create-volume](https://cmssdt.cern.ch/jenkins/job/openstack-create-volume)

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

## [openstack-delete-vms](https://cmssdt.cern.ch/jenkins/job/openstack-delete-vms)

**Description:** Job to delete openstack instances providing only the name

**Project is `enabled`.**

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

