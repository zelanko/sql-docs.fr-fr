---
title: SQL Server, objet Backup Device | Microsoft Docs
description: Découvrez l’objet Backup Device, qui fournit des compteurs permettant de superviser les unités de sauvegarde de Microsoft SQL Server utilisées pour les opérations de sauvegarde et de restauration.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 116a4cc015e74fd737c5e9fb9d5f1f920abaf377
ms.sourcegitcommit: 9470c4d1fc8d2d9d08525c4f811282999d765e6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86458841"
---
# <a name="sql-server-backup-device-object"></a>SQL Server, objet Unité de sauvegarde
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  L’objet **Unité de sauvegarde** fournit des compteurs permettant de surveiller les unités de sauvegarde de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisées pour les opérations de sauvegarde et de restauration. Surveillez les unités de sauvegarde lorsque vous voulez déterminer le débit ou la progression et les performances de vos opérations de sauvegarde et de restauration par unité. Pour surveiller le débit de l’opération de sauvegarde ou de restauration de l’ensemble de la base de données, utilisez le compteur **Débit de sauvegarde/restauration/s** de l’objet [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Bases de données**. Pour plus d’informations, voir [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md).  
  
 Ce tableau décrit le compteur **Unité de sauvegarde** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Compteurs Unité de sauvegarde de SQL Server|Description|  
|---------------------------------------|-----------------|  
|**Débit d'unité en octets/s**|Débit des opérations de lecture et d'écriture (en octets par seconde) pour une unité de sauvegarde utilisée pour la sauvegarde ou la restauration de bases de données. Ce compteur n'existe que lorsque les opérations de sauvegarde ou de restauration sont en cours d'exécution.|  
  
## <a name="see-also"></a>Voir aussi  
 [Unités de sauvegarde &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
