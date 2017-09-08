---
title: DBCC CHECKCATALOG (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/16/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DBCC_CHECKCATALOG_TSQL
- DBCC CHECKCATALOG
- CHECKCATALOG_TSQL
- CHECKCATALOG
dev_langs:
- TSQL
helpviewer_keywords:
- catalogs [SQL Server], consistency checks
- checking catalog consistency
- DBCC CHECKCATALOG statement
- integrity [SQL Server], catalogs
- consistency [SQL Server], catalogs
ms.assetid: 8076eb4e-f049-44bf-9a35-45cdd6ef0105
caps.latest.revision: 51
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f63850a2cf39d783daee65431da349d04cba3b03
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="dbcc-checkcatalog-transact-sql"></a>DBCC CHECKCATALOG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Vérifie la cohérence du catalogue dans la base de données spécifiée. La base de données doit être en ligne.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DBCC CHECKCATALOG   
[   
    (   
    database_name | database_id | 0  
    )  
]  
    [ WITH NO_INFOMSGS ]   
```  
  
## <a name="arguments"></a>Arguments  
 *database_name* | *database_id* | 0  
 Nom ou ID de la base de données dont vous souhaitez vérifier la cohérence du catalogue. En l'absence de spécification, ou si 0 est spécifié, la base de données actuelle est utilisée. Les noms de base de données doivent être conformes aux règles des [identificateurs](../../relational-databases/databases/database-identifiers.md).  
  
 WITH NO_INFOMSGS  
 Supprime tous les messages d'information.  
  
## <a name="remarks"></a>Notes  
Une fois la commande DBCC CATALOG terminée, un message est enregistré dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si la commande DBCC est correctement exécutée, le message indique que l'exécution a réussi, ainsi que la durée d'exécution de la commande. Si la commande DBCC s’arrête avant la fin de la vérification en raison d’une erreur, le message indique la commande s’est terminé, une valeur d’état et la durée d’exécution de la commande. Le tableau suivant répertorie et décrit les valeurs d'état pouvant être incluses dans le message.
  
|État| Description|  
|-----------|-----------------|  
|0|Erreur numéro 8930 générée. Ceci indique une corruption des métadonnées qui a provoqué l'arrêt de la commande DBCC.|  
|1|Erreur numéro 8967 générée. Une erreur DBCC interne s'est produite.|  
|2|Une erreur s'est produite lors de la réparation de la base de données en mode urgence.|  
|3|Ceci indique une corruption des métadonnées qui a provoqué l'arrêt de la commande DBCC.|  
|4|Une assertion ou une violation d'accès a été détectée.|  
|5|Une erreur inconnue s'est produite et a arrêté la commande DBCC.|  
  
DBCC CHECKCATALOG effectue différentes vérifications de cohérence entre les tables de métadonnées système. DBCC CHECKCATALOG utilise un instantané de base de données interne pour fournir la cohérence transactionnelle nécessaire à la réalisation de ces vérifications. Pour plus d’informations, consultez [afficher la taille du fichier partiellement alloué d’un instantané de base de données &#40; Transact-SQL &#41; ](../../relational-databases/databases/view-the-size-of-the-sparse-file-of-a-database-snapshot-transact-sql.md) et la section « DBCC interne de base de données utilisation de l’instantané » [DBCC &#40; Transact-SQL &#41; ](../../t-sql/database-console-commands/dbcc-transact-sql.md).
Si un instantané ne peut pas être créé, DBCC CHECKCATALOG acquiert un verrou de base de données exclusif pour obtenir la cohérence requise. Si des incohérences sont détectées, elles ne peuvent pas être réparées et la base de données doit être restaurée à partir d'une sauvegarde.
  
> [!NOTE]  
>  Exécution de DBCC CHECKCATALOG sur **tempdb** ne procède à aucune vérification. Effet, pour des raisons de performances, les instantanés de base de données ne sont pas disponibles sur **tempdb**. Cela signifie que la cohérence transactionnelle requise ne peut pas être obtenue. Recyclez le serveur pour résoudre toute **tempdb** problèmes liés aux métadonnées.  
  
> [!NOTE]  
>  DBCC CHECKCATALOG ne vérifie pas les données FILESTREAM. FILESTREAM stocke les objets BLOB dans le système de fichiers.  
  
DBCC CHECKCATALOG est également exécutée dans le cadre de [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md).
  
## <a name="result-sets"></a>Jeux de résultats  
Si aucune base de données n'est spécifiée, DBCC CHECKCATALOG retourne :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
Si [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] est spécifié en tant que nom de base de données, DBCC CHECKCATALOG retourne :
  
```sql
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Permissions  
 Nécessite l’appartenance dans le **sysadmin** rôle de serveur fixe ou le **db_owner** rôle de base de données fixe.  
  
## <a name="examples"></a>Exemples  
L'exemple suivant vérifie l'intégrité du catalogue dans la base de données active et dans la base de données `AdventureWorks`.
  
```sql
-- Check the current database.  
DBCC CHECKCATALOG;  
GO  
-- Check the AdventureWorks2012 database.  
DBCC CHECKCATALOG (AdventureWorks2012);  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
[DBCC &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Tables système &#40; Transact-SQL &#41;](../../relational-databases/system-tables/system-tables-transact-sql.md)
  

