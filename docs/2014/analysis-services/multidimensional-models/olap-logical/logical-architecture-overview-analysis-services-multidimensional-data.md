---
title: Vue d’ensemble de l’architecture logique (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], examples
- cubes [Analysis Services], about cubes
ms.assetid: 1a547bce-dacf-4d32-bc0f-3829f4b026e1
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b945aa26f0cd9137763a3a8d84b0f74c7d2311bc
ms.sourcegitcommit: 8cb26b7dd40280a7403d46ee59a4e57be55ab462
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "68889612"
---
# <a name="logical-architecture-overview-analysis-services---multidimensional-data"></a>Vue d'ensemble de l'architecture logique (Analysis Services - données multidimensionnelles)
  Analysis Services s'exécute en mode de déploiement du serveur qui détermine l'architecture de la mémoire et l'environnement d'exécution utilisés par différents types de modèles Analysis Services. Le mode serveur est déterminé lors de l'installation. Le **mode multidimensionnel et d’exploration de données** prend en charge les données OLAP et l’exploration de données traditionnelles. Le **mode tabulaire** prend en charge les modèles tabulaires. Le **mode intégré SharePoint** fait référence à une instance de Analysis Services qui a été installée en tant que PowerPivot pour SharePoint, utilisé pour le chargement et l’interrogation des modèles de données Excel ou PowerPivot à l’intérieur d’un classeur.  
  
 Cette rubrique explique l'architecture de base d'Analysis Services lors de l'exploitation en mode multidimensionnel et d'exploration de données. Pour plus d’informations sur les autres modes, consultez [modélisation &#40;tabulaire&#41; SSAS tabulaire](../../tabular-models/tabular-models-ssas.md) et [comparaison des &#40;solutions tabulaires et&#41;multidimensionnelles SSAS](https://docs.microsoft.com/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas).  
  
## <a name="basic-architecture"></a>Architecture de base  
 Une instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] peut contenir plusieurs bases de données, et une base de données peut contenir en même temps des objets OLAP et des objets d'exploration de données. Les applications se connectent à une instance spécifiée de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] et à une base de données spécifiée. Un ordinateur serveur peut héberger plusieurs instances de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Les instances de [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] sont nommées « \<ServerName > \\ < nom_instance \> ». L’illustration suivante montre toutes les relations mentionnées entre des objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 ![Relations des objets AMO en cours d’exécution](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/amo-runningobjects.gif "Relations des objets AMO en cours d’exécution")  
  
 Les classes Basic sont le jeu minimum d'objets requis pour générer un cube. Ce jeu minimum d'objets est une dimension, un groupe de mesures et une partition. L'agrégation est facultative.  
  
 Les dimensions sont construites à partir d'attributs et de hiérarchies. Les hiérarchies sont formées par un jeu ordonné d'attributs, où chaque attribut du jeu correspond à un niveau dans la hiérarchie.  
  
 Les cubes sont construits à partir de dimensions et de groupes de mesures. Les dimensions dans la collection de dimensions d'un cube appartiennent à la collection de dimensions de la base de données. Les groupes de mesures sont des collections de mesures qui ont la même vue de source de données et ont le même sous-ensemble de dimensions du cube. Un groupe de mesures dispose d'une ou de plusieurs partitions pour gérer les données physiques. Un groupe de mesures peut avoir une conception d'agrégation par défaut. La conception d'agrégation par défaut peut être utilisée par toutes les partitions dans le groupe de mesures ; de plus, chaque partition peut avoir sa propre conception d'agrégation.  
  
 Objets Server  
 Chaque instance d'[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] est vue comme un objet serveur différent dans AMO (Analysis Management Objects) ; chaque instance différente est connectée à un objet <xref:Microsoft.AnalysisServices.Server> par une connexion différente. Chaque objet serveur contient une ou plusieurs sources de données, vues de source de données et objets de base de données, ainsi qu'assemblys et rôles de sécurité.  
  
 Objets Dimension  
 Chaque objet de base de données contient plusieurs objets de dimension. Chaque objet de dimension contient un ou plusieurs attributs, organisés en hiérarchies.  
  
 Objets de cube  
 Chaque objet de base de données contient un ou plusieurs objets de cube. Un cube est défini par ses mesures et ses dimensions. Les mesures et les dimensions d'un cube sont dérivées des tables et des vues de la vue de source de données sur laquelle est basé le cube ou qui est générée à partir des définitions des mesures et des dimensions.  
  
