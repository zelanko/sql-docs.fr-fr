---
title: "SQL Server Integration Services (SSIS) de montée en charge pour la haute disponibilité | Documents Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2405235bcfa09d2cc49e007f4eae6975d9ebf7a5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="scale-out-support-for-high-availability"></a>Support de monter en charge pour la haute disponibilité

Dans SSIS monter en charge, le travail côté haute disponibilité est fournie via l’exécution de packages avec mise à l’échelle de plusieurs des travailleurs.
Master côté haute disponibilité est obtenue avec [Always On pour le catalogue SSIS](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb) et cluster de basculement Windows. Plusieurs instances de l’échelle des principales sont hébergés dans un cluster de basculement Windows. Lorsque le service de mise à l’échelle à Master ou SSISDB est arrêté sur le nœud principal, le service ou le SSISDB sur le nœud secondaire continue à accepter les demandes d’utilisateur et de communiquer avec montée en puissance des processus de travail. 

Pour configurer la principale côté haute disponibilité, suivez les étapes ci-dessous.

## <a name="1-prerequisites"></a>1. Conditions préalables
Configurez un cluster de basculement Windows. Pour obtenir des instructions, voir le billet de blog [Installing the Failover Cluster Feature and Tools for Windows Server 2012](http://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx) (Installation de la fonctionnalité de cluster de basculement et des outils pour Windows Server 2012). Vous devez installer la fonctionnalité et les outils sur tous les nœuds de cluster.

## <a name="2-install-scale-out-master-on-primary-node"></a>2. Installer la mise à l’échelle des principales sur le nœud principal
Installer les Services du moteur de base de données, Integration Services et l’échelle des principales sur le nœud principal pour l’échelle des maître. 

Pendant l’installation, vous devez 
### <a name="21-set-the-account-running-scale-out-master-service-to-a-domain-account"></a>2.1 définir le compte de service de mise à l’échelle des principale en cours d’exécution à un compte de domaine.
Ce compte doit être en mesure d’accéder à l’avenir les SSISDB sur le nœud secondaire dans un cluster de basculement Windows. Comme service de mise à l’échelle des principale et SSISDB séparément de basculement, ils ne peuvent pas être sur le même nœud.

![Configuration de serveur à haute disponibilité](media/ha-server-config.PNG)

### <a name="22-include-scale-out-master-service-dns-host-name-in-the-cns-of-scale-out-master-certificate"></a>2.2 incluent la montée en puissance Out Master service nom d’hôte DNS dans le certificat de noms communs d’échelle Out principal.

Ce nom d’hôte sera utilisé dans le point de terminaison de mise à l’échelle des Master. 

![Configuration de master à haute disponibilité](media/ha-master-config.PNG)

## <a name="3-install-scale-out-master-on-secondary-node"></a>3. Installer la mise à l’échelle des principales sur le nœud secondaire
Installer les Services du moteur de base de données, Integration Services et l’échelle des principales sur le nœud secondaire pour l’échelle des maître. 

Vous devez utiliser le même certificat de mise à l’échelle des Master avec le nœud principal. Exporter le certificat de mise à l’échelle des Master SSL sur le nœud principal avec la clé privée et l’installer dans le magasin de certificats racine de l’ordinateur loacl sur le nœud secondaire. Sélectionnez ce certificat lors de l’installation de mise à l’échelle des Master.

![Fichier de configuration à haute disponibilité maître 2](media/ha-master-config2.PNG)

> [!Note]
> Vous pouvez configurer plusieurs sauvegarde mise à l’échelle les masques en répétant les opérations de mise à l’échelle des maître secondaire.

## <a name="4-set-up-ssisdb-always-on"></a>4. Configurez toujours SSISDB sur

Les instructions pour définir AlwaysOn pour SSISDB peut être consulté à [Always On pour le catalogue SSIS (SSISDB)](../service/ssis-catalog.md#always-on-for-ssis-catalog-ssisdb).

En outre, vous devez créer un écouteur de gourp de disponibilité pour le groupe de disponibilité À que SSISDB ajouté. Consultez [créer ou configurer un écouteur de groupe de disponibilité](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).

## <a name="5-update-scale-out-master-service-configuration-file"></a>5. Mettre à jour le fichier de configuration de service de mise à l’échelle des principale
Fichier de configuration de service de mise à l’échelle des principale de mise à jour, \<pilote\>: \Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config, sur les nœuds principaux et secondaires. Mise à jour **SqlServerName** à *[nom DNS de l’écouteur disponibilité groupe], [Port]*.

## <a name="6-enable-package-execution-logging"></a>6. Activer la journalisation de l’exécution de package

Journalisation dans SSISDB est effectuée par la connexion **MS_SSISLogDBWorkerAgentLogin ## ##**, dont un mot de passe est généré automatiquement. Pour rendre le fonctionnement de l’enregistrement pour tous les réplicas de SSISDB, procédez comme suit.

### <a name="61-change-the-password-of-msssislogdbworkeragentlogin-on-primary-sql-server"></a>6.1 modifier le mot de passe de **MS_SSISLogDBWorkerAgentLogin ## ##** sur le serveur Sql principal.
### <a name="62-add-the-login-to-secondary-sql-server"></a>6.2 ajouter la connexion au serveur Sql secondaire.
### <a name="63-update-connection-string-of-logging"></a>6.3 mettre à jour la chaîne de connexion de la journalisation.
Appelez la procédure stockée [catalogue]. [update_logdb_info] avec 

@server_name= '*[Nom DNS de l’écouteur disponibilité groupe], [Port]*' 

et @connection_string = ' Source de données =*[nom DNS de l’écouteur disponibilité groupe]*,*[Port]*; Initial Catalog = SSISDB ; Id d’utilisateur = MS_SSISLogDBWorkerAgentLogin ## ## ; Mot de passe =*[Password]*] ;'.

## <a name="7-congifure-scale-out-master-service-role-of-windows-failover-cluster"></a>7. Rôle du service Congifure Scale Out principale du cluster de basculement Windows

Gestionnaire du cluster de basculement, connectez-vous au cluster pour monter en charge. Sélectionnez le cluster et cliquez sur **Action** dans le menu, puis **configurer un rôle en cours...** .

Dans la liste dépilé des **Assistant haute disponibilité**, sélectionnez **Service générique** dans **sélectionner un rôle** page et choisissez SQL Server Integration Services échelle Out Master 14.0 dans **sélectionner un Service** page.

Dans le **Point d’accès Client** , entrez le nom d’hôte DNS échelle Out Master service.

![Haute disponibilité Assistant 1](media/ha-wizard1.PNG)

Terminez l’Assistant.

## <a name="8-update-master-address-in-ssisdb"></a>8. Mettre à jour principale adresse dans SSISDB

Sur le serveur SQL principal, exécutez la procédure stockée [SSIS]. [catalogue]. [update_master_address] avec le paramètre @MasterAddress = N'https : / / [nom d’hôte de service de mise à l’échelle des maître DNS] : [Port Master]'. 

## <a name="9-add-scale-out-worker"></a>9. Ajouter la montée en charge de travail

Maintenant, vous pouvez ajouter la mise à l’échelle des travailleurs à l’aide de [échelle Out Manager](integration-services-ssis-scale-out-manager.md). Entrez *[nom DNS de l’écouteur SQL Server disponibilité groupe]*,*[Port]* dans la page de connexion.





