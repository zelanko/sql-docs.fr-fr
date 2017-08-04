---
title: "Haute disponibilité et récupération d’urgence pour Master Data Services | Documents Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/28/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: sabotta
ms.author: carlasab
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2afbf59101a0605dba2e79f09777160cb4de5cab
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---



# <a name="high-availability-and-disaster-recovery-for-master-data-services"></a>Haute disponibilité et récupération d’urgence pour Master Data Services

**Résumé :** Cet article décrit une solution pour Master Data Services (MDS) hébergé sur une configuration de groupe de disponibilité AlwaysOn. L’article décrit comment installer et configurer SQL 2016 Master Data Services sur un groupe de disponibilité SQL 2016 AlwaysOn. L’objectif principal de cette solution est d’améliorer la haute disponibilité et la récupération d’urgence des données du serveur principal MDS hébergées sur une base de données SQL Server.

## <a name="introduction"></a>Introduction


Cet article décrit une solution pour Master Data Services (MDS) hébergé sur une configuration de groupe de disponibilité AlwaysOn. L’article explique comment installer et configurer SQL 2016 MDS sur un groupe de disponibilité de SQL 2016 AlwaysOn (AG). L’objectif principal de cette solution est d’améliorer la haute disponibilité et la récupération d’urgence des données du serveur principal MDS hébergées sur une base de données SQL Server.

Pour implémenter la solution, vous devez effectuer les tâches suivantes, abordées dans cet article.

