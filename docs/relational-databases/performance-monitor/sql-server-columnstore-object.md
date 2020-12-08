---
title: SQL Server, objet columnstore | Microsoft Docs
description: Découvrez l’objet SQLServer:Columnstore, qui fournit des compteurs permettant de superviser l’exécution des index columnstore dans SQL Server.
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: ae663a49-012f-4ffe-a332-f03157843052
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 61f950b5322270ce1b72b1734b92474dfb18b2bb
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96505786"
---
# <a name="sql-server-columnstore-object"></a>SQL Server, objet columnstore
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L’objet **SQLServer:Columnstore** fournit des compteurs permettant de surveiller l’exécution des index columnstore dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Le tableau suivant décrit les compteurs **Columnstore** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs ColumnStore|Description|  
|--------------------------|-----------------|  
|**Rowgroups delta fermés**|Nombre de rowgroups delta fermés.|  
|**Rowgroups delta compressés**|Nombre de rowgroups delta compressés.|  
|**Rowgroups delta créés**|Nombre de rowgroups delta créés.|  
|**Taux d’accès au cache de segments**|Pourcentage de segments de colonne détectés dans le pool columnstore sans devoir effectuer de lecture à partir du disque.|  
|**Base du taux d’accès au cache de segments**|À usage interne uniquement.|
|**Lectures de segments/s**|Nombre de lectures de segments physiques effectuées.|  
|**Total des tampons de suppression migrés**|Nombre de nettoyages du tampon de suppression par le moteur de tuple.|  
|**Total des évaluations de la stratégie de fusion**|Nombre d’évaluations de la stratégie de fusion pour columnstore.|  
|**Total des rowgroups compressés**|Nombre total de rowgroups compressés.|  
|**Nombre total de rowgroups prêts pour la fusion**|Nombre de rowgroups sources prêts pour l’opération MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups fusionnés et compressés**|Nombre de rowgroups cibles compressés créés avec MERGE depuis le démarrage de SQL Server.|  
|**Total des rowgroups sources fusionnés**|Nombre de rowgroups sources fusionnés depuis le démarrage de SQL Server.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
