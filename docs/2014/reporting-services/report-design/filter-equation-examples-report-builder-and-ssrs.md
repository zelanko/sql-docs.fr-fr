---
title: Exemples d’équations de filtre (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- filtering data [Reporting Services], filter equation examples
ms.assetid: 66bec93d-7c3b-4d4a-8cb6-7a7bb2f34ec6
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5b6302cc01b86d67d02f128d72f717cfebb97b46
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56292417"
---
# <a name="filter-equation-examples-report-builder-and-ssrs"></a>Exemples d'équations de filtre (Générateur de rapports et SSRS)
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
|`[OrderDate]`|`DateTime`|`>`|`2008-01-01`|Inclut toutes les dates du 1er janvier 2008 à la date du jour.|  
|`[OrderDate]`|`DateTime`|`BETWEEN`|`2008-01-01`<br /><br /> `2008-02-01`|Inclut les dates à partir du 1er janvier 2008 jusqu'au 1er février 2008 compris.|  
|`[Territory]`|`Text`|`LIKE`|`*east`|Tous les noms de secteurs qui se terminent par « est ».|  
|`[Territory]`|`Text`|`LIKE`|`%o%th*`|Tous les secteurs dont le nom commence par Nord et Sud.|  
|`=LEFT(Fields!Subcat.Value,1)`|`Text`|`IN`|`B, C, T`|Toutes les valeurs de sous-catégorie commençant par les lettres B, C ou T.|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md)   
 [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)  
  
  
