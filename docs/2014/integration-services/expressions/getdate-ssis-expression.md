---
title: GETDATE (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- current date
- GETDATE function
- dates [Integration Services], GETDATE
ms.assetid: 6d20ec93-3244-4d63-baf6-70eff7bd598c
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ed8a87ea53054aff7db3ed5461c0074244ee97db
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166860"
---
# <a name="getdate-ssis-expression"></a>GETDATE (expression SSIS)
  Renvoie la date actuelle du système dans un format DT_DBTIMESTAMP. La fonction GETDATE ne prend aucun argument.  
  
> [!NOTE]  
>  La fonction GETDATE retourne un résultat d'une longueur de 29 caractères.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
GETDATE()  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="result-types"></a>Types de résultats  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 L'exemple suivant renvoie l'année de la date actuelle.  
  
```  
DATEPART("year",GETDATE())  
```  
  
 L’exemple suivant renvoie le nombre de jours entre une date de la colonne **ModifiedDate** et la date actuelle.  
  
```  
DATEDIFF("dd",ModifiedDate,GETDATE())  
```  
  
 L'exemple suivant ajoute trois mois à la date actuelle.  
  
```  
DATEADD("Month",3,GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [GETUTCDATE &#40;SSIS Expression&#41;](getutcdate-ssis-expression.md)   
 [Fonctions &#40;SSIS Expression&#41;](functions-ssis-expression.md)  
  
  
