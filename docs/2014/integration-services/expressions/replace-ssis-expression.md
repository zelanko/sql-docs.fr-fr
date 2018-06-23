---
title: REPLACE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- replacing string expression
- REPLACE function
ms.assetid: a6837043-ea70-4c6a-9c7a-6868b02b2adc
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 7888b72ed7193a1c2910db06a70496ee30761903
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042055"
---
# <a name="replace-ssis-expression"></a>REPLACE (expression SSIS)
  Renvoie une expression de caractères après le remplacement d'une chaîne de caractères située dans l'expression par une autre chaîne de caractères ou une chaîne vide.  
  
> [!NOTE]  
>  La fonction REPLACE utilise habituellement des chaînes longues. Les conséquences de la troncation peuvent être gérées naturellement ou être à l'origine d'un avertissement ou d'un message d'erreur. Pour plus d’informations, consultez [Syntaxe &#40;SSIS&#41;](syntax-ssis.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REPLACE(character_expression,searchstring,replacementstring)  
```  
  
## <a name="arguments"></a>Arguments  
 *character_expression*  
 Expression de caractères valide où la fonction va effectuer la recherche.  
  
 *searchstring*  
 Expression de caractères valide recherchée par la fonction.  
  
 *replacementstring*  
 Expression de caractères valide qui est l'expression de remplacement.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La longueur de *searchstring* ne doit pas être égale à zéro.  
  
 La longueur de *replacementstring* peut être égale à zéro.  
  
 Les arguments *searchstring* et *replacementstring* peuvent utiliser des variables et des colonnes.  
  
 La fonction REPLACE est opérationnelle seulement avec le type de données DT_WSTR. Les arguments*character_expression1, character_expression2* et *character_expression3* qui représentent des littéraux de chaîne ou des colonnes de données du type de données DT_STR sont implicitement convertis dans le type de données DT_WSTR avant que la fonction REPLACE soit exécutée. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 La fonction REPLACE renvoie un résultat NULL si un argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant utilise un littéral de chaîne. Le résultat obtenu est « All Terrain Bike ».  
  
```  
REPLACE("Mountain Bike", "Mountain","All Terrain")  
```  
  
 L’exemple suivant supprime la chaîne « Bike » de la colonne **Product** .  
  
```  
REPLACE(Product, "Bike","")  
```  
  
 L’exemple suivant remplace des valeurs dans la colonne **DaysToManufacture** . La colonne a un type de données integer et l’expression comprend la conversion de **DaysToManufacture** vers le type de données DT_WSTR.  
  
```  
REPLACE((DT_WSTR,8)DaysToManufacture,"6","5")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [SOUS-chaîne &#40;Expression SSIS&#41;](substring-ssis-expression.md)   
 [Fonctions &#40;Expression SSIS&#41;](functions-ssis-expression.md)  
  
  