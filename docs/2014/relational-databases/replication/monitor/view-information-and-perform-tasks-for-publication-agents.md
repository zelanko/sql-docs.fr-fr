---
title: Afficher des informations et effectuer des tâches pour les Agents associés à une Publication (moniteur de réplication) | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- agents [SQL Server replication], viewing information
- viewing replication agent information
- agents [SQL Server replication], tasks in Replication Monitor
ms.assetid: 2a420da2-66f4-4650-9bdd-1992221ed3fd
caps.latest.revision: 38
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2a82df3ae01b49d8ad7c8b48c5a07d6f57d2dbe8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36039038"
---
# <a name="view-information-and-perform-tasks-for-the-agents-associated-with-a-publication-replication-monitor"></a>Afficher des informations et effectuer des tâches pour les agents associés à une publication (moniteur de réplication)
  Le moniteur de réplication fournit l'onglet **Agents** qui contient des informations sur les agents associés à la publication sélectionnée. L’agent de distribution et l’Agent de fusion sont associés à des abonnement (pour plus d’informations, consultez [Afficher des informations et effectuer des tâches pour les agents d’abonnement &#40;moniteur de réplication&#41;](view-information-and-perform-tasks-for-subscription-agents.md)).  
  
 Cet onglet affiche des informations sur les agents suivants :  
  
-   Agent d'instantané, utilisé par toutes les publications  
  
-   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
-   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
 Pour afficher plus d'informations sur les options de cet onglet, sélectionnez **Aide** sur la barre de menus. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](start-the-replication-monitor.md).  
  
### <a name="to-view-information-and-perform-tasks-for-the-agents-associated-with-a-publication"></a>Pour afficher des informations et effectuer des tâches pour les agents associés à une publication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Pour consulter les informations sur les agents, cliquez sur l'onglet **Agents** . Vous pouvez aussi accéder à des informations plus détaillées et effectuer des tâches sur cet onglet :  
  
    -   Pour afficher des informations détaillées sur un agent (telles que des messages d'informations et des messages d'erreur), cliquez avec le bouton droit sur l'agent, puis cliquez sur **Afficher les détails**.  
  
    -   Pour afficher des informations détaillées sur le travail qui exécute l'agent (par exemple, des détails sur la planification, les étapes de travail, etc.), cliquez avec le bouton droit sur l'agent, puis cliquez sur **Propriétés**.  
  
    -   Pour gérer des profils pour l'agent, cliquez avec le bouton droit sur l'agent, puis cliquez sur **Profils d'agent**. Pour plus d’informations, voir [Utiliser des profils d’Agent de réplication](../agents/replication-agent-profiles.md).  
  
    -   Pour démarrer un agent qui n'est pas en cours d'exécution, cliquez avec le bouton droit sur l'agent, puis cliquez sur **Démarrer l'agent**.  
  
    -   Pour arrêter un agent qui est en cours d'exécution, cliquez avec le bouton droit sur l'agent, puis cliquez sur **Arrêter l'agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir des seuils et des avertissements dans le moniteur de réplication](set-thresholds-and-warnings-in-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour une publication &#40;moniteur de réplication&#41;](view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Administration de l’Agent de réplication](../agents/replication-agent-administration.md)   
 [Surveillance de la réplication](../monitoring-replication.md)  
  
  