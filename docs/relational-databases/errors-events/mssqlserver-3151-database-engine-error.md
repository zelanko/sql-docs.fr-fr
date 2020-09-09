---
description: MSSQLSERVER_3151
title: MSSQLSERVER_3151 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4d787407483cfe29c02fe48fa985cfa024dfdfed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88491199"
---
# <a name="mssqlserver_3151"></a>MSSQLSERVER_3151
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Détails  
  
| Attribut | Valeur |  
| :-------- | :---- |  
|Nom du produit|SQL Server|  
|ID de l’événement|3151|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LDDB_MASTER_LOAD_FAILED|  
|Texte du message|Échec de la restauration de la base de données master. Arrêt du serveur SQL Server. Consultez les journaux d'erreurs et reconstruisez la base de données principale. Pour plus d'informations sur la façon de reconstruire la base de données master, consultez la documentation en ligne de SQL Server.|  
  
## <a name="explanation"></a>Explication  
Ceci est un message d’erreur général qui indique des problèmes variés avec la base de données **MASTER**.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez les journaux des erreurs pour plus d'informations. Pour créer une base de données **MASTER** utilisable, exécutez Setup.exe avec l’option REBUILDDATABASE. Pour plus d’informations, consultez « Procédure : installer SQL Server à partir de l’invite de commandes » dans la documentation en ligne de SQL Server.  
  
