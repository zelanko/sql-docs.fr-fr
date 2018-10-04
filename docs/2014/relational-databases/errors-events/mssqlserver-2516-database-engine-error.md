---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e88e90a56da7cb413c66da5f422b2b8f0d1abe91
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135589"
---
# <a name="mssqlserver2516"></a>MSSQLSERVER_2516
    
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
  
## <a name="see-also"></a>Voir aussi  
 [Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
  
