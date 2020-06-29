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
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85428129"
---
# <a name="string-padding-ssis"></a>Remplissage des chaînes (SSIS)
  L'évaluateur d'expression ne vérifie pas si une chaîne contient des espaces de début et de fin et ne complète pas les chaînes pour qu'elles aient la même longueur avant de les comparer. Pour compléter une chaîne dans une expression, vous pouvez concaténer des valeurs de colonne et des chaînes vides à l'aide de l'opérateur « + ». Pour plus d’informations, consultez [+ &#40;Concaténer&#41; &#40;expression SSIS&#41;](concatenate-ssis-expression.md).  
  
 Par contre, si vous souhaitez supprimer des espaces, l'évaluateur d'expression met à votre disposition les fonctions LTRIM, RTRIM et TRIM, qui permettent de supprimer les espaces de début et/ou de fin. Pour plus d’informations, consultez [LTRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md), [RTRIM &#40;Expression SSIS&#41;](rtrim-ssis-expression.md)[TRIM &#40;Expression SSIS&#41;](trim-ssis-expression.md).  
  
> [!NOTE]  
>  Le nombre de la fonction LEN inclut les espaces de début et de fin.  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), sur pragmaticworks.com  
  
  
