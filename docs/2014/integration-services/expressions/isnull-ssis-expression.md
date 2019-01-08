---
title: ISNULL (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 133162f206819fa3dae00ff6e91072ffc8b7140c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52805121"
---
# <a name="isnull-ssis-expression"></a>ISNULL (expression SSIS)
  Renvoie une valeur booléenne basée sur le test du caractère NULL d'une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression valide d'un type de données quelconque.  
  
## <a name="result-types"></a>Types de résultats  
 DT_BOOL  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie TRUE si la colonne **DiscontinuedDate** contient une valeur NULL.  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 L'exemple suivant renvoie « Unknown last name » si la valeur de la colonne **LastName** est NULL, sinon il renvoie la valeur de **LastName**.  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 L'exemple suivant renvoie toujours TRUE si la colonne **DaysToManufacture** est NULL, quelle que soit la valeur de la variable **AddDays**.  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
