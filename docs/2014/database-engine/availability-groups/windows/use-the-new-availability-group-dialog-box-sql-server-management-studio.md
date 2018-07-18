---
title: Utiliser la boîte de dialogue Nouveau groupe de disponibilité (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
caps.latest.revision: 39
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3501e3190495ffe41ce0a77e05c8048080e5536b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161150"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a>Utiliser la boîte de dialogue Nouveau groupe de disponibilité (SQL Server Management Studio)
  Cette rubrique contient des informations sur l'utilisation de la boîte de dialogue **Nouveau groupe de disponibilité** de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] pour créer un groupe de disponibilité AlwaysOn sur les instances [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] activées pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Un *groupe de disponibilité* définit un jeu de bases de données utilisateur qui basculent en tant qu'unité unique et un jeu de partenaires de basculement, appelés *réplicas de disponibilité*, qui prennent en charge le basculement.  
  
> [!NOTE]  
>  Pour obtenir une présentation des groupes de disponibilité, consultez [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
  
  
> [!NOTE]  
>  Pour plus d’informations sur les autres manières de créer un groupe de disponibilité, consultez [Tâches associées](#RelatedTasks)plus loin dans cette rubrique.  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
 Nous vous recommandons fortement de lire cette section avant d'essayer de créer votre premier groupe de disponibilité.  
  
###  <a name="PrerequisitesRestrictions"></a> Conditions préalables  
  
-   Avant de créer un groupe de disponibilité, vérifiez que les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergent les réplicas de disponibilité résident sur des nœuds WSFC (Windows Server Failover Clustering) différents au sein du même clustering de basculement WSFC. Vérifiez également que chaque instance du serveur est activée pour [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] et répond à toutes les autres conditions requises relatives à [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]. Pour plus d’informations, nous vous conseillons vivement de lire la rubrique [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Avant de créer un groupe de disponibilité, vérifiez que chaque instance de serveur qui hébergera un réplica de disponibilité possède un point de terminaison de mise en miroir de bases de données entièrement fonctionnel. Pour plus d’informations, consultez [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).  
  
-   Pour utiliser la boîte de dialogue **Nouveau groupe de disponibilité** , vous devez connaître les noms des instances de serveur qui hébergeront les réplicas de disponibilité. De plus, vous devez connaître les noms de toutes les bases de données que vous envisagez d’ajouter à votre nouveau groupe de disponibilité, et vous devez vérifier que ces bases de données respectent les conditions préalables requises et les restrictions de base de données de disponibilité décrites dans [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md). Si vous entrez des valeurs non valides, le nouveau groupe de disponibilité ne fonctionnera pas.  
  
###  <a name="Limitations"></a> Limitations  
 La boîte de dialogue **Nouveau groupe de disponibilité** ne permet pas d'effectuer les opérations suivantes :  
  
-   Créez un écouteur de groupe de disponibilité.  
  
-   Joindre les réplicas secondaires au groupe de disponibilité.  
  
-   Effectuer la synchronisation des données initiale.  
  
 Pour plus d'informations sur ces tâches de configuration, consultez [Suivi : Après la création d'un groupe de disponibilité](#FollowUp), plus loin dans cette rubrique.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.  
  
##  <a name="SSMSProcedure"></a> Utilisation de la boîte de dialogue Nouveau groupe de disponibilité (SQL Server Management Studio)  
 **Pour créer un groupe de disponibilité**  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal et cliquez sur le nom du serveur.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** .  
  
3.  Cliquez avec le bouton droit sur le nœud **Groupes de disponibilité** , puis sélectionnez la commande **Nouveau groupe de disponibilité** .  
  
4.  Cette commande ouvre la boîte de dialogue **Nouveau groupe de disponibilité** .  
  
5.  Sur la page **Général** , utilisez le champ **Nom du groupe de disponibilité** pour entrer le nom du nouveau groupe de disponibilité. Ce nom doit être un identificateur SQL Server valide et il doit être unique parmi tous les groupes de disponibilité du cluster WSFC. La longueur maximale d'un nom de groupe de disponibilité est de 128 caractères.  
  
6.  Dans la grille **Bases de données de disponibilité** , cliquez sur **Ajouter** et entrez le nom d'une base de données locale devant appartenir à ce groupe de disponibilité. Répétez cette opération pour chaque base de données à ajouter. Lorsque vous cliquez sur **OK**, la boîte de dialogue vérifie si votre base de données spécifiée respecte la configuration requise pour l'appartenance à un groupe de disponibilité. Pour plus d’informations sur ces conditions préalables requises, consultez [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
7.  Dans la grille **Bases de données de disponibilité** , cliquez sur **Ajouter** et entrez le nom d'une instance de serveur devant héberger un réplica secondaire. La boîte de dialogue n'essaie pas de se connecter à ces instances. Si vous spécifiez un nom de serveur incorrect, un réplica secondaire est ajouté mais vous ne pouvez pas vous y connecter.  
  
    > [!TIP]  
    >  Si vous avez ajouté un réplica et ne pouvez pas vous connecter à l'instance de serveur hôte, vous pouvez supprimer le réplica et en ajouter un nouveau. Pour plus d’informations, consultez [Supprimer un réplica secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) et [Ajouter un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
8.  Dans le volet **Sélectionner une page** de la boîte de dialogue, cliquez sur **Préférences de sauvegarde**. Puis, sur la page **Préférences de sauvegarde** , spécifiez à quel endroit les sauvegardes doivent se produire en fonction du rôle de réplica et attribuez des priorités de sauvegarde à chacune des instances de serveur qui hébergeront un réplica de disponibilité pour ce groupe de disponibilité. Pour plus d’informations, consultez [Propriétés de groupe de disponibilité : nouveau groupe de disponibilité &#40;page Préférences de sauvegarde&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).  
  
9. Pour créer le groupe de disponibilité, cliquez sur **OK**. Cette action entraîne la vérification par la boîte de dialogue du respect de la configuration requise par les bases de données spécifiées.  
  
     Pour quitter la boîte de dialogue sans créer le groupe de disponibilité, cliquez sur **Annuler**.  
  
##  <a name="FollowUp"></a> Suivi : Après avoir utilisé la boîte de dialogue Nouveau groupe de disponibilité pour créer un groupe de disponibilité  
  
-   Vous devez vous connecter en retour à chaque instance de serveur qui héberge un réplica secondaire pour le groupe de disponibilité et procéder comme suit :  
  
    1.  Joignez le réplica secondaire au groupe de disponibilité. Pour plus d’informations, consultez [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).  
  
    2.  Restaurez les sauvegardes actuelles de chaque base de données primaire et de son journal des transactions (à l'aide de RESTORE WITH NORECOVERY). Pour plus d’informations, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
    3.  Attachez immédiatement chaque base de données secondaire récemment préparée au groupe de disponibilité. Pour plus d’informations, consultez [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).  
  
-   Il est recommandé de créer un écouteur de groupe de disponibilité pour le nouveau groupe de disponibilité. Pour celà, vous devez être connecté à l'instance de serveur qui héberge le réplica principal actuel. Pour plus d'informations, consultez [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).  
  
##  <a name="RelatedTasks"></a> Tâches associées  
 **Pour configurer les propriétés du groupe de disponibilité et du réplica**  
  
-   [Modifier le mode de disponibilité d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [Modifier le mode de basculement d’un réplica de disponibilité &#40;SQL Server&#41;](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [Configurer la stratégie de basculement Flexible pour contrôler les Conditions pour le basculement automatique (groupes de disponibilité AlwaysOn)](configure-flexible-automatic-failover-policy.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [Configurer la sauvegarde sur des réplicas de disponibilité &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [Configurer l’accès en lecture seule sur un réplica de disponibilité &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [Configurer le routage en lecture seule pour un groupe de disponibilité &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [Modifier le délai d’expiration de session pour un réplica de disponibilité &#40;SQL Server&#41;](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 **Pour terminer la configuration du groupe de disponibilité**  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Autres méthodes de création d'un groupe de disponibilité**  
  
-   [Utiliser l’Assistant Groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Créer un groupe de disponibilité &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
 **Pour activer les groupes de disponibilité AlwaysOn**  
  
-   [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Pour configurer un point de terminaison pour la mise en miroir de bases de données**  
  
-   [Créer une base de données mise en miroir de point de terminaison pour les groupes de disponibilité AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Pour résoudre les problèmes de configuration de groupes de disponibilité AlwaysOn**  
  
-   [Résoudre les problèmes de Configuration des groupes de disponibilité AlwaysOn (SQL Server) supprimé](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Résoudre une opération d’ajout de fichier ayant échoué &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="RelatedContent"></a> Contenu associé  
  
-   [Guide de Solutions Microsoft SQL Server AlwaysOn pour une haute disponibilité et récupération d’urgence](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md)   
 [Conditions préalables, Restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
