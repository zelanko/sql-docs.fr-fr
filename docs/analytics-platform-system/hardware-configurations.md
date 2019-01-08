---
title: Les configurations matérielles - Analytique Platform System | Microsoft Docs
description: Le matériel Analytique Platform System (APS) est conçu avec des unités évolutives afin que vous achetez la bonne quantité de traitement et de stockage en fonction des besoins de votre entreprise. L’appliance met à l’échelle le stockage pour Parallel Data Warehouse à partir de quelques téraoctets à 6 sur plusieurs pétaoctets de données.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 2a252e5f2aebd8d51b9b0eb1f353ded504155c2e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52507944"
---
# <a name="hardware-configurations---analytics-platform-system"></a>Configurations matérielles - Analytique Platform System
Le matériel Analytique Platform System (APS) est conçu avec des unités évolutives afin que vous achetez la bonne quantité de traitement et de stockage en fonction des besoins de votre entreprise. L’appliance met à l’échelle le stockage pour SQL Server Parallel Data Wareouse (PDW) à partir de quelques téraoctets à 6 sur plusieurs pétaoctets de données.  
  
## <a name="contents"></a>Sommaire  
  
-   [Configurations d’un Rack](#section1)  
  
-   [Configurations multiples de Rack](#section2)  

  
## <a name="section1"></a>Configurations d’un Rack  
Le premier rack dans l’appliance contient les composants requis pour exécuter PDW. La configuration de l’appliance minimale est un Rack et réseau ainsi qu’une unité d’échelle de Base. Ces diagrammes montrent les façons dont le premier rack de l’appliance peut être configuré. Vous pouvez avoir entre 2 et 9 nœuds de calcul dans le rack premier, selon le fournisseur de matériel.  
  
### <a name="first-rack-configurations---dell"></a>Tout d’abord monter en Rack Configurations - DELL  
La configuration minimale pour un dispositif de DELL a 3 nœuds de calcul. Vous pouvez ajouter jusqu'à 2 unités d’échelle de données à la première rack pour un total de 9 nœuds de calcul.  
  
![Premières configurations rack de Dell](media/first-rack-configurations-dell.png "premières configurations rack de Dell")  
  
### <a name="first-rack-configurations---hpe"></a>Tout d’abord monter en Rack de Configurations - HPE  
La configuration minimale pour une appliance HPE possède 2 nœuds de calcul. Vous pouvez ajouter jusqu'à 3 unités d’échelle de données à la première rack pour un total de 8 nœuds de calcul.  
  
![HPE monter en rack tout d’abord les configurations pour HPE](media/first-rack-configurations-hpe.png "HPE tout d’abord les configurations en rack")  
  
## <a name="section2"></a>Configurations multiples de rack  
Pour augmenter la capacité de PDW, vous pouvez ajouter des unités d’échelle de données, ainsi que les composants de Rack & réseau supplémentaires que nécessaire pour fournir la puissance appropriée, la mise en réseau et monter en rack d’infrastructure. Chaque supplémentaires Rack & réseau requiert un hôte passif.  
  
Chaque fournisseur de matériel Spécifie le nombre d’unités d’échelle de données que vous pouvez ajouter étant donné la capacité de votre appliance. Nous vous recommandons d’ajouter suffisamment unités d’échelle de données pour voir au moins une augmentation de 20 pour cent des performances. Par exemple, ajout une échelle de données unité vers un appareil qui a déjà 20 unités d’échelle de données peut entraîner un gain de performances négligeables. Le gain net serait justifie le coût et effort.  
  
### <a name="scale-out-example---hpe"></a>Monter en charge de l’exemple - HPE  
Ce diagramme illustre une appliance de 3 rack HP qui contient 20 nœuds de calcul.  
  
![Appliance HPE avec 20 nœuds de calcul](media/scale-out-hpe.png "appliance HPE avec 20 nœuds de calcul")  
  
### <a name="scale-out-example---dell-quanta"></a>Montée en puissance exemple - DELL, Quanta  
Ce diagramme illustre une appliance de DELL ou Quanta 3 rack qui contient les nœuds de calcul 21.  
  
![Appliance de Dell avec des nœuds de calcul 21](media/scale-out-dell.png "appliance de Dell avec des nœuds de calcul 21")  
 
