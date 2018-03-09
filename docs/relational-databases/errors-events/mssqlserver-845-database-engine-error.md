---
title: MSSQLSERVER_845 | Microsoft Docs
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
- 845 (Database Engine error)
ms.assetid: 8fff6ad4-234c-44be-b123-e25d5e1cd63e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9615f970ef6a58e461c9fc35d1bd5cc325f2d37
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver845"></a>MSSQLSERVER_845
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|845|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|BUFLATCH_TIMEOUT|  
|Texte du message|Dépassement du délai lors de l'attente du type de verrou de mémoire tampon %d, page %S_PGID, ID de base de données %d.|  
  
## <a name="explanation"></a>Explication  
Un processus était en attente d'obtention d'un verrou mais n'a pas pu se le procurer suite à l'expiration du délai. Cette situation peut se produire si une opération d'E/S prend trop de temps à s'accomplir, souvent à cause d'autres tâches qui bloquent les processus système. Dans d'autres cas, elle est due à une défaillance matérielle.  
  
## <a name="user-action"></a>Action de l'utilisateur  
L'exécution des tâches suivantes peut éviter cette erreur :  
  
-   Réduisez la charge de travail.  
  
-   Recherchez des erreurs d'E/S associées dans le journal des erreurs ou le journal des événements. Les erreurs d'E/S sont généralement liées à un disque défectueux.  
  
-   Recherchez dans le journal des erreurs les tâches improductives et d'autres erreurs critiques.  
  
-   Si des erreurs critiques telles que les assertions surviennent fréquemment, corrigez-les.  
  
Si le problème persiste, contactez le service de support technique de Microsoft.  
  