1.  [Installation et de basculement Windows Server cluster (WSFC)](#windows-server-failover-cluster-wsfc).

2.  [Configurer le groupe de disponibilité AlwaysOn](#sql-server-alwayson-availability-group).

3.  [Configurer MDS s’exécute sur un nœud WSFC](#configure-mds-to-run-on-an-wsfc-node).

Les sections ci-dessus vous présente brièvement les technologies, suivies des instructions. Pour plus d’informations sur les technologies, veuillez consulter les documents liés dans chaque section.

Cette solution décrite dans cet article s’appuie sur SQL Server AlwaysOn AG, dans laquelle chaque base de données a plusieurs réplicas synchrones ou asynchrones. Qu’un seul réplica accepte la transaction (accepte les demandes de l’utilisateur). Il s’agit du réplica principal.

Chaque réplica possède son propre stockage, il n’existe aucun stockage partagé centralisée dans cette solution. Lorsqu’il existe une défaillance logicielle ou une défaillance matérielle affecte le réplica principal, le réplica principal peut être basculé vers un réplica synchrone ou asynchrone que soit automatiquement ou manuellement en se basant sur la configuration et les situations. Cela garantit la haute disponibilité de la base de données avec une interruption minimale pour les utilisateurs.

Réplicas asynchrones sont généralement hébergées sur un centre de données distant à partir du centre de données du réplica principal. En cas de scénarios d’urgence, le réplica principal peut être basculé vers un autre centre de données. Cela garantit la récupération d’urgence de la base de données.

À des fins de démonstration, la solution décrite dans cet article utilise les versions suivantes du logiciel. Les versions antérieures doivent fonctionner même avec potentiellement légèrement différent.

-   Windows Server 2012 R2 avec cluster de basculement de serveur

-   SQL Server 2016 avec la fonctionnalité de Master Data Services

En outre, la solution utilise deux machines virtuelles, **MDS-HA1** et **MDS-HA2**, pour héberger les deux réplicas. Tant qu’il est pris en charge par SQL Server AlwaysOn AG, MDS ne limite pas le nombre de réplicas que vous pouvez utiliser.

Cet article suppose que vous disposez des connaissances de base sur Windows Server, un Cluster de basculement Windows Server, SQL Server AlwaysOn et SQL Server MDS.

## <a name="what-is-not-covered"></a>Ce qui n’est pas couverte

Ce document ne couvre pas les éléments suivants :

-   Comment faire d’IIS, le serveur web qui héberge le contrôleur de l’interface utilisateur, hautement disponible et récupérable après un incident de service de données. MDS n’impose pas de toutes les exigences particulières sur IIS, les techniques standards pour rendre IIS hautement disponible et l’équilibrage de charge peuvent fonctionner ici également.

-   Comment utiliser un cluster de basculement (FCI) SQL Server AlwaysOn pour prendre en charge la haute disponibilité (HA) sur le serveur principal MDS. Clustering de basculement SQL Server est une autre solution de haute disponibilité et est officiellement pris en charge par SQL Server, et il ne fonctionne pas avec MDS.

-   Comment utiliser une solution hybride de cluster de basculement SQL Server (ICF) et le groupe de disponibilité AlwaysOn pour prendre en charge la haute disponibilité sur le serveur principal MDS. La solution hybride ne fonctionne pas avec MDS.

## <a name="design-consideration"></a>Considération de conception

Figure 1 montre une configuration classique utilisée principalement dans le groupe de disponibilité AlwaysOn. Dans le centre de données primaire, il existe deux réplicas avec une relation de validation synchrone, et les réplicas dispose du privilège VOTE. Cela est principalement utilisée pour améliorer la haute disponibilité au cas où le réplica principal échoue.

Dans le centre de données de récupération d’urgence, il existe un réplica secondaire avec une relation de validation asynchrone avec le réplica principal. Ce centre de données est généralement dans une région géographique différente de celle du centre de données principal. Le réplica secondaire ne dispose pas de privilège VOTE.

Cette configuration est utilisée pour obtenir la récupération au cas où le centre de données principal est dans un incident, notamment un incendie, un tremblement de terre, un périphérique. Permet d’obtenir la configuration à la fois à haute disponibilité et de reprise après sinistre est relativement faible coût.

![Configuration standard pour le groupe de disponibilité AlwaysOn](media/Fig1_TypicalConfig.png)

Figure 1. Une Configuration de groupe de disponibilité AlwaysOn classique

Si vous n’avez pas besoin de prendre en compte la récupération d’urgence, vous n’avez pas besoin d’avoir un réplica dans un deuxième centre de données. Si vous avez besoin améliorer la haute disponibilité, vous pouvez avoir plusieurs réplicas synchrones dans le même centre de données primaire avec.

Par conséquent, il est important de tenir compte des scénarios et les impératifs et choisir le nombre de réplicas synchrone et asynchrone, vous devez, et quel centre de données vous devez les placer dans.

## <a name="windows-server-failover-cluster-wsfc"></a>Cluster de basculement Windows Server (WSFC)

Cette section décrit les tâches suivantes.

1.  [Installer la fonctionnalité de Cluster de basculement Windows](#install-failover-cluster-feature).

2.  [Créer un Cluster de basculement Windows Server](#create-a-windows-server-failover-cluster).

Comme indiqué dans la Figure 1 dans la section précédente, la solution décrite dans cet article inclut Cluster de basculement Windows Server (WSFC). Nous devons configurer WSFC, car SQL AlwaysOn dépend WFSC pour le basculement et la détection de défaillance.

WSFC est une fonctionnalité pour améliorer la disponibilité des applications et services. Il se compose d’un groupe d’instances de serveur windows indépendant avec le Service de Cluster de basculement Microsoft en cours d’exécution sur ces instances. Les instances de serveur windows (ou les nœuds qu’elles sont appelées parfois) sont connectés afin qu’ils puissent communiquer entre eux, et la détection de défaillance est possible. WSFC fournissent des fonctionnalités de détection et de basculement échec. Si un nœud ou un service échoue dans le cluster, puis la défaillance est détectée, et un autre nœud automatiquement ou manuellement commence à fournir des services hébergés sur le nœud défaillant. Par conséquent, les utilisateurs rencontrent uniquement des interruptions minimales de services et amélioration de la disponibilité de service.  

### <a name="prerequisites"></a>Configuration requise

Le système d’exploitation Windows Server est installé sur toutes les instances et les mises à jour sont corrigés.

>[!NOTE] 
>Il s’agit de **hautement recommandé** que vous installez la même version de Windows et de la même fonctionnalité définie sur toutes les instances pour éviter tout problème d’incompatibilité potentielle.

### <a name="install-failover-cluster-feature"></a>Installer la fonctionnalité de Cluster de basculement

Procédez comme suit pour chaque instance de Windows Server installer la fonctionnalité WSFC sur chaque instance. Vous avez besoin d’autorisations d’administrateur.

1.  Ouvrez **le Gestionnaire de serveur** dans Windows Server, puis cliquez sur **Ajout de rôles et fonctionnalités** dans le volet droit. Cette action lance la **Ajout de rôles et de la fonctionnalité Assistant**.

2.  Cliquez sur **suivant** jusqu'à ce que vous atteigniez le **fonctionnalités** page.

3.  Sélectionnez le **le Clustering de basculement** case à cocher, puis cliquez sur **suivant** pour terminer l’installation. Voir la Figure 2.

    Si vous êtes invité à confirmer la **ajouter des fonctionnalités qui sont requises pour le clustering de basculement**, cliquez sur **ajouter des fonctionnalités**. Voir la Figure 3.

    ![Assistant Ajout de rôles et fonctionnalités, le Clustering de basculement](media/Fig2_SelectFeatures.png)

    Figure 2

    ![Assistant Ajout de rôles et fonctionnalités, requis pour le cluster de basculement](media/Fig3_RequiredFeaturesFailover.png)

    Figure 3

4.  Sur le **Confirmation** , cliquez sur **installer** pour installer la fonctionnalité clustering avec basculement.

5.  Sur le **résultat** , vérifiez que tout a été installé correctement sans erreurs et avertissements.

### <a name="create-a-windows-server-failover-cluster"></a>Créer un cluster de basculement Windows Server

Une fois la fonctionnalité WSFC est installée sur toutes les instances, vous pouvez configurer WSFC. Vous devez uniquement effectuer cette opération sur un seul nœud.

1.  Ouvrez **le Gestionnaire de serveur** dans Windows Server, puis cliquez sur **Gestionnaire du Cluster de basculement** sur la **outil** menu en haut à droite pour lancer le gestionnaire.

2.  Dans **Gestionnaire du Cluster de basculement**, cliquez sur **valider la Configuration** dans le volet droit. Voir la Figure 4.

    ![Gestionnaire du Cluster de basculement, valider la Configuration](media/Fig4_ValidateConfig.png)

    Figure 4

3.  Dans le **valider une Configuration** **Assistant**, cliquez sur **suivant**.

4.  Dans le **sélectionner des serveurs ou un Cluster** boîte de dialogue zone, ajoutez les noms de serveur qui hébergera SQL Server, puis cliquez sur **suivant**. Voir la Figure 5.

    Dans cet exemple, nous avons ajouté deux instances, MDS-HA1 et HA2 de MDS.

    ![Valider un Assistant de Configuration, de sélectionner des serveurs ou d’une page de Cluster](media/Fig5_AddServer.png)

    Figure 5

5.  Sur le **Options de test** , cliquez sur **exécuter tous les tests**, puis cliquez sur **suivant**.

6.  Cliquez sur **suivant** à la fin de la validation.

    Le **validation** page affiche la progression et le **Résumé** page affiche un résumé des validations. Consultez les Figures 6 et 7.

7.  Sur le **Résumé** page, consultez les messages d’avertissement ou d’erreur.

    Erreurs doivent être corrigées. Toutefois, les avertissements ne peuvent pas être un problème. Un message d’avertissement signifie que « l’élément testée peut disposer de la, mais il est quelque chose que vous devez vérifier ». Par exemple, la figure 7 représente un « latence d’accès disque valider » qui peut être le disque est occupé à d’autres tâches temporairement en raison de l’avertissement, et vous pouvez l’ignorer. Vous devez vérifier le document en ligne pour chaque avertissement et le message d’erreur pour plus de détails. Voir la Figure 7.
 
    ![Valider l’Assistant Configuration, page de validation](media/Fig6_ValidationTests.png)

    Figure 6

    ![Assistant Validation d’une Configuration, page Résumé](media/Fig7_ValidationSummary.png)

    Figure 7

8.  Sur le **Résumé** page, vérifiez que le **créer le cluster maintenant en utilisant les nœuds validés** case à cocher est sélectionnée, puis cliquez sur **Terminer** pour démarrer le **création d’un Cluster** **Assistant**.

9.  Dans le **création d’un Cluster** **Assistant**, cliquez sur **suivant**.

10. Sur le **le Point d’accès pour administrer le Cluster** page, entrez le nom du cluster WSFC, puis cliquez sur **suivant**. Dans cet exemple, nous utilisons « MDS-HA » comme nom de cluster. Voir la Figure 8.

    ![Entrez le nom du Cluster](media/Fig8_EnterClusterName.png)

    Figure 8

11. Continuez à cliquer sur **suivant** pour terminer la création du cluster. Le **résumé de Cluster MDS-HA** section affiche les informations de cluster. Voir la Figure 9.

    ![Afficher les informations de résumé pour le Cluster](media/Fig9_ClusterSummary.png)

    Figure 9

    Si vous avez besoin ajouter un nœud ultérieurement, cliquez sur **ajouter un nœud** action dans le volet de droite dans **Gestionnaire du Cluster de basculement**.

Remarques :

-   La fonctionnalité WSFC n’est peut-être pas disponible sur toutes les éditions de Windows Server. Assurez-vous que votre édition possède cette fonctionnalité.

-   Assurez-vous que vous disposez des autorisations appropriées pour le programme d’installation de WSFC dans active directory. S’il existe un problème, consultez [Guide pas à pas du Cluster de basculement : configuration des comptes dans Active Directory](https://technet.microsoft.com/library/cc731002(v=ws.10).aspx).

Pour plus d’informations sur WSFC, consultez [Clusters de basculement](https://technet.microsoft.com/library/cc732488(v=ws.10).aspx).

## <a name="sql-server-alwayson-availability-group"></a>Groupe de disponibilité SQL Server AlwaysOn

Cette section décrit les tâches suivantes.

1.  [Groupe de disponibilité AlwaysOn activer SQL Server](#enable-sql-server-alwayson-availability-group-on-every-sql-server-instance).

2.  [Créer un groupe de disponibilité](#create-an-availability-group).

3.  [Validez et testez le groupe de disponibilité](#validation-and-test-the-availability-group).

SQLServer AlwaysOn solutions fournissent une haute disponibilité et récupération d’urgence pour les bases de données SQL Server. AlwaysOn a deux solutions possibles.
Les deux sont appuient sur WSFC.

-   Groupes de disponibilité AlwaysOn (AG)

-   Les Instances de Cluster de basculement AlwaysOn (FCI).

Groupe de disponibilité améliore la disponibilité au niveau de la base de données. Le groupe de disponibilité (il s’agit d’un ensemble de bases de données utilisateur) et son nom de réseau virtuel sont enregistrés en tant que ressources dans WSFC.

FCI améliore la disponibilité au niveau de l’instance. Service SQL Server et les services associés sont enregistrés en tant que ressources dans WSFC. En outre, la solution FCI requiert stockage sur disque partagé symétrique, telles que des partages de fichiers réseau SAN ou SMB, qui doit être disponible pour tous les nœuds du cluster WFC.


### <a name="prerequisites"></a>Conditions préalables

-   Installez SQL Server sur tous les nœuds. Pour plus d’informations, consultez [Installer SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server).

-   (Recommandé) Installez l’exacte même ensemble de fonctionnalités de SQL Server et la version sur chaque nœud. En particulier, MDS doivent être installés.

-   (Recommandé) Utilisez la même configuration sur chaque instance de SQL Server. En particulier, le même classement du serveur doit être configuré sur toutes les instances de SQL Server.

-   (Recommandé) Utiliser le même compte de service pour exécuter chaque instance de SQL Server. Dans le cas contraire, vous devez accorder l’autorisation sur chaque instance de SQL Server pour vous assurer que les instances de SQL Server peuvent communiquer avec eux.

-   Vérifiez que le paramètre de pare-feu Windows autorise les instances de SQL Server à communiquer entre eux.

### <a name="enable-sql-server-alwayson-availability-group-on-every-sql-server-instance"></a>Groupe de disponibilité AlwaysOn activer SQL Server sur chaque Instance SQL Server

1.  Dans le **Gestionnaire de Configuration SQL Server** cliquez sur **service SQL Server** dans le volet gauche, cliquez sur **SQL Server** dans le volet droit, puis cliquez sur **propriétés**. Voir la Figure 10.

    ![Fenêtre de propriétés de SQL Server](media/Fig10_SQLServerProperties.png)

    La figure 10

2.  Dans le **SQL Server (MSSQLSERVER)** **propriétés** boîte de dialogue, cliquez sur le **haute disponibilité AlwaysOn** onglet, puis sélectionnez le **activer les groupes de disponibilité AlwaysOn** case à cocher. Lorsqu’une valeur s’affiche dans le **nom de cluster de basculement Windows** zone de texte, cliquez sur **OK** pour continuer. Voir la Figure 11.

    ![Activer l’option de groupes de disponibilité AlwaysOn](media/Fig11_EnableAlwaysOn.png)

    Figure 11

3.  Quand une page d’avertissement s’affiche, cliquez sur **OK** pour continuer. Voir la Figure 12.

    ![Confirmer pour arrêter et redémarrer le service](media/Fig12_WarningServiceStopStart.png)

    Figure 12

4.  Cliquez sur **redémarrer**, redémarrer le **SQL Server** de service et que ce changement soit effectif. Voir la Figure 10.

>[!NOTE] 
>Vous pouvez modifier le compte de service exécutant le service SQL Server en utilisant le **Gestionnaire de Configuration SQL Server**. Cliquez sur le **session** onglet dans le **SQL Server (MSSQLSERVER)** **propriétés** boîte de dialogue. Voir la Figure 11.

### <a name="create-an-availability-group"></a>Créer un groupe de disponibilité

Une fois la fonctionnalité AlwaysOn est activée dans toutes les instances de SQL Server, vous créez un nouveau groupe de disponibilité qui contient la base de données MDS sur un nœud.

Groupe de disponibilité peut être créé uniquement sur les bases de données existantes. Par conséquent, soit créer une base de données MDS sur un nœud, ou de créer une base de données temporaire et de supprimer puis de la base de données temporaire. Dans cet exemple, nous créer une base de données emptyMDS et créer un groupe de disponibilité sur cette base de données MDS.

1.  Lancez **SQL Server Management Studio** (**SSMS**) sur un nœud, puis connectez-vous à l’instance locale de SQL Server avec les informations d’identification appropriées.

2.  Dans SSMS, ouvrez un **nouvelle requête** fenêtre et exécutez le script suivant pour créer une base de données vide. Remplacez C:\\temporaire avec l’emplacement que vous souhaitez utiliser pour effectuer une sauvegarde complète.

    ```
    CREATE DATABASE MDS\_Sample
    GO
    BACKUP DATABASE MDS\_Sample TO DISK='C:\\temp'
    GO
    ```

    >[!NOTE] 
    >Une sauvegarde de base de données complète est nécessaire pour créer le groupe de disponibilité sur cette base de données.

3.  Dans le **l’Explorateur d’objets**, développez le **haute disponibilité AlwaysOn** dossier puis cliquez sur **Assistant Nouveau groupe de disponibilité** pour lancer le **Assistant Nouveau groupe de disponibilité**. Voir la Figure 13.

    ![Assistant de lancer un nouveau groupe de disponibilité](media/Fig13_AvailabilityGroupsFolder.png)

    Figure 13

4.  Dans le **nouveau groupe de disponibilité** Assistant, cliquez sur **suivant** pour afficher les **spécifier le nom** page. Tapez un nom pour le groupe de disponibilité, puis cliquez sur **suivant**. Voir la Figure 14.

    ![Entrez le nom du groupe de disponibilité](media/Fig14_AvailabilityGroupName.png)

    La figure 14

5.  Cliquez sur la base de données que vous venez de créer sur le **sélectionner une base de données** page, puis cliquez sur **suivant**. Voir la Figure 15.

    ![Sélectionnez la base de données](media/Fig15_AvailabilityGroupSelectDatabase.png)

    Figure 15

6.  Sur le **spécifier les réplicas** , ajoutez un autre réplica en cliquant sur **ajouter un réplica**. Cette page répertorie déjà les instances de SQL Server en cours, locales en tant que réplica. Voir la Figure 16.

7.  Dans le **se connecter au serveur** boîte de dialogue zone, ajouter les informations d’identification appropriées, puis cliquez sur **connexion**.

    ![Se connecter à une instance de SQL Server](media/Fig16_AddReplicaConnectServer.png)

    Figure 16

    Vous devez maintenant voir deux réplicas dans la liste. Répétez cette étape pour ajouter d’autres nœuds en tant que réplicas. Voir la Figure 17.

    ![Afficher la liste des réplicas](media/Fig17_AvailabilityGroupSQLReplicas.png)

    Figure 17

    Pour chaque réplica, configurez les éléments suivants **validation synchrone**, **le basculement automatique**, et **secondaire accessible en lecture** paramètres. Voir la Figure
17.

    **Validation synchrone**: Cela garantit que si une transaction est validée sur le réplica principal d’une base de données, puis la transaction est également validée sur tous les autres réplicas synchrones. Validation asynchrone ne garantit pas que cela, et elle peut rester derrière le réplica principal.

    Vous devez généralement activer la validation synchrone uniquement lorsque les deux nœuds sont dans le même centre de données. Si elles se trouvent dans différents centres de données, validation synchrone peut ralentir les performances de la base de données.

    Si cette case à cocher n’est pas sélectionnée, la validation asynchrone est utilisée.

    **Le basculement automatique :** lorsque le réplica principal est arrêté, le groupe de disponibilité bascule automatiquement vers son réplica secondaire lorsque le basculement automatique est activée. Cela ne peut être activée que sur les réplicas avec validation synchrone.

    **Secondaire accessible en lecture :** par défaut, les utilisateurs ne peuvent pas se connecter à tous les réplicas secondaires. Cela permet aux utilisateurs de se connecter au réplica secondaire avec un accès en lecture seule.

8.  Sur le **spécifier les réplicas** , cliquez sur le **écouteur** onglet et procédez comme suit. Voir la Figure 18.

    A.  Cliquez sur **créer un écouteur de groupe de disponibilité** pour configurer un écouteur de groupe de disponibilité pour la connexion de base de données MDS.

    B.  Entrez un **écouteur nom DNS**, telles que MDSSQLServer.

    c.  Entrez le port SQL par défaut, 1433, dans le **Port** zone de texte.

    d.  Entrez le protocole DHCP dans le **Mode réseau** zone de texte, puis cliquez sur **suivant** pour continuer.

    >[!NOTE] 
    >Si vous le souhaitez, vous pouvez choisir « Adresse IP statique » comme le **Mode réseau** et entrez une adresse IP statique. Vous pouvez également entrer un port autre que 1433. 

    ![Configurer l’écouteur](media/Fig18_AvailabilityGroupCreateListener.png)

    La figure 18

9.  Sur le **sélectionner la synchronisation des données** , cliquez sur **complète**et spécifiez un partage réseau qui permettre accéder à chaque nœud. Cliquez sur **Suivant** pour continuer. Voir la Figure 19.

    Ce partage réseau sera utilisé pour stocker la sauvegarde de base de données pour créer les réplicas secondaires. Si ce n’est pas disponible pour votre organisation, choisissez un autre préférence de synchronisation de données. Reportez-vous à [groupe de disponibilité AlwaysOn de SQL Server 2016](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server) sur la façon d’utiliser d’autres options pour créer des réplicas secondaires. La figure 17 répertorie également les autres options.

    ![Configurer la synchronisation des données](media/Fig19_AvailabilityGroupDataSync.png)

    Figure 19 

10. Sur le **Validation** , vérifiez que toutes les validations réussissent et corriger les erreurs éventuelles. Cliquez sur **Suivant** pour continuer.

11. Sur le **Résumé** , examinez les paramètres de configuration, cliquez sur **Terminer**. Cela créera le groupe de disponibilité et le configurer.

12. Sur le **résultat** , vérifiez que toutes les mesures nécessaires ont été effectuées.

### <a name="validation-and-test-the-availability-group"></a>Validation et Test du groupe de disponibilité

1.  Ouvrez SSMS et se connecter au nom DNS de l’écouteur vous venez de créer dans le [créer un groupe de disponibilité](#create-an-availability-group) section. Dans cet exemple, il est MDSSQLServer.

2.  Dans **l’Explorateur d’objets**, développez le **haute disponibilité AlwaysOn** dossier, le bouton droit sur le groupe de disponibilité que vous venez créé dans le [créer un groupe de disponibilité](#create-an-availability-group) section, puis cliquez sur **afficher le tableau de bord**. Voir la Figure 20. L’état de ses réplicas et du nouveau groupe de disponibilité s’affiche.

    ![Afficher le tableau de bord](media/Fig20_ShowDashboard.png)

    Figure 20 

3.  Cliquez sur **basculement** pour effectuer un basculement vers un réplica synchrone et un réplica asynchrone. Cela consiste à vérifier que le basculement se produit correctement sans problème.

 Le programme d’installation AlwaysOn est terminée.

Pour plus d’informations sur le groupe de disponibilité AlwaysOn, consultez [groupe de disponibilité AlwaysOn de SQL Server 2016](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server).

## <a name="configure-mds-to-run-on-an-wsfc-node"></a>Configurer MDS pour être exécuté sur un nœud WSFC

Cette solution présentée dans cet article nécessite uniquement la base de données MDS principal est en cours d’exécution sur un WSFC. Autres parties de MDS, tels que les applications web et le Gestionnaire de configuration de MDS, peuvent être exécutés sur le nœud WSFC ou en dehors du cluster WSFC, tant que MDS peuvent se connecter pour le groupe de disponibilité.

1.  Ouvrez **Gestionnaire de Configuration de Service de données Master** sur un nœud, cliquez sur **Configuration de la base de données**, puis cliquez sur **créer la base de données** pour lancer le **Assistant Création de base de données**.

2.  Sur le **serveur de base de données** , tapez le nom DNS écouteur du groupe de disponibilité dans le **instance SQL Server** zone de texte, cliquez sur **tester la connexion**, puis cliquez sur **suivant**. Voir la Figure 21.

    ![Configurer le serveur de base de données avec l’écouteur de groupe de disponibilité](media/Fig21_MDSDatabaseServerListener.png)

    Figure 21

3.  Sur le **base de données** , tapez le nom de la base de données que vous avez créé dans le [créer un groupe de disponibilité](#create-an-availability-group) section, puis cliquez sur **suivant**. Voir la Figure 22.

    ![Créer et configurer la base de données](media/Fig22_MDSCreateDatabase.png)

    La figure 22

4.  Terminer la **créer la base de données** **Assistant**. Pour plus d’informations, consultez [Configuration et Installation de Services de données Master](https://docs.microsoft.com/sql/master-data-services/master-data-services-installation-and-configuration).

5.  Cliquez sur **Applications Web** dans **Gestionnaire de Configuration de Service de données Master** à configurer l’Application Web, puis cliquez sur **appliquer** pour appliquer les paramètres à MDS. Voir la Figure 23. Pour plus d’informations, consultez [Configuration et Installation de Services de données Master](https://docs.microsoft.com/sql/master-data-services/master-data-services-installation-and-configuration).

    ![Configurer l’application Web](media/Fig23_MDSWebApplication.png)

    La figure 23

    Le programme d’installation MDS est terminée. Vous pouvez répéter les étapes ci-dessus pour configurer MDS à s’exécuter sur tous les nœuds. La base de données principale est le même sur le même groupe de disponibilité.

6.  Si vous avez créé précédemment une base de données temporaire (consultez [créer un groupe de disponibilité](#create-an-availability-group) section) pour créer un groupe de disponibilité AlwaysOn, vous devez supprimer la base de données temporaire

    Pour plus d’informations sur le Service de données Master, consultez [Master Data Services](https://docs.microsoft.com/sql/master-data-services/master-data-services-overview-mds).

## <a name="conclusion"></a>Conclusion

Dans ce livre blanc, nous avons vu comment installer et configurer la base de données Master Data Services sur le groupe de disponibilité AlwaysOn de SQL Server. Cette configuration offre une haute disponibilité et récupération d’urgence sur la base de données Master Data Services. Pour implémenter cette configuration, vous devez installer et configurer Windows Server basculement Cluster, SQL Server groupe de disponibilité AlwaysOn et Master Data Services.

## <a name="feedback"></a>Commentaires

Ce document vous a-t-il été utile ? Veuillez envoyez-nous vos commentaires en cliquant sur **commentaires** en haut de l’article. 

Vos commentaires nous aideront à améliorer la qualité des livres blancs que nous diffusons. 


