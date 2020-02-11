---
title: RTRIM (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- RTRIM function
- trailing blanks
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 53d9bfbb7418a3bc6727ccc7160a5364bac39f58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62768775"
---
# <a name="rtrim-ssis-expression"></a>RTRIM (expression SSIS)
  Renvoie une chaîne de caractères après la suppression des espaces de fin.  
  
> [!NOTE]  
>  La fonction RTRIM ne supprime pas les espaces blancs tels que les caractères de tabulation ou de saut de ligne. Le codage Unicode founit des points de code pour divers types d'espaces, mais cette fonction ne reconnaît que le point de code Unicode 0x0020. Ainsi, lorsque les chaînes du jeu de caractères codés sur deux octets (DBCS) sont converties en Unicode, elles peuvent comporter d'autres caractères d'espaces que 0x0020 si bien que la fonction ne peut pas les supprimer. Pour éliminer tout type d'espace, utilisez par exemple la méthode de suppression des espaces de fin (RTrim) de Microsoft Visual Basic .NET dans un script exécuté à partir du composant Script.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RTRIM(character expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression_caractère*  
 Expression de caractères dont les espaces doivent être supprimés.  
  
## <a name="result-types"></a>Types des résultats  
 DT_WSTR  
  
## <a name="remarks"></a>Notes  
 La fonction RTRIM n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *character_expression* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que RTRIM effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](cast-ssis-expression.md).  
  
 La fonction RTRIM renvoie un résultat NULL si l'argument est NULL.  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant supprime les espaces de fin d'un littéral de chaîne. Le résultat obtenu est «Hello».  
  
```  
RTRIM("Hello   ")  
```  
  
 L'exemple suivant supprime les espaces de fin d'une concaténation des colonnes **FirstName** et **LastName** .  
  
```  
RTRIM(FirstName + " " + LastName)  
```  
  
 L'exemple suivant supprime les espaces de fin de la variable **FirstName** .  
  
```  
RTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [LTRIM &#40;expression SSIS&#41;](trim-ssis-expression.md)   
 [TRIM &#40;expression SSIS&#41;](trim-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
