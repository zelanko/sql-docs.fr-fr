---
title: Composants matériels
description: Analytics Platform System (APS) utilise des composants évolutifs afin que vous puissiez acheter le volume de traitement et de stockage adéquat en fonction des besoins de votre entreprise. Lorsque vous commandez des points d’accès, vous aurez besoin d’une combinaison de ces composants matériels de base.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: db9966315d60fd4de1de7ae6805620d3f2144e6f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401142"
---
# <a name="hardware-components-for-analytics-platform-system"></a>Composants matériels pour Analytics Platform System

Analytics Platform System (APS) utilise des composants évolutifs afin que vous puissiez acheter le volume de traitement et de stockage adéquat en fonction des besoins de votre entreprise. Lorsque vous commandez des points d’accès, vous aurez besoin d’une combinaison de ces composants matériels de base. Des fournisseurs de matériel spécifiques peuvent utiliser des conventions d’affectation de noms différentes ou des composants supplémentaires.  
 
  
## <a name="rackandnetwork"></a>Rack et réseau 
 
Les composants APS sont tous stockés dans un ou plusieurs racks qui s’adaptent à votre centre de données. Chaque rack est fourni avec des unités de distribution de l’alimentation (PDU), deux commutateurs InfiniBand et deux commutateurs Ethernet.  
  
![Rack et réseau](media/rack-and-network.png "Rack et réseau APS")  
  
## <a name="datascaleunit"></a>Unité d’échelle des données
 
Une unité d’échelle de données contient les hôtes de données et le stockage en attachement direct (DAS) pour le traitement et le stockage des données utilisateur. Pour ajouter de la capacité, vous ajoutez des unités d’échelle de données en fonction des configurations prises en charge par votre fournisseur de matériel. Au fur et à mesure que le nombre d’unités d’échelle de données augmente, vous devez ajouter des composants de réseau & de rack supplémentaires, si nécessaire, pour fournir davantage d’énergie, de réseau et d’infrastructure en rack.  
  
### <a name="data-host"></a>Hôte de données  

Un hôte de données est un serveur dédié au traitement des données utilisateur. Le Data Warehouse parallèles (PDW) exécute un nœud de calcul sur chaque hôte de données. Pour les appareils HPE, l’unité d’échelle de données comporte deux hôtes de données. Pour les appareils Dell et Quanta, l’unité d’échelle de données comprend trois hôtes de données.  
  
### <a name="direct-attached-storage"></a>Stockage en attachement direct
 
Le stockage en attachement direct (DAS) est un pool de disques connectés aux hôtes de données. Tous les hôtes de données peuvent accéder à n’importe quel disque. Dans le cadre de l’architecture Shared Nothing, les nœuds de calcul exécutés sur les hôtes de données ne partagent pas de disques individuels. Toutefois, pour la haute disponibilité, l’accès au stockage est partagé et chacun des hôtes de données peut accéder à tous les disques.  
  
### <a name="data-scale-unit-architecture---dell-and-quanta"></a>Architecture des unités d’échelle de données-DELL et quanta
  
![Unité d’extensibilité](media/scalability-unit-dell.png "Unité d’extensibilité Dell")  
  
### <a name="data-scale-unit-architecture---hpe"></a>Architecture d’unité d’échelle de données-HPE 
 
![Unité d’extensibilité HPE](media/scalability-unit-hpe.png "Unité d’extensibilité HPE")  
  
### <a name="data-scale-unit-description"></a>Description de l’unité d’échelle des données

Une unité d’échelle de données dispose d’un serveur (hôte) pour chaque nœud de calcul et d’un groupe de disques à attachement direct qui est attaché à SAS (Serial Attached SCSI). Au sein du Cabinet de stockage, la baie de disques est divisée en deux moitiés, chacune disposant d’alimentations redondantes. Les espaces de stockage Windows Server gèrent les données utilisateur en dupliquant les données entre les paires de disques en miroir RAID 1. Les disques de chaque paire de disques sont stockés dans différentes moitiés de la baie de disques.  
  
La baie de disques contient également des disques de secours à chaud et un disque système. En cas de défaillance d’un disque, les espaces de stockage utilisent la bonne copie des données sur le disque opérationnel pour reconstruire une copie dupliquée des données sur un disque de rechange à chaud. Il s’agit d’une fonctionnalité importante de réparation automatique qui permet de se protéger contre la perte de données.  
  
Le nombre total de disques pour les nœuds de calcul :  
  
-   DELL a 96 disques = (3 serveurs) * (16 disques par serveur) \* (2 pour les disques redondants).  
  
-   HPE a 64 disques = (2 serveurs) * (16 disques par serveur) \* (2 pour les disques redondants).  
  
-   En outre, chaque baie de disques contient des disques de rechange à chaud et un disque système.  
  
**Pour une haute disponibilité**, lorsqu’un nœud de calcul bascule, il peut continuer à fonctionner et à accéder à ses données utilisateur via l’autre hôte dans l’unité d’échelle de données. Au moins l’un des hôtes physiques attachés directement doit fonctionner ou l’accès aux données au stockage est perdu.  
  
**Pour les tailles de disque**, le stockage en attachement direct peut avoir 1, 2 ou 3 téraoctets de disques. Toutes les unités d’échelle de données doivent avoir des disques de la même taille.  
  
## <a name="basescaleunit"></a>Unité d’échelle de base 
 
L’unité d’échelle de base contient le nombre minimal d’hôtes de l’alimentation au cerveau, les hôtes de données et le stockage en attachement direct requis pour l’appliance. Il comprend les composants suivants. 
  
### <a name="orchestration-host"></a>Hôte d’orchestration  
Ce serveur est le cerveau des PDW.
  
### <a name="passive-host"></a>Hôte passif  
Ce serveur fournit une haute disponibilité. Il est en ligne et prêt à exécuter des travaux en cas de défaillance de l’orchestration ou de l’hôte de données. L’hôte d’orchestration, l’hôte passif et les serveurs d’unités d’échelle de données sont configurés en tant que cluster de basculement Windows. Chaque rack de l’appliance nécessite un hôte passif.  
  
### <a name="optional-passive-host"></a>Hôte passif facultatif  
Pour ajouter une redondance supplémentaire, vous avez la possibilité d’ajouter un deuxième hôte passif à l’unité d’échelle de base.  
  
### <a name="data-scale-unit"></a>Unité d’échelle des données  
L’unité d’échelle de base comprend une unité d’échelle de données qui est placée au bas du rack.  
  
Ce diagramme illustre l’unité d’échelle de base, ainsi que le rack et le réseau. Il s’agit de la configuration minimale requise pour une appliance Analytics Platform System.  
  
![Unité d’échelle de base](media/base-scale-unit.png "Unité d’échelle de base")  
 
