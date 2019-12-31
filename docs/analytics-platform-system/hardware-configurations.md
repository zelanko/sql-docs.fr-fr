---
title: Configurations matérielles
description: Le matériel de l’appliance Analytics Platform System (APS) est conçu avec des unités évolutives afin que vous achetiez la quantité appropriée de traitement et de stockage en fonction des besoins de votre entreprise. L’Appliance met à l’échelle le stockage pour les Data Warehouse parallèles de quelques téraoctets à plus de 6 pétaoctets de données.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ee16045931da345f06c141597ccd25d19a36dea7
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401131"
---
# <a name="hardware-configurations---analytics-platform-system"></a>Configurations matérielles-système d’analyse-plateforme
Le matériel d’Analytics Platform System (APS) est conçu avec des unités évolutives afin que vous achetiez la quantité appropriée de traitement et de stockage en fonction des besoins de votre entreprise. L’Appliance met à l’échelle le stockage pour SQL Server Parallel Data Wareouse (PDW) de quelques téraoctets à plus de 6 pétaoctets de données.  
  
## <a name="contents"></a>Contenu  
  
-   [Configurations à un seul rack](#section1)  
  
-   [Configurations à plusieurs racks](#section2)  

  
## <a name="section1"></a>Configurations à un seul rack  
Le premier rack de l’appliance contient les composants requis pour exécuter PDW. La configuration d’appliance minimale est un rack et un réseau, ainsi qu’une unité d’échelle de base. Ces diagrammes montrent comment configurer le premier rack de l’appliance. Vous pouvez avoir entre 2 et 9 nœuds de calcul dans le premier rack, en fonction du fabricant du matériel.  
  
### <a name="first-rack-configurations---dell"></a>Premières configurations de rack-DELL  
La configuration minimale d’une appliance DELL comporte 3 nœuds de calcul. Vous pouvez ajouter jusqu’à 2 unités d’échelle de données au premier rack pour un total de 9 nœuds de calcul.  
  
![Configurations Dell First rack](media/first-rack-configurations-dell.png "Configurations Dell First rack")  
  
### <a name="first-rack-configurations---hpe"></a>Premières configurations de rack-HPE  
La configuration minimale pour une appliance HPE comprend 2 nœuds de calcul. Vous pouvez ajouter jusqu’à 3 unités d’échelle de données au premier rack pour un total de 8 nœuds de calcul.  
  
![Configurations du premier rack HPE pour HPE](media/first-rack-configurations-hpe.png "Configurations du premier rack HPE")  
  
## <a name="section2"></a>Configurations à plusieurs racks  
Pour ajouter de la capacité à PDW, vous pouvez ajouter des unités d’échelle de données, ainsi que des composants de réseau de & de rack supplémentaires, le cas échéant, afin de fournir l’infrastructure appropriée, mise en réseau et rack. Chaque réseau & de rack supplémentaire nécessite un hôte passif.  
  
Chaque fournisseur de matériel spécifie le nombre d’unités d’échelle de données que vous pouvez ajouter en fonction de la capacité de votre appliance. Nous vous recommandons d’ajouter suffisamment d’unités d’échelle de données pour voir au moins une majoration de 20% des performances. Par exemple, l’ajout d’une unité d’échelle de données à un appareil qui possède déjà 20 unités d’échelle de données peut entraîner un gain de performances négligeable. Le gain net ne devrait pas justifier le coût et l’effort.  
  
### <a name="scale-out-example---hpe"></a>Exemple scale out-HPE  
Ce diagramme montre un appareil HP à 3 racks contenant 20 nœuds de calcul.  
  
![Appareil HPE avec 20 nœuds de calcul](media/scale-out-hpe.png "Appareil HPE avec 20 nœuds de calcul")  
  
### <a name="scale-out-example---dell-quanta"></a>Exemple de Scale Out-DELL, quanta  
Ce diagramme illustre une appliance DELL ou quanta 3 rack qui contient 21 nœuds de calcul.  
  
![Appliance Dell avec 21 nœuds de calcul](media/scale-out-dell.png "Appliance Dell avec 21 nœuds de calcul")  
 
