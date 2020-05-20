---
title: sp_helpstats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpstats
- sp_helpstats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpstats
ms.assetid: 00ab3cfd-2736-4fc0-b1b2-16dd49fb2fe5
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b4f84f187ea3f511b8dddcc79c712dfd7809748d
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82824420"
---
# <a name="sp_helpstats-transact-sql"></a>sp_helpstats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne les informations statistiques sur les colonnes et les index de la table spécifiée.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]Pour obtenir des informations sur les statistiques, interrogez les affichages catalogue [sys. stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) et [sys. stats_columns](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md) .  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpstats[ @objname = ] 'object_name'   
     [ , [ @results = ] 'value' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @objname = ] 'object_name'`Spécifie la table sur laquelle fournir des informations statistiques. *object_name* est de type **nvarchar (520)** et ne peut pas être null. Vous pouvez spécifier un nom en une ou deux parties.  
  
`[ @results = ] 'value'`Spécifie l’étendue des informations à fournir. Les entrées valides sont **All** et **stats**. **Toutes les** listes de statistiques pour tous les index et les colonnes sur lesquelles des statistiques sont créées ; **Stats** répertorie uniquement les statistiques qui ne sont pas associées à un index. *value* est de type **nvarchar (5),** avec stats comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Le tableau suivant décrit les colonnes du jeu de résultats.  
  
|Nom de la colonne|Description|  
|-----------------|-----------------|  
|**statistics_name**|Nom des statistiques. Retourne **sysname** et ne peut pas avoir la valeur null.|  
|**statistics_keys**|Clés sur lesquelles sont basées les statistiques. Retourne une valeur de type **nvarchar (2078)** et ne peut pas être null.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez DBCC SHOW_STATISTICS pour afficher des informations statistiques détaillées sur l'index ou les statistiques de votre choix. Pour plus d’informations, consultez [DBCC SHOW_STATISTICS &#40;Transact-sql&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md) et [sp_helpindex &#40;transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md).  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'appartenance au rôle **public** .  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée des statistiques, réparties sur une seule colonne, pour toutes les colonnes possibles de toutes les tables utilisateur de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] en exécutant `sp_createstats`. Ensuite, `sp_helpstats` est exécutée pour rechercher les statistiques résultantes créées sur la table `Customer`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_createstats;  
GO  
EXEC sp_helpstats   
@objname = 'Sales.Customer',  
@results = 'ALL';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `statistics_name               statistics_keys`  
  
 `----------------------------  ----------------`  
  
 `_WA_Sys_00000003_22AA2996     AccountNumber`  
  
 `AK_Customer_AccountNumber     AccountNumber`  
  
 `AK_Customer_rowguid           rowguid`  
  
 `CustomerType                  CustomerType`  
  
 `IX_Customer_TerritoryID       TerritoryID`  
  
 `ModifiedDate                  ModifiedDate`  
  
 `PK_Customer_CustomerID        CustomerID`  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Moteur de base de données des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)  
  
  
