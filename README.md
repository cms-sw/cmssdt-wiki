# Updating readme

# New newcomer's guide

```text
- e-group:

  * ai-admins: get access GitLab repos and foreman

  * cms-sdt-aibox-admins: Add access CMS SDT Build openstack project

  * cms-git-vocmssdt-admins: To have access to puppet gitlab repos

  * cms-sdt-logs: For jenkins errors logs


- get gibhub user in cms-bot/categories as L2 of externals

- update puppet recipe (jenkins, vocmssdt, vocmssdt/sdt/builders etc) to have user CERN access added as administrator

- Update Jenkins configuration to allow all admin rights to user

- Add user in github teams so that he/she is able to manage github repositories

  * https://github.com/orgs/cms-data/teams/uploaders

  * https://github.com/orgs/cms-externals/teams/developers

- Hypernews fourms to subscribe

  * Computing Project Announcements
  * Software Distribution Tools Discussions
  * CERN Computing Announcements
  * External Package Management
  * Offline Announcements
  * Release Integration
  * Software Development
  * Software Development Tools
  * Software Release Announcements
  * Computing Tools  



------------------

1. top level page from there you can find links to various services we maintain:  https://cmssdt.cern.ch/SDT/
2. github repositories:
   - our main projects in github are
     - https://github.com/cms-sw
     - https://github.com/cms-externals 
     - https://github.com/cms-data

  - main repositories we work on day to day basis:
    * https://github.com/cms-sw/cmssw (CMS offilce code C++/python)
    * https://github.com/cms-sw/cmsdist: collection of RPM spec files (kind of build recipes for building externals and cmssw)
    * https://github.com/cms-sw/pkgtool: a home make tools for building externals. It is written in Python which uses cmsdist to generate rpms
    * https://github.com/cms-sw/cmspkg: A home made tool to replace apt-get to upload and distribute rpms
    * https://github.com/cms-sw/cms-bot: Collection of bash/python scripts for make small tasks/jobs we run in Jenkins (cmssdt.cern.ch/jenkins)

3. Openstack project for cmssdt: https://openstack.cern.ch CMS SDT Build
    I think you need to be in an e-group to access it. I will take care of it.

4. Foreman for managing hostgroups and puppet configurations: https://judy.cern.ch/

5. Puppet configurations for our host groups are maintain in gitlab:
    https://gitlab.cern.ch/ai/it-puppet-hostgroup-vocmssdt
    https://gitlab.cern.ch/ai/it-puppet-module-cmssw
 
   We use devel branch of these repos.

-------------------------

   CMSSW packages and categories map is availalble here https://github.com/cms-sw/cms-bot/blob/master/categories.py

   This file also havd the github names of users who are responsible for these categories and how can run tests.

------------------------------

  These are the commands one can run on our build/dev machines to build RPMs for our externals.

1. clone the repositories needed to build (cmsdist for RPM spec files and pkgtools for cmsBuild command to build RPM)
git clone git@github.com:cms-sw/cmsdist
git clone git@github.com:cms-sw/pkgtools

2. Checkout the correct cmsdist branch. I am using here the default branch i.e. IB/CMSSW_9_1_X/gcc530 but you can use any branch you are interested. You can find out the cmsdist branches and archs in https://github.com/cms-sw/cms-bot/blob/master/config.map file. Use the correct branch for correct architecture. For example you can not use IB/CMSSW_9_1_X/gcc530 to build slc6_amd64_gcc700.

   pushd cmsdst
     git checkout IB/CMSSW_9_1_X/gcc530
   popd

3. If external spec file already exists then update it or if it is a new package then create a new spec file.
4. build your updated/new package. For example following command should build boost external for slc6_amd64_gcc530 arch using cms.week0 repository

  ./pkgtools/cmsBuild -a slc6_amd64_gcc530 --repo cms -i build -j 10 build boost

After this you should have RPMs build/install in `pwd`/build directory. The logs of the build are available under `pwd`/build/BUILD/slc6_amd64_gcc530/xxxx directories.

  Once have some time then try to ply with it. For example just add a empty line in root.spec and try to build. Ideally when we test by hand then we build cmssw-tool-conf package (which depends on every thing). So if root package is changed then update root.spec and build cmssw-tool-conf to get every package rebuilt due to root.spec update.

```

