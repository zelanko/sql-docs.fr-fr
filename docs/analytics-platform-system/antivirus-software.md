---
title: Antivirus
description: Si votre centre de données nécessite un logiciel antivirus, suivez ces instructions pour installer un logiciel antivirus sur le système d’analyse de plate-forme (APS). Nous vous recommandons de ne pas installer de logiciel antivirus, sauf s’il s’agit d’une exigence ferme de votre centre de données.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: c3687b839e52e64350591402c3aa19e9c2c54ac7
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401471"
---
# <a name="antivirus-software-for-analytics-platform-system-aps"></a>Logiciel antivirus pour Analytics Platform System (APS)
Si votre centre de données nécessite un logiciel antivirus, suivez ces instructions pour installer un logiciel antivirus sur Analytics Platform System. Nous vous recommandons de ne pas installer de logiciel antivirus, sauf s’il s’agit d’une exigence ferme de votre centre de données.  
  
> [!WARNING]  
> Nous vous recommandons vivement d’évaluer individuellement le risque de sécurité pour chaque ordinateur et le système de plateforme d’analyse dans son ensemble, et de sélectionner les outils qui conviennent au niveau de risque de sécurité de chaque ordinateur. En outre, nous vous recommandons, avant de déployer un projet de protection antivirus, de tester l’ensemble du système sous une charge complète pour mesurer les modifications de stabilité et de performances.  
>   
> Le logiciel de protection antivirus requiert des ressources système pour s’exécuter. Vous devez effectuer des tests avant et après l’installation de votre logiciel antivirus pour déterminer s’il existe des effets sur les performances sur le système de plateforme d’analyse.  
  
Cette rubrique est basée sur les instructions de [sélection d’un logiciel antivirus à exécuter sur les ordinateurs qui exécutent SQL Server](https://support.microsoft.com/kb/309422) et [l’article 961804](https://support.microsoft.com/kb/961804/en-us)de la base de connaissances.  
  
## <a name="exclusion-list-for-physical-hosts"></a>Liste d’exclusions pour les hôtes physiques  
Pour installer le logiciel antivirus sur les hôtes physiques, excluez la liste suivante de répertoires et de processus. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
**Exclure ces répertoires :**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V-répertoire de configuration de machine virtuelle  
  
-   Disques durs C:\users\public\documents\hyper-v\virtual Hard Disks-répertoire du lecteur de disque dur virtuel par défaut  
  
-   C:\clusterStorage-répertoires de lecteur de disque dur virtuel  
  
**Exclure ces processus :**  
  
-   Gestion des machines virtuelles (VMMS. exe)  
  
-   Processus de travail des machines virtuelles (Vmwp. exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Liste d’exclusions pour les machines virtuelles (VM)  
Pour installer le logiciel antivirus sur les machines virtuelles, excluez la liste suivante de répertoires et de fichiers. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
**_PDW_region_CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_-AD01** et ** _appliance_domain_-AD02**  
  
-   Aucune restriction  
  
**Machines virtuelles de nœud de calcul**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
**_appliance_domain_-VMM**  
  
-   Aucune restriction  
  
**_appliance_domain_-WDS**  
  
-   Aucune restriction  
  
**_appliance_domain_ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion d’appliance &#40;Analytics Platform System&#41;](appliance-management-tasks.md)  
  
