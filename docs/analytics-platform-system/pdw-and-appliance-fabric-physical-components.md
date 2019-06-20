---
title: Composants physiques du matériel - Analytique Platform System | Microsoft Docs
description: Noms et descriptions pour les composants physiques de fabric PDW et une appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 0adbd92d1a29a98a80de65268c53ea63e3941d07
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639918"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Composants physiques du matériel - Analytique Platform System
Noms et descriptions pour les composants physiques de fabric PDW et une appliance. 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>Diagrammes de composants  
Cela affiche les noms des composants physiques et où ils se trouvent dans le rack premier d’une appliance de nœud de calcul-6.  
  
![Noms de composant de région PDW - HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames-HP")  
  
Le nom réel pour les composants PDW est le nom de région PDW, suivi par un tiret, suivi par le nom du composant. Par exemple, si le nom de région PDW est PDW123, les noms réels sont **PDW123-CTL01**, **PDW123-CMP01**, etc.  
  
De même, le nom réel pour les composants d’infrastructure appliance est le domaine de l’appliance, suivi d’un tiret, suivi par le nom du composant. Par exemple, si le domaine de l’appliance est FSW123, l’infrastructure de l’appliance les machines virtuelles sont **FSW123-WDS**, **FSW123-AD01**, **FSW123-VMM**, etc.  
  
Voici une vue consolidée d’une région PDW avec 6 nœuds de calcul.  
  
![Noms des composants PDW](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>Composants PDW  
Les machines virtuelles PDW font partie de la région PDW.  
  
*PDW_region*-CTL01  
Une machine virtuelle qui exécute le nœud de contrôle. Cela s’exécute sur HST01 et peut basculer vers HST02.  
  
> [!WARNING]  
> SQL Server PDW ne prend pas en charge la création d’un instantané de la machine virtuelle de CTL01 à l’aide du Gestionnaire Hyper-V. Instantanés s’appuient sur un stockage local, ce qui provoquera des erreurs si la machine virtuelle tente de basculer vers sa sauvegarde. Création d’un instantané peut également entraîner des problèmes de fiabilité avec d’autres de la machine virtuelle que le basculement vers le serveur passif.  
  
*PDW_region*-CMP01 via *PDW_Region*-CMP06  
Une machine virtuelle qui exécute le nœud de calcul. Dans ce diagramme de nœud de calcul-6, les hôtes HSA01 via HSA06 exécuter nœud de calcul CMP01 de machines virtuelles via CMP06 respectivement.  
  
## <a name="fabric"></a>Composants d’infrastructure appliance  
Ces composants font partie de l’infrastructure de l’appliance.  
  
### <a name="virtual-machines"></a>Machines virtuelles  
*appliance_domain*-WDS  
Cette hôtes d’ordinateurs virtuels Windows Services de déploiement (WDS), qui utilise le système de plateforme d’Analytique déploiement les systèmes d’exploitation Windows sur le réseau de l’appliance. Il héberge également le service DHCP, ce qui permet les hôtes de l’appliance joindre le réseau de l’appliance sans avoir une adresse IP préconfigurée.  
  
Le *appliance_domain*- WDS virtual machine s’exécute sur HST01 et peut basculer vers HST02. La machine virtuelle WDS et l’ordinateur virtuel VMM, vous pouvez déployer Windows sur les hôtes physiques lors de l’installation de l’appliance. Pendant le cycle de vie du matériel, WDS et VMM effectuent des opérations telles que le remplacement d’un ordinateur hôte.  
  
*appliance_domain*-VMM  
Virtual Machine Manager (VMM) s’exécute sur une machine virtuelle et peut basculer vers HST02. VMM héberge System Center pour déployer le système d’exploitation sur les hôtes physiques. VMM fournit également Windows Server Update Services (WSUS) pour appliquer ou supprimer des mises à jour de Windows sur l’ensemble des hôtes et des machines virtuelles.  
  
*appliance_domain*-AD01, *appliance_domain*-AD02  
Active Directory Domain Services, qui contient le système DNS (Domain Name), s’exécute sur une machine virtuelle sur HST01 et HST02. Pour la haute disponibilité de l’appliance, AD01 et AD02 sont des contrôleurs de domaine répliqué, et ils ne basculent pas. Si un échoue, l’autre est déjà disponible avec les données correctes.  
  
*appliance_domain*-ISCSI01  
Une des machines virtuelles ISCSI s’exécute sur chacun des hôtes avec stockage attaché (HSA01 HSA06). Cette machine virtuelle ne bascule.  
  
### <a name="hosts"></a>Hôtes  
*appliance_domain*-HST01 via *appliance_domain*-HST06  
Les hôtes pour les machines de virtuelles de fabric nœud et une appliance PDW contrôle. HST03 est un hôte passif facultatif.  
  
*appliance_domain*-HSA01 via *appliance_domain*-HSA08  
Les hôtes avec stockage attaché (HSA). Chaque nœud de calcul une machine virtuelle HAS hôte s’exécute et l’autre ISCSI VM.  
  
### <a name="cluster-for-pdw"></a>Cluster pour PDW  
*appliance_domain*-WFOHST01  
Le cluster PDW est nommé WFOHST01. Il gère tous les hôtes physiques et machines virtuelles qui appartiennent à PDW.  
  
### <a name="direct-attached-storage"></a>Stockage en attachement direct  
*appliance_domain*-DAS01 via *appliance_domain*-DAS03  
Il s’agit du stockage en attachement direct qui est connecté aux nœuds de calcul. HP a un DAS toutes deux nœuds de calcul. Dell et Quanta ont un DAS toutes trois nœuds de calcul.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[Configuration de l’appliance &#40;Analytique Platform System&#41;](appliance-configuration.md)  
[Tâches de gestion appliance &#40;Analytique Platform System&#41;](appliance-management-tasks.md)  
  
