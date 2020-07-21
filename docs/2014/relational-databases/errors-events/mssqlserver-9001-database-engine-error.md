---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e1a2f311ddd5ae1c6eee51ac3960b36fe1f2716e
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86550794"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|9001|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_NOT_AVAIL|  
|Texte du message|Le journal de la base de données '%.*ls' n'est pas disponible. Consultez le journal des événements pour voir s'il contient des messages d'erreur liés à ce problème. Résolvez toutes les erreurs et redémarrez la base de données.|  
  
## <a name="explanation"></a>Explication  
 Le journal de la base de données a été mis hors connexion. Habituellement cela signifie une panne catastrophique qui nécessite le redémarrage de la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Diagnostiquez d'autres erreurs et redémarrez l'instance de SQL Server si elle n'a pas déjà redémarré.  
  
  
