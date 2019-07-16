---
title: UserName (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f1ebb5dc504b799575b2ccf9e47368e4e6511dac
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097273"
---
# <a name="username-mdx"></a>UserName (MDX)


  Retourne le nom de domaine et le nom d'utilisateur de la connexion en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Notes  
 La valeur retournée est une chaîne affichée selon le format suivant :  
  
 *nom de domaine\nom d’utilisateur de domaine*  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le nom de l'utilisateur qui exécute la requête.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
