---
title: Fonction Previous (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 403a9384-6ca4-42e8-97ca-ac3f6fe4316b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e3e856bf37328c5abaf4edd5bf296c1d557a2be7
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59971645"
---
# <a name="previous-function-report-builder-and-ssrs"></a>Fonction Previous (Générateur de rapports et SSRS)
  Retourne la valeur ou la valeur d'agrégation spécifiée pour l'instance précédente d'un élément dans l'étendue spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Previous(expression, scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (`Variant` ou `Binary`) Expression à utiliser pour identifier les données et pour laquelle récupérer la valeur précédente, par exemple, `Fields!Fieldname.Value` ou `Sum(Fields!Fieldname.Value)`.  
  
 *portée*  
 (`String`) Facultatif. Le nom d’un groupe ou région de données ou null (`Nothing` dans [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), qui spécifie la portée à partir de laquelle récupérer la valeur précédente spécifiée par *expression*.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un `Variant` ou `Binary`.  
  
## <a name="remarks"></a>Notes  
 La fonction `Previous` retourne la valeur précédente de l'expression évaluée dans l'étendue spécifiée après que cette dernière a été correctement triée et filtrée.  
  
 Si *expression* ne contient pas d’agrégat, la `Previous` fonction des valeurs par défaut à l’étendue actuelle pour l’élément de rapport.  
  
 Dans le groupe de détails, utilisez `Previous` pour spécifier la valeur d'une référence de champ dans l'instance précédente de la ligne de détails.  
  
> [!NOTE]  
>  Le `Previous` fonction prend uniquement en charge les références de champ dans le groupe de détails. Par exemple, dans une zone de texte du groupe de détails, `=Previous(Fields!Quantity.Value)` retourne les données du champ `Quantity` de la ligne précédente. Cette expression dans la première ligne retourne une valeur Null (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]).  
  
 Si *expression* contient une fonction d’agrégation qui utilise une étendue par défaut, `Previous` agrège les données au sein de l’instance précédente de l’étendue spécifiée dans l’agrégat appel de fonction.  
  
 Si *expression* contient une fonction d’agrégation qui spécifie une portée différente de la valeur par défaut, le *étendue* paramètre pour le `Previous` fonction doit être une étendue contenante pour l’étendue spécifiée dans l’appel de fonction d’agrégation.  
  
 Les fonctions `Level`, `InScope`, `Aggregate` et `Previous` ne peut pas être utilisé dans le *expression*paramètre. La spécification du paramètre *recursive* pour une fonction d’agrégation n’est pas prise en charge.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple de code ci-dessous, quand il est placé sur la ligne de données par défaut d’une région de données, fournit la valeur du champ `LineTotal` de la ligne précédente.  
  
### <a name="code"></a>Code  
  
```  
=Previous(Fields!LineTotal.Value)  
```  
  
### <a name="description"></a>Description  
 L'exemple suivant montre une expression qui calcule la somme des ventes réalisées au cours d'un jour spécifique du mois et la valeur précédente pour le même jour du mois d'une année précédente. L’expression est ajoutée à une cellule d’une ligne qui appartient au groupe enfant `GroupbyDay`. Son groupe parent est `GroupbyMonth`, ayant lui-même le groupe parent `GroupbyYear`. L'expression affiche les résultats pour GroupbyDay (étendue par défaut), puis pour `GroupbyYear` (le parent du groupe parent `GroupbyMonth`).  
  
 Par exemple, pour une région de données avec un groupe parent nommé `Year`, son groupe enfant nommé `Month`et son groupe enfant nommé `Day` (3 niveaux imbriqués). L’expression `=Previous(Sum(Fields!Sales.Value,"Day"),"Year")` d’une ligne associée au groupe `Day` retourne la valeur des ventes réalisées le même jour du même mois de l’année précédente.  
  
### <a name="code"></a>Code  
  
```  
=Sum(Fields!Sales.Value) & " " & Previous(Sum(Fields!Sales.Value,"GroupbyDay"),"GroupbyYear")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
