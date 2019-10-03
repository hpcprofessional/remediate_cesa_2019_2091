# cesa_2019_2091

This module contains a [Bolt Task](https://puppet.com/docs/bolt/latest/bolt.html) that will remediate CVEs described in [CESA-2019:2091](https://lists.centos.org/pipermail/centos-cr-announce/2019-August/006149.html) and parallel issues present on other Enterprise Linux 7 (EL7) platforms. 

#### Table of Contents

1. [Description](#description)
2. [Setup - The basics of getting started with cesa_2019_2091](#setup)
    * [Beginning with cesa\_2019\_2091](#beginning-with-cesa_2019_2091)
3. [Usage - Configuration options and additional functionality](#usage)
4. [Limitations - OS compatibility, etc.](#limitations)
5. [Development - Guide for contributing to the module](#development)

## Description

This remediation addresses the following CVEs:

* [CVE-2018-15686]( https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-15686 )
* [CVE-2018-16866]( https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-16866 )
* [CVE-2018-16888]( https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2018-16888 )

Remediation is performed by using yum to updating key systemd packages to newer versions. Affected systemd RPM packages include:

* systemd
* systemd-libs
* systemd-sysv

## Setup


### Beginning with cesa\_2019\_2091

Using a Puppet file or other method, install in an appropriate place such that the task is visible to your task runner.

  **EXAMPLE** 
  
    $ bolt task show
    
	cesa_2019_2091::remediate   remediates CVE-2018-15686, CVE-2018-16866, and CVE-2018-16888
    


## Usage

Using your prefered method of running bolt tasks, run the task.

   **EXAMPLE**
   
   $ bolt task run cesa\_2019\_2091::remediate -n cent7-1,cent7-2,cent7-3


## Limitations

This remediation relies on yum, yum repositories, and related technologies to update RPM packages.

This remediation updates the relevant RPM packages to the latest available version without additional version checks. If your system remains vulnerable to these CVEs, it is likely sufficiently updated RPMs are **not** available in your yum repository as presntly configured.

This remediation targets the standard systemd packages most likely to be affected by these CVEs. Additional packages which may require attention are described in the relevant [CentOS-CR-announce mailing list announcement](https://lists.centos.org/pipermail/centos-cr-announce/2019-August/006149.html)


## Development

Pull requests welcome

## Release Notes

| Version | Notes                                                              |
| ------- | -------------------------------------------------------------------|
| 0.1.0   | Initial release                                                    |
|         |                                                                    |
