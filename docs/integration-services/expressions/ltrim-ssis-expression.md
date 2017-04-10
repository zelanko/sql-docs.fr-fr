---
title: "LTRIM (expression SSIS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "espaces à gauche"
  - "LTRIM (fonction)"
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
caps.latest.revision: 33
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 33
---
# LTRIM (expression SSIS)
  Renvoie une chaîne de caractères après avoir supprimé les espaces de début.  
  
> [!NOTE]  
>  La fonction LTRIM ne supprime pas les espaces blancs tels que les caractères de tabulation ou de saut de ligne. Le codage Unicode founit des points de code pour divers types d'espaces, mais cette fonction ne reconnaît que le point de code Unicode 0x0020. Ainsi, lorsque les chaînes du jeu de caractères codés sur deux octets (DBCS) sont converties en Unicode, elles peuvent comporter d'autres caractères d'espaces que 0x0020 si bien que la fonction ne peut pas les supprimer. Pour éliminer tout type d'espace, utilisez par exemple la méthode de suppression des espaces de début (LTrim) de Microsoft Visual Basic .NET dans un script exécuté à partir du composant Script.  
  
## Syntaxe  
  
```  
  
LTRIM(character expression)  
```  
  
## Arguments  
 *expression_caractère*  
 Expression de caractères dont les espaces doivent être supprimés.  
  
## Types des résultats  
 DT_WSTR  
  
## Notes  
 La fonction LTRIM n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *expression_caractères* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que LTRIM effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 La fonction LTRIM renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
 L'exemple suivant supprime les espaces de début d'un littéral de chaîne. Le résultat obtenu est «Hello».  
  
```  
LTRIM("    Hello")  
```  
  
 L'exemple suivant supprime les espaces de début de la colonne **FirstName** .  
  
```  
LTRIM(FirstName)  
```  
  
 L'exemple suivant supprime les espaces de début de la variable **FirstName** .  
  
```  
LTRIM(@FirstName)  
```  
  
## Voir aussi  
 [RTRIM &#40;expression SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [TRIM &#40;expression SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  