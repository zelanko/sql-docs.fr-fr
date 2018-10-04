---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a25d8e388e09621994b373cf3d6b206cd9c68b0b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48170349"
---
# <a name="mssqleng021075"></a>MSSQL_ENG021075
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21075|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'instantané initial de la publication '%1!' n'est pas encore disponible.|  
  
## <a name="explanation"></a>Explication  
 L'erreur MSSQL_ENG021075 est signalée si l'Agent de Distribution ou l'Agent de fusion est démarré avant que l'Agent d'instantané ait terminé la génération de l'instantané.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Si l'Agent d'instantané pour la publication n'a pas été démarré depuis que l'abonnement a été créé, ou s'il n'a pas été démarré depuis la dernière fois que vous avez choisi de réinitialiser l'abonnement, démarrez l'Agent d'instantané et laissez-le terminer avant de démarrer l'Agent de distribution ou l'Agent de fusion. Pour plus d’informations, consultez [Créer et appliquer un instantané](create-and-apply-the-snapshot.md).  
  
 Si l'Agent d'instantané ne se termine pas, recherchez les erreurs dans son historique et résolvez-les. Pour obtenir des informations sur l’affichage de l’état de l’agent et des détails de l’erreur dans le moniteur de réplication, consultez [Afficher des informations et effectuer des tâches pour les agents associés à une publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
 Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut fournir des pistes conduisant à l'erreur et/ou à d'autres messages d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
