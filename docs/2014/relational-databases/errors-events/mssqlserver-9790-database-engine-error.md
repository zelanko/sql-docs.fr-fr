---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5747a13e60182596610f25dd4ed1243670ff5018
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48151173"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
    
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
  
  
