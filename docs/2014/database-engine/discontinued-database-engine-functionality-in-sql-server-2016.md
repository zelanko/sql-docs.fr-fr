---
title: Fonctionnalités de Moteur de base de données abandonnées dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- VIA protocol
- unsupported features [SQL Server]
- SQL Mail
- discontinued functionality [SQL Server]
- RESTORE WITH DBO_ONLY
- BACKUP WITH PASSWORD
- user instances enabled
- BACKUP WITH MEDIAPASSWORD
- AWE
- SQL-DMO
- '*= and =*'
- 80 compatibility levels
- COMPUTE BY
- user instance timeout
- sp_dropalias
- COMPUTE
- WITH APPEND
- sys.database_principal_aliases
- sp_dboption
- DATABASEPROPERTY
- FASTFIRSTROW hint
- SET DISABLE_DEF_CNST_CHK
ms.assetid: d686cdf0-d11d-4dba-9ec8-de1a5f189f25
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2ebb9b4e3db7cf8f7a19fd582dceb0b19f5c47d0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67463466"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a>Fonctionnalités du moteur de base de données supprimées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités du [!INCLUDE[ssDE](../includes/ssde-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="SQL14"></a>Fonctionnalités supprimées dans[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Le tableau suivant répertorie les fonctionnalités qui ont été supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
|Category|Fonctionnalité supprimée|Remplacement|  
|--------------|--------------------------|-----------------|  
|Niveau de compatibilité|Niveau de compatibilité 90|Les bases de données doivent être définies au moins au niveau de compatibilité 100. Lorsqu'une base de données avec un niveau de compatibilité inférieur à 100 est mise à niveau vers [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], le niveau de compatibilité de la base de données est défini sur la valeur 100 pendant l'opération de mise à niveau.|  
  
## <a name="Denali"></a>Fonctionnalités supprimées dans[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Le tableau suivant répertorie les fonctionnalités qui ont été supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
|Category|Fonctionnalité supprimée|Remplacement|  
|--------------|--------------------------|-----------------|  
|Sauvegarde et restauration|La **sauvegarde {database &#124; log} avec le mot de passe** et la **sauvegarde {Database &#124; log} avec MEDIAPASSWORD** sont abandonnées. La **restauration de {DATABASE &#124; log} avec [Media] Password**continue d’être déconseillée.|None|  
|Sauvegarde et restauration|**RESTAURER {DATABASE &#124; LOG}... AVEC DBO_ONLY**|**RESTORE {DATABASE &#124; LOG}...... AVEC RESTRICTED_USER**|  
|Niveau de compatibilité|niveau de compatibilité 80|Les bases de données doivent être définies au moins au niveau de compatibilité 90.|  
|Options de configuration|`sp_configure 'user instance timeout'` et `'user instances enabled'`|Utilisez la fonctionnalité de base de données locale. Pour plus d’informations, consultez [SqlLocalDB Utility](../tools/sqllocaldb-utility.md)|  
|Protocoles de connexion|La prise en charge du protocole VIA est supprimée.|Utilisez à la place TCP.|  
|Objets de base de données|Clause `WITH APPEND` sur les déclencheurs|Recréez la totalité du déclencheur.|  
|Options de la base de données|`sp_dboption`|`ALTER DATABASE`|  
|Mail|SQL Mail|Utilisez la messagerie de la base de données. Pour plus d’informations, consultez [Database mail](../relational-databases/database-mail/database-mail.md) et [utiliser Database mail au lieu de SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).|  
|Gestion de la mémoire|Extensions Address Windowing Extensions (AWE) 32 bits et prise en charge de l'ajout de mémoire à chaud 32 bits.|Utilisez un système d'exploitation 64 bits.|  
|Métadonnées|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|Programmabilité|Objets SQL-DMO (SQL Server Distributed Management Objects)|SMO (SQL Server Management Objects)|  
|Indicateurs de requête|`FASTFIRSTROW`évit|`OPTION (FAST`*n* `)`.|  
|Serveurs distants|La possibilité pour les utilisateurs de créer des serveurs distants à l'aide de `sp_addserver` est supprimée. 
  `sp_addserver` avec l'option « locale » reste disponible. Des serveurs distants conservés pendant la mise à niveau ou créés par réplication peuvent être utilisés.|Remplacez les serveurs distants à l'aide de serveurs liés.|  
|Sécurité|`sp_dropalias`|Remplacez les alias par une combinaison de comptes d'utilisateurs et de rôles de base de données. Utilisez `sp_dropalias` pour supprimer les alias dans les bases de données mises à niveau.|  
|Sécurité|Le paramètre de version de **PWDCOMPARE** qui représente une valeur d’une connexion [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] antérieure à 2000 est abandonné.|None|  
|Programmabilité de Service Broker dans SMO|La classe **Microsoft. SqlServer. Management. Smo. Broker. BrokerPriority** n’implémente plus l’interface **Microsoft. SqlServer. Management. Smo. IObjectPermission** .||  
|Options définies|`SET DISABLE_DEF_CNST_CHK`|Aucun.|  
|Tables système|sys.database_principal_aliases|Utilisez des rôles à la place d'alias.|  
|Transact-SQL|
  `RAISERROR` dans le format `RAISERROR integer 'string'` est supprimé.|Réécrivez l’instruction à l’aide de la syntaxe **RAISERROR (...)** actuelle.|  
|Syntaxe Transact-SQL|`COMPUTE / COMPUTE BY`|Utilisez `ROLLUP`.|  
|Syntaxe Transact-SQL|Utilisation de ** \* ** et **=&#42;**|Utilisez la syntaxe de jointure ANSI. Pour plus d’informations, consultez [from (Transact-SQL).](https://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)|  
|XEvents|databases_data_file_size_changed, databases_log_file_size_changed<br /><br /> eventdatabases_log_file_used_size_changed<br /><br /> locks_lock_timeouts_greater_than_0<br /><br /> locks_lock_timeouts|Remplacé par événement database_file_size_change, database_file_size_change<br /><br /> événement database_file_size_change<br /><br /> lock_timeout_greater_than_0<br /><br /> lock_timeout|  
  
 **Modifications supplémentaires de XEvent**  
  
 **resource_monitor_ring_buffer_record**:  
  
-   Champs supprimés : single_pages_kb, multiple_pages_kb  
  
-   Champs ajoutés : target_kb, pages_kb  
  
 **memory_node_oom_ring_buffer_recorded**:  
  
-   Champs supprimés : single_pages_kb, multiple_pages_kb  
  
-   Champs ajoutés : target_kb, pages_kb  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités du moteur de base de données déconseillées dans SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
