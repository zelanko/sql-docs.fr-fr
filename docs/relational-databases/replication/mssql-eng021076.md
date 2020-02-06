---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: fc907238dd294106b4086c7df647acb051dc9d1f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76288043"
---
# <a name="mssql_eng021076"></a>MSSQL_ENG021076
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|21076|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'instantané initial de l'article '%1!' n'est pas encore disponible.|  
  
## <a name="explanation"></a>Explication  
 L'erreur MSSQL_ENG021076 peut se déclencher si l'Agent de distribution est démarré avant que l'Agent d'instantané ait terminé de générer l'instantané. Cette erreur n'est déclenchée que si la publication ne contient qu'un seul article. Si la publication contient plus d'un article, c'est l'erreur MSSQL_ENG021075 qui est déclenchée à la place. Pour plus d’informations, voir [MSSQL_ENG021075](../../relational-databases/replication/mssql-eng021075.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si l'Agent d'instantané pour la publication n'a pas été démarré depuis la création de l'abonnement, ou depuis la dernière fois que vous avez réinitialisé l'abonnement, démarrez l'Agent d'instantané et laissez-le se terminer avant de démarrer l'Agent de distribution. Pour plus d’informations, consultez [Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
 Si l'Agent d'instantané ne se termine pas, recherchez les erreurs dans son historique et résolvez-les. Pour obtenir des informations sur l’affichage de l’état de l’agent et des détails de l’erreur dans le moniteur de réplication, consultez [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
