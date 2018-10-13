---
title: Composants matériels - Analytique Platform System | Microsoft Docs
description: Analytique Platform System (APS) utilise des composants évolutifs afin que vous pouvez acheter la quantité exacte de traitement et de stockage en fonction des besoins de votre entreprise. Lorsque vous commandez des points d’accès, vous devez une combinaison de ces composants matériels de base.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 8cf7fd100f72e14b09ea086a1ebff5140a9068a4
ms.sourcegitcommit: 08b3de02475314c07a82a88c77926d226098e23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49119966"
---
# <a name="hardware-components-for-analytics-platform-system"></a>Composants matériels pour Analytique Platform System

Analytique Platform System (APS) utilise des composants évolutifs afin que vous pouvez acheter la quantité exacte de traitement et de stockage en fonction des besoins de votre entreprise. Lorsque vous commandez des points d’accès, vous devez une combinaison de ces composants matériels de base. Fournisseurs de matériel spécifique peuvent utiliser différentes conventions d’affectation de noms ou des composants supplémentaires.  
 
  
## <a name="rackandnetwork"></a>Rack et réseau 
 
Composants de points d’accès sont stockés dans un ou plusieurs racks qui entrent dans votre centre de données. Chaque rack est fourni avec les unités de distribution d’alimentation (PDU), les deux commutateurs InfiniBand et les deux commutateurs Ethernet.  
  
![Rack et réseau](media/rack-and-network.png "APS en rack et du réseau")  
  
## <a name="datascaleunit"></a>Unité d’échelle de données
 
Une unité d’échelle de données contient les hôtes de données et le stockage en attachement direct (DAS) pour le traitement et stockage des données utilisateur. Pour ajouter de la capacité, vous ajoutez des unités d’échelle de données en fonction des configurations qui sont prises en charge par votre fournisseur de matériel. Que le nombre d’unités d’échelle de données augmente, vous devez ajouter supplémentaire Rack & composants réseau, en fonction des besoins, pour fournir plus alimentation, réseau et monter en rack d’infrastructure.  
  
### <a name="data-host"></a>Hôte de données  

Un hôte de données est un serveur dédié au traitement des données de l’utilisateur. Parallel Data Warehouse (PDW) s’exécute à un nœud de calcul sur chaque hôte de données. Pour les appliances de HPE, l’unité d’échelle de données a deux hôtes de données. Pour les appliances de Dell et Quanta, l’unité d’échelle de données a trois hôtes de données.  
  
### <a name="direct-attached-storage"></a>Stockage en attachement direct
 
Le stockage en attachement direct (DAS) est un pool de disques sont connectés aux hôtes de données. Tous les hôtes de données peuvent accéder à des disques. Dans le cadre de la sans partage architecture, les nœuds de calcul en cours d’exécution sur les hôtes de données ne partagent pas de disques individuels. Toutefois, pour la haute disponibilité, l’accès au stockage est partagé et chacun des hôtes de données peut accéder à tous les disques.  
  
### <a name="data-scale-unit-architecture---dell-and-quanta"></a>Architecture d’unité données mise à l’échelle - DELL et Quanta
  
![Unité d’extensibilité](media/scalability-unit-dell.png "unité d’extensibilité de Dell")  
  
### <a name="data-scale-unit-architecture---hpe"></a>Architecture d’unité de mise à l’échelle de données - HPE 
 
![Unité d’extensibilité de HPE](media/scalability-unit-hpe.png "unité d’extensibilité de HPE")  
  
### <a name="data-scale-unit-description"></a>Description d’unité de mise à l’échelle de données

Une unité d’échelle de données possède un serveur (hôte) pour chaque nœud de calcul et un tableau d’un disque en attachement direct qui est attaché avec SCSI SAS (Serial Attached). Dans le fichier CAB de stockage, la baie de disques est divisée en deux ayant chacune des alimentations redondantes. Espaces de stockage de Windows Server gère les données de l’utilisateur en dupliquant les données entre les paires de disque en miroir RAID 1. Les disques dans chaque paire de disque sont stockés dans différentes moitiés de la baie de disques.  
  
La baie de disques contient également des disques de secours à chaud et un disque de système. Si un disque tombe en panne, espaces de stockage utilise la copie en bon état des données sur le disque fonctionne pour reconstruire une copie des données sur un échange à chaud. Il s’agit d’une fonctionnalité importante de réparation automatique qui vous aide à protéger contre la perte de données.  
  
Le nombre total de disques pour les nœuds de calcul :  
  
-   DELL a 96 disques = (3 serveurs) * (16 disques par serveur) \* (2 pour les disques redondants).  
  
-   HPE a 64 disques = (2 serveurs) * (16 disques par serveur) \* (2 pour les disques redondants).  
  
-   En outre, chaque baie de disques a de disques de secours à chaud et un disque de système.  
  
**Pour la haute disponibilité**, lorsqu’un nœud de calcul échoue, il peut fonctionnent toujours et accéder à ses données utilisateur via l’autre ordinateur hôte dans l’unité d’échelle de données. Au moins un des hôtes physiques attachés directs doit fonctionner ou accès aux données dans le stockage est perdue.  
  
**Tailles de disque**, le stockage en attachement direct peut avoir 1, 2 ou 3 disques téraoctet. Toutes les unités d’échelle de données doivent avoir des disques de la même taille.  
  
## <a name="basescaleunit"></a>Unité d’échelle de base 
 
L’unité d’échelle de Base contient le nombre minimal de puissance cerveau hôtes, les hôtes de données et stockage en attachement direct qui est requis pour l’appliance. Il inclut les composants suivants. 
  
### <a name="orchestration-host"></a>Hôte d’orchestration  
Ce serveur exécute le cerveau de PDW.
  
### <a name="passive-host"></a>Hôte passif  
Ce serveur offre une haute disponibilité. Il est en ligne et prêt à exécuter des tâches en cas de panne de l’orchestration ou un hôte de données. L’hôte d’orchestration, hôte passif et serveurs d’unité de données mise à l’échelle sont configurés comme un cluster de basculement Windows. Chaque rack de l’appliance nécessite un seul hôte passif.  
  
### <a name="optional-passive-host"></a>Hôte passif facultatif  
Pour renforcer la redondance, vous avez la possibilité d’ajouter un second hôte passif à l’unité d’échelle de Base.  
  
### <a name="data-scale-unit"></a>Unité d’échelle de données  
L’unité d’échelle de Base inclut une unité d’échelle de données qui est placée au bas du rack.  
  
Ce diagramme illustre l’unité d’échelle de Base ainsi que le Rack et le réseau. Il s’agit de la configuration minimale pour une appliance Analytique Platform System.  
  
![Unité d’échelle base](media/base-scale-unit.png "unité d’échelle de Base")  
 
