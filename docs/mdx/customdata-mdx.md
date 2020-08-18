---
description: CustomData (MDX)
title: CustomData (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ed7bfe2841caf9bd5b2c6e6caf102323db6d62ed
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88413165"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  Retourne la valeur de la propriété de chaîne de connexion **CustomData** si elle est définie ; Sinon, **null**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 La fonction **CustomData** peut récupérer la propriété de chaîne de connexion **CustomData** et transmettre un paramètre de configuration à utiliser par les fonctions et les instructions MDX (Multidimensional Expressions), telles que [username (MDX)](../mdx/username-mdx.md) et [Call Statement (MDX)](../mdx/mdx-data-manipulation-call.md). Par exemple, cette fonction peut être utilisée dans une expression de sécurité dynamique pour sélectionner les membres de jeu autorisés/refusés pour la valeur de chaîne dans la propriété de chaîne de connexion **CustomData** .  
  
## <a name="example"></a>Exemple  
 La requête suivante affiche la valeur retournée par la fonction **CustomData** dans une mesure calculée :  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
