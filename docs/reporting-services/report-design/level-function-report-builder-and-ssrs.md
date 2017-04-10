---
title: "Fonction Level (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 41235402-bb9e-4cb7-b91e-431e77db19cf
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Fonction Level (G&#233;n&#233;rateur de rapports et SSRS)
  Retourne le niveau de profondeur actuel d'une hiérarchie récursive.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Syntaxe  
  
```  
  
Level(scope)  
```  
  
#### Paramètres  
 *portée*  
 (**Chaîne**) (Facultatif). Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## Type de retour  
 Retourne un **Integer**. Si le paramètre *scope* spécifie un dataset ou une région de données, ou encore un regroupement non récursif (c’est-à-dire sans élément **Parent**), la fonction **Level** retourne 0. Si vous omettez le paramètre *scope* , elle retourne le niveau de l'étendue actuelle.  
  
## Notes  
 La valeur retournée par la fonction **Level** est une valeur de base zéro, c'est-à-dire que le premier niveau d'une hiérarchie est 0.  
  
 La fonction **Level** peut être utilisée pour appliquer un retrait dans une hiérarchie récursive, comme une liste d'employés.  
  
 Pour plus d’informations sur les hiérarchies récursives, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
##  Exemple  
 L'exemple de code ci-dessous indique le niveau de ligne dans le groupe Employees :  
  
```  
=Level("Employees")  
```  
  
## Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  