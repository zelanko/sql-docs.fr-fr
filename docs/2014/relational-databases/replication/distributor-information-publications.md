---
title: Réplication SQL Server boîte de dialogue « informations sur le serveur de distribution » | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.Distributor.Publications.f1
- sql12.rep.monitor.Distributor.commonjobs..f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.merge.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.snapshot.f1
- sql12.rep.monitor.Distributor.SubscriptionSummary.tran.f1
ms.assetid: 1f499277-7f12-42ba-8cf4-52b683434944
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8ca0717a63c9660c225ec238e1e4d2423f7d01ba
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010788"
---
# <a name="distributor-information-dialog-box"></a>Boîte de dialogue informations sur le serveur de distribution 
Cette rubrique fournit des informations sur la boîte de dialogue serveur de **distribution** 

## <a name="publications"></a>Publications

  L'onglet **Publications** fournit des informations résumées pour toutes les publications sur le serveur de distribution sélectionné dans le volet gauche.  
  
### <a name="options"></a>Options  
 Les informations affichées relatives aux publications prises en charge par le serveur de distribution incluent une colonne qui contient l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du serveur de publication. Dans le cas contraire, les informations de publication sont les mêmes que les informations de publication fournies lorsque vous consultez des publications dans la vue Serveur de publication du Moniteur de réplication. Pour plus d'informations sur les colonnes de l'onglet **Publications** , consultez [Publisher Information, Publications](publisher-information-publications.md).  

## <a name="subscription-watch-list"></a>Liste de suivi des abonnements

### <a name="transactional-replication"></a>Réplication transactionnelle 
  Les informations pour les abonnements transactionnels incluent le nom du serveur de publication. Dans le cas contraire, les fonctionnalités et les informations fournies dans cette boîte de dialogue sont les mêmes que celles de la vue Serveur de publication. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez [Informations sur le serveur de distribution, Liste de suivi des abonnements &#40;Publication transactionnelle, SQL Server 2005 et versions ultérieures&#41;](publisher-information-subscription-watch-list-transactional.md).  

### <a name="merge-replication"></a>Réplication de fusion
  Les informations pour les abonnements de publication de fusion incluent le nom du serveur de publication. Dans le cas contraire, les fonctionnalités et les informations fournies dans cette boîte de dialogue sont les mêmes que celles de la vue Serveur de publication. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez [Informations sur le serveur de publication, Liste de suivi des abonnements &#40;Publication de fusion, SQL Server 2005 et versions ultérieures&#41;](publisher-information-subscription-watch-list-merge-publication.md). 

### <a name="snapshot-replication"></a>Réplication d'instantané
  Les informations pour les abonnements de publication d'instantané incluent le nom du serveur de publication. Dans le cas contraire, les fonctionnalités et les informations fournies dans cette boîte de dialogue sont les mêmes que celles de la vue Serveur de publication. Pour plus d’informations sur l’utilisation de cette boîte de dialogue, consultez [Informations sur le serveur de distribution, Liste de suivi des abonnements &#40;Publication d’instantané, SQL Server 2005 et versions ultérieures&#41;](publisher-information-subscription-watch-list-snapshot.md).  

## <a name="agents"></a>Agents
   L’onglet **Agents** affiche des informations sur les agents et les travaux de maintenance associés au serveur de publication et à l’Abonné.  
  
 Les agents qui sont disponibles dans l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution incluent tous les agents qui sont disponibles dans l'onglet **Agents** pour un serveur de publication. Toutefois, l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution  inclut également un agent de distribution et un agent de fusion.  
  
 Pour plus d'informations sur l'instantané, le lecteur de journal et les agents de lecture de file d'attente, et les travaux de maintenance, consultez [Publisher Information, Agents](publisher-information-agents.md). Remarquez que lorsque vous affichez les informations de l'agent sous l'onglet **Agents** pour un serveur de distribution, les informations du serveur de publication sont présentes pour les agents de lecture du journal et de l'instantané. Toutefois, dans l'onglet **Agents** pour un serveur de distribution dans la vue Serveur de distribution, vous pouvez également sélectionner **Agent de distribution** et **Agent de fusion**.  
  
### <a name="options"></a>Options  
 Les sections suivantes décrivent les données qui sont affichées sous cet onglet pour l'agent de distribution et l'agent de fusion.  
  
### <a name="distributor-agent"></a>Agent de distribution  
 **État**  
 État de l'Agent. La liste ci-dessous indique les valeurs d'état possibles :  
  
-   Erreur    
-   Recommencer    
-   Exécution en cours    
-   Non exécuté    
-   Jamais démarré  
  
 **Publisher**  
 Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du serveur de publication.  
  
 **Publication**  
 Nom de la publication à laquelle l'agent est associé.  
  
 **Abonnement**  
 Nom de l'abonnement, sous la forme : [*SubscriberName*].[*Database*].  
  
 **Type**  
 Type de réplication: émission, réception ou anonyme.  
  
 **Dernière heure de début**  
 Dernière heure à laquelle l'Agent a démarré.  
  
 **Durée**  
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
  
-   Erreur    
-   Recommencer    
-   Exécution en cours    
-   Non exécuté    
-   Jamais démarré  
  
 **Publisher**  
 Instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du serveur de publication.  
  
 **Publication**  
 Nom de la publication à laquelle l'agent est associé.  
  
 **Abonnement**  
 Nom de l'abonnement, sous la forme : [*SubscriberName*].[*Database*].  
  
 **Type**  
 Type de réplication: émission, réception ou anonyme.  
  
 **Dernière heure de début**  
 Dernière heure à laquelle l'Agent a démarré.  
  
 **Durée**  
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
  
 
## <a name="see-also"></a>Voir aussi  
 [Démarrer le moniteur de réplication](monitor/start-the-replication-monitor.md)   
 [Surveillance de la réplication](monitoring-replication.md)  
  
  
