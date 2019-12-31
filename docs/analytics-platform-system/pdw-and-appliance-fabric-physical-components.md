---
title: Composants physiques de l’appliance
description: Noms et descriptions des composants physiques PDW et appliance fabric.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 5cbed66f53189668518e04848002ae69adb8c614
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74400919"
---
# <a name="appliance-physical-components---analytics-platform-system"></a>Composants physiques d’appliance-système de plateforme d’analyse
Noms et descriptions des composants physiques PDW et appliance fabric. 
  
<!-- MISSING LINKS See also [HDInsight Physical Components &#40;Analytics Platform System&#41;](hdinsight-physical-components.md).  -->  
  
## <a name="diagrams"></a>Diagrammes de composants  
Cela indique les noms des composants physiques et leur emplacement dans le premier rack d’une appliance à 6 nœuds de calcul.  
  
![Noms des composants de région PDW - HP](./media/pdw-and-appliance-fabric-physical-components/APS_HW_ComponentNames-HP.png "APS_HW_ComponentNames-HP")  
  
Le nom réel des composants PDW est le nom de la région PDW, suivi d’un tiret, suivi du nom du composant. Par exemple, si le nom de la région PDW est PDW123, les noms réels sont **PDW123-CTL01**, **PDW123-CMP01**, etc.  
  
De même, le nom réel des composants de l’infrastructure d’appliances correspond au domaine de l’appliance, suivi d’un tiret, suivi du nom du composant. Par exemple, si le domaine de l’appliance est FSW123, les machines virtuelles de la structure de l’appliance sont **FSW123-WDS**, **FSW123-ad01**, **FSW123-VMM**, etc.  
  
Voici une vue consolidée d’une région PDW avec 6 nœuds de calcul.  
  
![Noms des composants PDW](./media/pdw-and-appliance-fabric-physical-components/APS_HW_Names.png "APS_HW_Names")  
  
## <a name="pdw"></a>Composants PDW  
Les machines virtuelles PDW font partie de la région PDW.  
  
*PDW_region*CTL01  
Un ordinateur virtuel qui exécute le nœud de contrôle. Cette opération s’exécute sur HST01 et peut basculer vers HST02.  
  
> [!WARNING]  
> SQL Server PDW ne prend pas en charge la création d’un instantané de la machine virtuelle CTL01 à l’aide du Gestionnaire Hyper-V. Les instantanés s’appuient sur le stockage local, ce qui provoque des erreurs si l’ordinateur virtuel tente de basculer vers sa sauvegarde. La création d’un instantané peut également entraîner des problèmes de fiabilité avec les autres machines virtuelles qui basculent vers le serveur passif.  
  
*PDW_region*-CMP01 via *PDW_Region*-CMP06  
Un ordinateur virtuel qui exécute le nœud de calcul. Dans ce diagramme de nœud de calcul 6, les hôtes HSA01 via HSA06 exécutent les machines virtuelles de nœud de calcul CMP01 via CMP06, respectivement.  
  
## <a name="fabric"></a>Composants de l’infrastructure d’appliances  
Ces composants font partie de l’infrastructure de l’appliance.  
  
### <a name="virtual-machines"></a>Virtual Machines  
*appliance_domain*-WDS  
Cet ordinateur virtuel héberge les services de déploiement Windows (WDS), que le système d’analyse de la plateforme utilise pour déployer les systèmes d’exploitation Windows sur le réseau de l’appliance. Il héberge également le service DHCP, qui permet aux hôtes de l’appliance de joindre le réseau de l’appliance sans disposer d’une adresse IP préconfigurée.  
  
L’ordinateur virtuel *appliance_domain*-WDS s’exécute sur HST01 et peut basculer vers HST02. L’ordinateur virtuel WDS et l’ordinateur virtuel VMM, déployez Windows sur les hôtes physiques lors de l’installation de l’appliance. Pendant le cycle de vie de l’appliance, WDS et VMM effectuent des opérations telles que le remplacement d’un ordinateur hôte.  
  
*appliance_domain*-VMM  
Le Virtual Machine Manager (VMM) s’exécute sur un ordinateur virtuel et peut basculer vers HST02. VMM héberge System Center pour déployer le système d’exploitation sur les hôtes physiques. VMM fournit également Windows Server Update Services (WSUS) pour appliquer ou supprimer des mises à jour Windows sur tous les ordinateurs hôtes et machines virtuelles.  
  
*appliance_domain*-AD01, *appliance_domain*-AD02  
Active Directory Domain Services, qui contient le système DNS (Domain Name System), s’exécute sur un ordinateur virtuel à la fois sur HST01 et HST02. Pour une haute disponibilité de l’appliance, AD01 et AD02 sont des contrôleurs de domaine répliqués qui ne basculent pas. Si l’un d’eux échoue, l’autre est déjà disponible avec les données correctes.  
  
*appliance_domain*ISCSI01  
Une machine virtuelle ISCSI s’exécute sur chacun des hôtes avec stockage attaché (HSA01-HSA06). Cette machine virtuelle ne bascule pas.  
  
### <a name="hosts"></a>Hôtes  
*appliance_domain*-HST01 via *appliance_domain*-HST06  
Hôtes du nœud de contrôle PDW et des machines virtuelles de l’infrastructure d’appliances. HST03 est un hôte passif facultatif.  
  
*appliance_domain*-HSA01 via *appliance_domain*-HSA08  
Hôtes avec stockage attaché (HSA). Chaque hôte a un hôte qui exécute une machine virtuelle à nœud de calcul et une machine virtuelle ISCSI.  
  
### <a name="cluster-for-pdw"></a>Cluster pour PDW  
*appliance_domain*WFOHST01  
Le cluster PDW est nommé WFOHST01. Il gère tous les ordinateurs hôtes physiques et les machines virtuelles qui appartiennent à PDW.  
  
### <a name="direct-attached-storage"></a>Stockage en attachement direct  
*appliance_domain*-DAS01 via *appliance_domain*-DAS03  
Il s’agit du stockage attaché direct qui est connecté aux nœuds de calcul. HP possède un DAS pour chacun des deux nœuds de calcul. Dell et quanta possèdent un DAS pour chaque nœud de calcul.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS [Hardware Configurations &#40;Analytics Platform System&#41;](../architecture/hardware-configurations.md)  -->  
[Configuration de l’appliance &#40;Analytics Platform System&#41;](appliance-configuration.md)  
[Tâches de gestion d’appliance &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
