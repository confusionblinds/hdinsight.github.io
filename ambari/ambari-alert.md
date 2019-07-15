---
title: Azure HDInsight Solutions | <Feature_Area> | <Problem Type>
description: Learn how to resolve <scenario>
services: hdinsight
author: csunilkumar
ms.author: sunilkc
ms.service: hdinsight
ms.custom: troubleshooting
ms.topic: Ambari Alert
ms.date: 11/04/2018
---
# Azure HDInsight Solutions | Ambari Alerts | Debugging Ambari Alerts

## Troubleshooting Ambari Alerts.
Ambari alert log path ```/var/log/ambari-server/ambari-alerts.log```

## Gathering more information
- Checking if the alCheck if the alerting service is stopped and try starting the service.


Enabling debug log for Ambari alert requires changing following in file ```/etc/ambari-server/conf/log4j.properties```

From 
```
# Log alert state changes
log4j.logger.alerts=INFO,alerts
```
<br>

To <br>
```
# Log alert state changes
log4j.logger.alerts=DEBUG,alert
```

## Issue Description
Getting following Ambari Alerts for livy services.

---
ExecutionFailed: Execution of 'curl -s -o /dev/null -w'%{http_code}' --negotiate -u: -k http://hn1-kcspar.wirvoukot1hebbchksbaxhgtxd.cx.internal.cloudapp.net:8998/sessions | grep 200 ' returned 1. curl: option --negotiate: the installed libcurl version doesn't support this
curl: try 'curl --help' or 'curl --manual' for more information
---

- SSH to one of the head nodes of the cluster, try executing the command ``` curl --negotiate -u: -k http://hn1-kcspar.wirvoukot1hebbchksbaxhgtxd.cx.internal.cloudapp.net:8998/sessions```
- ``` which curl ``` should return the path for curl program confirm if the path is ```/usr/bin/curl``` .
  -   If the output is different from ```/usr/bin/curl``` then default curl has be changed.



