---
title: Capacité de traitement et de stockage
description: Les besoins de votre entreprise déterminent le nombre d’unités d’échelle de données et la taille des disques de nœuds de calcul dont vous avez besoin dans votre appliance d’analyse de système de plateforme d’analyse (APS).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 143c37b6b55b96f8a0225c98db2212f07b2cd3a5
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "74400543"
---
# <a name="processing-and-storage-capacity-in-analytics-platform-system"></a>Capacité de traitement et de stockage dans Analytics Platform System
Les besoins de votre entreprise déterminent le nombre d’unités d’échelle de données et la taille des disques de nœuds de calcul dont vous avez besoin dans votre appliance d’analyse de système de plateforme d’analyse (APS). Utilisez ces calculs de traitement et de stockage pour guider vos décisions d’achat et de planification de la capacité.  
  
  
## <a name="planning-for-processing-capacity"></a><a name="section1"></a>Planification de la capacité de traitement  
Les performances de requête pour SQL Server Parallel Data Warehouse (PDW) dépendent en grande partie du nombre de cœurs de processeur qui travaillent sur vos données en parallèle. Dans les limites, l’augmentation du parallélisme améliore les performances des requêtes de traitement massivement parallèle (MPP). Même si la taille de vos données est relativement faible, la puissance du moteur de requête MPP est améliorée grâce à un plus grand parallélisme.  
  
Par exemple, une appliance avec 12 nœuds de calcul a des cœurs de processeur 192 qui traitent vos données en parallèle. C’est la parallélisation 192 ! Une appliance avec des nœuds de calcul 56 a 896 cœurs qui fonctionnent en parallèle. Cette magnitude de parallélisme n’est pas réalisable sans l’informatique MPP.  
  
À mesure que le nombre de nœuds de calcul augmente, la montée en charge de l’appliance nécessite l’ajout de plusieurs nœuds de calcul à la fois pour obtenir un avantage notable. Les fournisseurs de matériel ne prennent en charge que des configurations spécifiques d’unités d’échelle de données pour s’assurer que l’avantage de la mise à l’échelle de l’appliance compense le coût de la redistribution des données sur plusieurs nœuds de calcul.  
  
### <a name="data-scale-unit-configuration-examples---hpe"></a>Exemples de configuration d’unité d’échelle de données-HPE  
Voici des exemples de configurations HPE prises en charge pour la mise à l’échelle des données Uunits. Ils peuvent varier par rapport aux configurations prises en charge les plus récentes, mais sont fournis comme exemple d’augmentation de la capacité d’environ 20%.  
  
La majoration est le gain de capacité en ce qui concerne l’augmentation des Uunits de l’échelle des données d’une ligne à l’autre. Par exemple, l’augmentation des unités d’échelle de données de 6 à 8 donne une majoration de 33% dans les cœurs de processeur et la mémoire.  Cela augmente également l’espace disque qui n’est pas indiqué dans ce tableau.  
  
|Unités d’échelle de données|Nœuds de calcul|Cœurs d’unité centrale|Mémoire (Go)|Garantie|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|2|32|512|-|  
|2|4|64|1 024|100 %|  
|3|6|96|1536|50%|  
|4|8|128|2 048|33 %|  
|5|10|160|2560|25%|  
|6|12|192|3 072|20%|  
|8|16|256|4096|33 %|  
|10|20|320|5120|25%|  
|12|24|384|6144|20%|  
|16|32|512|8 192|33 %|  
|20|40|640|10240|25%|  
|24|48|768|12288|20%|  
|28|56|896|14336|17 %|  
  
Explication :  
  
-   **Unités d’échelle de données** par appliance. Pour en savoir plus sur les unités d’échelle de données, consultez [composants matériels du système d’analyse de plateforme](hardware-components.md).  
  
-   **Nœuds de calcul** par appliance.  
  
-   **Cœurs d’UC** par appliance. Il y a 16 cœurs par nœud de calcul, un cœur par paire de disques en miroir. Pour la structure des disques de nœud de calcul, consultez [composants matériels du système d’analyse de plateforme](hardware-components.md).  
  
-   **Mémoire** par appliance. Chaque noyau a 256 Go de mémoire.  
  
