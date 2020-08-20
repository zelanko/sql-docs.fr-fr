---
description: MSSQLSERVER_2814
title: MSSQLSERVER_2814 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2814 (Database Engine error)
ms.assetid: 22800748-9be9-4511-9428-6b8b40e5bef9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 174836221e6040bde4fff244e3d5377f90b0089e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482723"
---
# <a name="mssqlserver_2814"></a>MSSQLSERVER_2814
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|2814|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|PR_POSSIBLE_INFINITE_RECOMPILE|  
|Texte du message|Recompilation infinie détectée pour SQLHANDLE %hs, PlanHandle %hs, décalage de début %d, décalage de fin %d. Dernière raison de la recompilation : %d.|  
  
## <a name="explanation"></a>Explication  
Une ou plusieurs instructions ont provoqué la recompilation du lot de requêtes au moins 50 fois. L'instruction spécifiée doit être corrigée pour éviter d'autres recompilations.  
  
Le tableau suivant répertorie les raisons de la recompilation.  
  
|Code de la raison|Description|  
|---------------|---------------|  
|1|Schéma modifié|  
|2|Statistiques modifiées|  
|3|Compilation différée|  
|4|Option Set modifiée|  
|5|Table temporaire modifiée|  
|6|Ensemble de lignes à distance modifié|  
|7|Autorisations de recherche modifiées|  
|8|Environnement de notification de requête modifié|  
|9|Affichage partition modifié|  
|10|Options de curseur modifiées|  
|11|Option (recompilation) demandée.|  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Affichez l'instruction qui engendre la recompilation en exécutant la requête suivante. Remplacez les espaces réservés *sql_handle*, *starting_offset*, *ending_offset*, et *plan_handle* par les valeurs spécifiées dans le message d’erreur. Les colonnes **database_name** et **object_name** ont la valeur NULL pour les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ad hoc et préparées.  
  
    ```sql   
    SELECT DB_NAME(st.dbid) AS database_name,  
        OBJECT_NAME(st.objectid) AS object_name,  
        st.text  
    FROM sys.dm_exec_query_stats AS qs  
    CROSS APPLY sys.dm_exec_sql_text (*sql_handle*) AS st  
    WHERE qs.statement_start_offset = *starting_offset*  
    AND qs.statement_end_offset = *ending_offset*  
    AND qs.plan_handle = *plan_handle*;
    ```
  
2.  En fonction de la description du code de la raison, modifiez l'instruction, le lot ou la procédure pour éviter les recompilations. Par exemple, une procédure stockée peut contenir une ou plusieurs instructions SET. Ces instructions doivent être supprimées de la procédure. Pour plus d’exemples de causes de recompilation et de résolutions, consultez [Batch Compilation, Recompilation, and Plan Caching Issues in SQL Server 2005](/previous-versions/sql/sql-server-2005/administrator/cc966425(v=technet.10)).  
  
3.  Si le problème persiste, contactez les services d'assistance Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
[Classe d'événements SQL:StmtRecompile](../event-classes/sql-stmtrecompile-event-class.md)  
  
