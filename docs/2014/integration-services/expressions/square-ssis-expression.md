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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a7b312453000aaf3862eef91c5c660ecf6ecb9cf
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52787231"
---
# <a name="square-ssis-expression"></a>SQUARE (expression SSIS)
  Renvoie le carré d'une expression numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SQUARE(numeric_expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_numérique*  
 Expression numérique d'un type de données numérique. Pour plus d’informations, consultez [Types de données Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="result-types"></a>Types de résultats  
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
  
  
