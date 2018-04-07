---
title: Haute disponibilité de système de plateforme Analytique
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: Décrit l’architecture système de plateforme Analytique (APS) pour la haute disponibilité.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 5ab245e9-0316-4d25-a626-4745ce856925
caps.latest.revision: 9
ms.openlocfilehash: 9fd057a4cd673f06034e0093ca93be7ceaf345ea
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="analytics-platform-system-high-availability"></a>Haute disponibilité de système de plateforme Analytique
Décrit l’architecture système de plateforme Analytique (APS) pour la haute disponibilité.  
  
## <a name="high-availability-architecture"></a>Architecture haute disponibilité  
![Architecture des appliances](media/appliance-architecture.png "architecture des appliances")  
  
## <a name="network"></a>Réseau  
Disponibilité du réseau, la solution de points d’accès possède deux réseaux InfiniBand. Si un des réseaux InfiniBand tombe en panne, l’autre est toujours disponible. En outre, Active Directory a répliqué les contrôleurs de domaine pour résoudre les demandes entrantes pour le réseau InfiniBand correct.  
  
Pour plus d’informations, consultez [cartes réseau InfiniBand de configurer](configure-infiniband-network-adapters.md).  
  
## <a name="storage"></a>Stockage  
Pour sécuriser les données, points d’accès utilise RAID 1 pour conserver deux copies de toutes les données utilisateur de mise en miroir. En cas de défaillance d’un disque, le matériel du système permet de reconstruire les données sur un disque et définit une alerte qu’il existe une défaillance du disque.  
  
Pour conserver les données disponibles en ligne, points d’accès utilise des espaces de stockage Windows et les volumes partagés de cluster pour gérer les disques de données utilisateur dans le stockage en attachement direct. Il existe un pool de stockage par l’unité d’échelle de données organisée dans des Volumes partagés de Cluster qui sont disponibles pour les hôtes de nœud de calcul par le biais des points de montage.  
  
Pour garantir que le pool de stockage reste en ligne, chaque hôte dans l’unité d’échelle de données possède un ordinateur virtuel ISCSI ne bascule pas. Cette architecture est importante, car si un hôte échoue, les données sont toujours accessibles via les autres hôtes dans l’unité d’échelle des données.  
  
## <a name="hosts"></a>Hôtes  
Pour la disponibilité de l’hôte, tous les hôtes sont configurés dans un Cluster de basculement Windows. Chaque rack possède un hôte passif. Éventuellement, le premier rack, qui contrôle SQL Server Parallel Data Warehouse (PDW) et l’infrastructure d’application, peut avoir un second hôte passif. Si un hôte échoue, les ordinateurs virtuels qui sont configurés pour le basculement, bascule vers un hôte passif disponible.  
  
## <a name="pdw-nodes-and-appliance-fabric"></a>Les nœuds PDW et l’infrastructure d’application  
Points d’accès pour la haute disponibilité des nœuds PDW et l’infrastructure d’application utilise la virtualisation. Chacun des composants de l’ensemble fibre optique PDW et appliance s’exécutent dans une machine virtuelle.  
  
Chaque ordinateur virtuel est défini comme un rôle dans le cluster de basculement Windows. En cas d’échec d’un ordinateur virtuel, le cluster redémarre sur un ordinateur hôte disponible passif. Les ordinateurs virtuels sont déployés à l’aide de System Center Virtual Machine Manager. Lorsqu’un basculement se produit, l’ordinateur virtuel en cours d’exécution sur l’ordinateur hôte passif peut toujours accéder à ses données utilisateur via le réseau InfiniBand.  
  
Le nœud de contrôle et les machines virtuelles de nœud calcul chacun configurés comme un cluster à nœud unique. Le cluster à nœud unique gère les réseaux InfiniBand en tant que ressource de cluster pour garantir que le cluster est toujours à l’aide de l’adresse IP InfiniBand active. Le cluster à nœud unique gère les processus d’empaquetage qui s’exécutent sur l’ordinateur virtuel. Par exemple, le cluster à nœud unique a SQL Server et le Service de déplacement des données (DMS) en tant que ressources pour qu’il puisse commencer les dans l’ordre approprié. Le nœud contrôle de machine virtuelle contrôle également l’ordre de démarrage pour les autres machines virtuelles qui s’exécutent sur l’hôte d’orchestration.  
  
