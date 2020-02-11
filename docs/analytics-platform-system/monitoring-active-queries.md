---
title: Surveiller les requêtes actives
description: Utilisez la console d’administration et les vues système Data Warehouse parallèles pour surveiller les requêtes actives sur Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 9157db745b999711966f0019747ba1d61823569e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400913"
---
# <a name="monitoring-active-queries---parallel-data-warehouse"></a>Surveillance des requêtes actives-Data Warehouse parallèles
Cet article explique comment utiliser la console d’administration et les vues système SQL Server PDW pour surveiller les requêtes actives. Pour plus d’informations sur ces outils, consultez [surveiller l’appliance à l’aide de la console d’administration](monitor-the-appliance-by-using-the-admin-console.md) et des [vues système](tsql-system-views.md) .  
  
## <a name="prerequisites"></a>Conditions préalables requises  
Quelle que soit la méthode utilisée pour surveiller les requêtes actives, la connexion doit avoir les autorisations décrites dans « utiliser l’ensemble de la console d’administration » dans [accorder des autorisations pour utiliser la console d’administration](grant-permissions.md#grant-permissions-to-use-the-admin-console).  
  
## <a name="PermsAdminConsole"></a>Surveiller les requêtes actives  
Vous pouvez utiliser la console d’administration et les vues système SQL Server PDW pour surveiller les requêtes actives. Procédez comme suit.  
  
### <a name="to-monitor-active-queries-by-using-the-admin-console"></a>Pour surveiller les requêtes actives à l’aide de la console d’administration  
  
1.  Connectez-vous à la console d’administration. Pour obtenir des instructions [, consultez surveiller l’appliance à l’aide de la console d’administration](monitor-the-appliance-by-using-the-admin-console.md) .  
  
2.  Dans le menu supérieur, cliquez sur **requêtes**. Vous verrez un tableau contenant des informations de base sur les requêtes les plus récentes sur l’appliance, y compris la connexion qui a envoyé la requête, les heures de début et de fin de la requête et l’état actuel de la requête.  
  
3.  Pour afficher la commande de requête, placez le pointeur de la souris sur l’ID de la requête dans la colonne de gauche pour cette ligne.  
  
    Pour afficher des informations plus détaillées sur une requête particulière, cliquez sur l’ID de requête. Vous verrez des informations, notamment la requête complète et le plan de requête, avec des informations d’État pour chaque étape de l’exécution de la requête. Si des erreurs ont été retournées, vous pouvez également consulter des informations détaillées sur les erreurs. <!-- MISSING LINKS See [Understanding Query Plans &#40;SQL Server PDW&#41;](../sqlpdw/understanding-query-plans-sql-server-pdw.md) for information on how to interpret the query plan information available in the Admin Console.  -->
  
### <a name="to-monitor-active-queries-by-using-the-system-views"></a>Pour surveiller les requêtes actives à l’aide des vues système  
La vue système principale utilisée pour surveiller les requêtes est [sys. dm_pdw_exec_requests](../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md). Utilisez cette vue système pour rechercher la `request_id` pour une requête active ou récente, en fonction du texte de la requête.  
  
Par exemple, la requête suivante recherche le `request_id` et le actuel `status` pour toute requête qui sélectionne toutes les colonnes de `memberAddresses` la table.  
  
```sql  
SELECT request_id, command, status   
FROM sys.dm_pdw_exec_requests   
WHERE command   
LIKE '%SELECT * FROM db1..memberAddresses%';  
```  
  
Une fois `request_id` que l’a été identifié pour une requête, utilisez les autres `dm_pdw_exec_requests` informations de la table pour en savoir plus sur le traitement de la requête, ou utilisez [sys. dm_pdw_request_steps](../relational-databases/system-dynamic-management-views/sys-dm-pdw-request-steps-transact-sql.md) pour afficher l’état des étapes de requête individuelles pour l’exécution de la requête.  
  
<!-- MISSING LINKS 
## See Also  
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
  
