---
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
caps.latest.revision: 12
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 8f40def8cedfcdd2a090941fb2dc8a6547a2d766
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3937"></a>MSSQLSERVER_3937
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|MSSQLSERVER|  
|ID d'événement|3937|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Texte du message|Une erreur s'est produite en tentant d'avertir le pilote de filtre FILESTREAM qu'une transaction était restaurée. Code d'erreur : 0x%0x.|  
  
## <a name="explanation"></a>Explication  
Une erreur a été retournée par le pilote RsFx lors de la publication d'une notification de restauration pour une transaction. Cela est probablement dû à une insuffisance de ressources. Cela peut provoquer une petite fuite de mémoire dans le pilote de filtre RsFx, mais elle sera libérée lorsque le processus sqlservr.exe qui a créé la transaction se terminera.  
  
## <a name="user-action"></a>Action de l'utilisateur  

