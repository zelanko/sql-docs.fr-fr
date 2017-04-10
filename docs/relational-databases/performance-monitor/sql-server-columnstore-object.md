---
title: "SQL Server, objet columnstore | Microsoft Docs"
ms.custom: ""
ms.date: "04/12/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
caps.latest.revision: 8
author: "barbkess"
ms.author: "barbkess"
manager: "jhubbard"
caps.handback.revision: 8
---
# SQL Server, objet columnstore
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  L’objet **SQLServer:Columnstore** fournit des compteurs permettant de surveiller l’exécution des index columnstore dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le tableau suivant décrit les compteurs **Columnstore** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs ColumnStore|Description|  
|--------------------------|-----------------|  
|**Rowgroups delta fermés**|Nombre de rowgroups delta fermés.|  
|**Rowgroups delta compressés**|Nombre de rowgroups delta compressés.|  
|**Rowgroups delta créés**|Nombre de rowgroups delta créés.|  
|**Taux d’accès au cache de segments**|Pourcentage de segments de colonne détectés dans le pool columnstore sans devoir effectuer de lecture à partir du disque.|  
|**Base du taux d’accès au cache de segments**|À usage interne uniquement|
|**Lectures de segments/s**|Nombre de lectures de segments physiques effectuées.|  
|**Total des tampons de suppression migrés**|Nombre de nettoyages du tampon de suppression par le moteur de tuple.|  
|**Total des évaluations de la stratégie de fusion**|Nombre d’évaluations de la stratégie de fusion pour columnstore.|  
|**Total des rowgroups compressés**|Nombre total de rowgroups compressés.|  
|**Nombre total de rowgroups prêts pour la fusion**|Nombre de rowgroups sources prêts pour l’opération MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups fusionnés et compressés**|Nombre de rowgroups cibles compressés créés avec MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups sources fusionnés**|Nombre de rowgroups sources fusionnés depuis le démarrage de SQL Server.|  
  
## Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  