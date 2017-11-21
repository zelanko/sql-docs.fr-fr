---
title: MSSQLSERVER_17803 | Microsoft Docs
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
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: eb589ae903f8f3aa59d6b3180aae35416686cd10
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17803|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SRV_NOMEMORY|  
|Texte du message|Une erreur d'allocation de mémoire s'est produite au cours de l'établissement de la connexion. Réduisez la charge de mémoire qui n'est pas essentielle ou augmentez la quantité de mémoire système. La connexion a été fermée.%.*ls|  
  
## <a name="explanation"></a>Explication  
Le serveur manque de mémoire.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Déterminez la cause de la mémoire insuffisante au niveau du serveur. Les étapes de résolution des problèmes de mémoire génériques peuvent être utiles  
  

