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
ms.openlocfilehash: 22767609a0281cc21a38d51716661ac98a8ffc24
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68118369"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
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
  
