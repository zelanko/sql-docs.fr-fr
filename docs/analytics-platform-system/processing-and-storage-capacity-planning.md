---
title: Capacité de stockage et traitement - Analytique Platform System | Microsoft Docs
description: Besoins de votre entreprise déterminent le nombre d’unités d’échelle de données et la taille des disques de nœud de calcul dont vous avez besoin dans votre appliance Analytique Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 7188ace65e31d92cc5acfdc684457b219836d2d1
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52527801"
---
# <a name="processing-and-storage-capacity-in-analytics-platform-system"></a>Capacité de stockage et de traitement d’Analytique Platform System
Besoins de votre entreprise déterminent le nombre d’unités d’échelle de données et la taille des disques de nœud de calcul dont vous avez besoin dans votre appliance Analytique Platform System (APS). Utilisez ces calculs de traitement et de stockage pour guider votre capacité d’achat et planification des décisions.  
  
  
## <a name="section1"></a>Planification de capacité de traitement  
Performances des requêtes pour SQL Server Parallel Data Warehouse (PDW) dépendent fortement du nombre de cœurs de processeur travailler sur vos données en parallèle. Dans les limites, l’augmentation du parallélisme améliore les performances de requête de traitement massivement parallèle (MPP). Même si la taille de vos données est relativement faible, la puissance du moteur de requête MPP est renforcée par avoir un meilleur parallélisme.  
  
Par exemple, un matériel avec 12 nœuds de calcul a 192 cœurs de processeur qui traitent de vos données en parallèle. C’est le degré de parallélisme 192 ! Une appliance dotée des nœuds de calcul 56 a 896 cœurs travaillent en parallèle. Cette grandeur de parallélisme n’est pas réalisable sans informatique MPP.  
  
À mesure que le nombre de nœuds de calcul augmente, montée en charge l’appliance nécessite l’ajout de plusieurs nœuds de calcul à un moment pour obtenir un avantage notable. Fournisseurs de matériel prend en charge des configurations spécifiques uniquement à l’échelle des unités de données pour vous assurer que l’avantage de la mise à l’échelle de l’appliance compense le coût de redistribuer les données sur plusieurs nœuds de calcul.  
  
### <a name="data-scale-unit-configuration-examples---hpe"></a>Exemples de configuration d’unité d’échelle de données - HPE  
Voici des exemples des configurations HPE pris en charge pour les données à l’échelle Uunits. Ils peuvent être différentes des plus récente configurations prises en charge, mais sont fournis sous la forme d’un exemple montrant comment augmenter la capacité en environ 20 pour cent.  
  
Majoration est le pourcentage de capacité de gain en augmentant la Uunits de mise à l’échelle de données à partir d’une ligne à la suivante. Par exemple, augmenter les unités d’échelle de données à partir de 6 à 8 donne une augmentation de 33 % des cœurs de processeur et mémoire.  Elle augmente également l’espace disque qui n’est pas indiqué dans cette table.  
  
|Unités d’échelle de données|Nœuds de calcul|Cœurs de processeur|Mémoire (Go)|Majoration|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|2|32|512|-|  
|2|4|64|1024|100%|  
|3|6|96|1536|50|  
|4|8|128|2048|33%|  
|5|10|160|2560|25%|  
|6|12|192|3072|20%|  
|8|16|256|4096|33%|  
|10|20|320|5120|25%|  
|12|24|384|6144|20%|  
|16|32|512|8192|33%|  
|20|40|640|10240|25%|  
|24|48|768|12288|20%|  
|28|56|896|14336|17%|  
  
Explication :  
  
-   **Unités d’échelle de données** par appliance. Pour en savoir plus sur les unités d’échelle de données, consultez [composants matériel de système de plateforme Analytique](hardware-components.md).  
  
-   **Nœuds de calcul** par appliance.  
  
-   **Cœurs de processeur** par appliance. Il existe 16 noyaux par nœud de calcul, un seul cœur par chaque paire de disque en miroir. Pour la structure de disque du nœud de calcul, consultez [composants matériel de système de plateforme Analytique](hardware-components.md).  
  
-   **Mémoire** par appliance. Chaque cœur a 256 Go de mémoire.  
  
