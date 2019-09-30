---
title: YEAR (expression SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c3583baedb1766944a89b9f4491c53a94a17f3fa
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71297302"
---
# <a name="year-ssis-expression"></a>YEAR (expression SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Renvoie un entier qui représente la partie année d'une date.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a>Arguments  
 *date*  
 Date à n'importe quel format de date.  
  
## <a name="result-types"></a>Types des résultats  
 DT_I4  
  
## <a name="remarks"></a>Notes  
 La fonction YEAR renvoie un résultat NULL si l'argument est NULL.  
  
 Un littéral de date doit être explicitement converti dans l'un des types de données date. Pour plus d’informations, consultez [Types de données Integration Services](../../integration-services/data-flow/integration-services-data-types.md).  
  
> [!NOTE]  
>  La validation de l'expression échoue lorsqu'un littéral de date est explicitement converti en un des types de données de date suivants : DT_DBTIMESTAMPOFFSET et DT_DBTIMESTAMP2.  
  
 L'utilisation de la fonction YEAR est plus directe mais elle est équivalente à celle de la fonction DATEPART("Year", date).  
  
## <a name="expression-examples"></a>Exemples d'expressions  
 Cet exemple renvoie le nombre représentant l'année dans un littéral de date. Si le format de la date est « mm/jj/aaaa », l'exemple renvoie « 2002 ».  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 L’exemple suivant renvoie l’entier qui représente l’année dans la colonne **ModifiedDate** .  
  
```  
YEAR(ModifiedDate)  
```  
  
 L'exemple suivant renvoie l'entier qui représente l'année de la date actuelle.  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DATEADD &#40;expression SSIS&#41;](../../integration-services/expressions/dateadd-ssis-expression.md)   
 [DATEDIFF &#40;expression SSIS&#41;](../../integration-services/expressions/datediff-ssis-expression.md)   
 [DATEPART &#40;expression SSIS&#41;](../../integration-services/expressions/datepart-ssis-expression.md)   
 [DAY &#40;expression SSIS&#41;](../../integration-services/expressions/day-ssis-expression.md)   
 [MONTH &#40;expression SSIS&#41;](../../integration-services/expressions/month-ssis-expression.md)   
 [Fonctions &#40;expression SSIS&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
