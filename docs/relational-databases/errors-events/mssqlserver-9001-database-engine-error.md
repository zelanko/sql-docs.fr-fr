---
title: MSSQLSERVER_9001 | Microsoft Docs
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
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1eaae857105a13a133c2fc9cd216d701df9f51d5
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9001|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_NOT_AVAIL|  
|Texte du message|Le journal de la base de données '%.*ls' n'est pas disponible. Consultez le journal des événements pour voir s'il contient des messages d'erreur liés à ce problème. Résolvez toutes les erreurs et redémarrez la base de données.|  
  
## <a name="explanation"></a>Explication  
Le journal de la base de données a été mis hors connexion. Habituellement cela signifie une panne catastrophique qui nécessite le redémarrage de la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Diagnostiquez d'autres erreurs et redémarrez l'instance de SQL Server si elle n'a pas déjà redémarré.  
  

