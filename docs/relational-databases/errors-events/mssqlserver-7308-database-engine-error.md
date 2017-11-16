---
title: MSSQLSERVER_7308 | Microsoft Docs
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
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
caps.latest.revision: 7
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b1566e13224284179f42dc24002e37dec0063e17
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|7308|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|RMT_STA_DISABLED|  
|Texte du message|Le fournisseur OLE DB '%ls' ne peut pas être utilisé pour les requêtes distribuées, car le fournisseur est configuré pour s'exécuter en mode STA.|  
  
## <a name="explanation"></a>Explication  
Vous avez utilisé un fournisseur OLE DB configuré pour s'exécuter en mode thread unique cloisonné (STA, Single-Threaded Apartment). Les fournisseurs OLE DB qui s'exécutent en mode STA ne peuvent pas être utilisés pour les requêtes distribuées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour corriger cette erreur, configurez le fournisseur afin qu'il s'exécute en mode multithread cloisonné (MTA, Multi-Threaded Apartment). Si le fournisseur ne prend pas en charge le mode MTA, et qu'il ne peut pas effectuer une mise à niveau vers une version qui le prend en charge, envisagez de configurer le fournisseur pour une exécution hors processus. Le fournisseur doit être en mesure de vous indiquer s’il prend en charge le mode MTA ou une exécution hors processus.  
  

