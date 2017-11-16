---
title: MSSQLSERVER_617 | Microsoft Docs
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
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
caps.latest.revision: 14
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 570073a75fd1a325837812aa0f75dba2e1a90902
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|617|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|NODESHASH|  
|Texte du message|Le descripteur de l'ID d'objet %ld dans l'ID de base de données %d n'a pas été trouvé dans la table de hachage lors de la tentative de déhachage. Une entrée est manquante dans une table de travail. Réexécutez la requête. Si un curseur est concerné, fermez et rouvrez le curseur.|  
  
## <a name="explanation"></a>Explication  
SQL Server ne peut pas localiser la table de travail pour une entrée spécifique.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
1.  Si un curseur est impliqué, fermez et rouvrez celui-ci.  
  
2.  Réexécutez la requête.  
  