### <a name="data-scale-unit-configuration-examples---dell-quanta"></a>Mise à l’échelle unité configuration exemples de données - Dell, Quanta  
Voici des exemples des configurations pour les données à l’échelle Uunits Dell et Quanta pris en charge. Ils peuvent être différentes des plus récente configurations prises en charge, mais sont fournis sous la forme d’un exemple montrant comment augmenter la capacité en environ 20 pour cent.  
  
Majoration est le pourcentage de capacité de gain en augmentant la Uunits de mise à l’échelle de données à partir d’une ligne à la suivante. Par exemple, augmenter les unités d’échelle de données à partir de 6 à 8 donne une augmentation de 33 % des cœurs de processeur et mémoire. Elle augmente également l’espace disque qui n’est pas indiqué dans cette table.  
  
|Unités d’échelle de données|Nœuds de calcul|Cœurs de processeur|Mémoire (Go)|Majoration|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|3|48|768|-|  
|2|6|96|1536|100%|  
|3|9|144|2,304|50|  
|4|12|192|3,072|33%|  
|5|15|240|3,840|25%|  
|6|18|288|4,608|20%|  
|7|21|336|5,376|17%|  
|8|24|384|6,144|14%|  
|9|27|432|6,912|13%|  
|12|36|576|9,216|33%|  
|15|45|720|11,520|25%|  
|18|54|864|13,824|20%|  
  
## <a name="section2"></a>Planification de la capacité de stockage  
Cette table estime que vous pouvez charger et stocker jusqu'à 6 plusieurs pétaoctets de données non compressées sur une appliance Analytique Platform System entièrement intégrée. 
  
|fournisseur|Taille du lecteur|Nœud de par calcul de stockage de données physiques|Nombre maximal de nœuds de calcul par rack|Stockage de données maximal physiques par rack|Estimation du stockage de données maximal d’utilisateurs par rack|Racks maximales|Estimation du stockage de données maximal d’utilisateurs par appareil|  
|----------|--------------|------------------------------------------|----------------------------------|------------------------------------------|------------------------------------------------|-----------------|-----------------------------------------------------|  
|HPE|1 TO|16 TO|8|128 TO|320 TO|7|2,240 TO|  
|HPE|2 TO|32 TO|8|256 TO|640 TO|7|4,480 TO|  
|HPE|3 TO|48 TO|8|384 TO|960 TO|7|6,720 TO|  
|DELL|1 TO|16 TO|9|144 TO|360 TO|6|2,160 TO|  
|DELL|2 TO|32 TO|9|288 TO|720 TO|6|4 320 TO|  
|DELL|3 TO|48 TO|9|432 TO|TO-1 080 PIXELS|6|6,480 TO|  
  
Explication :  
  
-   **Taille du lecteur** est 1, 2 ou 3 To pour chaque fournisseur de matériel.  
  
-   **Stockage de données physiques par nœud de calcul** = (taille du lecteur) * (16 disques par nœud de calcul). Les disques en miroir ne sont pas inclus dans la mesure où ils sont pour la redondance.  
  
-   **Les nœuds de calcul maximale par rack** est spécifique au fournisseur de matériel.  
  
-   **Stockage de données maximal physiques par rack** = (stockage de données physiques par nœud de calcul) * (nombre maximal de nœuds de calcul par rack).  
  
-   **Estimation du stockage de données maximal d’utilisateurs par rack** = (stockage physique des données maximale par rack) * (5 pour un taux de compression 5:1) \* (50 % pour les journaux et tempDB). Il s’agit de pessimiste pour les données utilisateur non compressé qui peuvent être chargées et stockées sur l’appliance. Ceci est une estimation et n’est pas appliquée par le logiciel. Le stockage des données utilisateur réel dépend de vos données et votre configuration.  
  
-   **Racks maximales** est propre à chaque fournisseur de matériel.  
  
-   **Estimation du stockage de données maximal par appliance** = (stockage de données maximal estimé par rack) * (racks Maximum). Il s’agit de pessimiste de la taille de total général des données utilisateur que vous pouvez charger et stocker sur un matériel totalement intégré.  
  
