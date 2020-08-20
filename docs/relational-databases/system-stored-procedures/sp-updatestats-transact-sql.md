---
description: sp_updatestats (Transact-SQL)
title: sp_updatestats (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_updatestats_TSQL
- sp_updatestats
dev_langs:
- TSQL
helpviewer_keywords:
- sp_updatestats
ms.assetid: 01184651-6e61-45d9-a502-366fecca0ee4
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: fbcfad5e5639fab399d65bd5ffbc24a1e0bd6cea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473464"
---
# <a name="sp_updatestats-transact-sql"></a>sp_updatestats (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

S’exécute `UPDATE STATISTICS` sur toutes les tables définies par l’utilisateur et les tables internes de la base de données actuelle.  
  
Pour plus d’informations sur `UPDATE STATISTICS` , consultez [update statistics &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md). Pour plus d’informations sur les statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).  
    
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_updatestats [ [ @resample = ] 'resample']  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="arguments"></a>Arguments  
`[ @resample = ] 'resample'` Spécifie que **sp_updatestats** utilisera l’option reéchantillonner de l’instruction [Update Statistics](../../t-sql/statements/update-statistics-transact-sql.md) . Si **'resample'** n’est pas spécifié, **sp_updatestats** met à jour les statistiques à l’aide de l’échantillonnage par défaut. **resample** est de type **varchar (8)** avec la valeur non par défaut.  
  
## <a name="remarks"></a>Notes  
 **sp_updatestats** s’exécute `UPDATE STATISTICS` en spécifiant le `ALL` mot clé, sur toutes les tables définies par l’utilisateur et les tables internes de la base de données. sp_updatestats affiche des messages indiquant sa progression. Une fois la mise à jour terminée, cette procédure signale que les statistiques ont été mises à jour pour toutes les tables.  
  
**sp_updatestats** met à jour les statistiques sur les index non cluster désactivés et ne met pas à jour les statistiques sur les index cluster désactivés.  
  
Pour les tables sur disque, **sp_updatestats** met à jour les statistiques en fonction des informations de **modification_counter** dans l’affichage catalogue **sys. dm_db_stats_properties** , en mettant à jour les statistiques où au moins une ligne a été modifiée. Les statistiques sur les tables optimisées en mémoire sont toujours mises à jour lors de l’exécution de **sp_updatestats**. Par conséquent, n’exécutez pas **sp_updatestats** plus que nécessaire.  
  
**sp_updatestats** pouvez déclencher une recompilation de procédures stockées ou d’autres codes compilés. Toutefois, **sp_updatestats** peut ne pas provoquer de recompilation, si un seul plan de requête est possible pour les tables référencées et les index qu’ils contiennent. Une recompilation serait inutile dans ce cas, même si les statistiques sont mises à jour.  
  
Pour les bases de données dont le niveau de compatibilité est inférieur à 90, l’exécution de **sp_updatestats** ne conserve pas le dernier paramètre NORECOMPUTE pour des statistiques spécifiques. Pour les bases de données dont le niveau de compatibilité est égal ou supérieur à 90, sp_updatestats conserve la dernière option NORECOMPUTE pour des statistiques spécifiques. Pour plus d’informations sur la désactivation et la réactivation des mises à jour des statistiques, consultez [Statistiques](../../relational-databases/statistics/statistics.md).  
  
## <a name="permissions"></a>Autorisations  

Pour exécuter **sp_updatestats**, l’utilisateur doit être le propriétaire de la base de données (le `dbo` , pas uniquement le membre du rôle `db_owner` ) ou être membre du rôle serveur fixe sysadmin.

## <a name="examples"></a>Exemples  
Cet exemple met à jour les statistiques des tables de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_updatestats;   
```  

## <a name="automatic-index-and-statistics-management"></a>Gestion automatique des index et des statistiques
Tirez parti de solutions comme [Adaptive Index Defrag](https://github.com/Microsoft/tigertoolbox/tree/master/AdaptiveIndexDefrag) pour gérer automatiquement la défragmentation des index et les mises à jour des statistiques pour une ou plusieurs bases de données. Cette procédure choisit automatiquement s’il faut reconstruire ou réorganiser un index en fonction de son niveau de fragmentation, entre autres, et mettre à jour les statistiques avec un seuil linéaire.

## <a name="see-also"></a>Voir aussi  
 [Options ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_createstats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-createstats-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [Procédures stockées système](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
 
