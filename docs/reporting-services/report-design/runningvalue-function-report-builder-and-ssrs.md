---
title: "Fonction RunningValue (G&#233;n&#233;rateur de rapports et SSRS) | Microsoft Docs"
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
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
caps.latest.revision: 8
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# Fonction RunningValue (G&#233;n&#233;rateur de rapports et SSRS)
  Retourne un agrégat cumulé de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée pour l'étendue donnée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## Syntaxe  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### Paramètres  
 *expression*  
 Expression sur laquelle effectuer l’agrégation, par exemple `[Quantity]`.  
  
 *function*  
 (**Enum**) Nom de la fonction d’agrégation à appliquer à l’expression, par exemple **Sum**. Cette fonction ne peut pas être de type **RunningValue**, **RowNumber**ou **Aggregate**.  
  
 *portée*  
 (**String**) Constante de chaîne qui représente le nom d’un dataset, d’une région de données ou d’un groupe, ou Null (**Nothing** en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), qui spécifie le contexte dans lequel évaluer l’agrégation. **Nothing** spécifie le contexte le plus à l'extérieur, habituellement le dataset du rapport.  
  
## Type de retour  
 Déterminé par la fonction d'agrégation spécifiée dans le paramètre *function* .  
  
## Notes  
 La valeur de **RunningValue** se réinitialise à 0 pour chaque nouvelle instance de l'étendue. Si vous spécifiez un groupe, la valeur d'exécution est réinitialisée lorsque l'expression de groupe change. Si vous indiquez une région de données, le cumul est réinitialisé pour chaque nouvelle instance de la région de données. Si vous spécifiez un dataset, la valeur d'exécution n'est pas réinitialisée dans l'ensemble du dataset.  
  
 **RunningValue** ne peut pas être utilisé dans une expression de filtre ou de tri.  
  
 Le jeu des données pour lequel la valeur d'exécution est calculée doit avoir le même type de données. Pour convertir des données qui ont plusieurs types de données numériques en un même type de données, utilisez des fonctions de conversion telles que **CInt**, **CDbl** ou **CDec**. Pour plus d'informations, consultez [Fonctions de conversion de types de données](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 *Scope* ne peut pas être une expression.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre Scope des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre Scope des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir les fonctions **First**, **Last**, **Previous**ou **RunningValue** .  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour calculer la valeur d'exécution du nombre de lignes, utilisez **RowNumber**. Pour plus d’informations, consultez [Fonction RowNumber &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/rownumber-function-report-builder-and-ssrs.md).  
  
 Pour plus d’informations, consultez [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## Exemples  
 L'exemple de code suivant fournit le cumul du champ nommé `Cost` de l'étendue la plus à l'extérieur, à savoir le dataset.  
  
```  
=RunningValue(Fields!Cost.Value, Sum, Nothing)  
```  
  
 L'exemple de code suivant fournit le cumul du champ nommé `Score` dans le dataset nommé `DataSet1`.  
  
```  
=RunningValue(Fields!Score.Value,sum,"DataSet1")  
```  
  
 L'exemple de code suivant fournit le cumul du champ nommé `Traffic Charges` dans l'étendue la plus à l'extérieure.  
  
```  
=RunningValue(Fields!Traffic Charges.Value, Sum, Nothing)  
```  
  
## Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md)  
  
  