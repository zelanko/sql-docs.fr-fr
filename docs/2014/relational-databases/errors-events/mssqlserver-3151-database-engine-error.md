---
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 18db8cfd54a9df36564d64c0cd94407bfefb21f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914793"
---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
    
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
 Consultez les journaux des erreurs pour plus d'informations. Pour créer une base de données **MASTER** utilisable, exécutez Setup.exe avec l’option REBUILDDATABASE. Pour plus d’informations, consultez « Comment : Installer SQL Server à partir de l’invite de commandes » dans la documentation en ligne de SQL Server.  
  
  
