---
title: STATS_DATE (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATS_DATE_TSQL
- STATS_DATE
dev_langs:
- TSQL
helpviewer_keywords:
- statistical information [SQL Server], last time updated
- STATS_DATE function
- query optimization statistics [SQL Server], last time updated
- last time statistics updated
ms.assetid: f9ec3101-1e41-489d-b519-496a0d6089fb
caps.latest.revision: 43
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44fc7524040db874abc5d596b641cba985dcf893
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="statsdate-transact-sql"></a>STATS_DATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Retourne la date de la mise à jour la plus récente des statistiques pour une table ou vue indexée.  
  
 Pour plus d’informations sur la mise à jour des statistiques, consultez [statistiques](../../relational-databases/statistics/statistics.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STATS_DATE ( object_id , stats_id )  
```  
  
## <a name="arguments"></a>Arguments  
 *object_id*  
 ID de la table ou vue indexée avec les statistiques.  
  
 *stats_id*  
 ID de l'objet de statistiques.  
  
## <a name="return-types"></a>Types de retour  
 Retourne **datetime** en cas de réussite. Retourne **NULL** en cas d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les fonctions système peuvent être utilisées dans la liste de sélection, dans la clause WHERE et partout où une expression peut être utilisée.  
  
## <a name="permissions"></a>Permissions  
 Requiert l'appartenance au rôle de base de données fixe db_owner ou l'autorisation d'afficher les métadonnées pour la table ou vue indexée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-return-the-dates-of-the-most-recent-statistics-for-a-table"></a>A. Retourner les dates des statistiques les plus récentes pour une table  
 L'exemple suivant retourne la date de la mise à jour la plus récente de chaque objet de statistiques dans la table `Person.Address`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_update_date  
FROM sys.stats   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
 Si les statistiques correspondent à un index, le *stats_id* valeur dans le [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) affichage catalogue est le même que le *index_id* valeur dans le [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) affichage catalogue et la requête suivante retourne les mêmes résultats que la requête précédente. Si les statistiques ne correspondent pas à un index, elles figurent dans les résultats sys.stats mais pas dans les résultats sys.indexes.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('Person.Address');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Exemples : [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] et[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-learn-when-a-named-statistics-was-last-updated"></a>B. Savoir quand une statistique nommée a été modifiée  
 L’exemple suivant crée des statistiques sur la colonne LastName de la table DimCustomer. Il exécute ensuite une requête pour afficher la date des statistiques. Puis il mises à jour les statistiques et exécute la requête pour afficher la date de mise à jour.  
  
```  
  
--First, create a statistics object  
USE AdventureWorksPDW2012;  
GO  
CREATE STATISTICS Customer_LastName_Stats  
ON AdventureWorksPDW2012.dbo.DimCustomer (LastName)  
WITH SAMPLE 50 PERCENT;  
GO  
  
--Return the date when Customer_LastName_Stats was last updated  
USE AdventureWorksPDW2012;  
GO  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
--Update Customer_LastName_Stats so it will have a different timestamp in the next query  
GO  
UPDATE STATISTICS dbo.dimCustomer (Customer_LastName_Stats);  
  
--Return the date when Customer_LastName_Stats was last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer')  
    AND s.name = 'Customer_LastName_Stats';  
GO  
  
```  
  
### <a name="c-view-the-date-of-the-last-update-for-all-statistics-on-a-table"></a>C. Afficher la date de la dernière mise à jour de toutes les statistiques sur une table  
 Cet exemple retourne la date de lors de la dernière mise à jour de chaque objet de statistiques sur la table DimCustomer.  
  
```  
--Return the dates all statistics on the table were last updated.  
SELECT stats_id, name AS stats_name,   
    STATS_DATE(object_id, stats_id) AS statistics_date  
FROM sys.stats s  
WHERE s.object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
 Si les statistiques correspondent à un index, le *stats_id* valeur dans le [sys.stats](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md) affichage catalogue est le même que le *index_id* valeur dans le [sys.indexes](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md) affichage catalogue et la requête suivante retourne les mêmes résultats que la requête précédente. Si les statistiques ne correspondent pas à un index, elles figurent dans les résultats sys.stats mais pas dans les résultats sys.indexes.  
  
```  
USE AdventureWorksPDW2012;  
GO  
SELECT name AS index_name,   
    STATS_DATE(object_id, index_id) AS statistics_update_date  
FROM sys.indexes   
WHERE object_id = OBJECT_ID('dbo.DimCustomer');  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions système &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_autostats &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [Statistiques](../../relational-databases/statistics/statistics.md)  
  
  


