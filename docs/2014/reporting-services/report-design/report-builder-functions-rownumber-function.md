---
title: Fonction RowNumber (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 150a46a736a9c6ddd2f8c394f3f173906cd07132
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042815"
---
# <a name="rownumber-function-report-builder-and-ssrs"></a>Fonction RowNumber (Générateur de rapports et SSRS)
  Retourne un nombre évolutif du nombre de lignes pour l'étendue spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RowNumber(scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *portée*  
 (`String`) Le nom d’un dataset, région de données, ou groupe ou null (`Nothing` dans [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), qui spécifie le contexte dans lequel évaluer le nombre de lignes. `Nothing` Spécifie le contexte le plus extérieur, habituellement le dataset de rapport.  
  
## <a name="remarks"></a>Notes  
 `RowNumber` Retourne une valeur d’exécution du nombre de lignes dans l’étendue spécifiée, tout comme [RunningValue](report-builder-functions-runningvalue-function.md) retourne la valeur en cours d’exécution d’une fonction d’agrégation. Lorsque vous spécifiez une étendue, vous spécifiez quand réinitialiser le nombre de lignes à 1.  
  
 *scope* ne peut pas être une expression. *scope* doit être une étendue contenante. Les étendues classiques, de la relation contenant-contenu le plus à l'extérieur à celle située le plus à l'intérieur, sont un dataset de rapport, une région de données, des groupes de lignes ou des groupes de colonnes.  
  
 Pour incrémenter des valeurs sur plusieurs colonnes, spécifiez comme étendue le nom d'un groupe de colonnes. Pour incrémenter des nombres en bas de lignes, spécifiez comme étendue le nom d'un groupe de lignes.  
  
> [!NOTE]  
>  L'inclusion d'agrégats qui spécifient un groupe de lignes et un groupe de colonnes dans une même expression n'est pas prise en charge.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Exemple de code  
 Voici une expression que vous pouvez utiliser pour le `BackgroundColor` propriété d’une ligne de détail de la région de données du tableau matriciel pour faire alterner la couleur des lignes de détails pour chaque groupe, en commençant toujours par le blanc.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  