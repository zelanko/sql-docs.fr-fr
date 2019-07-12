---
title: Limitations de sécurité pour SQL Server sur Linux
description: Cet article décrit SQL Server sur les restrictions de Linux.
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 01/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.openlocfilehash: 033390cb2776988179fc40b2f3a2d9e65b98a05a
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834723"
---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitations de sécurité pour SQL Server sur Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Actuellement, SQL Server sur Linux présente les limitations suivantes :

* Une stratégie de mot de passe standard est fournie. La seule option que vous pouvez configurer est l’option MUST_CHANGE.  
* La gestion de clés extensible (EKM) n’est pas prise en charge. 
* Le stockage des clés dans Azure Key Vault n’est pas pris en charge.
* SQL Server génère son propre certificat auto-signé pour sécuriser le processus de connexion. Pour SSL ou TLS, SQL Server peut être configuré pour utiliser un certificat fourni par l'utilisateur. 

Pour plus d’informations sur les fonctionnalités de sécurité disponibles dans SQL Server, consultez le [centre de sécurité pour le moteur de base de données SQL Server et Azure SQL Database](../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md).

## <a name="next-steps"></a>Étapes suivantes

Pour les tâches de sécurité courantes, consultez [prise en main des fonctionnalités de sécurité de SQL Server sur Linux](sql-server-linux-security-get-started.md). Pour obtenir un script pour modifier numéro de port TCP, les répertoires de SQL Server et configurer des traceflags ou le classement, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md)
