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
manager: kfile
ms.openlocfilehash: 172915d99b231490cbdca24f70d1d38da27a1d3d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248322"
---
# <a name="customdata-mdx"></a>CustomData (MDX)


  Retourne la valeur de la **CustomData** la propriété de chaîne de connexion si défini ; sinon, **null**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Le **CustomData** fonction peut récupérer le **CustomData** propriété de chaîne de connexion et passer un paramètre utilisable par les fonctions MDX (Multidimensional Expressions) et les instructions, telles que de configuration [UserName (MDX)](../mdx/username-mdx.md) et [instruction CALL (MDX)](../mdx/mdx-data-manipulation-call.md). Par exemple, cette fonction peut être utilisée dans une expression de la sécurité dynamique pour sélectionner les membres du jeu autorisé/refusé pour la valeur de chaîne dans le **CustomData** propriété chaîne de connexion.  
  
## <a name="example"></a>Exemple  
 La requête suivante affiche la valeur retournée par la **CustomData** fonction dans une mesure calculée :  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
