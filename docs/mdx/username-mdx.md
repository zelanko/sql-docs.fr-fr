---
description: UserName (MDX)
title: Nom d’utilisateur (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 6fbcc17cc34c6f4353698b918d0ab5ee3dc55701
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341135"
---
# <a name="username-mdx"></a>UserName (MDX)


  Retourne le nom de domaine et le nom d'utilisateur de la connexion en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UserName [ ( ) ]  
```  
  
## <a name="remarks"></a>Notes  
 La valeur retournée est une chaîne affichée selon le format suivant :  
  
 *domain-name\user-name*  
  
## <a name="example"></a>Exemple  
 L'exemple ci-dessous retourne le nom de l'utilisateur qui exécute la requête.  
  
```  
WITH MEMBER Measures.x AS UserName  
SELECT Measures.x ON COLUMNS  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des fonctions MDX &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
