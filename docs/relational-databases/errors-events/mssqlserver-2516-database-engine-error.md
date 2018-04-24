---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba0df2fc4cd14e46ac5b4bee465f2db72f8ff282
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2516|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_REPAIR_DIFF_MAP_INVALIDATED|  
|Texte du message|La réparation de la bitmap différentielle pour la base de données NAME n'est pas valide. La chaîne de sauvegarde différentielle est interrompue. Vous devez d'abord effectuer une sauvegarde complète de la base de données avant d'effectuer une sauvegarde différentielle.|  
  
## <a name="explanation"></a>Explication  
Ce message d'information est retourné lorsque l'erreur MSSQLEngine_2515 est réparée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Effectuez une sauvegarde de base de données complète.  
  
## <a name="see-also"></a> Voir aussi  
[Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](~/relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
