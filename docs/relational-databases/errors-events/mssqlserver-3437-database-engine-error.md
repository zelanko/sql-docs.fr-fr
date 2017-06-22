---
title: MSSQLSERVER_3437 | Microsoft Docs
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
- 3437 (Database Engine error)
ms.assetid: b38216e2-b650-43bd-97af-061d54f60031
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 62fcf4360a9b5eefc971bf0f5443a9e9e96004aa
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3437"></a>MSSQLSERVER_3437
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3437|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODTC|  
|Texte du message|Une erreur s'est produite lors de la récupération de la base de données '%.*ls'. Impossible de se connecter à MS DTC pour vérifier l'état d'avancement de la transaction %S_XID. Corrigez MS DTC et réexécutez la récupération.|  
  
## <a name="explanation"></a>Explication  
Une ou plusieurs transactions distribuées utilisant MS DTC ([!INCLUDE[msCoName](../../includes/msconame-md.md)] Distributed Transaction Coordinator) étaient incomplètes lorsque la base de données a été fermée. La récupération de cette base de données a échoué car [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas se connecter à MS DTC pour terminer ou restaurer les transactions.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour récupérer cette base de données, vous devez d'abord résoudre le problème avec MS DTC. Pour analyser ce problème, examinez les journaux des événements Windows. Si vous ne parvenez pas à résoudre le problème avec MS DTC et à récupérer la base de données, restaurez une sauvegarde de la base de données.  
  

