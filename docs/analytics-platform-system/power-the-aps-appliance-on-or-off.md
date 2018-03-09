---
title: "L’alimentation de l’Appliance APS On ou Off (système de plateforme Analytique)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2258f8e3-e7a1-4455-8a5e-10d4d15775d6
caps.latest.revision: "45"
ms.openlocfilehash: 5e96898197098556d256c46b517ea42650c4c3ac
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="power-the-aps-appliance-on-or-off"></a>Le dispositif de points d’accès de l’alimentation ou désactiver
Cette rubrique décrit comment mettre sous tension ou hors tension votre Systemappliance de plateforme Analytique qui est en cours d’exécution Parallel Data Warehouse et éventuellement une région HDInsight en cours d’exécution. Utilisez cette rubrique lorsqu’un dispositif de système de plateforme Analytique est déplacé, ou pour mettre sur un appareil après une panne catastrophique.  
  
Mise sous tension de l’application et n’est pas le même que le démarrage et arrêt des services d’application. Pour plus d’informations sur ce sujet, consultez [PDW l’état des Services &#40; Système de plateforme Analytique &#41; ](pdw-services-status.md). Pour plus d’informations sur la mise sous tension ou désactiver un SQL Server 2008 Parallel Data Warehouse, consultez le fichier d’aide de SQL Server 2008 Parallel Data Warehouse. Pour plus d’informations sur la mise sous tension ou désactiver de SQL Server 2012 AU1 AU2 Parallel Data Warehouse, consultez le fichier d’aide pour ces versions.  
  
Lorsque ces instructions spécifient la connexion à un nœud SQL Server PDW, la connexion peut être locale à l’aide de périphériques connectés (KVM) ou à distance à l’aide du Bureau à distance. Certaines actions doivent être physique (activation sur un bouton d’alimentation) et autres (par exemple, d’arrêt) peuvent être physiques ou des commandes à l’aide de Windows.  
  
Connexions aux nœuds de SQL Server PDW peuvent être établies en utilisant les adresses IP attribuées aux nœuds, ou à partir de la **HST01** ordinateur en utilisant le **Gestionnaire du Cluster de basculement** (**cluadmin.msc**) ou **Gestionnaire Hyper-V** (**virtmgmt.msc**) les applications et le droit sur le nom du nœud.  
  
## <a name="PowerOff"></a>Mise hors tension de l’appareil  
  
### <a name="before-you-begin"></a>Avant de commencer  
Avant la mise hors tension l’appliance, vous devez se terminer toutes les activités sur l’appareil. Pour mettre fin à toutes les activités :  
  
-   Utilisez le **Sessions** page de la Console d’administration pour identifier les utilisateurs en cours. Contactez-le et demandez-lui de fermer la session.  
  
-   Si nécessaire vous pouvez utiliser la **KILL** instruction pour forcer l’arrêt d’une connexion client. Soyez prudent lors de l’arrêt de connexions. Lorsque l’interruption survient, certains processus transactionnels, par exemple une mise à jour en cours d’exécution longue, doit activité de restauration SQL Server avant de procéder à la récupération de la base de données. Restauration d’une mise à jour partielle ou une suppression, peut prendre beaucoup de temps.  
  
### <a name="to-power-off-the-appliance"></a>Pour mettre hors tension de l’appareil  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre indiqué, et chaque étape doit terminer avant l’exécution de l’étape suivante, sauf indication contraire. Les étapes de manière désordonnée ou sans attendre de chaque étape peuvent générer des erreurs lors de l’application est sous tension à une date ultérieure.  
  
1.  Connectez-vous au nœud de contrôle de PDW (***PDW_region*-CTL01** ) et de la connexion avec le compte d’administrateur système de plateforme Analytique appliance domaine.  
  
2.  Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour ouvrir le **Configuration Manager**.  
  
3.  Dans le Gestionnaire de Configuration, sous la **parallèle topologie de l’entrepôt de données** menu, cliquez sur le **l’état des Services** onglet, puis cliquez sur **arrêter la région** pour arrêter les services PDW.  
  
4.  S’il existe une région HDInsight, sous le **HDInsight topologie** menu, cliquez sur le **l’état des Services** onglet, puis cliquez sur **arrêter la région** pour arrêter les services de HDInsight.  
  
5.  Se connecter à  ***appliance_domain*-HST01** et de la connexion avec le compte d’administrateur de domaine appliance.  
  
6.  À l’aide de la **Gestionnaire du Cluster de basculement** se connecter à la  ***appliance_domain*-WFOHST01** cluster si pas automatiquement connecté et, dans le volet de Navigation, cliquez sur **Rôles**. Dans le **rôles** volet :  
  
    1.  Multisélection des ordinateurs virtuels. Effectuez un clic droit, puis sélectionnez **arrêter**.  
  
    2.  Attendez que tous les ordinateurs virtuels sélectionnés à se fermer.  
  
7.  En l’absence d’une région HDInsight :  
  
    1.  Se connecter au cluster HDInsight. Pour ce faire, cliquez sur **Gestionnaire du Cluster de basculement**, sélectionnez **se connecter au Cluster**et spécifiez  ***appliance_domain*-WFOHST02** le nom de cluster.  
  
    2.  Sous le cluster HDInsight, cliquez sur **rôles**. Dans le **rôles** volet :  
  
        1.  Sélectionner plusieurs toutes les machines virtuelles, effectuez un clic droit, puis sélectionnez **arrêter**.  
  
        2.  Attendez que les ordinateurs virtuels pour l’arrêter.  
  
8.  Fermer le **Gestionnaire du Cluster de basculement** application.  
  
9. Arrêtez tous les serveurs à l’exception de  ***appliance_domain*-HST01**.  
  
10. Arrêter le  ***appliance_domain*-HST01** server.  
  
11. Arrêtez les unités de Distribution d’alimentation (PDU).  
  
## <a name="PowerOn"></a>Le dispositif de mise sous tension  
  
### <a name="to-power-on-the-appliance"></a>Pour mettre sous tension l’appareil  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre indiqué, et chaque étape doit terminer avant l’exécution de l’étape suivante, sauf indication contraire. Les étapes de manière désordonnée ou sans attendre de chaque étape peuvent entraîner des erreurs de démarrage.  
  
1.  Mise sous tension les unités d’alimentation (PDU) et attendez que les commutateurs pour démarrer automatiquement.  
  
2.  Mettez sous tension le  ***appliance_domain*-HST01** server.  
  
3.  Connectez-vous à  ***appliance_domain*-HST01** en tant que l’administrateur de domaine d’application.  
  
4.  Démarrer le **Gestionnaire Hyper-V** programme (**virtmgmt.msc**) et connectez-vous à  ***appliance_domain*-HST01** si ne pas connecté par défaut.  
  
    1.  Si vous ne peut pas se connecter par nom, car le  ***PDW_region*-AD01** est ne pas en cours d’exécution, essayez de vous connecter à l’aide de l’adresse IP.  
  
    2.  Dans le **virtuels** volet, recherchez  ***PDW_region*-AD01** et vérifiez qu’il s’exécute. Si ce n’est pas le cas, démarrer cet ordinateur virtuel et attendez qu’elle doit être entièrement démarré.  
  
5.  Mise sous tension le reste des serveurs dans l’appliance.  
  
6.  Sur **HST01** connecté comme administrateur de domaine d’application, à partir de **Gestionnaire Hyper-V**:  
  
    1.  Se connecter à  ***appliance_domain*-HST02**.  
  
    2.  Dans le **virtuels** volet, recherchez  ***PDW_region*-AD02** et vérifiez qu’il s’exécute.  Si ce n’est pas le cas, démarrer cet ordinateur virtuel et attendez qu’elle doit être entièrement démarré.  
  
7.  À l’aide de la **Gestionnaire du Cluster de basculement** se connecter à la  ***appliance_domain*-WFOHST01** de cluster, si pas automatiquement connecté, puis, dans le  **Navigation** volet, cliquez sur **rôles**. Dans le **rôles** volet :  
  
    1.  Sélectionner plusieurs toutes les machines virtuelles, effectuez un clic droit, puis cliquez sur **Démarrer**.  
  
    2.  Attendez que tous les ordinateurs virtuels sélectionnés démarrer avant de passer à l’étape suivante.  
  
    3.  Si nécessaire pour les machines virtuelles ayant basculé, les arrêter, déplacez-les et les redémarrer sur l’hôte principal approprié.  
  
8.  Si l’application a une région HDInsight, connectez-vous au cluster HDInsight. (Pour ce faire, cliquez sur **Gestionnaire du Cluster de basculement**, sélectionnez **se connecter au Cluster**et spécifiez  ***appliance_domain*-WFOHST01** le nom de cluster.)  
  
    1.  Sous le cluster HDInsight, cliquez sur **rôles**. Dans le **rôles** volet.  
  
        1.  Sélectionner plusieurs toutes les machines virtuelles, effectuez un clic droit, puis sélectionnez **Démarrer**,  
  
        2.  Attendez que tous les ordinateurs virtuels sélectionnés démarrer avant de passer à l’étape suivante.  
  
        3.  Si nécessaire pour les machines virtuelles ayant basculé, les arrêter, déplacez-les et les redémarrer sur l’hôte principal approprié.  
  
9. Déconnectez **HST01** si vous le souhaitez.  
  
10. Se connecter à  ***PDW_region*-CTL01** utilisant le compte d’administrateur de domaine appliance.  
  
11. Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour lancer le **Configuration Manager**.  
  
12. Dans le **Configuration Manager**, dans le **parallèle topologie de l’entrepôt de données** menu, cliquez sur le **l’état des Services** onglet, puis cliquez sur **démarrer région**pour démarrer les services PDW.  
  
13. Si l’application possède une région HDInsight, dans le menu de la topologie de HDInsight, cliquez sur le **l’état des Services** onglet, puis cliquez sur **démarrer la région** pour démarrer les services HDInsight.  
  
### <a name="to-verify-the-appliance-health"></a>Pour vérifier l’intégrité de l’équipement  
Une fois l’application a démarré, ouvrez le **Console d’administration** et vérifiez la page de contrôle d’intégrité pour les alertes susceptibles d’indiquer les conditions d’échec. Pour plus d’informations, consultez [contrôler le matériel à l’aide de la Console d’administration &#40; Système de plateforme Analytique &#41; ](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion d’application &#40; Système de plateforme Analytique &#41;](appliance-management-tasks.md)  
  
