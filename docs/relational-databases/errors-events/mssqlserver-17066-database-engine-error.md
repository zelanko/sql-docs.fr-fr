---
title: MSSQLSERVER_17066 | Microsoft Docs
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
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
caps.latest.revision: 16
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ddca4870c0de6a18648c04264ea01b3c6364c70b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver17066"></a>MSSQLSERVER_17066
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|17066|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLASSERT_ONLY|  
|Texte du message|Assertion SQL Server : fichier : \<%s>, ligne=%d Échec d’assertion = ’%s’. Cette erreur est éventuellement liée à un délai d'attente. Si l'erreur persiste après une nouvelle exécution de l'instruction, utilisez DBCC CHECKDB pour vérifier l'intégrité structurelle de la base de données ou redémarrez le serveur pour vous assurer que les structures de données en mémoire ne sont pas corrompues.|  
  
## <a name="explanation"></a>Explication  
Cette erreur peut être provoquée par des erreurs temporaires liées à un délai d'attente ou par une corruption des données en mémoire ou sur disque.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Réexécutez l'instruction qui a provoqué le déclenchement de l'exception. Si l'erreur a été provoquée par un événement lié à un délai d'attente, elle peut ne pas se reproduire. Si le problème persiste, exécutez DBCC CHECKDB pour rechercher une corruption sur disque. Redémarrez le serveur pour vérifier que les structures de données en mémoire ne sont pas endommagées.  
  
## <a name="see-also"></a> Voir aussi  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
