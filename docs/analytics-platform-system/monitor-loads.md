---
title: Surveiller les chargements
description: Surveiller les chargements actifs et récents à l’aide de la console d’administration APS (Analytics Platform System) ou du système d’Data Warehouse parallèles (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: b284fdcef506924c26e452196db6e9518faa1351
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400964"
---
# <a name="monitor-loads-into-parallel-data-warehouse"></a>Surveiller les chargements dans des Data Warehouse parallèles
Surveiller les chargements [dwloader](dwloader.md) actifs et récents à l’aide de la console d’administration APS (Analytics Platform System) ou des [vues système](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-reference-tsql-system-views/)de l’Data Warehouse parallèle (PDW). 
  
> [!TIP]  
> Certaines charges sont lancées à l’aide d’instructions INSERT ou d’outils décisionnels qui utilisent des instructions SQL pour effectuer la charge. 

<!-- MISSING LINKS
To monitor this type of load, see [Monitoring Active Queries](monitor-active-queries.md).  
-->
  
## <a name="prerequisites"></a>Conditions préalables requises  
Quelle que soit la méthode utilisée pour surveiller une charge, la connexion doit avoir l’autorisation d’accéder aux sources de données sous-jacentes. 

<!-- MISSING LINKS
For the permissions to grant, see "Use All of the Admin Console" in [Grant Permissions to Use the Admin Console](grant-permissions-admin-console.md). 

--> 
  
## <a name="monitoring-loads"></a>Surveillance des chargements  
Les sections suivantes décrivent comment surveiller les chargements.  
  
### <a name="to-monitor-loads-by-using-the-admin-console"></a>Pour surveiller les charges à l’aide de la console d’administration  
  
1.  Connectez-vous à la console d’administration. <!-- MISSING LINKS See [Monitor the Appliance by Using the Admin Console;](monitor-admin-console.md) for instructions. --> 
  
2.  Dans le menu supérieur, cliquez sur **charges**. Vous verrez une table triable qui affiche tous les téléchargements récents et actifs, ainsi que des informations supplémentaires, par exemple si la charge est terminée ou si elle est toujours active. Cliquez sur les en-têtes de colonne pour trier les lignes.  
  
3.  Pour afficher des détails supplémentaires pour une charge spécifique, cliquez sur l' **ID** de chargement dans la colonne de gauche. Dans l’affichage détaillé, vous pouvez voir la progression à chaque étape de la charge.  
  
Pour plus d’informations sur les métadonnées relatives à la charge affichée dans la console d’administration, consultez les vues système suivantes :  
  
-   [sys.dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages](https://msdn.microsoft.com/library/mt203879.aspx)  
  
-   [sys.pdw_loader_backup_runs](../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
### <a name="to-monitor-loads-by-using-system-views"></a>Pour surveiller les charges à l’aide des vues système  
Pour surveiller les charges actives et récentes à l’aide de SQL Server PDW vues, suivez les étapes ci-dessous. Pour chaque vue système utilisée, consultez la documentation de cette vue pour obtenir des informations sur les colonnes et les valeurs potentielles retournées par la vue.  
  
1.  Recherchez la `request_id` pour la charge dans la vue [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md) en recherchant la ligne de commande du chargeur dans `command` la colonne pour cette vue.  
  
    Par exemple, la commande suivante retourne le texte de la commande et l’état actuel `request_id`, ainsi que le.  
  
    ```sql  
    SELECT request_id, status, command FROM sys.dm_pdw_exec_requests;  
    ```  
  
2.  Utilisez le `request_id` pour récupérer des informations supplémentaires sur la charge à l’aide des vues [sys. pdw_loader_run_stages](../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md) et [sys. pdw_loader_backup_run_details](../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md) . Par exemple, la requête suivante retourne les `run_id` informations et au début, à la fin et à la durée de la charge, ainsi que toutes les erreurs et les informations sur le nombre de lignes traitées :  
  
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
  
