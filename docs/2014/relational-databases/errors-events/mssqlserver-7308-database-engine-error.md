---
title: MSSQLSERVER_7308 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7308 (Database Engine error)
- single-threaded apartment mode
ms.assetid: cca9eab9-afb9-463d-abfd-0802257e2c99
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3b64f55f2ce7f71a358cc202a428191d5f1998f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209519"
---
# <a name="mssqlserver7308"></a>MSSQLSERVER_7308
    
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
  
  
