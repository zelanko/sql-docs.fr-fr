---
description: MSSQLSERVER_1222
title: MSSQLSERVER_1222 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1222 (Database Engine error)
ms.assetid: c5b1c2f4-f591-4cc1-aa17-204636a27f29
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2d6df8434df48d2492857826164b7730a4ac2d71
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88335895"
---
# <a name="mssqlserver_1222"></a>MSSQLSERVER_1222
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
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
  
