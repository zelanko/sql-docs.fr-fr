---
title: Haute disponibilité
description: Découvrez comment Analytics Platform System (APS) est conçu pour la haute disponibilité.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6246ed25909a2e366d8bbafcd912a4fd923cc84a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401101"
---
# <a name="analytics-platform-system-high-availability"></a>Haute disponibilité du système d’analyse de plateforme
Découvrez comment Analytics Platform System (APS) est conçu pour la haute disponibilité.  
  
## <a name="high-availability-architecture"></a>Architecture haute disponibilité  
![Architecture de l’appliance](media/appliance-architecture.png "Architecture de l’appliance")  
  
## <a name="network"></a>Réseau  
Pour la disponibilité du réseau, l’appliance APS a deux réseaux InfiniBand. Si l’un des réseaux InfiniBand tombe en panne, l’autre est toujours disponible. De plus, Active Directory possède des contrôleurs de domaine répliqués pour résoudre les demandes entrantes sur le réseau InfiniBand approprié.  
  
Pour plus d’informations, consultez [configurer des cartes réseau InfiniBand](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Stockage  
Pour garantir la sécurité des données, APS utilise la mise en miroir RAID 1 pour gérer deux copies de toutes les données utilisateur. En cas de défaillance d’un disque, le système matériel reconstruit les données sur un disque de rechange et définit une alerte indiquant une défaillance de disque.  
  
Pour que les données restent disponibles en ligne, APS utilise des espaces de stockage Windows et des volumes partagés en cluster pour gérer les disques de données utilisateur dans le stockage en attachement direct. Un pool de stockage par unité d’échelle de données est organisé en volumes partagés de cluster qui sont disponibles pour les hôtes de nœud de calcul par le biais de points de montage.  
  
Pour vous assurer que le pool de stockage reste en ligne, chaque ordinateur hôte de l’unité d’échelle de données dispose d’une machine virtuelle ISCSI qui ne bascule pas. Cette architecture est importante car si un hôte échoue, les données sont toujours accessibles via les autres hôtes de l’unité d’échelle de données.  
  
## <a name="hosts"></a>Hôtes  
Pour la disponibilité des ordinateurs hôtes, tous les ordinateurs hôtes sont configurés dans un cluster de basculement Windows. Chaque rack a un hôte passif. Éventuellement, le premier rack, qui contrôle SQL Server les Data Warehouse parallèles et la structure de l’appareil, peut avoir un deuxième hôte passif. En cas de défaillance d’un ordinateur hôte, les ordinateurs virtuels qui sont configurés pour le basculement sont basculés vers un hôte passif disponible.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>Nœuds PDW et structure d’appliances  
Pour la haute disponibilité des nœuds PDW et de la structure d’appliances, APS utilise la virtualisation. Chacun des composants de l’infrastructure PDW et appliance s’exécute sur une machine virtuelle.  
  
Chaque ordinateur virtuel est défini en tant que rôle dans le cluster de basculement Windows. En cas de défaillance d’un ordinateur virtuel, le cluster le redémarre sur un hôte passif disponible. Les machines virtuelles sont déployées à l’aide de System Center Virtual Machine Manager. En cas de basculement, l’ordinateur virtuel en cours d’exécution sur l’hôte passif est toujours en mesure d’accéder à ses données utilisateur via le réseau InfiniBand.  
  
Les machines virtuelles du nœud de contrôle et du nœud de calcul sont configurées en tant que cluster à nœud unique. Le cluster à nœud unique gère les réseaux InfiniBand en tant que ressource de cluster pour s’assurer que le cluster utilise toujours l’adresse IP InfiniBand active. Le cluster à nœud unique gère les processus PDW qui s’exécutent sur l’ordinateur virtuel. Par exemple, le cluster à nœud unique a SQL Server et le service de déplacement des données (DMS) en tant que ressources afin qu’il puisse les démarrer dans le bon ordre. La machine virtuelle du nœud de contrôle contrôle également l’ordre de démarrage pour les autres machines virtuelles qui s’exécutent sur l’hôte de l’orchestration.  
  
