---
description: MSSQLSERVER_3937
title: MSSQLSERVER_3937 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3937 (Database Engine error)
ms.assetid: 312d5bbe-c8de-42db-af4b-4ccb448ce6ef
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 90e05045031d4bab8c2975a6e2349df85ca588c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456143"
---
# <a name="mssqlserver_3937"></a>MSSQLSERVER_3937
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|MSSQLSERVER|  
|ID de l’événement|3937|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|XACT_FILESTREAM_ROLLBACK_ERROR|  
|Texte du message|Une erreur s'est produite en tentant d'avertir le pilote de filtre FILESTREAM qu'une transaction était restaurée. Code d’erreur : 0x%0x.|  
  
## <a name="explanation"></a>Explication  
Une erreur a été retournée par le pilote RsFx lors de la publication d'une notification de restauration pour une transaction. Cela est probablement dû à une insuffisance de ressources. Cela peut provoquer une petite fuite de mémoire dans le pilote de filtre RsFx, mais elle sera libérée lorsque le processus sqlservr.exe qui a créé la transaction se terminera.  
  
## <a name="user-action"></a>Action de l'utilisateur  
