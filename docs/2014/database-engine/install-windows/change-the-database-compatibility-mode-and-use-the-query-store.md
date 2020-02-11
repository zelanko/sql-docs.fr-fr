---
title: Migrer les plans de requête | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- query plans [SQL Server], migrating
- upgrading SQL Server, migrating query plans
- plan guides [SQL Server], migrating query plans
ms.assetid: 7e02a137-6867-4f6a-a45a-2b02674f7e65
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 66f1f8f57dca3ad2edba3f4b63100b2de3ae5659
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62779111"
---
# <a name="migrate-query-plans"></a>Migrer des plans de requête
  Dans la plupart des cas, la mise à niveau d'une base de données vers la dernière version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] améliore les performances des requêtes. Toutefois, si vous avez des requêtes critiques réglées avec soin pour la performance, vous pouvez conserver les plans de requête pour ces requêtes avant d'effectuer la mise à niveau en créant un repère de plan pour chaque requête. Si, après avoir effectué la mise à niveau, l'optimiseur de requête choisit un plan moins efficace pour l'une ou plusieurs des requêtes, vous pouvez activer les repères de plan et forcer l'optimiseur de requête à utiliser les plans de pré-mise à niveau.  
  
 Pour créer des repères de plan avant d'effectuer la mise à niveau, procédez comme suit :  
  
1.  Enregistrez le plan actuel pour chaque requête critique à l’aide de la procédure stockée [sp_create_plan_guide](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql) et en spécifiant le plan de requête dans l’indicateur de requête USE plan.  
  
2.  Vérifiez que le repère de plan est appliqué à la requête.  
  
3.  Mettez la base de données à niveau vers la dernière version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Les plans sont conservés dans la base de données mise à niveau, dans les repères de plan et servent de secours en cas de régressions de plan après la mise à niveau.  
  
     Nous vous recommandons de ne pas activer les repères de plan après la mise à niveau, car vous risquez de passer à côté d'opportunités de meilleurs plans dans la nouvelle version ou de recompilations bénéfiques en raison de statistiques mises à jour.  
  
4.  Si des plans moins efficaces sont choisis après la mise à niveau, activez l'ensemble ou un sous-ensemble des repères de plan pour remplacer les nouveaux plans.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment enregistrer un plan de pré-mise à niveau pour une requête en créant un repère de plan.  
  
### <a name="step-1-collect-the-plan"></a>Étape 1 : collecter le plan  
 Le plan de requête enregistré dans le repère de plan doit être au format XML. Les plans de requête XML peuvent être générés des manières suivantes :  
  
-   [SET SHOWPLAN_XML](/sql/t-sql/statements/set-showplan-xml-transact-sql)  
  
-   [SET STATISTICS XML](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
-   Interrogation de la colonne query_plan de la fonction de gestion dynamique [sys. dm_exec_query_plan](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql) .  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] Classes d’événements [Showplan XML](../../relational-databases/event-classes/showplan-xml-event-class.md), [Showplan XML Statistics Profile](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md)et [Showplan XML for Query Compile](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md) .  
  
 L'exemple suivant collecte le plan de requête pour l'instruction `SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;` en interrogeant des vues de gestion dynamique.  
  
```  
USE AdventureWorks;  
GO  
SELECT query_plan  
    FROM sys.dm_exec_query_stats AS qs   
    CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
    CROSS APPLY sys.dm_exec_text_query_plan(qs.plan_handle, DEFAULT, DEFAULT) AS qp  
    WHERE st.text LIKE N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;%';  
GO  
```  
  
### <a name="step-2-create-the-plan-guide-to-force-the-plan"></a>Étape 2 : créer le repère de plan nécessaire à l'application forcée du plan  
 À l'aide du plan de requête au format XML (obtenu à l'aide de n'importe laquelle des méthodes décrites précédemment) dans le repère de plan, copiez et collez le plan de requête en tant que littéral de chaîne à l'intérieur de l'indicateur de requête USE PLAN spécifié dans la clause OPTION de sp_create_plan_guide.  
  
 Dans le plan XML lui-même, échappez les guillemets (') qui apparaissent dans le plan en ajoutant un deuxième guillemet avant de créer le repère de plan. Par exemple, si un plan contient `WHERE A.varchar = 'This is a string'`, vous devez utiliser un caractère d'échappement en modifiant le code par `WHERE A.varchar = ''This is a string''`.  
  
 L'exemple suivant crée un repère de plan pour le plan de requête collecté lors de l'étape 1 et insère le plan d'exécution XML pour la requête dans le paramètre `@hints`. Pour des raisons de concision, une partie seulement de la sortie du plan d'exécution est incluse dans cet exemple.  
  
```  
EXECUTE sp_create_plan_guide   
@name = N'Guide1',  
@stmt = N'SELECT City, StateProvinceID, PostalCode FROM Person.Address ORDER BY PostalCode DESC;',  
@type = N'SQL',  
@module_or_batch = NULL,  
@params = NULL,  
@hints = N'OPTION(USE PLAN N''<ShowPlanXML xmlns=''''https://schemas.microsoft.com/sqlserver/2004/07/showplan''''   
    Version=''''0.5'''' Build=''''9.00.1116''''>  
    <BatchSequence><Batch><Statements><StmtSimple>  
    ...  
    </StmtSimple></Statements></Batch>  
    </BatchSequence></ShowPlanXML>'')';  
GO  
```  
  
### <a name="step-3-verify-that-the-plan-guide-is-applied-to-the-query"></a>Étape 3 : vérifier que le repère de plan est appliqué à la requête  
 Réexécutez la requête et examinez le plan de requête produit. Vous devez constater que le plan correspond à celui que vous avez spécifié dans le repère de plan.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_create_plan_guide &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql)   
 [Indicateurs de requête &#40;&#41;Transact-SQL](/sql/t-sql/queries/hints-transact-sql-query)   
 [Repères de plan](../../relational-databases/performance/plan-guides.md)  
  
  
