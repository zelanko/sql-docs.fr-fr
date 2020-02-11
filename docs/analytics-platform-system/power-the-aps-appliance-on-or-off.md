---
title: Mettez l’appliance sous tension ou hors tension.
description: Mettre l’appliance sous tension ou hors tension pour Analytics Platform System
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee70338b5a46ec60d808e489d982fd80692c5d1d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400621"
---
# <a name="power-the-appliance-on-or-off-for-analytics-platform-system"></a>Mettre l’appliance sous tension ou hors tension pour Analytics Platform System
Cette rubrique explique comment mettre sous tension ou mettre hors tension votre plateforme d’analyse Systemappliance qui exécute des Data Warehouse parallèles. Utilisez cette rubrique lorsqu’une appliance d’analyse de système de plateforme est déplacée, ou pour mettre sous tension un appareil après une panne de courant catastrophique.  
  
La mise sous tension et la désactivation de l’appliance ne sont pas les mêmes que le démarrage et l’arrêt des services de l’appliance. Pour plus d’informations sur ce sujet, consultez l' [État des services PDW &#40;Analytics Platform System&#41;](pdw-services-status.md). Pour plus d’informations sur la mise sous tension ou la désactivation d’une Data Warehouse parallèle SQL Server 2008, consultez le fichier d’aide SQL Server de Data Warehouse parallèles 2008. Pour plus d’informations sur la mise sous tension ou la désactivation d’un SQL Server 2012 AU1 ou d’un Data Warehouse parallèle AU2, consultez le fichier d’aide de ces versions.  
  
Lorsque ces instructions spécifient la connexion à un nœud de SQL Server PDW, la connexion peut être locale à l’aide d’appareils connectés (KVM) ou à distance à l’aide de Bureau à distance. Certaines actions doivent être physiques (activation d’un commutateur d’alimentation), tandis que d’autres peuvent être physiques ou utiliser des commandes Windows.  
  
Vous pouvez établir des connexions à des nœuds de SQL Server PDW à l’aide des adresses IP attribuées aux nœuds, ou à partir de l’ordinateur **HST01** à l’aide des applications **Gestionnaire du cluster de basculement** (**Cluadmin. msc**) ou du **Gestionnaire Hyper-V** (**virtmgmt. msc**) et en cliquant avec le bouton droit sur le nom du nœud.  
  
## <a name="PowerOff"></a>Mettre l’appareil hors tension  
  
### <a name="before-you-begin"></a>Avant de commencer  
Avant de mettre l’appareil hors tension, vous devez mettre fin à toutes les activités de l’appliance. Pour mettre fin à toutes les activités :  
  
-   Utilisez la page **sessions** de la console d’administration pour identifier les utilisateurs actuels. Contactez-le et demandez-lui de se déconnecter.  
  
-   Si nécessaire, vous pouvez utiliser l’instruction **Kill** pour forcer l’arrêt d’une connexion cliente. Soyez prudent lors de la suppression des connexions. Lorsqu’il est interrompu, certains processus transactionnels, comme une mise à jour à long terme, doivent restaurer l’activité avant que SQL Server puisse terminer la récupération de la base de données. La restauration d’une mise à jour ou d’une suppression partiellement terminée peut prendre du temps.  
  
### <a name="to-power-off-the-appliance"></a>Pour mettre l’appareil hors tension  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre exact indiqué et chaque étape doit se terminer avant l’exécution de l’étape suivante, sauf indication contraire. L’exécution des étapes dans le désordre ou sans attendre la fin de chaque étape peut entraîner des erreurs lorsque l’appliance est mise sous tension ultérieurement.  
  
1.  Connectez-vous au nœud de contrôle PDW (**_PDW_region_-CTL01** ) et connectez-vous avec le compte d’administrateur de domaine de l’appliance Analytics Platform System.  
  
2.  Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour ouvrir le **Configuration Manager**.  
  
3.  Dans le Configuration Manager, dans le menu **topologie des Data Warehouse parallèles** , cliquez sur l’onglet **État des services** , puis sur arrêter la **région** pour arrêter les services PDW.   
  
4.  Connectez-vous à ** _appliance_domain_-HST01** et connectez-vous avec le compte d’administrateur de domaine de l’appliance.  
  
