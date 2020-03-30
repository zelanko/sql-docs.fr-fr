---
title: MSSQLSERVER_17066 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17066 (Database Engine error)
ms.assetid: 7d650bbf-c583-4af8-9e22-993ee2880d95
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cf83c11229024b7214b7fca7d777b3d2b46d2b06
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68100387"
---
# <a name="mssqlserver_17066"></a>MSSQLSERVER_17066
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|17066|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLASSERT_ONLY|  
|Texte du message|Assertion SQL Server : fichier : \<%s>, ligne=%d Échec d’assertion = ’%s’. Cette erreur est éventuellement liée à un délai d'attente. Si l'erreur persiste après une nouvelle exécution de l'instruction, utilisez DBCC CHECKDB pour vérifier l'intégrité structurelle de la base de données ou redémarrez le serveur pour vous assurer que les structures de données en mémoire ne sont pas corrompues.|  
  
## <a name="explanation"></a>Explication  
Cette erreur peut être provoquée par des erreurs temporaires liées à un délai d'attente ou par une corruption des données en mémoire ou sur disque.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Réexécutez l'instruction qui a provoqué le déclenchement de l'exception. Si l'erreur a été provoquée par un événement lié à un délai d'attente, elle peut ne pas se reproduire. Si le problème persiste, exécutez DBCC CHECKDB pour rechercher une corruption sur disque. Redémarrez le serveur pour vérifier que les structures de données en mémoire ne sont pas endommagées.  
  
## <a name="see-also"></a>Voir aussi  
[DBCC CHECKDB &#40;Transact-SQL&#41;](~/t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)  
  
