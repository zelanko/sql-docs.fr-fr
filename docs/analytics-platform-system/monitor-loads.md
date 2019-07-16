---
title: Contrôler des chargements pour Parallel Data Warehouse | Microsoft Docs
description: Contrôler des chargements d’actifs et récents à l’aide de la Console d’administration Analytique Platform System (APS) ou les vues du système (PDW) de l’entrepôt de données parallèle ».
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 1eadf20e036c6c76cd3bece7c404fde2af4a7d70
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960605"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Moniteur de charge dans Parallel Data Warehouse
Moniteur actif et récent [dwloader](dwloader.md) charge à l’aide de la Console d’administration Analytique Platform System (APS) ou Parallel Data Warehouse (PDW) [vues système](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/). 
  
> [!TIP]  
> Certaines charges sont lancées à l’aide des instructions INSERT ou des outils d’analyse décisionnelle qui utilisent des instructions SQL pour effectuer le chargement. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Prérequis  
Quelle que soit la méthode utilisée pour surveiller la charge, la connexion doit avoir l’autorisation pour accéder aux sources de données sous-jacentes. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Surveillance des charges  
Les sections suivantes décrivent comment contrôler des chargements.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Pour contrôler des chargements à l’aide de la Console d’administration  
  
1.  Ouvrez une session sur la Console d’administration. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  Dans le menu supérieur, cliquez sur **charges**. Vous verrez un tableau triable indiquant tous les récentes et de charges actives ainsi que des informations supplémentaires, telles que la charge est terminée ou qu’il est toujours active. Cliquez sur les en-têtes de colonne pour trier les lignes.  
  
3.  Pour afficher des détails supplémentaires pour une charge spécifique, cliquez sur la charge **ID** dans la colonne de gauche. Dans la vue détaillée, vous pouvez voir la progression à chaque étape de la charge.  
  
Consultez ces vues système pour plus d’informations sur les métadonnées relatives à la charge qui est indiquée dans la Console d’administration :  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Pour contrôler des chargements en utilisant des vues système  
Pour surveiller les actifs et récents charges en utilisant des vues SQL Server PDW, suivez les étapes ci-dessous. Pour chaque vue système est utilisée, consultez la documentation de cette vue pour plus d’informations sur les colonnes et les valeurs possibles retournées par la vue.  
  
1.  Rechercher la `request_id` de la charge dans le [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) afficher par recherche de la ligne de commande du chargeur dans les `command` colonne pour cette vue.  
  
    Par exemple, la commande suivante retourne le texte de la commande et l’état actuel, ainsi que les `request_id`.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Utilisez le `request_id` pour récupérer des informations supplémentaires pour la charge à l’aide de la [sys.pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) , et [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) vues. Par exemple, la requête suivante retourne le `run_id` et plus d’informations sur les heures de début, fin et durée de la charge, ainsi que toutes les erreurs et des informations sur le nombre de lignes traitées :  
  
    ```sql  
    SELECT lbr.run_id,   
    er.submit_time, er.end_time, er.total_elapsed_time, er.error_id, lbr.rows_processed, lbr.rows_rejected, lbr.rows_inserted   
    FROM sys.dm_pdw_exec_requests er   
    LEFT OUTER JOIN   
    sys.pdw_loader_backup_runs lbr   
    ON (er.request_id=lbr.requst_id)   
    WHERE er.request_id='12738';  
    ```  
  
<!-- MISSING LINKS

## See Also  
[Common metadata query examples](metadata-query-examples.md)
-->  
  
