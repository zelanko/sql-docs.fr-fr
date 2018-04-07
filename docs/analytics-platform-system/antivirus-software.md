---
title: Logiciel antivirus (système de plateforme Analytique)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60ab9a88-d339-4917-a38b-f9481aef38fd
caps.latest.revision: 29
ms.openlocfilehash: 27e3bc7eae50c0418c0dcb4df99565b3f0edeadf
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="antivirus-software"></a>Logiciel antivirus
Si votre centre de données requiert un logiciel antiviru, utilisez ces instructions pour installer un logiciel antivirus sur le système de plateforme d’Analytique. Nous vous recommandons ne pas l’installation de logiciel antivirus, sauf si elle est une exigence d’entreprise de votre centre de données.  
  
> [!WARNING]  
> Nous recommandons vivement qu’individuellement évaluer le risque de sécurité pour chaque ordinateur et de système de plateforme d’Analytique dans son ensemble, et que vous sélectionnez les outils appropriés pour le niveau de risque pour la sécurité de chaque ordinateur. En outre, nous vous recommandons d’avant de mettre un projet de la protection contre les virus, tester l’ensemble du système sous une charge complète pour mesurer les modifications de stabilité et de performances.  
>   
> Protection antivirus nécessite des ressources système à exécuter. Vous devez effectuer le test avant et après l’installation de votre logiciel antivirus pour déterminer s’il y a aucun effet de performances sur le système de plateforme Analytique.  
  
Cette rubrique est basée sur les instructions de [comment choisir un logiciel antivirus s’exécute sur les ordinateurs qui exécutent SQL Server](http://support.microsoft.com/kb/309422) et [961804 de l’Article KB](http://support.microsoft.com/kb/961804/en-us).  
  
## <a name="exclusion-list-for-physical-hosts"></a>Liste d’exclusion pour les ordinateurs hôtes physiques  
Pour installer le logiciel antivirus sur les hôtes physiques, excluez la liste suivante des répertoires et des processus. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
**Exclure les répertoires suivants :**  
  
-   C:\ProgramData\Microsoft\Windows\Hyper-V - répertoire de configuration de machine virtuelle  
  
-   Disques durs C:\Users\Public\Documents\Hyper-V\Virtual - répertoire du lecteur de disque dur virtuel par défaut  
  
-   C:\clusterStorage - répertoires de lecteur de disque dur virtuel  
  
**Exclure les processus :**  
  
-   Gestion d’ordinateurs virtuels (Vmms.exe)  
  
-   Processus de travail de machine virtuelle (Vmwp.exe)  
  
## <a name="exclusion-list-for-virtual-machines-vms"></a>Liste d’exclusion pour les Machines virtuelles (VM)  
Pour installer le logiciel antivirus sur les machines virtuelles, excluez la liste suivante de répertoires et fichiers. Ils ne doivent pas être analysés par le logiciel antivirus.  
  
***PDW_region*-CTL01**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain *-AD01** et ***appliance_domain *-AD02**  
  
-   Aucune restriction  
  
**Machines virtuelles de nœud de calcul**  
  
-   C:\windows\cluster\  
  
-   G:\  
  
***appliance_domain*-VMM**  
  
-   Aucune restriction  
  
***appliance_domain*-WDS**  
  
-   Aucune restriction  
  
***appliance_domain*-ISCSI01**  
  
-   C:\iscsitarget  
  
## <a name="see-also"></a>Voir aussi  
[Tâches de gestion appliance &#40;Analytique plate-forme système&#41;](appliance-management-tasks.md)  
  
