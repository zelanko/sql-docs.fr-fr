---
title: "Informations du serveur de distribution, Agents | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.monitor.Distributor.commonjobs..f1
ms.assetid: 5d601a64-6af0-42f9-81b1-cf0087f1c50d
caps.latest.revision: "13"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a60816a7220a5d1c2b9f15aeeac98e1a74da21ea
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="distributor-information-agents"></a>Informations du serveur de distribution, Agents
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] L’onglet **Agents** affiche des informations sur les agents et les travaux de maintenance associés au serveur de publication et à l’Abonné.  
  
 Les agents qui sont disponibles dans l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution incluent tous les agents qui sont disponibles dans l'onglet **Agents** pour un serveur de publication. Toutefois, l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution  inclut également un agent de distribution et un agent de fusion.  
  
 Pour plus d'informations sur l'instantané, le lecteur de journal et les agents de lecture de file d'attente, et les travaux de maintenance, consultez [Publisher Information, Agents](../../relational-databases/replication/publisher-information-agents.md). Remarquez que lorsque vous affichez les informations de l'agent sous l'onglet **Agents** pour un serveur de distribution, les informations du serveur de publication sont présentes pour les agents de lecture du journal et de l'instantané. Toutefois, dans l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution, vous pouvez également sélectionner **Agent de distribution** et **Agent de fusion**.  
  
## <a name="options"></a>Options  
 Les sections suivantes décrivent les données qui sont affichées sous cet onglet pour l'agent de distribution et l'agent de fusion.  
  
### <a name="distributor-agent"></a>Agent de distribution  
 **État**  
 État de l'Agent. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Réessayer  
  
-   Exécution en cours  
  
-   Non exécuté  
  
-   Jamais démarré  
  
 **Serveur de publication**  
 Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du serveur de publication.  
  
 **Publication**  
 Nom de la publication à laquelle l'agent est associé.  
  
 **Abonnement**  
 Nom de l'abonnement, sous la forme : [*SubscriberName*].[*Database*].  
  
 **Type**  
 Type de réplication: émission, réception ou anonyme.  
  
 **Dernière heure de début**  
 Dernière heure à laquelle l'Agent a démarré.  
  
 **Duration**  
 Durée pendant laquelle l'agent s'est exécuté. Cette durée représente le temps actuel si l'agent est en cours d'exécution ou le temps total d'exécution s'il a été exécuté et s'est terminé.  
  
 **Dernière action**  
 La dernière action effectuée au cours de la dernière exécution de l'Agent.  
  
 **Vitesse de transmission**  
 Vitesse, en commandes par seconde, à laquelle les commandes d'initialisation sont validées dans la base de données de distribution lors de la dernière exécution de l'Agent.  
  
 **Latence**  
 Durée, en secondes, écoulée entre la modification la plus récente validée dans la base de données de publication et la commande correspondante validée dans la base de données de distribution.  
  
 **#Trans**  
 Nombre de transactions validées dans la base de données de distribution lors de la dernière exécution de l'Agent.  
  
 **#Cmds**  
 Nombre de commandes validées dans la base de données de distribution lors de la dernière exécution de l'Agent. Une commande est équivalente à une modification des données, par exemple une mise à jour.  
  
 **Nb moy. de #Cmds**  
 Nombre moyen de commandes par transaction lors de la dernière exécution de l'Agent.  
  
### <a name="merge-agent"></a>Agent de fusion  
 **État**  
 État de l'Agent. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Error  
  
-   Réessayer  
  
-   Exécution en cours  
  
-   Non exécuté  
  
-   Jamais démarré  
  
 **Serveur de publication**  
 Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du serveur de publication.  
  
 **Publication**  
 Nom de la publication à laquelle l'agent est associé.  
  
 **Abonnement**  
 Nom de l'abonnement, sous la forme : [*SubscriberName*].[*Database*].  
  
 **Type**  
 Type de réplication: émission, réception ou anonyme.  
  
 **Dernière heure de début**  
 Dernière heure à laquelle l'Agent a démarré.  
  
 **Duration**  
 Durée pendant laquelle l'agent s'est exécuté. Cette durée représente le temps actuel si l'agent est en cours d'exécution ou le temps total d'exécution s'il a été exécuté et s'est terminé.  
  
 **Dernière action**  
 La dernière action effectuée au cours de la dernière exécution de l'Agent.  
  
 **Vitesse de transmission**  
 Vitesse, en commandes par seconde, à laquelle les modifications sont validées dans la base de données de distribution.  
  
 **Insertions du serveur de publication**  
 Nombre de commandes INSERT appliquées sur le serveur de publication.  
  
 **Mises à jour du serveur de publication**  
 Nombre de commandes UPDATE appliquées sur le serveur de publication.  
  
 **Suppressions du serveur de publication**  
 Nombre de commandes DELETE appliquées sur le serveur de publication.  
  
 **Conflits du serveur de publication**  
 Nombre de conflits sur le serveur de publication pendant le processus de fusion.  
  
 **Insertions de l'abonné**  
 Nombre de commandes INSERT appliquées sur l'abonné.  
  
 **Mises à jour de l'abonné**  
 Nombre de commandes UPDATE appliquées sur l'abonné.  
  
 **Suppressions de l'abonné**  
 Nombre de commandes DELETE appliquées sur l'abonné.  
  
 **Conflits de l'abonné**  
 Nombre de conflits sur l'abonné pendant le processus de fusion.  
  
## <a name="see-also"></a> Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Afficher des informations et exécuter des tâches pour un serveur de publication &#40;moniteur de réplication&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publisher-replication-monitor.md)   
 [Afficher des informations et effectuer des tâches pour les agents associés à une publication &#40;moniteur de réplication&#41;](../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-publication-agents.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  
