---
title: "RTRIM (expression SSIS) | Microsoft Docs"
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
  - "RTRIM (fonction)"
  - "espaces à droite"
ms.assetid: 529bd43e-3f8a-4682-a33e-569176aa7fc4
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# RTRIM (expression SSIS)
  Renvoie une chaîne de caractères après la suppression des espaces de fin.  
  
> [!NOTE]  
>  La fonction RTRIM ne supprime pas les espaces blancs tels que les caractères de tabulation ou de saut de ligne. Le codage Unicode founit des points de code pour divers types d'espaces, mais cette fonction ne reconnaît que le point de code Unicode 0x0020. Ainsi, lorsque les chaînes du jeu de caractères codés sur deux octets (DBCS) sont converties en Unicode, elles peuvent comporter d'autres caractères d'espaces que 0x0020 si bien que la fonction ne peut pas les supprimer. Pour éliminer tout type d'espace, utilisez par exemple la méthode de suppression des espaces de fin (RTrim) de Microsoft Visual Basic .NET dans un script exécuté à partir du composant Script.  
  
## Syntaxe  
  
```  
  
RTRIM(character expression)  
```  
  
## Arguments  
 *character_expression*  
 Expression de caractères dont les espaces doivent être supprimés.  
  
## Types des résultats  
 DT_WSTR  
  
## Notes  
 La fonction RTRIM n'est opérationnelle qu'avec le type de données DT_WSTR. Un argument *character_expression* qui est un littéral de chaîne ou une colonne de données avec le type de données DT_STR est implicitement converti dans le type de données DT_WSTR avant que RTRIM effectue son opération. Les autres types de données doivent être explicitement convertis vers le type de données DT_WSTR. Pour plus d’informations, consultez [Types de données d’Integration Services](../../integration-services/data-flow/integration-services-data-types.md) et [Cast &#40;expression SSIS&#41;](../../integration-services/expressions/cast-ssis-expression.md).  
  
 La fonction RTRIM renvoie un résultat NULL si l'argument est NULL.  
  
## Exemples d'expressions  
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
  
## Voir aussi  
 [LTRIM &#40;expression SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md)   
 [TRIM &#40;expression SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  