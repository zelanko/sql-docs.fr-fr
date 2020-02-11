---
title: Utiliser l’Assistant Basculement d’un groupe de disponibilité (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.failoverwizard.progress.f1
- sql12.swb.failoverwizard.f1
- sql12.swb.failoverwizard.selectnewprimary.f1
- sql12.swb.failoverwizard.confirmdataloss.f1
- sql12.swb.failoverwizard.connecttoreplicas.f1
helpviewer_keywords:
- failover [SQL Server], failover
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], configuring
ms.assetid: 4a602584-63e4-4322-aafc-5d715b82b834
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d440aace866527797252b67e3b397cc76d7dbdc7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787963"
---
# <a name="use-the-fail-over-availability-group-wizard-sql-server-management-studio"></a>Utiliser l’Assistant Basculement d’un groupe de disponibilité (SQL Server Management Studio)
  Cette rubrique explique comment effectuer un basculement manuel planifié ou forcé (basculement forcé) sur un groupe de disponibilité AlwaysOn à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou PowerShell dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un groupe de disponibilité bascule au niveau d'un réplica de disponibilité. Si vous basculez vers un réplica secondaire à l'état SYNCHRONIZED, l'Assistant exécute un basculement manuel planifié (sans perte de données). Si vous basculez vers un réplica secondaire à l’état UNSYNCHRONIZED ou NOT SYNCHRONIZING, l’Assistant effectue un basculement manuel forcé, également appelé *basculement forcé* (avec perte de données possible). Les deux formes de basculement manuel transfèrent le réplica secondaire auquel vous êtes connecté au rôle principal. Un basculement manuel planifié transfère actuellement l'ancien réplica principal sur le rôle secondaire. Après un basculement forcé, lorsque l'ancien réplica principal passe en ligne, il est transféré au rôle secondaire.  
  


  
