---
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f2ce32667d4f9615edcc7f15bf3d29d5d32490ad
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553914"
---
# <a name="mssqlserver_1222"></a>MSSQLSERVER_1222
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|1222|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LK_TIMEOUT|  
|Texte du message|Délai de requête de verrou dépassé.|  
  
## <a name="explanation"></a>Explication  
 Une autre transaction a maintenu un verrou sur une ressource requise plus longtemps que cette requête pouvait attendre.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Effectuez les tâches ci-dessous pour atténuer le problème :  
  
1.  Localisez la transaction qui maintient le verrou sur la ressource requise, si possible. Utilisez les vues de gestion dynamique **sys.dm_os_waiting_tasks** et **sys.dm_tran_locks**.  
  
2.  Si la transaction continue à maintenir le verrou, mettez fin à cette transaction, le cas échéant.  
  
3.  Exécutez de nouveau la requête.  
  
 Si cette erreur se produit fréquemment, modifiez le délai d'attente de verrouillage ou modifiez les transactions incriminées pour qu'elles maintiennent le verrou moins longtemps.  
  
  
