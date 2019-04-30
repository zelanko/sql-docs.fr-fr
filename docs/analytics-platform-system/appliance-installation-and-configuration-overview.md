---
title: Appliance installer et configurer - Analytique Platform System | Microsoft Docs
description: Guide des administrateurs d’appliance Analytique Platform System (APS) via les premières étapes pour configurer et commencer à utiliser votre nouveau matériel.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5b6aa75cdab85fce9ef308d3e853ddb0107c28ee
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63276352"
---
# <a name="appliance-installation-and-configuration-for-analytics-platform-system"></a>Installation de l’appliance et de configuration pour l’Analytique Platform System
Guide des administrateurs d’appliance Analytique Platform System (APS) via les premières étapes pour configurer et commencer à utiliser votre nouveau matériel.  
  
<!-- MISSING LINKS ## <a name="BeforeYouBegin"></a>Before You Begin  
Before you begin to install, configure, and use your new appliance, we recommend reviewing information about the appliance components. Review the following to familiarize yourself with the appliance:  
  
-   Review [Understanding the Appliance Nodes and Hardware (SQL Server PDW)](assetId:///f60f419f-d1e1-403d-8cf9-07e7ef6d6627) to be sure you understand the components included in your new appliance.  
  
-   Review [Connecting to SQL Server PDW (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808) to understand how and when appliance administrators will connect to each appliance node.  
-->

## <a name="InstallHardware"></a>1. Installer le matériel  
Votre nouveau dispositif sera remis sur palettes à l’ancrage dans votre centre de données.  
  
> [!IMPORTANT]  
> Dans certains cas, votre fabricant de matériel déballer, monter en rack et connecter l’application pour vous dans votre centre de données. Si par conséquent, ces instructions ne sont pas nécessaires et vous pouvez passer à la [3. Configurer l’Appliance](#ConfigureAppliance) section ci-dessous.  
  
Si votre fabricant de matériel n’effectue pas l’installation de matériel, procédez comme suit pour installer le matériel.  
  
|||  
|-|-|  
|**Tâche**|**Description**|  
|Vérifiez la documentation|Vérifiez que vous avez reçu tous les documents nécessaires et les informations de votre fournisseur de matériel indépendants (IHV). Consultez [informations à obtenir à partir de votre fabricant de matériel &#40;Analytique Platform System&#41;](information-to-obtain-from-your-ihv.md).|  
|Installer le matériel|Vérifiez que le centre de données peut prendre en charge de l’appliance. Déplacer les composants de l’appliance vers le centre de données. Les commutateurs réseau, PDU, de monter en rack et le câblage. Consultez [Installation matérielle &#40;Analytique Platform System&#41;](hardware-installation.md).|  
  
## <a name="PowerOnAppliance"></a>2. L’Appliance de mise sous tension  
  
|||  
|-|-|  
|**Tâche**|**Description**|  
|L’appliance de mise sous tension|Alimentation sur chaque nœud de composant matériel dans l’ordre requis, en attente en fonction des besoins pour confirmer qu’aucune erreur est rencontrée.|  
  
## <a name="ConfigureAppliance"></a>3. Configurer l’Appliance  
  
|||  
|-|-|  
|**Tâche**|**Description**|  
|||  
|Configurer l’appliance à l’aide de l’ordinateur SQL Server PDW**Configuration Manager**|Utilisez le Gestionnaire de Configuration pour définir les mots de passe appliance, fuseaux horaires, paramètres de pare-feu et de réseau, des certificats de sécurité et de performances et d’autres paramètres sur votre appliance. Consultez [Configuration de l’Appliance &#40;Analytique Platform System&#41;](appliance-configuration.md).|  
  
> [!WARNING]  
> Modifications de configuration doivent uniquement être effectuées à l’aide de l’ordinateur SQL Server PDW**Configuration Manager**. Modifications non exposées via **Configuration Manager** ne sont pas pris en charge. Par exemple, l’appliance SQL Server PDW ne prend en charge le paramètre de langue anglais des États-Unis.  
  
## <a name="SoftwareServicing"></a>4. Configurer la maintenance logicielle  
  
|||  
|-|-|  
|**Tâche**|**Description**|  
|Appliquer des mises à jour de SQL Server PDW|(Facultatif) Vous devrez peut-être appliquer une ou plusieurs mises à jour de SQL Server PDW pour mettre à jour de votre logiciel de SQL Server PDW vers la dernière version. Consultez [appliquer des correctifs de système de plateforme Analytique &#40;Analytique Platform System&#41;](apply-analytics-platform-system-hotfixes.md).|  
|Configurer Windows Server Update Services|Configurer l’appliance pour recevoir des mises à jour de Windows Server Update Services pour prendre en charge des logiciels. Consultez [Téléchargez et appliquez les mises à jour Microsoft &#40;Analytique Platform System&#41;](download-and-apply-microsoft-updates.md).|  
  
## <a name="NextSteps"></a>Étapes suivantes  
Une fois que vous avez terminé toutes les étapes précédentes, votre application est prête à être utilisée. Vous ou autres membres du personnel à votre emplacement peut effectuer les tâches suivantes.  
  
|||  
|-|-|  
|**Tâche**|**Description**|  
|Installer des pilotes de SQL Server PDW et configurez la connectivité|Configurer des ordinateurs locaux pour vous connecter à SQL Server PDW à l’aide de SQL Server Data Tools, sqlcmd, informatique décisionnelle ou autres outils. <!-- MISSING LINKS See [Client Tools (SQL Server PDW)](assetId:///721851d5-e521-4d5b-ba6d-8e2e9d3c7808).-->|  
|Créer des rôles serveur et les ouvertures de session et affecter des autorisations|Planifier et créer des rôles d’ouvertures de session et le serveur qui permettra aux utilisateurs de se connecter à SQL Server PDW avec les autorisations appropriées. <!-- MISSING LINKS See [PDW Permissions &#40;SQL Server PDW&#41;](../sqlpdw/pdw-permissions-sql-server-pdw.md).-->|  
|Configurer la passerelle de gestion de données Azure|La passerelle permet aux utilisateurs d’accéder aux données des points d’accès local en exposant les données de points d’accès comme sécuriser les flux OData Azure. La passerelle est déjà installée sur le nœud de contrôle. Demandez à Microsoft pour obtenir une assistance avec la configuration.|  
|Requêtes d’analyse et aux utilisateurs des appliances|Utilisez la Console d’administration et d’autres ressources pour surveiller les requêtes et les utilisateurs de l’appliance. Consultez [surveiller l’Appliance à l’aide de la Console d’administration &#40;Analytique Platform System&#41;](monitor-the-appliance-by-using-the-admin-console.md)<!-- MISSING LINKS and [User Sessions &#40;SQL Server PDW&#41;](../sqlpdw/user-sessions-sql-server-pdw.md)-->.|  
|Charger des données dans SQL Server PDW|Charger des données à votre appliance. <!-- MISSING LINKS See [Load &#40;SQL Server PDW&#41;](../sqlpdw/load-sql-server-pdw.md).-->|  
|Créer un plan de récupération d’urgence|Planifier la façon dont vous voulez protéger vos données des défaillances matérielles ou remplacent des données. Créer un plan à l’aide de sauvegardes régulières et de restauration des plans en cas de corruption des données ou de perte. <!-- MISSING LINKS See [Create a Disaster Recovery Plan &#40;SQL Server PDW&#41;](../sqlpdw/create-a-disaster-recovery-plan-sql-server-pdw.md).-->|  
|Surveiller l’appliance|Surveiller l’état de l’appliance, d’intégrité et les performances à l’aide de la Console d’administration, les journaux et les vues système. Corrigez ou signaler des problèmes. Consultez [état de contrôle d’intégrité de l’analyse &#40;Analytique Platform System&#41;](../relational-databases/system-dynamic-management-views/sys-dm-pdw-component-health-status-transact-sql.md).|  