### <a name="data-scale-unit-configuration-examples---dell-quanta"></a>Exemples de configuration d’unité d’échelle de données-Dell, quanta  
Voici des exemples de configurations prises en charge par Dell et quanta pour la mise à l’échelle des données Uunits. Ils peuvent varier par rapport aux configurations prises en charge les plus récentes, mais sont fournis comme exemple d’augmentation de la capacité d’environ 20%.  
  
La majoration est le gain de capacité en ce qui concerne l’augmentation des Uunits de l’échelle des données d’une ligne à l’autre. Par exemple, l’augmentation des unités d’échelle de données de 6 à 8 donne une majoration de 33% dans les cœurs de processeur et la mémoire. Cela augmente également l’espace disque qui n’est pas indiqué dans ce tableau.  
  
|Unités d’échelle de données|Nœuds de calcul|Cœurs de processeur|Mémoire (Go)|Garantie|  
|--------------------|-----------------|-------------|-----------------|----------|  
|1|3|48|768|-|  
|2|6|96|1536|100 %|  
|3|9|144|2 304|50%|  
|4|12|192|3 072|33 %|  
|5|15|240|3 840|25%|  
|6|18|288|4 608|20%|  
|7|21|336|5 376|17 %|  
|8|24|384|6 144|14 %|  
|9|27|432|6 912|13%|  
|12|36|576|9 216|33 %|  
|15|45|720|11 520|25%|  
|18|54|864|13 824|20%|  
  
## <a name="planning-for-storage-capacity"></a><a name="section2"></a>Planification de la capacité de stockage  
Ce tableau estime que vous pouvez charger et stocker jusqu’à 6 pétaoctets de données non compressées sur un appareil système de plateforme d’analyse entièrement construit. 
  
|Fournisseur|Taille du lecteur|Stockage physique des données par nœud de calcul|Nombre maximal de nœuds de calcul par rack|Stockage de données maximal physique par rack|Estimation du stockage de données utilisateur maximal par rack|Racks maximum|Estimation du stockage de données utilisateur maximal par Appliance|  
|----------|--------------|------------------------------------------|----------------------------------|------------------------------------------|------------------------------------------------|-----------------|-----------------------------------------------------|  
|HPE|1 To|16 TO|8|128 To|320 TO|7|2 240 TO|  
|HPE|2 To|32 To|8|256 To|640 TO|7|4 480 TO|  
|HPE|4 To|64 To|8|512 TO|1280 TO|7|8 960 TO|  
|DELL|1 To|16 TO|9|144 TO|360 TO|6|2 160 TO|  
|DELL|2 To|32 To|9|288 TO|720 TO|6|4 320 TO|  
|DELL|4 To|64 To|9|576 TO|1440 TO|6|8 640 TO|   
  
Explication :  
  
-   La **taille du lecteur** est 1, 2 ou 4 to pour chaque fournisseur de matériel.  
  
-   **Stockage physique des données par nœud de calcul** = (taille du lecteur) * (16 disques par nœud de calcul). Les disques mis en miroir ne sont pas inclus dans la mesure où ils sont destinés à la redondance.  
  
-   Le **nombre maximal de nœuds de calcul par rack** est spécifique au fournisseur de matériel.  
  
-   **Stockage de données maximal physique par rack** = (stockage de données physiques par nœud de calcul) * (nombre maximal de nœuds de calcul par rack).  
  
-   **Estimation du stockage de données utilisateur maximal par rack** = (stockage de données maximal physique par rack) * (5 pour un taux de compression de 5:1) \* (50% pour les journaux et tempdb). Il s’agit d’une estimation prudente des données utilisateur non compressées qui peuvent être chargées et stockées sur l’appliance. Il s’agit d’une estimation qui n’est pas appliquée par un logiciel. Le stockage de données utilisateur réel dépend de vos données et de votre configuration.  
  
-   Les **racks maximaux** sont spécifiques à chaque fournisseur de matériel.  
  
-   **Estimation du stockage de données maximal par Appliance** = (stockage de données maximal estimé par rack) * (racks maximum). Il s’agit d’une estimation prudente de la taille totale des données utilisateur que vous pouvez charger et stocker sur une appliance entièrement créée.  
  
