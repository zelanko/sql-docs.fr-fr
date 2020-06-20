---
title: MSSQL_ENG021076 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021076 error
ms.assetid: 612e5c59-ba3e-49c3-a3df-56bac3d850a2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 900c20dcbfe14e3e9dae40defb66f5441b3fa6b9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010142"
---
# <a name="mssql_eng021076"></a>MSSQL_ENG021076
    
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
 L'erreur MSSQL_ENG021076 peut se déclencher si l'Agent de distribution est démarré avant que l'Agent d'instantané ait terminé de générer l'instantané. Cette erreur n'est déclenchée que si la publication ne contient qu'un seul article. Si la publication contient plus d'un article, c'est l'erreur MSSQL_ENG021075 qui est déclenchée à la place. Pour plus d’informations, voir [MSSQL_ENG021075](mssql-eng021075.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si l'Agent d'instantané pour la publication n'a pas été démarré depuis la création de l'abonnement, ou depuis la dernière fois que vous avez réinitialisé l'abonnement, démarrez l'Agent d'instantané et laissez-le se terminer avant de démarrer l'Agent de distribution. Pour plus d’informations, consultez [Créer et appliquer un instantané](create-and-apply-the-snapshot.md).  
  
 Si l'Agent d'instantané ne se termine pas, recherchez les erreurs dans son historique et résolvez-les. Pour obtenir des informations sur l’affichage de l’état de l’agent et des détails de l’erreur dans le moniteur de réplication, consultez [Afficher des informations et effectuer des tâches à l’aide du moniteur de réplication](monitor/view-information-and-perform-tasks-replication-monitor.md).  
  
 Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