5.  À l’aide de l' **Gestionnaire du cluster de basculement** Connectez-vous au cluster ** _appliance_domain_-WFOHST01** , s’il n’est pas automatiquement connecté, puis, dans le volet de navigation, cliquez sur **rôles**. Dans le volet **rôles** :  
  
    1.  Sélectionnez plusieurs machines virtuelles. Cliquez dessus avec le bouton droit, puis sélectionnez **arrêter**.  
  
    2.  Attendez la fin de l’arrêt de toutes les machines virtuelles sélectionnées.  
  
6.  Fermez l’application **Gestionnaire du cluster de basculement** .  
  
7. Arrêtez tous les serveurs à l’exception **de _appliance_domain_-HST01**.  
  
8. Arrêtez le serveur ** _appliance_domain_-HST01** .  
  
9. Arrêtez les unités de distribution de l’alimentation (PDU).  
  
## <a name="PowerOn"></a>Mise sous tension de l’appareil  
  
### <a name="to-power-on-the-appliance"></a>Pour mettre l’appareil sous tension  
  
> [!WARNING]  
> Toutes les étapes doivent être effectuées dans l’ordre exact indiqué et chaque étape doit se terminer avant l’exécution de l’étape suivante, sauf indication contraire. L’exécution des étapes dans le désordre ou sans attendre la fin de chaque étape peut entraîner des erreurs de démarrage.  
  
1.  Mettez sous tension les unités de distribution de l’alimentation (PDU) et attendez que les commutateurs démarrent automatiquement.  
  
2.  Mettez sous tension le serveur ** _appliance_domain_-HST01** .  
  
3.  Connectez-vous à ** _appliance_domain_-HST01** en tant qu’administrateur de domaine de l’appliance.  
  
4.  Démarrez le programme du **Gestionnaire Hyper-V** (**virtmgmt. msc**) et connectez-vous à ** _appliance_domain_-HST01** si vous n’êtes pas connecté par défaut.  
  
    1.  Si vous ne pouvez pas vous connecter par nom, car le ** _PDW_region_-ad01** n’est pas en cours d’exécution, essayez de vous connecter à l’aide de l’adresse IP.  
  
    2.  Dans le volet **machines virtuelles** , recherchez ** _PDW_region_-ad01** et confirmez qu’il est en cours d’exécution. Si ce n’est pas le cas, démarrez cette machine virtuelle et attendez le démarrage complet de celle-ci.  
  
5.  Mettez sous tension les autres serveurs de l’appliance.  
  
6.  Quand vous êtes connecté à **HST01** en tant qu’administrateur de domaine de l’appliance, à partir du **Gestionnaire Hyper-V**:  
  
    1.  Connectez-vous à ** _appliance_domain_-HST02**.  
  
    2.  Dans le volet **machines virtuelles** , recherchez ** _PDW_region_-AD02** et confirmez qu’il est en cours d’exécution.  Si ce n’est pas le cas, démarrez cette machine virtuelle et attendez le démarrage complet de celle-ci.  
  
7.  À l’aide de l' **Gestionnaire du cluster de basculement** Connectez-vous au cluster ** _appliance_domain_-WFOHST01** , s’il n’est pas automatiquement connecté, puis, dans le volet de **navigation** , cliquez sur **rôles**. Dans le volet **rôles** :  
  
    1.  Sélectionnez plusieurs machines virtuelles, cliquez dessus avec le bouton droit, puis cliquez sur **Démarrer**.  
  
    2.  Attendez la fin de l’exécution de toutes les machines virtuelles sélectionnées avant de passer à l’étape suivante.  
  
    3.  Si nécessaire pour les machines virtuelles qui ont basculé, arrêtez-les, déplacez-les, puis redémarrez-les sur l’hôte principal approprié.  
  
8. Déconnectez-vous de **HST01** si vous le souhaitez.  
  
9. Connectez-vous à ** _PDW_region_-CTL01** à l’aide du compte d’administrateur de domaine de l’appliance.  
  
10. Exécutez `C:\Program Files\Microsoft SQL Server Parallel Data Warehouse\100\dwconfig.exe` pour lancer la **Configuration Manager**.  
  
11. Dans le **Configuration Manager**, dans le menu **topologie des Data Warehouse parallèles** , cliquez sur l’onglet **État des services** , puis cliquez sur Démarrer la **région** pour démarrer les services PDW.  
  
### <a name="to-verify-the-appliance-health"></a>Pour vérifier l’intégrité de l’appliance  
Une fois l’appliance démarrée, ouvrez la **console d’administration** et recherchez dans la page intégrité les alertes qui peuvent indiquer des conditions d’échec. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md).  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion d’appliance &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
