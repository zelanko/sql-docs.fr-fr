---
title: "Chaîne de remplissage (SSIS) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2cf3de41a65e975c99c68d459c804f1195fa4cd7
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="string-padding-ssis"></a>Remplissage des chaînes (SSIS)
  L'évaluateur d'expression ne vérifie pas si une chaîne contient des espaces de début et de fin et ne complète pas les chaînes pour qu'elles aient la même longueur avant de les comparer. Pour compléter une chaîne dans une expression, vous pouvez concaténer des valeurs de colonne et des chaînes vides à l'aide de l'opérateur « + ». Pour plus d’informations, consultez [+ &#40;Concaténer&#41; &#40;expression SSIS&#41;](../../integration-services/expressions/concatenate-ssis-expression.md).  
  
 Par contre, si vous souhaitez supprimer des espaces, l'évaluateur d'expression met à votre disposition les fonctions LTRIM, RTRIM et TRIM, qui permettent de supprimer les espaces de début et/ou de fin. Pour plus d’informations, consultez [LTRIM &#40;Expression SSIS&#41;](../../integration-services/expressions/ltrim-ssis-expression.md), [RTRIM &#40;Expression SSIS&#41;](../../integration-services/expressions/rtrim-ssis-expression.md) [TRIM &#40;Expression SSIS&#41;](../../integration-services/expressions/trim-ssis-expression.md).  
  
> [!NOTE]  
>  Le nombre de la fonction LEN inclut les espaces de début et de fin.  
  
## <a name="related-content"></a>Contenu connexe  
 Article technique, [SSIS Expression Cheat Sheet](http://go.microsoft.com/fwlink/?LinkId=746575), sur pragmaticworks.com  
  
  
