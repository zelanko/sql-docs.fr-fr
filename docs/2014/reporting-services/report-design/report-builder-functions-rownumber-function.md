---
title: Fonction RowNumber (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9d718ba8-d323-49fb-aac8-e7013a117b75
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d4a06a24525b3d9d0c4e4a5f3f0b749a7db70261
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66105167"
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
 *scope*  
 (`String`) Nom d'un dataset, d'une région de données ou d'un groupe, ou valeur Null (`Nothing` en [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]), qui spécifie le contexte dans lequel évaluer le nombre de lignes. 
  `Nothing` spécifie le contexte le plus à l'extérieur, habituellement le dataset du rapport.  
  
## <a name="remarks"></a>Notes  
 `RowNumber`retourne une valeur d’exécution du nombre de lignes dans l’étendue spécifiée, tout comme [RunningValue](report-builder-functions-runningvalue-function.md) retourne la valeur d’exécution d’une fonction d’agrégation. Lorsque vous spécifiez une étendue, vous spécifiez quand réinitialiser le nombre de lignes à 1.  
  
 *scope* ne peut pas être une expression. *scope* doit être une étendue contenante. Les étendues classiques, de la relation contenant-contenu le plus à l'extérieur à celle située le plus à l'intérieur, sont un dataset de rapport, une région de données, des groupes de lignes ou des groupes de colonnes.  
  
 Pour incrémenter des valeurs sur plusieurs colonnes, spécifiez comme étendue le nom d'un groupe de colonnes. Pour incrémenter des nombres en bas de lignes, spécifiez comme étendue le nom d'un groupe de lignes.  
  
> [!NOTE]  
>  L'inclusion d'agrégats qui spécifient un groupe de lignes et un groupe de colonnes dans une même expression n'est pas prise en charge.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="code-example"></a>Exemple de code  
 L'exemple ci-dessous est une expression que vous pouvez utiliser pour la propriété `BackgroundColor` d'une ligne de détails de région de données de tableau matriciel pour faire alterner la couleur des lignes de détails de chaque groupe, en commençant toujours par le blanc.  
  
```  
=IIF(RowNumber("GroupbyCategory") Mod 2, "White", "PaleGreen")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
