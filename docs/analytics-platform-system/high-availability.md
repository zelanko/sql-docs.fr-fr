---
title: Haute disponibilité d’Analytique Platform System | Microsoft Docs
description: Découvrez comment Analytique Platform System (APS) est conçu pour la haute disponibilité.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cdf1837bd3b3b1cdf8e189ae591cd6fbff58387a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960866"
---
# <a name="analytics-platform-system-high-availability"></a>Haute disponibilité d’Analytique Platform System
Découvrez comment Analytique Platform System (APS) est conçu pour la haute disponibilité.  
  
## <a name="high-availability-architecture"></a>Architecture de haute disponibilité  
![Architecture de l’appliance](media/appliance-architecture.png "architecture de l’Appliance")  
  
## <a name="network"></a>Réseau  
Disponibilité du réseau, l’appliance APS possède deux réseaux InfiniBand. Si un des réseaux InfiniBand tombe en panne, l’autre est toujours disponible. En outre, Active Directory a répliqué les contrôleurs de domaine pour résoudre les demandes entrantes vers le réseau InfiniBand correct.  
  
Pour plus d’informations, consultez [cartes réseau InfiniBand configurer](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Stockage  
Pour sécuriser les données, points d’accès utilise RAID 1 pour conserver deux copies de toutes les données utilisateur de mise en miroir. En cas de défaillance d’un disque, le matériel système reconstruit les données sur un disque de rechange et définit une alerte qu’il existe une défaillance de disque.  
  
Pour conserver les données disponibles en ligne, APS utilise des espaces de stockage Windows et les volumes partagés en cluster pour gérer les disques de données utilisateur dans le stockage en attachement direct. Il existe un pool de stockage par unité d’échelle de données organisée en Volumes partagés de Cluster qui sont disponibles pour les hôtes de nœud de calcul par le biais des points de montage.  
  
Pour garantir que le pool de stockage reste en ligne, chaque hôte dans l’unité d’échelle de données possède une machine virtuelle ISCSI qui ne bascule pas. Cette architecture est importante car si un hôte échoue, les données sont toujours accessibles via les autres hôtes dans l’unité d’échelle de données.  
  
## <a name="hosts"></a>Hôtes  
Pour la disponibilité de l’hôte, tous les hôtes sont configurés dans un Cluster de basculement Windows. Chaque rack possède un hôte passif. Si vous le souhaitez le premier rack, qui contrôle SQL Server Parallel Data Warehouse (PDW) et l’infrastructure de l’appliance, peut avoir un second hôte passif. Si un hôte échoue, les machines virtuelles qui sont configurés pour le basculement, bascule vers un hôte passif disponible.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>Nœuds PDW et fabric de l’appliance  
Pour la haute disponibilité des nœuds PDW et l’infrastructure de l’appliance APS utilise la virtualisation. Chacun des composants de fabric PDW et appliance s’exécutent dans une machine virtuelle.  
  
Chaque machine virtuelle est définie en tant que rôle dans le cluster de basculement Windows. En cas d’échec d’une machine virtuelle, le cluster redémarre sur un ordinateur hôte disponible passif. Les machines virtuelles sont déployées à l’aide de System Center Virtual Machine Manager. Lorsqu’un basculement se produit, la machine virtuelle en cours d’exécution sur l’ordinateur hôte passif peut toujours accéder à ses données utilisateur via le réseau InfiniBand.  
  
Le nœud de contrôle et les machines virtuelles de nœud calcul sont configurés comme un cluster à nœud unique. Le cluster à nœud unique gère les réseaux InfiniBand en tant que ressource de cluster pour garantir que le cluster est toujours à l’aide de l’IP InfiniBand active. Le cluster à nœud unique gère les processus PDW qui s’exécutent au sein de la machine virtuelle. Par exemple, le cluster à nœud unique a SQL Server et le Service de déplacement des données (DMS) en tant que ressources pour qu’elle peut les recommencer dans l’ordre approprié. Le nœud contrôle de machine virtuelle contrôle également l’ordre de démarrage pour les autres machines virtuelles qui s’exécutent sur l’hôte d’orchestration.  
  
