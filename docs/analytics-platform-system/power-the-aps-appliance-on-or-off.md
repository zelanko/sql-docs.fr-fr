---
title: L’alimentation de l’appliance ou désactiver - Analytique Platform System | Microsoft Docs
description: L’appliance ou désactiver l’alimentation pour l’Analytique Platform System
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 994b0f94448b7fb7901734b2ae737e26be23900f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62678627"
---
# <a name="power-the-appliance-on-or-off-for-analytics-platform-system"></a>L’appliance ou désactiver l’alimentation pour l’Analytique Platform System
Cette rubrique décrit comment à puissance ou de mise hors tension de votre Systemappliance de plateforme d’Analytique qui est en cours d’exécution Parallel Data Warehouse. Utilisez cette rubrique lorsqu’une appliance Analytique Platform System est déplacée, ou à puissance sur une appliance après une panne catastrophique.  
  
Mise sous tension de l’appliance et désactiver n’est pas identique à démarrage et arrêt des services de l’appliance. Pour plus d’informations sur ce sujet, consultez [l’état des Services PDW &#40;Analytique Platform System&#41;](pdw-services-status.md). Pour plus d’informations sur la mise sous tension ou désactiver un SQL Server 2008 Parallel Data Warehouse, consultez le fichier d’aide de SQL Server 2008 Parallel Data Warehouse. Pour plus d’informations sur la mise sous tension ou désactiver un SQL Server 2012 AU1 ou le AU2 Parallel Data Warehouse, consultez le fichier d’aide pour ces versions.  
  
Lorsque ces instructions spécifient la connexion à un nœud SQL Server PDW, la connexion peut être locale à l’aide de périphériques connectés (KVM) ou à distance à l’aide du Bureau à distance. Certaines actions doivent être physique (activation sur un commutateur d’alimentation) et autres (par exemple, d’arrêt) peuvent être physiques ou des commandes à l’aide de Windows.  
  
Connexions aux nœuds de SQL Server PDW peuvent être établies en utilisant les adresses IP attribuées aux nœuds, ou à partir de la **HST01** ordinateur en utilisant le **Gestionnaire du Cluster de basculement** (**cluadmin.msc**) ou **Gestionnaire Hyper-V** (**virtmgmt.msc**) des applications et cliquant sur le nom de nœud.  
  
## <a name="PowerOff"></a>Mise hors tension de l’Appliance  
  
### <a name="before-you-begin"></a>Avant de commencer  
Avant la mise hors tension de l’appliance, vous devez terminer la toutes les activités sur l’appliance. Pour terminer toutes les activités :  
  
-   Utilisez le **Sessions** page de la Console d’administration pour identifier les utilisateurs actuels. Contactez-le et demandez-lui de fermer la session.  
  
-   Si nécessaire vous pouvez utiliser la **KILL** instruction pour forcer l’arrêt d’une connexion client. Soyez prudent lors de l’arrêt de connexions. Lors de l’interruption, certains processus transactionnelles, par exemple une mise à jour en cours d’exécution longue, doit activité de restauration SQL Server avant de procéder à la récupération de la base de données. Restauration d’une mise à jour partiellement terminé ou une suppression, peut prendre du temps.  
  
### <a name="to-power-off-the-appliance"></a>Pour mettre hors tension de l’appliance  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre indiqué et chaque étape doit terminer avant l’exécution de l’étape suivante, sauf indication contraire. Les étapes en désordre ou sans attendre que chaque étape pour terminer peuvent engendrer des erreurs lors de l’appliance est sous tension à une date ultérieure.  
  
1.  Se connecter au nœud de contrôle de PDW ( **_PDW_region_-CTL01** ) et connectez-vous avec le compte administrateur de domaine Analytique Platform System appliance.  
  
2.  Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour ouvrir le **Configuration Manager**.  
  
3.  Dans le Gestionnaire de Configuration, sous le **topologie de l’entrepôt de données parallèle** menu, cliquez sur le **l’état des Services** onglet, puis cliquez sur **région arrêter** pour arrêter les services PDW.   
  
4.  Se connecter à  **_appliance_domain_-HST01** et connectez-vous avec le compte d’administrateur de domaine appliance.  
  
5.  À l’aide de la **Gestionnaire du Cluster de basculement** se connecter à la  **_appliance_domain_-WFOHST01** de cluster, si pas automatiquement connecté et, dans le volet de Navigation, cliquez sur **Rôles**. Dans le **rôles** volet :  
  
    1.  Multisélection des machines virtuelles. Effectuez un clic droit, puis sélectionnez **arrêter**.  
  
    2.  Attendez que toutes les machines virtuelles sélectionnées se termine en cours d’arrêt.  
  
6.  Fermer le **Gestionnaire du Cluster de basculement** application.  
  
7. Arrêtez tous les serveurs à l’exception  **_appliance_domain_-HST01**.  
  
8. Arrêter le  **_appliance_domain_-HST01** server.  
  
9. Arrêtez les unités de Distribution d’alimentation (PDU).  
  
## <a name="PowerOn"></a>L’Appliance de mise sous tension  
  
### <a name="to-power-on-the-appliance"></a>Pour l’appliance de mise sous tension  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre indiqué et chaque étape doit terminer avant l’exécution de l’étape suivante, sauf indication contraire. Les étapes en désordre ou sans attendre que chaque étape pour terminer peuvent engendrer des erreurs de démarrage.  
  
1.  Mise sous tension les unités de Distribution d’alimentation (PDU) et attendez que les commutateurs pour démarrer automatiquement.  
  
2.  Mettre sous tension le  **_appliance_domain_-HST01** server.  
  
3.  Connectez-vous à  **_appliance_domain_-HST01** en tant que l’administrateur de domaine d’application.  
  
4.  Démarrer le **Gestionnaire Hyper-V** programme (**virtmgmt.msc**) et connectez-vous à  **_appliance_domain_-HST01** si ne pas connecté par défaut.  
  
    1.  Si vous ne pouvez pas vous connecter par nom, car le  **_PDW_region_-AD01** est ne pas en cours d’exécution, essayez de vous connecter à l’aide de l’adresse IP.  
  
    2.  Dans le **Machines virtuelles** volet, recherchez  **_PDW_region_-AD01** et confirmez qu’il s’exécute. Si ce n’est pas le cas, démarrez cette machine virtuelle et attendez qu’elle doit être entièrement démarré.  
  
5.  Mise sous tension le reste des serveurs dans l’appliance.  
  
6.  Tout en sur **HST01** connecté comme administrateur de domaine d’application, à partir de **Gestionnaire Hyper-V**:  
  
    1.  Se connecter à  **_appliance_domain_-HST02**.  
  
    2.  Dans le **Machines virtuelles** volet, recherchez  **_PDW_region_-AD02** et confirmez qu’il s’exécute.  Si ce n’est pas le cas, démarrez cette machine virtuelle et attendez qu’elle doit être entièrement démarré.  
  
7.  À l’aide de la **Gestionnaire du Cluster de basculement** se connecter à la  **_appliance_domain_-WFOHST01** de cluster, si pas automatiquement connecté, puis, dans le  **Navigation** volet, cliquez sur **rôles**. Dans le **rôles** volet :  
  
    1.  Multisélection de tous les ordinateurs virtuels, effectuez un clic droit, puis cliquez sur **Démarrer**.  
  
    2.  Attendez que toutes les machines virtuelles sélectionnées démarrer avant de passer à l’étape suivante.  
  
    3.  Si nécessaire pour les machines virtuelles ayant basculé, les arrêter, déplacez-les et redémarrez-les sur l’hôte principal approprié.  
  
8. Déconnectez **HST01** si vous le souhaitez.  
  
9. Se connecter à  **_PDW_region_-CTL01** utilisant le compte d’administrateur de domaine appliance.  
  
10. Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour lancer le **Configuration Manager**.  
  
11. Dans le **Configuration Manager**, dans le **topologie de l’entrepôt de données parallèle** menu, cliquez sur le **l’état des Services** onglet, puis cliquez sur **démarrer région**pour démarrer les services PDW.  
  
### <a name="to-verify-the-appliance-health"></a>Pour vérifier l’intégrité de l’appliance  
Une fois que l’appliance a démarré, ouvrez le **Console d’administration** et vérifiez la page de contrôle d’intégrité pour les alertes qui peuvent indiquer les conditions d’échec. Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion appliance &#40;Analytique Platform System&#41;](appliance-management-tasks.md)  
  
