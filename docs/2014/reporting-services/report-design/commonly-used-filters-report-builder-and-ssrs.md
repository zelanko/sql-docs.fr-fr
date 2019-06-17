---
title: Filtres couramment utilisés (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- multivalued parameters [Reporting Services]
- single-valued parameters [Reporting Services]
- parameters [Reporting Services], multivalued
- valid values [Reporting Services]
ms.assetid: cb70d0cd-707b-4de5-b39f-e4eb57d316aa
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f807060994c2225dc1e6605344bbb3bd5d2709e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66106240"
---
# <a name="commonly-used-filters-report-builder-and-ssrs"></a>Filtres couramment utilisés (Générateur de rapports et SSRS)
  Pour créer un filtre, vous devez spécifier une ou plusieurs équations de filtre. Une équation de filtre comprend une expression, un type de données, un opérateur et une valeur. Cette rubrique donne des exemples de filtres couramment utilisés.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="filter-examples"></a>Exemples de filtres  
 Le tableau ci-dessous donne des exemples d'équations de filtre qui utilisent différents types de données et différent opérateurs. L'étendue de la comparaison est déterminée par l'élément de rapport pour lequel un filtre est défini. Par exemple, pour un filtre défini sur un dataset, **10 principaux %** représente les 10 premiers pour cent des valeurs dans le dataset ; pour un filtre défini sur un groupe, **10 principaux %** représente les 10 premiers pour cent des valeurs dans le groupe.  
  
|Expression simple|Type de données|Opérateur|Value|Description|  
|-----------------------|---------------|--------------|-----------|-----------------|  
|`[SUM(Quantity)]`|`Integer`|`>`|`7`|Inclut des valeurs de données supérieures à 7.|  
|`[SUM(Quantity)]`|`Integer`|`TOP N`|`10`|Inclut les 10 premières valeurs de données.|  
|`[SUM(Quantity)]`|`Integer`|`TOP %`|`20`|Inclut les 20 premiers pour cent des valeurs de données.|  
|`[Sales]`|`Text`|`>`|`=CDec(100)`|Inclut toutes les valeurs de type System.Decimal (types de données money SQL) supérieures à 100 $.|  
|`[OrderDate]`|`DateTime`|`>`|`2088-01-01`|Inclut toutes les dates du 1er janvier 2008 à la date du jour.|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|Inclut les dates à partir du 1er janvier 2008 jusqu'au 1er février 2008 compris.|  
|`[Territory]`|`Text`|`LIKE`|`*east`|Tous les noms de secteurs qui se terminent par « est ».|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|Tous les secteurs dont le nom commence par Nord et Sud.|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|Toutes les valeurs de sous-catégorie commençant par les lettres B, C ou T.|  
  
## <a name="examples-with-report-parameters"></a>Exemples avec des paramètres de rapport  
 Le tableau suivant fournit des exemples d'expressions de filtre comprenant une référence de paramètre à valeur unique ou à valeurs multiples.  
  
|Type de paramètre|Expression (de filtre)|Opérateur|Value|Type de données|  
|--------------------|---------------------------|--------------|-----------|---------------|  
|Valeur unique|`[EmployeeID]`|=|`[@EmployeeID]`|Entier|  
|Valeurs multiples|`[EmployeeID]`|IN|`[@EmployeeID]`|Entier|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)  
  
  
