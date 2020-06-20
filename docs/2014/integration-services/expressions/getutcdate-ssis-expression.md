---
title: GETUTCDATE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 8a124f6149a56240b62f72e06281ebbc1405d9e3
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84966599"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (expression SSIS)
  Renvoie la date actuelle du système en temps UTC (Universal Time Coordinate ou Greenwich Mean Time) au format DT_DBTIMESTAMP. La fonction GETUTCDATE ne comprend aucun argument.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="result-types"></a>Types des résultats  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie l'année de la date actuelle en temps UTC.  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 L’exemple suivant retourne le nombre de jours entre une date de la colonne **ModifiedDate** et la date UTC actuelle.  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 L'exemple suivant ajoute trois mois à la date UTC actuelle.  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GETDATE &#40;expression SSIS&#41;](getdate-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](functions-ssis-expression.md)  
  
  
