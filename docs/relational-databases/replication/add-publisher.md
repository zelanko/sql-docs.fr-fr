---
title: "Ajouter un serveur de publication | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.monitor.addpublisher.f1"
helpviewer_keywords: 
  - "boîte de dialogue Ajouter un serveur de publication"
ms.assetid: 4b57e298-655f-42c2-82bc-25cdad94a194
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Ajouter un serveur de publication
  La boîte de dialogue **Ajouter un serveur de publication** permet d'ajouter des serveurs de publication dans le volet de gauche du Moniteur de réplication. Après avoir ajouté un serveur de publication, sélectionnez le serveur de publication dans le volet de gauche pour afficher les informations sur ce dernier dans le volet de droite.  
  
## Options  
 **Ajouter**  
 Cliquez pour sélectionner un type de publication à ajouter, qui lance le **se connecter au serveur** boîte de dialogue. Les options sont :  
  
-   **Ajouter un serveur de publication SQL Server...**  
  
     Connectez-vous au serveur de publication à l'aide de la boîte de dialogue **Se connecter au serveur** .  
  
-   **Ajouter un serveur de publication Oracle...**  
  
     Connectez-vous au serveur de distribution [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associé au serveur de publication Oracle à l'aide de la boîte de dialogue **Se connecter au serveur** .  
  
-   **Spécifier un serveur de distribution et ajouter ses serveurs de publication…**  
  
     Connectez-vous au serveur de distribution [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] associé à un ou plusieurs serveurs de publication à l'aide de la boîte de dialogue **Se connecter au serveur** .  
  
 Après vous être connecté au serveur de publication ou au serveur de distribution, le nom du serveur de publication et celui de son serveur de distribution figurent dans la grille dans la partie supérieure de la boîte de dialogue.  
  
> [!NOTE]  
>  Le serveur de distribution et le serveur de publication sont généralement exécutés sur la même instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mais le serveur de distribution peut être exécuté sur une autre instance (cette configuration s'appelle un serveur de distribution distant).  
  
 **Supprimer**  
 Sélectionnez un serveur de publication dans la grille en haut de la boîte de dialogue, puis cliquez sur **Supprimer** pour supprimer le serveur de publication dans la liste des serveurs de publication doit être ajouté.  
  
> [!NOTE]  
>  Ce bouton ne permet pas de supprimer un serveur de publication qui figure dans le Moniteur de réplication. Pour supprimer un serveur de publication déjà affiché avec le bouton droit dans le volet gauche du moniteur de réplication et cliquez sur le serveur de publication **Supprimer**.  
  
 **Se connecter automatiquement au démarrage du Moniteur de réplication**  
 Sélectionnez cette option pour permettre au Moniteur de réplication de se connecter automatiquement au serveur de distribution et d'extraire les informations d'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette case à cocher est désactivée, vous devez vous connecter manuellement après le lancement du moniteur de réplication : cliquez sur le serveur de publication dans le volet gauche du moniteur de réplication, puis cliquez sur **Connect**.  
  
 **Actualiser automatiquement le statut de ce serveur de publication et de ses publications**  
 Sélectionnez cette option pour permettre au Moniteur de réplication d'actualiser l'état du serveur de publication sélectionné dans la grille située dans la partie supérieure de la boîte de dialogue. Si cette option est sélectionnée, le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état du serveur de publication et de ses publications. La fréquence d'interrogation est définie par l'option **Fréquence d'actualisation** . Pour plus d’informations sur l’actualisation dans le moniteur de réplication, consultez [mise en cache, l’actualisation et performances du moniteur de réplication](../../relational-databases/replication/monitor/caching-refresh-and-replication-monitor-performance.md).  
  
 **Fréquence d'actualisation**  
 Entrez une valeur (en secondes) pour définir la fréquence à laquelle le Moniteur de réplication interroge le serveur de distribution pour obtenir les informations d'état. Une valeur basse augmente la fréquence d'interrogation, ce qui peut affecter les performances du serveur de distribution si vous contrôlez un grand nombre de serveurs de publication. Il est recommandé de tester le système pour déterminer la valeur appropriée. L'option **Fréquence d'actualisation** est également utilisée si vous sélectionnez **Actualisation automatique** dans une fenêtre de détail du Moniteur de réplication.  
  
 **Afficher ce ou ces serveurs de publication dans le groupe suivant**  
 Sélectionnez un groupe de serveurs de publication dans la liste. Le serveur de publication se trouve dans ce groupe dans le volet de gauche. Les groupes permettent d'organiser les serveurs de publication et n'ont aucun impact sur le fonctionnement de la réplication. Si aucun groupe n'est défini et que vous voulez en créer un, cliquez sur **Nouveau groupe**.  
  
 **Nouveau groupe**  
 Cliquez pour créer un nouveau groupe de serveurs de publication. Un groupe de serveurs de publication permet d'organiser aisément les serveurs de publication dans le Moniteur de réplication. Les groupes n'affectent pas la réplication des données ni la relation entre les serveurs dans une topologie de réplication.  
  
## Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication-overview.md)  
  
  