---
title: MSSQLSERVER_9001 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9001 (Database Engine error)
ms.assetid: a54de936-90c6-4845-aa96-29d32f154601
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cfc717c63cb85207315d00ae8dc06fdd881a503c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912438"
---
# <a name="mssqlserver9001"></a>MSSQLSERVER_9001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9001|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LOG_NOT_AVAIL|  
|Texte du message|Le journal de la base de données '%.*ls' n'est pas disponible. Consultez le journal des événements pour voir s'il contient des messages d'erreur liés à ce problème. Résolvez toutes les erreurs et redémarrez la base de données.|  
  
## <a name="explanation"></a>Explication  
Le journal de la base de données a été mis hors connexion. Habituellement cela signifie une panne catastrophique qui nécessite le redémarrage de la base de données.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Diagnostiquez d'autres erreurs et redémarrez l'instance de SQL Server si elle n'a pas déjà redémarré.  
  
