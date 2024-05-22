# [Openstack](https://cmssdt.cern.ch/jenkins/view/Openstack)

**View description:** This view contains jobs responsible working with <a href="http://openstack.cern.ch">CERN Openstack</a> (creating, deleting VMs, etc.)

**View type:** List View

---

# Projects:

## [jenkins-delete-node](https://cmssdt.cern.ch/jenkins/job/jenkins-delete-node)

**Description:** Deletes nodes from jenkins and then deletes it on openstack.

**Project is `enabled`.**

**Upstream projects:**
* [grid-shutdown-node](#grid-shutdown-node):
* [lumi-shutdown-node](#lumi-shutdown-node):
* [openstack-delete-vms](#openstack-delete-vms):

**Downstream projects:**

**Sub-projects:**

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

