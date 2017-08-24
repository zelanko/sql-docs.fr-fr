---
title: "Limitations de sécurité pour SQL Server sur Linux | Documents Microsoft"
description: "Cette rubrique décrit les SQL Server sur les restrictions de Linux."
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 64da74cc-14bf-4636-a55e-8cc1fce2aaff
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 74357e2741e01e44f0f9d504456fca10f29f78e7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="security-limitations-for-sql-server-on-linux"></a>Limitations de sécurité pour SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../../docs/includes/tsql-appliesto-sslinux-only.md)]

Actuellement, SQL Server sur Linux a les limitations suivantes :

* Une stratégie de mot de passe standard est fournie. La seule option que vous pouvez configurer l’option MUST_CHANGE a.  
* Gestion de clés extensible n’est pas pris en charge. 
* À l’aide des clés stockées dans le coffre de clés Azure n’est pas pris en charge.
* SQL Server génère son propre certificat auto-signé pour le chiffrement des connexions. Actuellement, SQL Server ne peut pas être configuré pour utiliser un utilisateur de certificat pour SSL ou TLS. 

Pour plus d’informations sur les fonctionnalités de sécurité disponibles dans SQL Server, consultez le [centre de sécurité pour le moteur de base de données SQL Server et la base de données SQL Azure](https://msdn.microsoft.com/library/bb510589.aspx).

## <a name="next-steps"></a>Étapes suivantes

Pour les tâches de sécurité courantes, consultez [prise en main des fonctionnalités de sécurité de SQL Server sur Linux](sql-server-linux-security-get-started.md).   
Pour obtenir un script modifier le protocole TCP numéro de port, les répertoires de SQL Server et configurer des traceflags ou le classement, consultez [configurer SQL Server sur Linux avec mssql-conf](sql-server-linux-configure-mssql-conf.md).

