---
title: MSSQLSERVER_844 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 844 (Database Engine error)
ms.assetid: 2060c886-1226-4066-bc0c-de90a1cfb82b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bdc05bbc2cf4db3875149ed35ac82dd922800484
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85767817"
---
# <a name="mssqlserver_844"></a>MSSQLSERVER_844
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|844|  
|Source de l’événement|MSSQLSERVER|  
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
  
