---
title: Utiliser l’Assistant Groupe de disponibilité (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.newagwizard.f1
- sql12.swb.newavgroupwiz.f1
helpviewer_keywords:
- New Availability Group Wizard, availability replicas
- Availability Groups [SQL Server], wizards
- Availability Groups [SQL Server], creating
ms.assetid: e1f1dccc-9e65-471d-8fd1-b45085c9484a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70227f556ae268144549616dab0895e70ff39de8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75228740"
---
# <a name="use-the-availability-group-wizard-sql-server-management-studio"></a>Utiliser l'Assistant Groupe de disponibilité (SQL Server Management Studio)
  Cette rubrique explique comment utiliser l'Assistant Nouveau groupe de disponibilité (dans [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]) pour créer et configurer un groupe de disponibilité AlwaysOn dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]. Un *groupe de disponibilité* définit un jeu de bases de données utilisateur qui basculent en tant qu'unité unique et un jeu de partenaires de basculement, appelés *réplicas de disponibilité*, qui prennent en charge le basculement.  
  
> [!NOTE]  
>  Pour obtenir une présentation des groupes de disponibilité, consultez [Vue d’ensemble des groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).  
  
-   **Avant de commencer :**  
  
     [Conditions préalables requises, restrictions et recommandations](#PrerequisitesRestrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour créer et configurer un groupe de disponibilité, à l’aide de**  [Assistant Nouveau groupe de disponibilité (SQL Server Management Studio)](#RunAGwiz)  
  
> [!NOTE]  
>  Comme alternative à l'utilisation de l'Assistant Nouveau groupe de disponibilité, vous pouvez utiliser les applets de commande [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell. Pour plus d’informations, consultez [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md) ou [Créer un groupe de disponibilité &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md).  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
 Nous vous recommandons fortement de lire cette section avant d'essayer de créer votre premier groupe de disponibilité.  
  
###  <a name="prerequisites-restrictions-and-recommendations"></a><a name="PrerequisitesRestrictions"></a>Conditions préalables requises, restrictions et recommandations  
 Dans la plupart des cas, vous pouvez utiliser l'Assistant Nouveau groupe de disponibilité pour exécuter toutes les tâches nécessaires à la création et à la configuration d'un groupe de disponibilité. Toutefois, vous devrez peut-être accomplir certaines de ces tâches manuellement.  
  
-   Avant de créer un groupe de disponibilité, vérifiez que les instances de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergent les réplicas de disponibilité résident sur des nœuds WSFC (Windows Server Failover Clustering) différents au sein du même clustering de basculement WSFC. Vérifiez également que chaque instance du serveur répond à toutes les autres conditions requises relatives à [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] . Pour plus d’informations, nous vous conseillons vivement de lire la rubrique [Conditions préalables requises, restrictions et recommandations pour les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).  
  
-   Si une instance de serveur que vous sélectionnez pour héberger un réplica de disponibilité s'exécute sous un compte d'utilisateur de domaine et n'a pas encore de point de terminaison de mise en miroir de bases de données, l'Assistant peut créer le point de terminaison et accorder l'autorisation CONNECT au compte de service de l'instance de serveur. Toutefois, si le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute en tant que compte intégré, tel que Système local, Service local ou Service réseau, ou comme compte qui n'appartient pas au domaine, vous devez utiliser des certificats pour l'authentification du point de terminaison, et l'Assistant ne peut pas créer un point de terminaison de mise en miroir de bases de données sur l'instance de serveur. Dans ce cas, nous recommandons de créer les points de terminaison de mise en miroir de bases de données manuellement avant de lancer l'Assistant Nouveau groupe de disponibilité.  
  
     `To use certificates for a database mirroring endpoint:`  
  
     [CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)  
  
     [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   Les instances de cluster de basculement (FCI) SQL Server ne prennent pas en charge le basculement automatique par les groupes de disponibilité. Par conséquent, tout réplica de disponibilité hébergé par une instance de cluster de basculement ne peut être configuré que pour un basculement manuel.  
  
-   Si une base de données est chiffrée ou même contient une clé de chiffrement de base de données (DEK), vous ne pouvez pas utiliser [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] ou [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] pour ajouter la base de données à un groupe de disponibilité. Même si une base de données chiffrée a été déchiffrée, ses sauvegardes de fichiers journaux peuvent contenir des données chiffrées. Dans ce cas, la synchronisation complète initiale des données peut échouer sur la base de données. En effet, l'opération de journalisation de la restauration peut nécessiter le certificat utilisé par les clés de chiffrement de base de données (DEK), et le certificat peut être indisponible.  
  
     Pour qu'une base de données déchiffrée puisse être ajoutée à un groupe de disponibilité, à l'aide de l'Assistant :  
  
    1.  Créez une sauvegarde de fichier journal de la base de données principale.  
  
    2.  Créez une sauvegarde complète de la base de données principale.  
  
    3.  Restaurez la sauvegarde de la base de données sur l'instance de serveur qui héberge le réplica secondaire.  
  
    4.  Créez une nouvelle sauvegarde du journal de la base de données primaire.  
  
    5.  Restaurez cette sauvegarde de journal sur la base de données secondaire.  
  
-   **Conditions préalables requises pour que l'Assistant effectue une synchronisation des données initiale complète**  
  
    -   Tous les chemins d'accès des fichiers de base de données doivent être identiques sur chaque instance de serveur qui héberge un réplica pour le groupe de disponibilité.  
  
    -   Aucun nom de base de données primaire ne peut exister sur une instance de serveur qui héberge un réplica secondaire. Cela signifie qu'aucune des nouvelles bases de données secondaires ne peut exister pour le moment.  
  
    -   Vous devez spécifier un partage réseau pour que l'assistant crée des sauvegardes et puisse y accéder. Pour le réplica principal, le compte utilisé pour démarrer le [!INCLUDE[ssDE](../../../includes/ssde-md.md)] doit disposer d'autorisations de système de fichiers en lecture et en écriture sur un partage réseau. Pour les réplicas secondaires, le compte doit disposer d'une autorisation en lecture sur le partage réseau.  
  
        > [!IMPORTANT]  
        >  Les sauvegardes de journaux feront partie de votre chaîne de sauvegarde du journal. Stockez les fichiers de sauvegarde des journaux de manière appropriée.  
  
     Si vous ne pouvez pas utiliser l'Assistant pour effectuer la synchronisation des données initiale complète, vous devez préparer vos bases de données secondaires manuellement. Vous pouvez le faire avant ou après l'exécution de l'Assistant. Pour plus d’informations, consultez [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Requiert l’appartenance au rôle serveur fixe **sysadmin** et l’autorisation de serveur CREATE AVAILABILITY GROUP, l’autorisation ALTER ANY AVAILABILITY GROUP ou l’autorisation CONTROL SERVER.  
  
 Nécessite également l'autorisation CONTROL ON ENDPOINT si vous souhaitez autoriser l'Assistant Nouveau groupe de disponibilité à gérer le point de terminaison de mise en miroir de bases de données.  
  
##  <a name="using-the-new-availability-group-wizard"></a><a name="RunAGwiz"></a> Utilisation de l'Assistant Nouveau groupe de disponibilité  
  
1.  Dans l'Explorateur d'objets, connectez-vous à l'instance de serveur qui héberge le réplica principal.  
  
2.  Développez le nœud **Haute disponibilité AlwaysOn** et le nœud **Groupes de disponibilité** .  
  
3.  Pour lancer l'Assistant Nouveau groupe de disponibilité, sélectionnez la commande **Assistant Nouveau groupe de disponibilité** .  
  
4.  La première fois que vous exécutez cet Assistant, une page **Introduction** apparaît. Pour ignorer cette page dans le futur, vous pouvez cliquer sur **Ne plus afficher cette page**. Après avoir lu cette page, cliquez sur **Suivant**.  
  
5.  Sur la page **Spécifier le nom du groupe de disponibilité** , entrez le nom du nouveau groupe de disponibilité dans le champ **Nom du groupe de disponibilité** . Ce nom doit être un identificateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valide, qui est unique sur le cluster de basculement WSFC et dans l'ensemble de votre domaine. La longueur maximale d'un nom de groupe de disponibilité est de 128 caractères.  
  
6.  Sur la page **Sélectionner des bases de données** , la grille répertorie les bases de données utilisateur sur l'instance de serveur connectée qui peuvent devenir des *bases de données de disponibilité*. Sélectionnez une ou plusieurs des bases de données répertoriées pour participer au nouveau groupe de disponibilité. Ces bases de données seront initialement les *bases de données primaires*initiales.  
  
     Pour chaque base de données répertoriée, la colonne **Taille** affiche la taille de la base de données, si elle est connue. La colonne **État** indique si une base de données particulière satisfait aux [conditions préalables requises](prereqs-restrictions-recommendations-always-on-availability.md)pour les bases de données de disponibilité. Si les conditions préalables requises ne sont pas remplies, une courte description de l'état indique la raison pour laquelle la base de données est inéligible ; par exemple, si elle n'utilise pas le mode de récupération complet. Pour plus d'informations, cliquez sur la description de l'état.  
  
     Si vous modifiez une base de données pour la rendre éligible, cliquez sur **Actualiser** pour mettre à jour la grille de bases de données.  
  
7.  Sur la page **Spécifier les réplicas** , spécifiez et configurez un ou plusieurs réplicas pour le nouveau groupe de disponibilité. Cette page contient quatre onglets. Le tableau suivant présente ces onglets. Pour plus d’informations, consultez la rubrique [Page Spécifier les réplicas &#40;Assistant Nouveau groupe de disponibilité : Assistant Ajout de réplica&#41;](specify-replicas-page-new-availability-group-wizard-add-replica-wizard.md).  
  
    |Onglet|Brève description|  
    |---------|-----------------------|  
    |**Réplicas**|Cet onglet vous permet de spécifier chaque instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] qui hébergera un réplica secondaire. Notez que l'instance de serveur à laquelle vous êtes actuellement connecté doit héberger le réplica principal.|  
    |**Points de terminaison**|Utilisez cet onglet pour vérifier tous les points de terminaison de mise en miroir de bases de données existants et également, si ce point de terminaison manque sur une instance de serveur dont les comptes de service utilisent l'authentification Windows, pour créer le point de terminaison automatiquement. **Remarque :**  Si une instance de serveur s’exécute sous un compte d’utilisateur qui n’est pas un domaine, vous devez apporter une modification manuelle à votre instance de serveur avant de pouvoir continuer dans l’Assistant. Pour plus d'informations, consultez [Conditions préalables requises](#PrerequisitesRestrictions), plus haut dans cette rubrique.|  
    |**Préférences de sauvegarde**|Utilisez cet onglet pour spécifier vos préférences de sauvegarde pour le groupe de disponibilité dans son ensemble, ainsi que les priorités de sauvegarde pour les différents réplicas de disponibilité.|  
    |**Port d'écoute**|Utilisez cet onglet pour créer un écouteur de groupe de disponibilité. Par défaut, l'assistant ne crée pas d'écouteur.|  
  
8.  Sur la page **Sélectionner la synchronisation de données initiale** , choisissez comment vous souhaitez que vos nouvelles bases de données secondaires soient créées et jointes au groupe de disponibilité. Choisissez l’une des options suivantes :  
  
    -   **Complète**  
  
         Sélectionnez cette option si votre environnement répond aux conditions requises pour démarrer automatiquement la synchronisation initiale des données (pour plus d’informations, consultez [Conditions préalables requises, restrictions et recommandations](#PrerequisitesRestrictions), plus haut dans cette rubrique).  
  
         Si vous sélectionnez **Complet**, après avoir créé le groupe de disponibilité, l'assistant sauvegarde chaque base de données primaire et son journal des transactions sur un partage réseau et restaure les sauvegardes sur chaque instance de serveur qui héberge un réplica secondaire. L'assistant joint ensuite chaque base de données secondaire au groupe de disponibilité.  
  
         Dans le champ **Spécifier un emplacement réseau partagé accessible par tous les réplicas** , spécifiez un partage de sauvegarde dans lequel l’intégralité de l’instance de serveur qui héberge les réplicas dispose d’un accès en lecture-écriture. Pour plus d'informations, consultez [Conditions préalables requises](#PrerequisitesRestrictions), plus haut dans cette rubrique.  
  
    -   **Joindre uniquement**  
  
         Si vous avez préparé manuellement les bases de données secondaires sur les instances de serveur qui hébergeront les réplicas secondaires, vous pouvez sélectionner cette option. L'assistant joindra les bases de données secondaires existantes au groupe de disponibilité.  
  
    -   **Ignorer la synchronisation de données initiale**  
  
         Sélectionnez cette option si vous souhaitez utiliser votre propre base de données et sauvegardes de journaux de vos bases de données primaires. Pour plus d’informations, consultez [Démarrer un mouvement de données sur une base de données secondaire AlwaysOn &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).  
  
9. La page **Validation** vérifie si les valeurs que vous avez spécifiées dans cet Assistant répondent aux exigences de l'Assistant Nouveau groupe de disponibilité. Pour effectuer un changement, cliquez sur **Précédent** pour revenir à une page antérieure de l'assistant pour modifier une ou plusieurs valeurs. Cliquez sur **Suivant** pour revenir à la page **Validation** , puis cliquez sur **Réexécuter la validation**.  
  
10. Sur la page **Résumé** , examinez vos choix pour le nouveau groupe de disponibilité. Pour apporter une modification, cliquez sur **Précédent** pour revenir à la page appropriée. Après avoir apporté la modification, cliquez sur **Suivant** pour revenir à la page **Résumé** .  
  
    > [!IMPORTANT]  
    >  Lorsque le compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] d'une instance de serveur qui hébergera un nouveau réplica de disponibilité n'existe pas en tant que connexion, l'Assistant nouveau groupe de disponibilité doit créer la connexion. Dans la page **Résumé** , l'Assistant affiche des informations pour la connexion qui doit être créée. Si vous cliquez sur **Terminer**, l'Assistant crée cette connexion pour le compte de service SQL Server et accorde l'autorisation de connexion CONNECT.  
  
     Si vous êtes satisfait de vos sélections, cliquez éventuellement sur **script** pour créer un script des étapes que l’Assistant va exécuter. Ensuite, pour créer et configurer le nouveau groupe de disponibilité, cliquez sur **Terminer**.  
  
11. La page **État d’avancement** affiche l’état d’avancement des étapes de création du groupe de disponibilité (configuration de points de terminaison, création du groupe de disponibilité et jointure du réplica secondaire au groupe).  
  
12. Lorsque ces étapes sont terminées, la page **Résultats** affiche le résultat de chaque étape. Si toutes ces étapes aboutissent, le nouveau groupe de disponibilité est entièrement configuré. Si l'une des étapes se solde par une erreur, vous devrez peut-être effectuer la configuration manuellement ou faire appel à l'assistant pour l'étape qui a échoué. Pour plus d'informations sur la cause d'une erreur donnée, cliquez sur le lien « Erreur » associé dans la colonne **Résultat** .  
  
     À la fin de l'Assistant, cliquez sur **Fermer** pour le quitter.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
 **Pour terminer la configuration du groupe de disponibilité**  
  
-   [Joindre un réplica secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [Préparer manuellement une base de données secondaire pour un groupe de disponibilité &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [Joindre une base de données secondaire à un groupe de disponibilité &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Créer ou configurer un écouteur de groupe de disponibilité &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 **Autres méthodes de création d'un groupe de disponibilité**  
  
-   [Utiliser la boîte de dialogue Nouveau groupe de disponibilité &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Créer un groupe de disponibilité &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [Créer un groupe de disponibilité &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
 **Pour activer les groupes de disponibilité AlwaysOn**  
  
-   [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 **Pour configurer un point de terminaison de mise en miroir de bases de données**  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour groupes de disponibilité AlwaysOn &#40;SQL Server PowerShell&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Créer un point de terminaison de mise en miroir de bases de données pour l’authentification Windows &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [Utiliser des certificats pour un point de terminaison de mise en miroir de bases de données &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [Spécifier l’URL de point de terminaison lors de l’ajout ou lors de la modification d’un réplica de disponibilité &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **Pour résoudre les problèmes de configuration des groupes de disponibilité AlwaysOn**  
  
-   [Résoudre les problèmes de configuration de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;supprimé](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [Résoudre les problèmes liés à l’échec d’une opération d’ajout de fichier &#40;groupes de disponibilité AlwaysOn&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> Contenu associé  
  
-   **Blogs :**  
  
     [AlwaysON - HADRON Learning Series : Worker Pool Usage for HADRON Enabled Databases (en anglais)](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [Blogs de l'équipe de SQL Server AlwaysOn : Blog officiel de l'équipe de SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Blogs des ingénieurs du Service clientèle et du Support technique de SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Vidéos**  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 1 : Présentation de la solution haute disponibilité de la prochaine génération](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server, nom de code « Denali », série AlwaysOn, Partie 2 : Génération d'une solution haute disponibilité critique à l'aide d'AlwaysOn](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Livres blancs :**  
  
     [Guide de solutions Microsoft SQL Server AlwaysOn pour la haute disponibilité et la récupération d'urgence](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [Livres blancs de Microsoft pour SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Livres blancs de l'équipe de consultants clients de SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>Voir aussi  
 [Le point de terminaison de mise en miroir de bases de données &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)   
 [Vue d’ensemble de groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Conditions préalables requises, restrictions et recommandations pour groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
