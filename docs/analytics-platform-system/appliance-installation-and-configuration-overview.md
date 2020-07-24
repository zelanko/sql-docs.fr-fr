---
title: Installation et configuration de l’appliance
description: Guide les administrateurs d’appliances Analytics Platform System (APS) tout au long des premières étapes de configuration et de prise en main de votre nouvel appareil.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 49ed0f26f20d081f4f9b307e6be90a3f5bd8c372
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86942201"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Installation et configuration de l’appliance pour Analytics Platform System
Guide les administrateurs d’appliances Analytics Platform System (APS) tout au long des premières étapes de configuration et de prise en main de votre nouvel appareil.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="1-install-the-hardware"></a><a name="InstallHardware"></a>1. installer le matériel  
Votre nouvelle appliance sera livrée sur des palettes à la station d’accueil de votre centre de données.  
  
> [!IMPORTANT]  
> Dans certains cas, votre IHV décompressera, montera en rack et connectera l’appliance pour vous dans votre centre de données. Dans ce cas, ces instructions ne sont pas nécessaires et vous pouvez passer à la [troisième. Configurez la section Appliance](#ConfigureAppliance) ci-dessous.  
  
Si votre IHV n’effectue pas l’installation matérielle, procédez comme suit pour installer le matériel.  
  
|Tâche|Description|  
|-|-|  
|Confirmer la documentation|Confirmez que vous avez reçu tous les documents et informations nécessaires de la part de votre fournisseur de matériel indépendant (IHV). Consultez [les informations à obtenir auprès de votre fabricant de matériel &#40;Analytics Platform System&#41;](information-to-obtain-from-your-ihv.md).|  
|Installer le matériel|Vérifiez que le centre de données peut prendre en charge l’appliance. Déplacez les composants de l’appliance vers le centre de données. Monter en rack les commutateurs, les PDU et le câblage réseau. Consultez [installation matérielle &#40;Analytics Platform System&#41;](hardware-installation.md).|  
  
## <a name="2-power-on-the-appliance"></a><a name="PowerOnAppliance"></a>2. mise sous tension de l’appareil  
  
|Tâche|Description|  
|-|-|  
|Mise sous tension de l’appareil|Mettez sous tension chaque nœud de composant d’appliance dans l’ordre requis, en attendant le cas échéant pour confirmer qu’aucune erreur n’a été rencontrée.|  
  
## <a name="3-configure-the-appliance"></a><a name="ConfigureAppliance"></a>3. configurer l’appliance  
  
|Tâche|Description|  
|-|-|  
|Configurez l’appliance à l’aide de l’SQL Server PDW**Configuration Manager**|Utilisez la Configuration Manager pour définir les mots de passe d’appliance, les fuseaux horaires, les paramètres réseau et de pare-feu, les certificats de sécurité et les performances, ainsi que d’autres paramètres de votre appliance. Consultez [configuration de l’Appliance &#40;Analytics Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Les modifications de configuration doivent être effectuées uniquement à l’aide de la**Configuration Manager**SQL Server PDW. Les modifications non exposées par le biais de **Configuration Manager** ne sont pas prises en charge. Par exemple, l’appliance SQL Server PDW prend uniquement en charge le paramètre de langue Anglais (États-Unis).  
  
## <a name="4-set-up-software-servicing"></a><a name="SoftwareServicing"></a>4. configurer la maintenance des logiciels  
  
|Tâche|Description|  
|-|-|  
|Appliquer les mises à jour de SQL Server PDW|Facultatif Vous devrez peut-être appliquer une ou plusieurs mises à jour SQL Server PDW pour mettre à jour votre logiciel SQL Server PDW avec la dernière version. Consultez [appliquer des correctifs de système de plateforme analytics &#40;Analytics Platform system&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Configurer Windows Server Update Services|Configurez l’appliance pour recevoir des mises à jour de Windows Server Update Services pour les logiciels de prise en charge. Consultez [Télécharger et appliquer des mises à jour Microsoft &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="next-steps"></a><a name="NextSteps"></a>Étapes suivantes  
Une fois que vous avez effectué toutes les étapes précédentes, votre appliance est prête à être utilisée. Vous ou d’autres personnes à votre emplacement pouvez effectuer les tâches suivantes.  
  
|Tâche|Description|  
|-|-|  
|Installer des pilotes SQL Server PDW et configurer la connectivité|Configurez les ordinateurs locaux pour qu’ils se connectent à SQL Server PDW à l’aide de SQL Server Data Tools, sqlcmd, du logiciel Business Intelligence ou d’autres outils. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Créer des ouvertures de session et des rôles de serveur, et affecter des autorisations|Planifiez et créez des ouvertures de session et des rôles de serveur qui permettront aux utilisateurs de se connecter à SQL Server PDW avec les autorisations appropriées. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Configurer la passerelle Azure Gestion des données|La passerelle permet aux utilisateurs Azure d’accéder aux données APS locales en exposant les données APS en tant que flux OData sécurisés. La passerelle est déjà installée sur le nœud de contrôle. Demandez de l’aide à Microsoft sur la configuration.|  
|Surveiller les requêtes et les utilisateurs d’appliance|Utilisez la console d’administration et d’autres ressources pour surveiller les requêtes et les utilisateurs de l’appliance. Consultez [surveiller l’appliance à l’aide de la console d’administration &#40;Analytics Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Charger les données dans SQL Server PDW|Chargez des données sur votre appliance. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Créer un plan de récupération d’urgence|Planifiez la manière dont vous allez protéger vos données contre les défaillances matérielles ou les remplacements de données. Créez un plan à l’aide de sauvegardes régulières et de plans de restauration en cas de corruption ou de perte de données. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Surveiller l’appliance|Surveiller l’État, l’intégrité et les performances de l’appliance à l’aide des vues système, des journaux et de la console d’administration. Corrigez ou signalez les problèmes éventuels. Consultez [surveiller l’état d’intégrité de l’Appliance &#40;Analytics Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
