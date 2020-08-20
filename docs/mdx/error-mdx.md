---
description: Error (MDX)
title: Erreur (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f95ee71586f5571d91221fe8889198a44a1252b3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494922"
---
# <a name="error-mdx"></a>Error (MDX)


  Génère une erreur, et fournit éventuellement un message d'erreur spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>Arguments  
 *Error_Text*  
 Expression de chaîne valide contenant le message d'erreur à retourner.  
  
## <a name="examples"></a>Exemples  
 La requête suivante montre comment utiliser la fonction **Error** à l’intérieur d’une mesure calculée :  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
