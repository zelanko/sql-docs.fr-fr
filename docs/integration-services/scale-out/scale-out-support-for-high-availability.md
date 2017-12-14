---
title: "Prise en charge de SQL Server Integration Services (SSIS) Scale Out pour la haute disponibilité | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2202b61a9efce26edb0edcef53204351338ecee6
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="scale-out-support-for-high-availability"></a>Prise en charge de Scale Out pour la haute disponibilité

Dans SSIS Scale Out, la haute disponibilité côté Worker est fournie par le biais de l’exécution de packages avec plusieurs Scale Out Workers.
La haute disponibilité côté Master est obtenue avec [Always On pour le catalogue SSIS](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) et le cluster de basculement Windows. Plusieurs instances de Scale Out Master sont hébergées dans un cluster de basculement Windows. Quand le service Scale Out Master ou SSISDB est arrêté sur le nœud principal, le service ou SSISDB sur le nœud secondaire continue à accepter les demandes d’utilisateur et à communiquer avec les Scale Out Workers. 

Pour configurer la haute disponibilité côté Master, suivez les étapes ci-dessous.

## <a name="1-prerequisites"></a>1. Conditions préalables
Configurez un cluster de basculement Windows. Pour obtenir des instructions, voir le billet de blog [Installing the Failover Cluster Feature and Tools for Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installation de la fonctionnalité de cluster de basculement et des outils pour Windows Server 2012). Vous devez installer la fonctionnalité et les outils sur tous les nœuds de cluster.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Installer Scale Out Master sur le nœud principal
Installez les services Moteur de base de données, Integration Services et Scale Out Master sur le nœud principal pour Scale Out Master. 

Pendant l’installation, vous devez effectuer les étapes suivantes. 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 Définir le compte exécutant le service Scale Out Master sur un compte de domaine.
Ce compte doit être en mesure d’accéder à SSISDB sur le nœud secondaire dans un cluster de basculement Windows à l’avenir. Le service Scale Out Master et SSISDB pouvant basculer séparément, ils peuvent se trouver sur des nœuds différents.

![Configuration du serveur à haute disponibilité](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 Inclure le nom d’hôte DNS du service Scale Out Master dans les noms communs du Scale Out Master.

Ce nom d’hôte sera utilisé dans le point de terminaison de Scale Out Master. 

![Configuration de Master à haute disponibilité](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Installer Scale Out Master sur le nœud secondaire
Installez les services Moteur de base de données, Integration Services et Scale Out Master sur le nœud secondaire pour Scale Out Master. 

Vous devez utiliser le même certificat Scale Out Master que pour le nœud principal. Exportez le certificat SSL Scale Out Master sur le nœud principal avec la clé privée et installez-le dans le magasin de certificats racine de la machine locale sur le nœud secondaire. Sélectionnez ce certificat quand vous installez Scale Out Master.

![Configuration de Master à haute disponibilité 2](media/ha-master-config2.PNG)

> [!Note]
> Vous pouvez configurer plusieurs Scale Out Masters de sauvegarde en répétant les opérations pour le Scale Out Master secondaire.

## <a name="4-set-up-ssisdb-always-on"></a>4. Configurer Always On pour SSISDB

Pour savoir comment configurer Always On pour SSISDB, vous pouvez consulter [Always On pour le catalogue SSIS (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

En outre, vous devez créer un écouteur de groupe de disponibilité pour le groupe de disponibilité auquel est ajouté SSISDB. Consultez [Créer ou configurer un écouteur de groupe de disponibilité](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Mettre à jour le fichier de configuration du service Scale Out Master
Mettez à jour le fichier de configuration du service Scale Out Master, \<lecteur\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config, sur les nœuds principal et secondaire. Définissez **SqlServerName** sur *[nom DNS de l’écouteur de groupe de disponibilité],[port]*.

## <a name="6-enable-package-execution-logging"></a>6. Activer la journalisation de l’exécution des packages

La journalisation dans SSISDB est effectuée par la connexion **##MS_SSISLogDBWorkerAgentLogin##**, dont le mot de passe est généré automatiquement. Pour effectuer des journalisations de tous les réplicas de SSISDB, effectuez les étapes suivantes.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 Changer le mot de passe de **##MS_SSISLogDBWorkerAgentLogin##** sur le serveur SQL Server principal.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 Ajouter la connexion au serveur SQL Server secondaire.
### <a name="63-update-connection-string-of-logging"></a>6.3 Mettre à jour la chaîne de connexion de la journalisation.
Appelez la procédure stockée [catalog].[update_logdb_info] avec 

@server_name = '*[nom DNS de l’écouteur de groupe de disponibilité],[port]*' 

et @connection_string = 'Data Source=*[nom DNS de l’écouteur de groupe de disponibilité]*,*[port]*;Initial Catalog=SSISDB;User Id=##MS_SSISLogDBWorkerAgentLogin##;Password=*[mot de passe]*];'.

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Configurer le rôle du service Scale Out Master du cluster de basculement Windows

Dans le Gestionnaire du cluster de basculement, connectez-vous au cluster pour Scale Out. Sélectionnez le cluster et cliquez sur **Action** dans le menu, puis cliquez sur **Configurer un rôle...**.

Dans la fenêtre **Assistant Haute disponibilité** qui apparaît, sélectionnez **Service générique** dans la page **Sélectionner un rôle** et choisissez SQL Server Integration Services Scale Out Master 14.0 dans la page **Sélectionner un service**.

Dans la page **Point d’accès client**, entrez le nom d’hôte DNS du service Scale Out Master.

![Assistant Haute disponibilité 1](media/ha-wizard1.PNG)

Terminez l’Assistant.

## <a name="8-update-master-address-in-ssisdb"></a>8. Mettre à jour l’adresse du Master dans SSISDB

Sur le serveur SQL Server principal, exécutez la procédure stockée [SSIS].[catalog].[update_master_address] avec le paramètre @MasterAddress = N'https://[nom d’hôte DNS du service Scale Out Master]:[port Master ]'. 

## <a name="9-add-scale-out-worker"></a>9. Ajouter Scale Out Worker

Maintenant, vous pouvez ajouter des Scale Out Workers à l’aide de [Scale Out Manager](integration-services-ssis-scale-out-manager.md). Entrez *[nom DNS de l’écouteur de groupe de disponibilité SQL Server]*,*[port]* dans la page de connexion.




