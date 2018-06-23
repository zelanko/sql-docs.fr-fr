---
title: Fonction Union (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c87e16fe-c12a-4c9d-a9df-7a94e229fd04
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 46d0ee10acb57e4553c176be34572fc7f6dd02d5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043532"
---
# <a name="union-function-report-builder-and-ssrs"></a>Fonction Union (Générateur de rapports et SSRS)
  Retourne l'union de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée dans l'étendue donnée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Union(expression, scope, recursive)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (`SqlGeometry` ou `SqlGeography`) expression sur laquelle effectuer l’agrégation.  
  
 *portée*  
 (`String`) Facultatif. Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
 *récursifs*  
 (**Type énuméré**) Facultatif. `Simple` (par défaut) ou `RdlRecursive`. Indique s'il faut effectuer l'agrégation de manière récursive.  
  
## <a name="return"></a>Return  
 Retourne un objet spatial, `SqlGeometry` ou `SqlGeography`, selon le type d'expression. Pour plus d’informations sur `SqlGeometry` et `SqlGeography` des types de données spatiales, consultez [vue d’ensemble des Types de données spatiales](../../relational-databases/spatial/spatial-data-types-overview.md).  
  
## <a name="remarks"></a>Notes  
 Le jeu de données spécifié dans l'expression doit avoir le même type de données.  
  
 La valeur du paramètre *scope* doit être une constante de chaîne et ne peut pas être une expression. Pour les agrégats externes ou les agrégats qui ne spécifient pas d'autres agrégats, le paramètre *scope* doit faire référence à l'étendue actuelle ou à une étendue contenante. Les étendues de dataset ne sont pas prises en charge. Pour les agrégats d'agrégats, les agrégats imbriqués peuvent spécifier une étendue enfant.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir `First`, `Last`, `Previous`, ou `RunningValue` fonctions.  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 Le tableau suivant présente des exemples de `SqlGeometry` expressions et `Union` expressions, affichées au format WKT (Well Known Text) pour les données spatiales de résultat.  
  
|Champ avec données spatiales|Exemple|Résultat de la fonction Union|  
|-----------------------------|-------------|------------------|  
|[PointLocation]|POINT(1 2)<br /><br /> POINT (3 4)|MULTIPOINT((1 2), (3 4))|  
|[PathDefinition]|LINESTRING(1 2, 3 4)<br /><br /> LINESTRING(5 6, 7 8)|MULTILINESTRING((7 8, 5 6), (3 4, 1 2))|  
|[PolygonDefinition]|POLYGON((1 2, 3 4, 5 2, 1 2))<br /><br /> POLYGON((-1 2, -3 4, -5 2, -1 2))|MULTIPOLYGON(((1 2, 5 2, 3 4, 1 2)), ((-5 2, -1 2, -3 4, -5 2)))|  
  
```  
=Union(Fields!PointLocation.Value)  
=Union(Fields!PathDefinition.Value)  
=Union(Fields!PolygonDefinition.Value, "Group1")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  