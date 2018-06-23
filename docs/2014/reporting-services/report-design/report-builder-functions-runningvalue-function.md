---
title: Fonction RunningValue (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6bee2f15-0e69-49c8-9689-b04544063b1d
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 41f2345cf31347fba98448a02d4d3014b8883d73
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043535"
---
# <a name="runningvalue-function-report-builder-and-ssrs"></a>Fonction RunningValue (Générateur de rapports et SSRS)
  Retourne un agrégat cumulé de toutes les valeurs numériques non Null spécifiées par l'expression, évaluée pour l'étendue donnée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RunningValue(expression, function, scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 Expression sur laquelle effectuer l’agrégation, par exemple `[Quantity]`.  
  
 *function*  
 (`Enum`) Le nom de la fonction d’agrégation à appliquer à l’expression, par exemple, `Sum`. Cette fonction ne peut pas être `RunningValue`, `RowNumber`, ou `Aggregate`.  
  
 *portée*  
 (`String`) Constante de chaîne qui correspond au nom d'un dataset, d'une région de données ou d'un groupe, ou valeur Null (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), qui spécifie le contexte dans lequel évaluer l'agrégation. `Nothing` Spécifie le contexte le plus extérieur, habituellement le dataset de rapport.  
  
## <a name="return-type"></a>Type de retour  
 Déterminé par la fonction d'agrégation spécifiée dans le paramètre *function* .  
  
## <a name="remarks"></a>Notes  
 La valeur de `RunningValue` réinitialise à 0 pour chaque nouvelle instance de la portée. Si vous spécifiez un groupe, la valeur d'exécution est réinitialisée lorsque l'expression de groupe change. Si vous indiquez une région de données, le cumul est réinitialisé pour chaque nouvelle instance de la région de données. Si vous spécifiez un dataset, la valeur d'exécution n'est pas réinitialisée dans l'ensemble du dataset.  
  
 `RunningValue` ne peut pas être utilisé dans une expression de filtre ou de tri.  
  
 Le jeu des données pour lequel la valeur d'exécution est calculée doit avoir le même type de données. Pour convertir des données qui ont plusieurs types de données numériques vers le même type de données, utilisez les fonctions de conversion, comme `CInt`, `CDbl` ou `CDec`. Pour plus d'informations, consultez [Fonctions de conversion de types de données](http://go.microsoft.com/fwlink/?LinkId=96142).  
  
 *Scope* ne peut pas être une expression.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre Scope des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre Scope des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir `First`, `Last`, `Previous`, ou `RunningValue` fonctions.  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour calculer la valeur d'exécution du nombre de lignes, utilisez `RowNumber`. Pour plus d’informations, consultez [Fonction RowNumber &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-rownumber-function.md).  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="examples"></a>Exemples  
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
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  