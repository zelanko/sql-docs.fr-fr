---
description: ISNULL (expression SSIS)
title: ISNULL (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e166a88cf5f1f9b1c5c3d54f80e5367efe4ee90d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88425491"
---
# <a name="isnull-ssis-expression"></a>ISNULL (expression SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  Renvoie une valeur booléenne basée sur le test du caractère NULL d'une expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>Arguments  
 *expression*  
 Expression valide d'un type de données quelconque.  
  
## <a name="result-types"></a>Types des résultats  
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
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  
