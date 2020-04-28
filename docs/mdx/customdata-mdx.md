---
title: CustomData (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d2884e23cbee78acacdb72e386f0e99610e9629f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68135825"
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
  
  
