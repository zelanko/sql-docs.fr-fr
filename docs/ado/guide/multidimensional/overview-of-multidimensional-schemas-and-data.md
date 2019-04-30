---
title: Vue d’ensemble des données et des schémas multidimensionnels | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f06f62768637ebb48ffa6e1cfd2560ff3b53c383
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63194907"
---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Vue d’ensemble des données et des schémas multidimensionnels
## <a name="understanding-multidimensional-schemas"></a>Présentation des schémas multidimensionnels  
 L’objet de métadonnées central dans ADO MD est la *cube*, qui se compose d’un ensemble structuré de dimensions associées, hiérarchies, niveaux et membres.  
  
 Un *dimension* est une catégorie indépendante des données à partir de votre base de données multidimensionnelle à partir de vos entités métier. Une dimension contient généralement des éléments à utiliser comme critère de requête pour les mesures de la base de données.  
  
 Un *hiérarchie* est un chemin d’accès d’agrégation d’une dimension. Une dimension peut avoir plusieurs niveaux de granularité, qui ont des relations parent-enfant. Une hiérarchie définit la relation entre ces niveaux.  
  
 Un *niveau* est une étape d’agrégation dans une hiérarchie. Pour les dimensions avec plusieurs couches d’informations, chaque couche est un niveau.  
  
 Un *membre* est un élément de données dans une dimension. En règle générale, vous créez une légende ou décrivez une mesure de la base de données à l’aide de membres.  
  
 Les cubes sont représentés par [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) objets dans ADO MD. Dimensions, hiérarchies, niveaux et membres sont également représentés par leurs objets ADO MD correspondants : [Dimension](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [hiérarchie](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [niveau](../../../ado/reference/ado-md-api/level-object-ado-md.md), et [membre](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Dimensions  
 Les dimensions d’un cube dépendent de vos entités métier et les types de données à modéliser dans la base de données. En règle générale, chaque dimension est un point d’entrée indépendante ou d’un mécanisme de sélection des données.  
  
 Par exemple, un cube contenant des données de ventes a le des cinq dimensions suivantes : Vendeur, géographie, heure, produits et mesures. La dimension de mesures contient des valeurs de données de ventes réelles, tandis que les autres dimensions constituent des manières de classer et regrouper les valeurs de données de ventes.  
  
 La dimension Geography comprend l’ensemble suivant de membres :  
  
```console
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>Hierarchies  
 Hiérarchies définissent les manières dans lequel les niveaux d’une dimension peuvent être « remontées » ou regroupées. Une dimension peut avoir plusieurs hiérarchies. Il existe une hiérarchie naturelle dans la dimension Geography :  
  
### <a name="levels"></a>Levels  
 Dans l’exemple montre comment la dimension Géographie dans la figure précédente, chaque zone représente un niveau dans la hiérarchie.  
  
 Chaque niveau possède un jeu de membres, comme suit :  
  
-   Le monde `= {All}`  
  
-   Continents `= {North America, Europe}`  
  
-   Pays `= {Canada, USA, UK, Germany}`  
  
-   Régions `= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Villes `= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Membres  
 Les membres au niveau feuille d’une hiérarchie n’ont aucuns enfants, et membres au niveau racine n’ont aucun parent. Tous les autres membres ont au moins un parent et au moins un enfant. Par exemple, un parcours partiels de l’arborescence de la hiérarchie dans la dimension Geography génère les relations parent-enfant suivantes :  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 Les membres peuvent être consolidées dans une ou plusieurs hiérarchies par dimension. Envisagez une dimension de temps où il existe deux façons pour cumuler au niveau de l’année à partir du niveau de jours :  
  
 Cet exemple illustre également une autre caractéristique : Certains membres du niveau semaine de la hiérarchie année-semaine n’apparaissent pas dans n’importe quel niveau de la hiérarchie année-trimestre. Par conséquent, une hiérarchie ne devez pas inclure tous les membres d’une dimension.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO multidimensionnel (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Programmation avec ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Utilisation d’ADO avec ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Utilisation de données multidimensionnelles](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