## <a name="object-inheritance"></a>Héritage d'objet  
 Le modèle objet ASSL contient de nombreux groupes d'éléments répétés. Par exemple, le groupe d’éléments « `Dimensions` contenir `Hierarchies` » définit la hiérarchie de dimension d’un élément. `Cubes` et `MeasureGroups` contiennent le groupe d'élément, « `Dimensions` contient `Hierarchies` ».  
  
 Sauf en cas de remplacement explicite, un élément hérite les détails de ces groupes d'éléments répétés du niveau supérieur. Par exemple, les `Translations` pour un `CubeDimension` sont les mêmes que `Translations` pour son élément ancêtre `Cube`.  
  
 Pour remplacer explicitement des propriétés héritées d'un objet de niveau supérieur, un objet n'a pas besoin de répéter explicitement la totalité de la structure et des propriétés de l'objet de niveau supérieur. Les seules propriétés qu'un objet doit déclarer explicitement sont les propriétés que l'objet souhaite remplacer. Par exemple, un `CubeDimension` peut lister uniquement les `Hierarchies` qui doivent être désactivés dans le `Cube`, ou dont la visibilité doit être changée, ou dont certains détails `Level` n'ont pas été fournis au niveau `Dimension`.  
  
 Quelques propriétés spécifiées sur un objet fournissent des valeurs par défaut pour la même propriété sur un objet enfant ou descendant. Par exemple, `Cube.StorageMode` fournit la valeur par défaut de `Partition.StorageMode`. Pour les valeurs par défaut héritées, ASSL applique les règles suivantes :  
  
-   Lorsque la propriété de l'objet enfant est NULL dans XML, la valeur de la propriété a comme valeur par défaut la valeur héritée. Toutefois, si vous interrogez le serveur à propos de la valeur, le serveur renvoie la valeur NULL de l'élément XML.  
  
-   Il n'est pas possible de déterminer par programme si la propriété d'un objet enfant a été définie directement sur l'objet enfant ou héritée.  
  
## <a name="example"></a>Exemple  
 Le cube Imports contient deux mesures, Packages et Last, ainsi que trois dimensions connexes, Route, Source et Time.  
  
 ![Exemple de cube 1](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/cubeintro1.gif "Exemple de cube 1")  
  
 Les petites valeurs alphanumériques autour du cube représentent les membres des dimensions. Les membres sont par exemple ground (membre de la dimension Route), Africa (membre de la dimension Source) et 1st quarter (membre de la dimension Time).  
  
### <a name="measures"></a>mesures  
 Les valeurs dans les cellules de cube représentent les deux mesures, Packages et Last. La mesure Packages représente le nombre de lots importés et la fonction `Sum` est utilisée pour agréger les faits. La mesure Last représente la date de réception et la fonction `Max` est utilisée pour agréger les faits.  
  
### <a name="dimensions"></a>Dimensions  
 La dimension Route représente le mode de transport par lequel les importations arrivent à destination. Les membres de cette dimension sont notamment ground, nonground, air, sea, road ou rail. La dimension Source représente les lieux de production des biens importés, par exemple Africa ou Asia. La dimension Time représente les trimestres et les semestres d'une année.  
  
### <a name="aggregates"></a>Agrégats  
 Les utilisateurs professionnels d'un cube peuvent déterminer les valeurs des mesures pour chaque membre de toutes les dimensions, quel que soit le niveau du membre dans la dimension, parce que [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] agrège les valeurs à des niveaux supérieurs s'il y a lieu. Par exemple, les valeurs de mesure de l’illustration précédente peuvent être agrégées en fonction d’une hiérarchie de calendrier standard à l’aide de la hiérarchie Calendar Time de la dimension Time, comme illustré dans le diagramme suivant.  
  
 ![Diagramme des mesures organisées selon la dimension de temps](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/cubeintro2.gif "Diagramme des mesures organisées selon la dimension de temps")  
  
 Outre l'agrégation au sein d'une même dimension, les mesures peuvent faire l'objet d'une agrégation combinant un nombre de membres appartenant à différentes dimensions. Cela permet aux utilisateurs professionnels d'évaluer les mesures dans plusieurs dimensions en même temps. Par exemple, si un utilisateur professionnel souhaite analyser les importations trimestrielles arrivées par voie aérienne en provenance des hémisphères Est (Eastern Hemisphere) et Ouest (Western Hemisphere), il peut exécuter une requête sur le cube pour extraire le dataset suivant.  
  
