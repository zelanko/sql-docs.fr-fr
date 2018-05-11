---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5b737472be9bea3ac2a8e9e9a2fb393851dca457
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|9790|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Texte du message|Impossible d'acheminer le message entrant. La base de données MSDB système contenant les informations d'acheminement est en mode SINGLE USER.|  
  
## <a name="explanation"></a>Explication  
Une erreur s'est produite lors de la tentative de classement d'un message reçu sur le réseau : la base de données MSDB était en mode SINGLE USER.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Passez MSDB en mode MULTI USER à l'aide de la commande ALTER DATABASE.  
  
