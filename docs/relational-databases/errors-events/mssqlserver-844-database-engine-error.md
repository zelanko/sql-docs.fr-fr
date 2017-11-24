---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 38e7e2ac4a438f0a71bd1c61b9b57e41bd215245
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver844"></a>MSSQLSERVER_844
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|844|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|BUFLATCH_TIMEOUT_CONTINUE|  
|Texte du message|Un dépassement de délai s'est produit lors de l'attente du verrou de tampon -- type %d, bp %p, page %d:%d, état %#x, ID de base de données : %d, ID d'unité d'allocation : %I64d%ls, tâche 0x%p : %d, temps d'attente %d, indicateurs 0x%I64x, tâche propriétaire 0x%p.  Poursuite de l'attente.|  
  
## <a name="explanation"></a>Explication  
Un processus attend d'acquérir un verrou. Ce problème peut provenir d'une opération d'E/S qui tarde à s'achever. Le plus souvent, ce type d'erreur provient d'autres tâches qui bloquent les processus système. Dans d'autres cas, elle est due à une défaillance matérielle.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour prévenir cette erreur, procédez comme suit :  
  
-   Réduisez la charge de travail.  
  
-   Recherchez les erreurs d'E/S assimilées dans le journal des erreurs ou le journal des événements. Les erreurs d'E/S révèlent généralement un disque défectueux.  
  
-   Recherchez dans le journal des erreurs les tâches improductives et d’autres erreurs critiques.  
  
-   Si des erreurs critiques telles que les assertions surviennent fréquemment, corrigez-les.  
  
Si le problème persiste, contactez le service de support technique de Microsoft.  
  