||||.|||Dernière|||  
|-|-|-|--------------|-|-|----------|-|-|  
||||All Sources|Eastern Hemisphere|Western Hemisphere|All Sources|Eastern Hemisphere|Western Hemisphere|  
|All Time|||25110|6547|18563|Dec-29-99|Dec-22-99|Dec-29-99|  
||1st half||11173|2977|8196|Jun-28-99|Juin-20-99|Jun-28-99|  
|||1st quarter|5108|1452|3656|Mar-30-99|Mar-19-99|Mar-30-99|  
|||2nd quarter|6065|1525|4540|Jun-28-99|Juin-20-99|Jun-28-99|  
||2nd half||13937|3570|10367|Dec-29-99|Dec-22-99|Dec-29-99|  
|||3rd quarter|6119|1444|4675|Sep-30-99|Sep-18-99|Sep-30-99|  
|||4th quarter|7818|2126|5692|Dec-29-99|Dec-22-99|Dec-29-99|  
  
 Après la création d'un cube, il est possible de définir de nouvelles agrégations ou de modifier les agrégations existantes pour définir des options qui déterminent si les agrégations sont précalculées durant le traitement ou calculées lors de l'exécution des requêtes. **Rubrique connexe :** [agrégations et conceptions d’agrégation](../../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md).  
  
### <a name="mapping-measures-attributes-and-hierarchies"></a>Mappage de mesures, d'attributs et de hiérarchies  
 Les mesures, les attributs et les hiérarchies dans l'exemple de cube sont dérivés des colonnes suivantes des tables de faits et de dimension du cube.  
  
|Mesure ou attribut (niveau)|Membres|Table source|Colonne source|Valeur de colonne exemple|  
|------------------------------------|-------------|------------------|-------------------|-------------------------|  
|Mesure Packages|Non applicable|ImportsFactTable|.|12|  
|Mesure Last|Non applicable|ImportsFactTable|Dernière|May-03-99|  
|Niveau Route Category dans la dimension Route|nonground,ground|RouteDimensionTable|Route_Category|Nonground|  
|Niveau Route dans la dimension Route|air,sea,road,rail|RouteDimensionTable|Itinéraire|Sea|  
|Attribut Hemisphere dans la dimension Source|Eastern Hemisphere,Western Hemisphere|SourceDimensionTable|Hemisphere|Eastern Hemisphere|  
|Attribut Continent dans la dimension Source|Afrique, Asie, AustraliaEurope, N. America,S. America|SourceDimensionTable|Continent|Europe|  
|Attribut Half dans la dimension Time|1st half,2nd half|TimeDimensionTable|Half|2nd half|  
|Attribut Quarter dans la dimension Time|1st quarter,2nd quarter,3rd quarter,4th quarter|TimeDimensionTable|Quarter|3rd quarter|  
  
 Les données d'une cellule de cube proviennent généralement de plusieurs lignes de la table de faits. Par exemple, la cellule de cube à l’intersection du membre air, du membre Africa et du membre 1er trimestre contient une valeur dérivée de l’agrégation des lignes suivantes dans la table de faits **ImportsFactTable** .  
  
|||||||  
|-|-|-|-|-|-|  
|Import_ReceiptKey|RouteKey|SourceKey|TimeKey|.|Dernière|  
|3516987|1|6|1|15|Jan-10-99|  
|3554790|1|6|1|40|Jan-19-99|  
|3572673|1|6|1|34|Jan-27-99|  
|3600974|1|6|1|45|Feb-02-99|  
|3645541|1|6|1|20|Feb-09-99|  
|3674906|1|6|1|36|Feb-17-99|  
  
 Dans le tableau précédent, chaque ligne a les mêmes valeurs pour les colonnes **itinéraire**, **sourceKey**et **TimeKey** , ce qui indique que ces lignes contribuent à la même cellule de cube.  
  
 L'exemple présenté ici concerne un cube très simple, qui n'a qu'un seul groupe de mesures et auquel toutes les tables de dimension sont jointes à la table de faits dans un schéma en étoile. Dans un autre schéma commun, appelé schéma en flocons, une ou plusieurs tables de dimension sont jointes à une autre table de dimension au lieu d'être jointes directement à la table de faits. **Rubrique connexe :** [dimensions &#40;Analysis Services-données&#41;multidimensionnelles](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md).  
  
 L'exemple présenté ici ne contient qu'une seule table de faits. Quand un cube a plusieurs tables de faits, les mesures de chaque table de faits sont organisées en groupes de mesures et un groupe de mesures est lié à un jeu de dimensions spécifique par des relations de dimension définies. Ces relations sont définies en spécifiant les tables participantes dans la vue de source de données et la granularité de la relation. **Rubrique connexe :** [relations de dimension](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bases de données de modèle multidimensionnel &#40;SSAS&#41;](../multidimensional-model-databases-ssas.md)  
  
  
