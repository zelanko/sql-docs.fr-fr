---
title: SQUARE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQUARE
- square values
ms.assetid: cecf1bb2-3d55-40a6-9688-ed67bcc150b4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ea619cb05064788869e211b6cb5ef96cb4f7188d
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428130"
---
# <a name="square-ssis-expression"></a>SQUARE (expression SSIS)
  Renvoie le carré d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *numeric_expression*  
 Expression numérique d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types des résultats  
 DT_R8  
  
## <a name="remarks"></a>Notes  
 La fonction SQUARE renvoie un résultat NULL si l'argument est NULL.  
  
 L'argument est converti vers le type de données DT_R8 avant le calcul du carré.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le carré de 12. Le résultat retourné est 144.  
  
```  
SQUARE(12)  
```  
  
 L'exemple suivant renvoie le carré du résultat de la soustraction des valeurs de deux colonnes. Si **Value1** contient 12 et **Value2** contient 4, la fonction SQUARE retourne 64.  
  
```  
SQUARE(Value1 - Value2)  
```  
  
 L'exemple suivant renvoie la longueur du troisième côté d'un triangle rectangle en appliquant la fonction SQUARE à deux variables, puis en calculant la racine carrée de leur somme. Si la variable **Side1** a pour valeur 3 et que la variable **Side2** a pour valeur 4, la fonction SQRT renvoie 5.  
  
```  
SQRT(SQUARE(@Side1) + SQUARE(@Side2))  
```  
  
> [!NOTE]  
>  Dans les expressions, les noms de variables comportent toujours le préfixe \@.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
