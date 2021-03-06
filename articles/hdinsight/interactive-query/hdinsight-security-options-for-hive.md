---
title: Beveiligings opties voor Hive in azure HDInsight
description: Beveiligings opties voor-onderdelen in standaard-en ESP-clusters.
author: hrasheed-msft
ms.author: hrasheed
ms.reviewer: jasonh
ms.service: hdinsight
ms.custom: hdinsightactive
ms.topic: conceptual
ms.date: 10/02/2020
ms.openlocfilehash: 8573ba99b7aef13025b4f175640ac9583ad5a679
ms.sourcegitcommit: d767156543e16e816fc8a0c3777f033d649ffd3c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/26/2020
ms.locfileid: "92545953"
---
# <a name="security-options-for-hive-in-azure-hdinsight"></a>Beveiligings opties voor Hive in azure HDInsight

In dit document worden de aanbevolen beveiligings opties voor Hive in HDInsight beschreven. Deze opties kunnen worden geconfigureerd via Ambari.

![Beveiligings opties voor Hive](./media/hdinsight-security-options-for-hive/security-options-hive.png "Beveiligings opties voor Hive")

## <a name="hiveserver2-authentication"></a>HiveServer2-verificatie

Voor standaard clusters is de aanbevolen instelling voor HiveServer2-verificatie de standaard waarde die geen is. Als u verificatie wilt inschakelen, kunt u het beste een upgrade uitvoeren naar een [ESP](../domain-joined/hdinsight-security-overview.md) -cluster (Enterprise Security package). 

Voor ESP-clusters is [Kerberos](https://web.mit.edu/Kerberos/) -verificatie standaard ingeschakeld. Pluggable verificatie modules (PAM) en aangepaste verificatie schema's worden niet ondersteund.

## <a name="hiveserver2-authorization"></a>HiveServer2-autorisatie

Voor standaard clusters is de standaard instelling geen. [SqlStdAuth (op SQL-standaarden gebaseerde autorisatie)](https://cwiki.apache.org/confluence/display/Hive/SQL+Standard+based+hive+authorization) kan worden ingeschakeld. Autorisatie via [Apache zwerver](https://ranger.apache.org/) wordt niet ondersteund voor standaard clusters. U kunt het beste een upgrade uitvoeren naar een ESP-cluster voor de autorisatie van zwerver. 

Voor ESP-clusters is de autorisatie via zwerver standaard ingeschakeld. 


## <a name="ssl-encryption-for-hiveserver2"></a>SSL-versleuteling voor HiveServer2

Het inschakelen van Hiveserver2 SSL wordt niet aanbevolen voor de standaard-of ESP-clusters. SSL is ingeschakeld op de gateway. [Versleuteling in transit](../domain-joined/encryption-in-transit.md) kan worden ingeschakeld om de communicatie tussen de cluster knooppunten te versleutelen met behulp van [Internet Protocol Security (IPSec)](https://en.wikipedia.org/wiki/IPsec).


## <a name="next-steps"></a>Volgende stappen
* [Overzicht van HiveServer2-verificatie](https://cwiki.apache.org/confluence/display/Hive/Setting+up+HiveServer2#SettingUpHiveServer2-Authentication/SecurityConfiguration)
* [Overzicht van HiveServer2-autorisatie](https://cwiki.apache.org/confluence/display/Hive/LanguageManual+Authorization#:~:text=%20Overview%20of%20Authorization%20Modes%20%201%201,and%20Apache%20Sentry%20are%20apache%20projects...%20More%20)
* [Validatie van op SQL-standaarden gebaseerde Hive inschakelen](https://community.cloudera.com/t5/Community-Articles/Getting-started-with-SQLStdAuth/ta-p/244263)
* [Apache zwerver met hive](../domain-joined/apache-domain-joined-run-hive.md)