-   **[!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]pages**  
  
     [Page Sélectionner le nouveau réplica principal](#SelectNewPrimaryReplica) (plus loin dans cette rubrique)  
  
     [Page se connecter au réplica](#ConnectToReplica) (plus loin dans cette rubrique)  
  
     [Page confirmer la perte de données potentielle](#ConfirmPotentialDataLoss) (plus loin dans cette rubrique)  
  
     [Page Résumé &#40;assistants groupe de disponibilité AlwaysOn&#41;](summary-page-always-on-availability-group-wizards.md)  
  
     [Page progression &#40;assistants groupe de disponibilité AlwaysOn&#41;](progress-page-always-on-availability-group-wizards.md)  
  
     [Page résultats &#40;assistants groupe de disponibilité AlwaysOn&#41;](results-page-always-on-availability-group-wizards.md)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Avant votre premier basculement manuel planifié, consultez la section « Avant de commencer » dans [Effectuer un basculement manuel planifié d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
 Avant votre premier basculement forcé, consultez les sections « Avant de commencer » et « Suivi : tâches essentielles après un basculement forcé » dans [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Une commande de basculement retourne dès que le réplica secondaire cible a accepté la commande. Toutefois, la récupération de la base de données est asynchrone après que le basculement du groupe de disponibilité est terminé.  
  
-   La cohérence entre bases de données sur plusieurs bases de données dans le groupe de disponibilité n'est pas conservée lors d'un basculement.  
  
    > [!NOTE]  
    >  Les transactions entre bases de données et les transactions distribuées ne sont pas prises en charge par [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Pour plus d’informations, consultez [Transactions entre bases de données non prises en charge pour la mise en miroir de bases de données ou les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](transactions-always-on-availability-and-database-mirroring.md).  
  
###  <a name="Prerequisites"></a> Conditions préalables requises pour utiliser l'Assistant Basculer le groupe de disponibilité  
  
-   Vous devez être connecté à l'instance de serveur qui héberge un réplica de disponibilité actuellement disponible.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Requiert l'autorisation ALTER AVAILABILITY GROUP sur le groupe de disponibilité, l'autorisation CONTROL AVAILABILITY GROUP, l'autorisation ALTER ANY AVAILABILITY GROUP ou l'autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 **Pour utiliser l'Assistant Basculer le groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge un réplica secondaire du groupe de disponibilité devant être basculé et développez l'arborescence du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Pour lancer l’Assistant Basculer le groupe de disponibilité, cliquez avec le bouton droit sur le groupe de disponibilité que vous allez basculer, puis sélectionnez **Basculement**.  
  
4.  Les informations présentées dans la page d' **Introduction** varient selon qu'un réplica secondaire est éligible ou non à un basculement planifié. Si cette page indique «**Effectuer un basculement planifié pour ce groupe de disponibilité**», vous pouvez basculer le groupe de disponibilité sans perte de données.  
  
5.  Dans la page **Sélectionner le nouveau réplica principal** , vous pouvez afficher l’état du réplica principal actuel et du quorum WSFC avant de choisir le réplica secondaire qui deviendra le nouveau réplica principal ( *cible de basculement*). Pour un basculement manuel planifié, veillez à sélectionner un réplica secondaire dont la valeur **Disponibilité du basculement** est «**Aucune perte de données**». Pour un basculement forcé, pour toutes les cibles de basculement possibles, cette valeur sera «**perte de données***#***, avertissements ()**», où *#* indique le nombre d’avertissements qui existent pour un réplica secondaire donné. Pour afficher les avertissements d’une cible de basculement donnée, cliquez sur sa valeur « Disponibilité de basculement ».  
  
     Pour plus d'informations, consultez la [page Sélectionner le nouveau réplica principal](#SelectNewPrimaryReplica), plus loin dans cette rubrique.  
  
6.  Dans la page **Se connecter au réplica** , connectez -vous à la cible de basculement. Pour plus d'informations, consultez la [page Se connecter au réplica](#ConnectToReplica), plus loin dans cette rubrique.  
  
7.  Si vous effectuez un basculement forcé, l'Assistant affiche la page **Confirmer la perte de données potentielle** . Pour poursuivre le basculement, vous devez sélectionner **Cliquez ici pour confirmer le basculement avec perte de données potentielle**. Pour plus d'informations, consultez[Confirmer la perte de données potentielle](#ConfirmPotentialDataLoss)plus loin dans cette rubrique.  
  
8.  Dans la page **Résumé** , analysez les conséquences du basculement sur le réplica secondaire sélectionné.  
  
     Si vous êtes satisfait de vos sélections, cliquez éventuellement sur **Script** pour créer un script des étapes que l'assistant devra exécuter. Puis, pour basculer le groupe de disponibilité vers le réplica secondaire sélectionné, cliquez sur **Terminer**.  
  
9. La page **Progression** affiche la progression du basculement du groupe de disponibilité.  
  
10. Lorsque l'opération de basculement est terminée, la page **Résultats** s'affiche. À la fin de l'Assistant, cliquez sur **Fermer** pour le quitter.  
  
     Pour plus d’informations, consultez [Page Résultats &#40;Assistants de groupe de disponibilité AlwaysOn&#41;](results-page-always-on-availability-group-wizards.md).  
  
11. Après un basculement forcé, consultez la section « Suivi : après un basculement forcé » dans [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).  
  
## <a name="help-for-pages-that-are-exclusive-to-this-wizard"></a>Aide sur les pages qui sont exclusives à cet Assistant  
 Cette section décrit les pages qui sont propres à l' [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)].  
  
 
  
 Les autres pages de cette partie de l'Assistant comprennent un ou plusieurs autres Assistants de groupes de disponibilité AlwaysOn et sont documentées dans des rubriques d'aide (F1) distinctes.  
  
###  <a name="SelectNewPrimaryReplica"></a> Select New Primary Replica Page  
 Cette section décrit les options de la page **Sélectionner le nouveau réplica principal** . Utilisez cette page pour sélectionner le réplica secondaire (cible de basculement) vers lequel le groupe de disponibilité va basculer. Ce réplica devient le nouveau réplica principal.  
  
#### <a name="page-options"></a>Options des pages  
 **Réplica principal actuel**  
 Affiche le nom du réplica principal, s'il est en ligne.  
  
 **État du réplica principal**  
 Affiche l'état du réplica principal actuel, s'il est en ligne.  
  
 **État du quorum**  
 Affiche l'état du quorum WSFC du réplica de disponibilité, parmi les suivants :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Quorum normal**|Le cluster a démarré avec le quorum normal.|  
|**Quorum forcé**|Le cluster a démarré avec le quorum forcé.|  
|**Quorum inconnu**|L'état du quorum du cluster n'est pas disponible.|  
|**Non applicable**|Le nœud hébergeant le réplica de disponibilité n'a aucun quorum.|  
  
 Pour plus d’informations, consultez [Modes de quorum WSFC et configuration de vote &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-quorum-modes-and-voting-configuration-sql-server.md).  
  
 **Choisir un nouveau réplica principal**  
 Utilisez cette grille pour choisir le réplica secondaire qui deviendra le nouveau réplica principal. Les colonnes de la grille sont les suivantes :  
  
 **Instance de serveur**  
 Affiche le nom de l'instance de serveur qui héberge un réplica secondaire.  
  
 **Mode de disponibilité**  
 Affiche le mode de disponibilité de l'instance de serveur, parmi les suivants :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Validation synchrone**|En mode de validation synchrone, avant de valider des transactions, un réplica principal avec validation synchrone attend qu'un réplica secondaire avec validation synchrone confirme qu'il a terminé le renforcement du journal. Le mode de validation synchrone garantit qu'une fois qu'une base de données secondaire particulière est synchronisée avec la base de données primaire, les transactions validées sont entièrement protégées.|  
|**Validation asynchrone**|En mode de validation asynchrone, le réplica principal valide les transactions sans attendre d'accusé de réception confirmant qu'un réplica secondaire avec validation asynchrone a renforcé le journal. Le mode de validation asynchrone réduit la latence de transaction sur les bases de données secondaires, mais leur permet d'être antérieures aux bases de données primaires, ce qui rend possible la perte de données.|  
  
 Pour plus d’informations, consultez [modes de disponibilité (groupes de disponibilité AlwaysOn)](availability-modes-always-on-availability-groups.md).  
  
 **Mode de basculement**  
 Affiche le mode de basculement de l'instance de serveur, parmi les suivants :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Automatique**|Un réplica secondaire configuré pour le basculement automatique prend également en charge le basculement manuel planifié chaque fois que le réplica secondaire est synchronisé avec le réplica principal.|  
|**Manuel**|Il existe deux types de basculement manuel : planifié (sans perte de données) et forcé (avec perte de données possible). Pour un réplica secondaire donné, un seul de ces modes est pris en charge, en fonction du mode de disponibilité et, en mode avec validation synchrone, en fonction de l'état de synchronisation du réplica secondaire. Pour déterminer la forme du basculement manuel actuellement prise en charge par un réplica secondaire donné, consultez la colonne **Disponibilité de basculement** de cette grille.|  
  
 Pour plus d’informations, consultez [Basculement et modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md).  
  
 **Disponibilité du basculement**  
 Affiche la disponibilité de basculement du réplica secondaire, parmi les options suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Aucune perte de données**|Ce réplica secondaire prend actuellement en charge le basculement planifié. Cette valeur est présente uniquement lorsqu'un réplica secondaire en mode de validation synchrone est actuellement synchronisé avec le réplica principal.|  
|**Perte de données, avertissements (** *#* **)**|Ce réplica secondaire prend actuellement en charge le basculement forcé (avec perte de données possible). Cette valeur est présente chaque fois que le réplica secondaire n'est pas synchronisé avec le réplica principal. Cliquez sur le lien d'un avertissement de perte de données pour plus d'informations sur la perte de données.|  
  
 **Actualiser**  
 Cliquez pour actualiser la grille.  
  
 **Annuler**  
 Cliquez pour annuler l'Assistant. Sur la page **Sélectionner le nouveau réplica principal** , l'annulation de l'Assistant entraîne sa fermeture sans qu'aucune action ne soit effectuée.  
  
###  <a name="ConfirmPotentialDataLoss"></a> Confirm Potential Data Loss Page  
 Cette section décrit les options de la page **Confirmer la perte de données potentielle** , qui s'affiche uniquement si vous effectuez un basculement forcé. Cette rubrique est utilisée uniquement par l' [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]. Utilisez cette page pour indiquer si vous voulez prendre le risque de perdre des données pour forcer le basculement du groupe de disponibilité.  
  
#### <a name="confirm-potential-data-loss-options"></a>Options de confirmation de la perte potentielle de données  
 Si le réplica secondaire sélectionné n'est pas synchronisé avec le réplica principal, l'Assistant affiche un avertissement indiquant que le basculement vers ce réplica secondaire peut entraîner la perte de données sur une ou plusieurs bases de données.  
  
 **Cliquez ici pour confirmer le basculement avec perte de données potentielle.**  
 Si vous êtes prêt à risquer de perdre des données pour rendre les bases de données de ce groupe de disponibilité disponibles aux utilisateurs, cliquez sur cette case à cocher. Si vous n'êtes pas prêt à prendre le risque de perdre des données, vous pouvez cliquer sur **Précédent** pour revenir à la page **Sélectionner le nouveau réplica principal** , ou vous pouvez cliquer sur **Annuler** pour quitter l'Assistant sans basculer le groupe de disponibilité.  
  
 **Annuler**  
 Cliquez pour annuler l'Assistant. Sur la page **Confirmer la perte de données potentielle** , l'annulation de l'Assistant provoque sa fermeture sans effectuer aucune action.  
  
###  <a name="ConnectToReplica"></a> Connect to Replica Page  
 Cette section décrit les options de la page **Se connecter au réplica** de l' [!INCLUDE[ssAoFoAgWiz](../../../includes/ssaofoagwiz-md.md)]. Cette page s'affiche uniquement si vous n'êtes pas connecté au réplica secondaire cible. Utilisez cette page pour vous connecter au réplica secondaire que vous avez sélectionné comme nouveau réplica principal.  
  
#### <a name="page-options"></a>Options des pages  
 **Colonnes de la grille :**  
 **Instance de serveur**  
 Affiche le nom de l'instance du serveur qui hébergera le réplica de disponibilité.  
  
 **Connecté en tant que**  
 Affiche le compte qui est connecté à l'instance de serveur, une fois que la connexion a été établie. Si cette colonne affiche «**Non connecté**» pour une instance de serveur donnée, vous devez cliquer sur le bouton **Se connecter** .  
  
 **Connexion**  
 Cliquez sur ce bouton si cette instance de serveur s'exécute sous un compte différent de celui des autres instances de serveur auxquelles vous devez vous connecter.  
  
 **Annuler**  
 Cliquez pour annuler l'Assistant. Sur la page **Se connecter au réplica** , l'annulation de l'Assistant provoque sa fermeture sans effectuer aucune action.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Modes de disponibilité (groupes de disponibilité AlwaysOn)](availability-modes-always-on-availability-groups.md)   
 [Basculement et modes de basculement &#40;groupes de disponibilité AlwaysOn&#41;](failover-and-failover-modes-always-on-availability-groups.md)   
 [Effectuer un basculement manuel planifié d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)   
 [Effectuer un basculement manuel forcé d’un groupe de disponibilité &#40;SQL Server&#41;](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)   
 [Récupération d’urgence WSFC par le quorum forcé &#40;SQL Server&#41;](../../../sql-server/failover-clusters/windows/wsfc-disaster-recovery-through-forced-quorum-sql-server.md)  
  
  
