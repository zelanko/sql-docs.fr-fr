---
title: "Always On for SSIS Catalog (SSISDB) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.ssis.ssms.alwayson.f1"
ms.assetid: 7f089455-35ee-4c13-884e-9254b685d07d
caps.latest.revision: 17
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 16
---
# Always On for SSIS Catalog (SSISDB)
  La fonctionnalité des groupes de disponibilité AlwaysOn est une solution de haute disponibilité et de récupération d’urgence qui offre une alternative au niveau de l’entreprise à la mise en miroir de bases de données. Un groupe de disponibilité prend en charge un environnement de basculement pour un ensemble discret de bases de données utilisateur, appelées bases de données de disponibilité, qui basculent de concert. Pour plus d’informations, consultez [Groupes de disponibilité AlwaysOn](https://msdn.microsoft.com/library/hh510230.aspx).  
  
 Pour assurer la haute disponibilité du catalogue SSIS (base de données SSISDB) et de son contenu (projets, packages, journaux d’exécution, etc.), vous pouvez ajouter la base de données SSISDB (de la même façon que toute autre base de données utilisateur) à un groupe de disponibilité AlwaysOn. Quand un basculement se produit, le nœud secondaire devient automatiquement le nouveau nœud primaire.  
 
 > [!IMPORTANT]  Quand un basculement se produit, les packages en cours d’exécution ne redémarrent pas ou ne reprennent pas. 
 
 **Dans cette rubrique :**  
  
1.  [Conditions préalables](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#prereq)  
  
2.  [Configurer la prise en charge de SSIS pour AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Firsttime)  
  
3.  [Mise à niveau de la base de données SSISDB dans un groupe de disponibilité](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Upgrade)  
  
##  <a name="a-nameprereqa-prerequisites"></a><a name="prereq"></a> Conditions préalables  
 Avant d’activer la prise en charge d’AlwaysOn pour la base de données SSISDB, vous devez au préalable exécuter la procédure suivante.  
  
1.  Configurez un cluster de basculement Windows. Pour obtenir des instructions, voir le billet de blog [Installing the Failover Cluster Feature and Tools for Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installation de la fonctionnalité de cluster de basculement et des outils pour Windows Server 2012). Vous devez installer la fonctionnalité et les outils sur tous les nœuds de cluster.  
  
2.  Installez SQL Server 2016 avec la fonctionnalité Integration Services (SSIS) sur chaque nœud du cluster.  
  
3.  Activez la fonctionnalité AlwaysOn pour chaque instance SQL Server. Pour plus d’informations, consultez [Activer et désactiver les groupes de disponibilité AlwaysOn (SQL Server)](https://msdn.microsoft.com/library/ff878259.aspx) .  
  
##  <a name="a-namefirsttimea-configure-ssis-support-for-always-on"></a><a name="Firsttime"></a> Configurer la prise en charge de SSIS pour AlwaysOn  
  
-   [Étape 1 : créer un catalogue Integration Services](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step1)  
  
-   [Étape 2 : ajouter la base de données SSISDB à un groupe de disponibilité AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2)  
  
-   [Étape 3 : activer la prise en charge de SSIS pour AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3)  
  
> [!IMPORTANT]  
>  -   Vous devez exécuter les étapes suivantes sur le **nœud primaire** du groupe de disponibilité.  
> -   Après avoir ajouté la base de données SSISDB à un groupe AlwaysOn, vous devez activer la **prise en charge de SSIS pour AlwaysOn** .  
  
###  <a name="a-namestep1a-step-1-create-integration-services-catalog"></a><a name="Step1"></a> Étape 1 : créer un catalogue Integration Services  
  
1.  Lancez **SQL Server Management Studio** , puis connectez-vous à une instance SQL Server dans le cluster que vous voulez définir comme **nœud primaire** du groupe de disponibilité AlwaysOn pour la base de données SSISDB.  
  
2.  Dans l’Explorateur d’objets, développez le nœud du serveur, cliquez avec le bouton droit sur le nœud **Catalogues Integration Services** , puis cliquez sur **Créer un catalogue**.  
  
3.  Cliquez sur **Activer l'intégration du CLR**. Le catalogue utilise des procédures stockées du CLR.  
  
4.  Cliquez sur **Activer l’exécution automatique des procédures stockées Integration Services au démarrage de SQL Server** pour que la procédure stockée [catalog.startup](https://msdn.microsoft.com/library/hh230984.aspx) soit exécutée à chaque redémarrage de l’instance de serveur SSIS. La procédure stockée effectue la maintenance de l'état des opérations pour le catalogue SSISDB. Elle résout l’état de tous les packages en cours d’exécution si et quand l’instance de serveur SSIS s’arrête.  
  
5.  Entrez un **mot de passe**, puis cliquez sur **OK**. Le mot de passe protège la clé principale de la base de données utilisée pour le chiffrement des données du catalogue. Enregistrez le mot de passe dans un emplacement sécurisé. Il est également recommandé de sauvegarder la clé principale de base de données. Pour plus d'informations, consultez [Back Up a Database Master Key](https://msdn.microsoft.com/library/aa337546.aspx).  
  
###  <a name="a-namestep2a-step-2-add-ssisdb-to-an-always-on-availability-group"></a><a name="Step2"></a> Étape 2 : ajouter la base de données SSISDB à un groupe de disponibilité AlwaysOn  
 La procédure à suivre pour ajouter la base de données SSISDB à un groupe de disponibilité AlwaysOn est presque identique à celle qui permet d’ajouter n’importe quelle autre base de données utilisateur à un groupe de disponibilité. Voir [Utiliser l’Assistant groupe de disponibilité](https://msdn.microsoft.com/library/hh403415.aspx).  
  
 Vous devez fournir le mot de passe que vous avez spécifié lors de la création du catalogue SSIS dans la page **Sélectionner les bases de données** de l’Assistant **Nouveau groupe de disponibilité** .  
  
 ![New Availability Group](../../integration-services/service/media/ssis-newavailabilitygroup.png "New Availability Group")  
  
###  <a name="a-namestep3a-step-3-enable-ssis-support-for-always-on"></a><a name="Step3"></a> Étape 3 : activer la prise en charge de SSIS pour AlwaysOn  
 Après avoir créé le catalogue Integration Services, cliquez avec le bouton droit sur le nœud des **catalogues Integration Services** , puis cliquez sur **Enable AlwaysOn Support…**(Activer la prise en charge d’AlwaysOn). La boîte de dialogue **Enable Support for AlwaysOn** (Activer la prise en charge d’AlwaysOn) doit s’afficher. Si cette option de menu est désactivée, vérifiez que vous disposez de tous les composants requis, puis cliquez sur **Actualiser**.  
  
 ![Enable Support for AlwaysOn](../../integration-services/service/media/ssis-enablesupportforalwayson.png "Enable Support for AlwaysOn")  
  
> [!WARNING]  
>  Le basculement automatique de la base de données SSISDB n’est pas pris en charge tant que vous n’activez pas la prise en charge de SSIS pour AlwaysOn.  
  
 Les réplicas secondaires nouvellement ajoutés à partir du groupe de disponibilité AlwaysOn apparaissent dans le tableau. Cliquez sur **connexion** pour chaque réplica figurant dans la liste, puis entrez les informations d’identification pour la connexion au réplica. Le compte d’utilisateur doit être membre du groupe sysadmin sur chaque réplica pour pouvoir activer la prise en charge de SSIS pour AlwaysOn. Une fois connecté à chaque réplica, cliquez sur **OK** pour activer la prise en charge de SSIS pour AlwaysOn.  
  
##  <a name="a-nameupgradea-upgrading-ssisdb-in-an-availability-group"></a><a name="Upgrade"></a> Mise à niveau de la base de données SSISDB dans un groupe de disponibilité  
 Si vous mettez à niveau SQL Server à partir d’une version précédente et si la base de données SSISDB se trouve dans un groupe de disponibilité AlwaysOn, la mise à niveau peut être bloquée par la règle « Vérification : SSISDB est dans des groupes de disponibilité AlwaysOn ». Ce blocage se produit parce que la mise à niveau s’exécute en mode mono-utilisateur, alors qu’une base de données de disponibilité doit être une base de données multi-utilisateurs. Par conséquent, durant une mise à niveau ou une mise à jour corrective, toutes les bases de données de disponibilité, y compris la base de données SSISDB, sont mises hors connexion, et ne sont pas mises à niveau ou corrigées. Pour permettre la poursuite de la mise à niveau, vous devez supprimer la base de données SSISDB du groupe de disponibilité, mettre à niveau ou corriger chaque nœud, puis ajouter la base de données SSISDB au groupe de disponibilité.  
  
 Si vous êtes bloqué par la règle « Vérification : SSISDB est dans des groupes de disponibilité AlwaysOn », vous devez mettre à niveau SQL Server en procédant comme suit.  
  
1.  Supprimez la base de données SSISDB du groupe de disponibilité. Pour plus d’informations, consultez [Supprimer une base de données secondaire d’un groupe de disponibilité &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-a-secondary-database-from-an-availability-group-sql-server.md) et [Supprimer une base de données primaire d’un groupe de disponibilité &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
2.  Cliquez sur **Réexécuter** dans l’Assistant Mise à niveau. La règle « Vérification : SSISDB est dans des groupes de disponibilité AlwaysOn » ne bloque plus.  
  
3.  Cliquez sur **Suivant** pour continuer la mise à niveau.  
  
4.  Une fois tous les nœuds mis à niveau, ajoutez la base de données SSISDB au groupe de disponibilité AlwaysOn. Pour plus d’informations, consultez [Ajouter une base de données à un groupe de disponibilité &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/add-a-database-to-an-availability-group-sql-server.md).  
  
 Si vous n’êtes pas bloqué pendant la mise à niveau de SQL Server et si la base de données SSISDB se trouve dans un groupe de disponibilité AlwaysOn, vous devez mettre à niveau la base de données SSISDB séparément après avoir mis à niveau le moteur de base de données SQL Server. Utilisez l’Assistant Mise à niveau de SSIS pour mettre à niveau la base de données SSISDB comme décrit dans la procédure suivante.  
  
1.  Déplacez la base de données SSISDB hors du groupe de disponibilité, ou supprimez le groupe de disponibilité si la base de données SSISDB est la seule base de données figurant dans le groupe de disponibilité. Pour effectuer cette tâche, vous devez lancer **SQL Server Management Studio** sur le **nœud primaire** du groupe de disponibilité.  
  
2.  Supprimez la base de données SSISDB de tous les **nœuds de réplica**.  
  
3.  Mettez à niveau la base de données SSISDB sur le **nœud primaire**. Dans**l’Explorateur d’objets** de SQL Server Management Studio, développez **Catalogues Integration Services**, cliquez avec le bouton droit sur **SSISDB**, puis sélectionnez **Mise à niveau de la base de données**. Suivez les instructions de l’ **Assistant Mise à niveau de SSISDB** pour mettre à niveau la base de données. Vous devez lancer l’ **Assistant Mise à niveau de SSIDB** localement sur le **nœud primaire**.  
  
4.  Suivez les instructions de [l’étape 2 : ajouter la base de données SSISDB à un groupe de disponibilité AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step2) pour rajouter la base de données SSISDB à un groupe de disponibilité.  
  
5.  Suivez les instructions de [l’étape 3 : activer la prise en charge de SSIS pour AlwaysOn](../../integration-services/service/always-on-for-ssis-catalog-ssisdb.md#Step3).  
  
  