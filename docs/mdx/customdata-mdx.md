---
title: CustomData (MDX) | Documents Microsoft
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: EXISTS
dev_langs: kbMDX
helpviewer_keywords: Exists function
ms.assetid: 61d9f5a2-6f56-4179-a39b-317c8e0a2cdd
caps.latest.revision: "18"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5a9cb529cf70010c81f42adf42fdfe47e51054b3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="customdata-mdx"></a>CustomData (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur de la **CustomData** la propriété de chaîne de connexion s’il est défini ; sinon, **null**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CustomData()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Le **CustomData** fonction peut récupérer le **CustomData** propriété de chaîne de connexion et passer un paramètre à utiliser par les fonctions MDX (Multidimensional Expressions) et les instructions, telles que de configuration [UserName (MDX)](../mdx/username-mdx.md) et [instruction CALL (MDX)](../mdx/mdx-data-manipulation-call.md). Par exemple, cette fonction peut être utilisée dans une expression de la sécurité dynamique pour sélectionner les membres du jeu autorisé/refusé pour la valeur de chaîne dans le **CustomData** propriété de chaîne de connexion.  
  
## <a name="example"></a>Exemple  
 La requête suivante affiche la valeur retournée par la **CustomData** fonction dans une mesure calculée :  
  
```  
WITH MEMBER [Measures].CUSTOMDATADEMO AS CUSTOMDATA()  
SELECT [Measures].CUSTOMDATADEMO ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
