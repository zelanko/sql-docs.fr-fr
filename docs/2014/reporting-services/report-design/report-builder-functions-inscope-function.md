---
title: Fonction InScope (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: e677c9e02f452a486b9168f15c662362640ea86e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36142961"
---
# <a name="inscope-function-report-builder-and-ssrs"></a>Fonction InScope (Générateur de rapports et SSRS)
  Indique si l'instance actuelle d'un élément se trouve dans l'étendue spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *portée*  
 (`String`) Le nom d’un dataset, une région de données ou un groupe qui spécifie une étendue.  
  
## <a name="return-type"></a>Type de retour  
 Retourne un `Boolean`.  
  
## <a name="remarks"></a>Notes  
 Le `InScope` fonction teste l’étendue de l’instance actuelle d’un élément de rapport pour l’appartenance dans l’étendue spécifiée par le *étendue*paramètre.  
  
 *Scope* ne peut pas être une expression.  
  
 Une utilisation typique de le `InScope` fonction est dans des régions de données qui ont dynamique étendue. Par exemple, `InScope` peut être utilisé dans un lien d’extraction dans des cellules d’une région de données pour fournir un autre rapport nom et différents ensembles de paramètres en fonction de l’utilisateur clique sur la cellule. En voici un exemple :  
  
-   L’expression suivante, utilisée comme nom de rapport dans un lien d’extraction, ouvre le rapport `ProductDetail` si l’utilisateur clique sur une cellule située dans le groupe `Month` et le rapport `ProductSummary` s’il clique sur une autre cellule.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   L’expression suivante, utilisée dans les `Omit` propriété d’un paramètre de rapport d’extraction, passe le paramètre au rapport cible uniquement si la cellule où vous avez cliquée est dans le `Product` groupe.  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous indique si l'instance actuelle de l'élément se trouve dans l'étendue du groupe, de la région de données ou du dataset `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  