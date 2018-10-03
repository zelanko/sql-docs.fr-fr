---
title: Supprimées des fonctionnalités du moteur de base de données dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 9d5d292421616d9c3d6043cf792345a8de0d8840
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135289"
---
# <a name="discontinued-database-engine-functionality-in-sql-server-2014"></a>Fonctionnalités du moteur de base de données supprimées dans SQL Server 2014
  Cette rubrique décrit les fonctionnalités du [!INCLUDE[ssDE](../includes/ssde-md.md)] qui ne sont plus disponibles dans [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].  
  
## <a name="discontinued-features-in-includesssql14includessssql14-mdmd"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Le tableau suivant répertorie les fonctionnalités qui ont été supprimées dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
|Catégorie|Fonctionnalité supprimée|Remplacement|  
|--------------|--------------------------|-----------------|  
|Niveau de compatibilité|Niveau de compatibilité 90|Les bases de données doivent être définies au moins au niveau de compatibilité 100. Lorsqu'une base de données avec un niveau de compatibilité inférieur à 100 est mise à niveau vers [!INCLUDE[ssSQL14](../includes/sssql14-md.md)], le niveau de compatibilité de la base de données est défini sur la valeur 100 pendant l'opération de mise à niveau.|  
  
## <a name="discontinued-features-in-includesssql11includessssql11-mdmd"></a>Fonctionnalités supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
 Le tableau suivant répertorie les fonctionnalités qui ont été supprimées dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].  
  
|Catégorie|Fonctionnalité supprimée|Remplacement|  
|--------------|--------------------------|-----------------|  
|Sauvegarde et restauration|**SAUVEGARDE {base de données &#124; LOG} WITH PASSWORD** et **sauvegarde {base de données &#124; LOG} WITH MEDIAPASSWORD** sont supprimés. **RESTORE {DATABASE &#124; journal} avec mot de passe [MEDIA]** continue à être déconseillé.|None|  
|Sauvegarde et restauration|**RESTORE {DATABASE &AMP;#124; JOURNAL}... WITH DBO_ONLY**|**RESTORE {DATABASE &AMP;#124; JOURNAL}...... AVEC RESTRICTED_USER**|  
|Niveau de compatibilité|niveau de compatibilité 80|Les bases de données doivent être définies au moins au niveau de compatibilité 90.|  
|Options de configuration|`sp_configure 'user instance timeout'` et `'user instances enabled'`|Utilisez la fonctionnalité de base de données locale. Pour plus d’informations, consultez [utilitaire SqlLocalDB](../tools/sqllocaldb-utility.md)|  
|Protocoles de connexion|La prise en charge du protocole VIA est supprimée.|Utilisez à la place TCP.|  
|Objets de base de données|Clause `WITH APPEND` sur les déclencheurs|Recréez la totalité du déclencheur.|  
|Options de base de données|`sp_dboption`|`ALTER DATABASE`|  
|Messagerie|SQL Mail|Utilisez la messagerie de la base de données. Pour plus d’informations, consultez [Database Mail](../relational-databases/database-mail/database-mail.md) et [Use Database Mail Instead of SQL Mail](../relational-databases/policy-based-management/use-database-mail-instead-of-sql-mail.md).|  
|Gestion de la mémoire|Extensions Address Windowing Extensions (AWE) 32 bits et prise en charge de l'ajout de mémoire à chaud 32 bits.|Utilisez un système d'exploitation 64 bits.|  
|Métadonnées|`DATABASEPROPERTY`|`DATABASEPROPERTYEX`|  
|Programmabilité|Objets SQL-DMO (SQL Server Distributed Management Objects)|SMO (SQL Server Management Objects)|  
|Indicateurs de requête|Indicateur `FASTFIRSTROW`|`OPTION (FAST` *n* `)`.|  
|Serveurs distants|La possibilité pour les utilisateurs de créer des serveurs distants à l'aide de `sp_addserver` est supprimée. `sp_addserver` avec l'option « locale » reste disponible. Des serveurs distants conservés pendant la mise à niveau ou créés par réplication peuvent être utilisés.|Remplacez les serveurs distants à l'aide de serveurs liés.|  
|Sécurité|`sp_dropalias`|Remplacez les alias par une combinaison de comptes d'utilisateurs et de rôles de base de données. Utilisez `sp_dropalias` pour supprimer les alias dans les bases de données mis à niveau.|  
|Sécurité|Le paramètre de version de **PWDCOMPARE** représentant une valeur à partir d’une connexion antérieure à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 2000 n’est plus disponible.|None|  
|Programmabilité de Service Broker dans SMO|Le **Microsoft.SqlServer.Management.Smo.Broker.BrokerPriority** n’est plus la classe implémente le **Microsoft.SqlServer.Management.Smo.IObjectPermission** interface.||  
|Options définies|`SET DISABLE_DEF_CNST_CHK`|Aucun.|  
|Tables système|sys.database_principal_aliases|Utilisez des rôles à la place d'alias.|  
|Transact-SQL|`RAISERROR` dans le format `RAISERROR integer 'string'` est supprimé.|Réécrivez l’instruction à l’aide de cours **RAISERROR (…)**  syntaxe.|  
|Syntaxe Transact-SQL|`COMPUTE / COMPUTE BY`|Utilisez `ROLLUP`.|  
|Syntaxe Transact-SQL|Utilisation de **\* =** et **=\***|Utilisez la syntaxe de jointure ANSI. Pour plus d’informations, consultez [FROM (Transact-SQL).](http://msdn.microsoft.com/library/ms177634\(SQL.105\).aspx)|  
|XEvents|databases_data_file_size_changed, databases_log_file_size_changed<br /><br /> eventdatabases_log_file_used_size_changed<br /><br /> locks_lock_timeouts_greater_than_0<br /><br /> locks_lock_timeouts|Remplacé par événement database_file_size_change database_file_size_change<br /><br /> événement database_file_size_change<br /><br /> lock_timeout_greater_than_0<br /><br /> lock_timeout|  
  
 **Modifications supplémentaires de XEvent**  
  
 **resource_monitor_ring_buffer_record**:  
  
-   Champs supprimés : single_pages_kb, multiple_pages_kb  
  
-   Champs ajoutés : target_kb, pages_kb  
  
 **memory_node_oom_ring_buffer_recorded**:  
  
-   Champs supprimés : single_pages_kb, multiple_pages_kb  
  
-   Champs ajoutés : target_kb, pages_kb  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités dépréciées du moteur de base de données dans SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
