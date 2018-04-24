---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2a91804459fb6ad8b56e445bdaf3810985c88a22
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|3151|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LDDB_MASTER_LOAD_FAILED|  
|Texte du message|Échec de la restauration de la base de données master. Arrêt du serveur SQL Server. Check the error logs, and rebuild the master database. Pour plus d'informations sur la façon de reconstruire la base de données master, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
Ceci est un message d’erreur général qui indique des problèmes variés avec la base de données **MASTER**.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez les journaux des erreurs pour plus d'informations. Pour créer une base de données **MASTER** utilisable, exécutez Setup.exe avec l’option REBUILDDATABASE. Pour plus d'informations, consultez « Procédure : installer SQL Server à partir de l'invite de commandes » dans la documentation en ligne de SQL Server.  
  
