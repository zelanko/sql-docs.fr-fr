---
title: "Limitations de sécurité pour SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit les SQL Server sur les restrictions de Linux."
author: rothja
ms.author: jroth
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.workload: Inactive
ms.openlocfilehash: c197741feeec4e583272b9ef845ee4d337e742c2
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitations de sécurité pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Actuellement, SQL Server sur Linux a les limitations suivantes :

* Une stratégie de mot de passe standard est fournie. La seule option que vous pouvez configurer l’option MUST_CHANGE a.  
* Gestion de clés extensible n’est pas pris en charge. 
* À l’aide des clés stockées dans le coffre de clés Azure n’est pas pris en charge.
* SQL Server génère son propre certificat auto-signé pour le chiffrement des connexions. SQL Server peut être configuré pour utiliser un utilisateur de certificat pour TLS. 

Pour plus d’informations sur les fonctionnalités de sécurité disponibles dans SQL Server, consultez le [centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Étapes suivantes

Pour les tâches de sécurité courantes, consultez [prise en main des fonctionnalités de sécurité de SQL Server sur Linux](sql-server-linux-security-get-started.md). Pour obtenir un script modifier le protocole TCP numéro de port, les répertoires de SQL Server et configurer des traceflags ou le classement, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md).
