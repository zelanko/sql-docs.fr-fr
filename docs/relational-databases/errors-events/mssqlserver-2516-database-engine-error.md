---
title: MSSQLSERVER_2516 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2516 (Database Engine error)
ms.assetid: 79ed14b5-f53c-40c6-8334-8a083f732207
caps.latest.revision: 19
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c8ccf3ec56b38fa53290531aac17e966a23a5a8d
ms.lasthandoff: 04/11/2017

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
[Créer une sauvegarde complète de base de données &#40;SQL Server&#41;](~/relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  

