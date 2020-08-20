---
description: MSSQLSERVER_9001
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
ms.openlocfilehash: dcccb9a93c762cf7ccb1d690bc0894005dc30da3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494466"
---
# <a name="mssqlserver_9001"></a>MSSQLSERVER_9001
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
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
  
