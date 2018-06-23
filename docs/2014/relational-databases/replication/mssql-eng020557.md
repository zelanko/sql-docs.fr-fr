---
title: MSSQL_ENG020557 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG020557 error
ms.assetid: c43c6952-5b60-4347-b881-11a0004dce24
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2bec2f4f757cce10fa12be89606dd233c3b08d82
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143448"
---
# <a name="mssqleng020557"></a>MSSQL_ENG020557
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|20557|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Arrêt de l'Agent. Pour plus d'informations, reportez-vous à l'historique des travaux de l'Agent SQL Server pour le travail « %s ».|  
  
## <a name="explanation"></a>Explication  
 Un agent de réplication a été arrêté sans qu'aucune explication n'ait été écrite dans la table d'historique appropriée ou l'agent a été arrêté au milieu d'un processus.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Redémarrez l'Agent pour voir s'il va s'exécuter sans erreur. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) et [Concepts des exécutables de l’agent de réplication](concepts/replication-agent-executables-concepts.md).  
  
-   Vérifiez dans l'historique de l'Agent et des travaux si d'autres erreurs se sont produites vers la même heure. Pour des informations sur la manière dont vous pouvez afficher l'état des agents ainsi que des informations détaillées sur les erreurs dans le moniteur de réplication, consultez les rubriques suivantes :  
  
    -   Pour l’Agent d’instantané, l’Agent de lecture du journal et l’Agent de lecture de la file d’attente, consultez [Afficher des informations et effectuer des tâches pour les agents associés à une publication &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-publication-agents.md).  
  
    -   Pour l’Agent de distribution et l’Agent de fusion, consultez [Afficher des informations et effectuer des tâches pour les agents associés à un abonnement &#40;moniteur de réplication&#41;](monitor/view-information-and-perform-tasks-for-subscription-agents.md).  
  
-   Vérifiez que la connectivité de base fonctionne entre les ordinateurs auxquels l’Agent accède, puis connectez-vous à chaque ordinateur à l’aide d’un utilitaire tel que **sqlcmd** . Lors de la connexion, utilisez le même compte que celui qu'utilise l'Agent pour se connecter. Pour plus d'informations sur les autorisations requises pour chaque compte d'agent, consultez [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
-   Si l'erreur se produit lors de la création ou de l'application d'un instantané, vérifiez si les fichiers du répertoire d'instantanés comportent des erreurs.  
  
-   Si l'erreur continue de se produire, augmentez le facteur de journalisation de l'agent et spécifiez un fichier de sortie pour le journal. En fonction du contexte de l'erreur, cette action peut révéler les étapes qui conduisent à l'erreur et fournir d'autres messages d'erreur. Pour plus d'informations sur la configuration de la journalisation pour la réplication, consultez l'article [312292](http://support.microsoft.com/kb/312292)de la Base de connaissances Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  