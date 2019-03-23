---
title: Remplissage des chaînes (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 069fa1deababf347d7c45b62952960f7535115bf
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58393805"
---
# <a name="string-padding-ssis"></a>Remplissage des chaînes (SSIS)
  L'évaluateur d'expression ne vérifie pas si une chaîne contient des espaces de début et de fin et ne complète pas les chaînes pour qu'elles aient la même longueur avant de les comparer. Pour compléter une chaîne dans une expression, vous pouvez concaténer des valeurs de colonne et des chaînes vides à l'aide de l'opérateur « + ». Pour plus d’informations, consultez [+ &#40;Concaténer&#41; &#40;expression SSIS&#41;](concatenate-ssis-expression.md).  
  
 Par contre, si vous souhaitez supprimer des espaces, l'évaluateur d'expression met à votre disposition les fonctions LTRIM, RTRIM et TRIM, qui permettent de supprimer les espaces de début et/ou de fin. Pour plus d’informations, consultez [LTRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md), [RTRIM &#40;Expression SSIS&#41;](rtrim-ssis-expression.md) [TRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md).  
  
> [!NOTE]  
>  Le nombre de la fonction LEN inclut les espaces de début et de fin.  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Cheat Sheet](https://go.microsoft.com/fwlink/?LinkId=217683), sur pragmaticworks.com  
  
  
