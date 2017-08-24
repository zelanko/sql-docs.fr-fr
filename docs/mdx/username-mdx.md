---
title: "Nom d’utilisateur (MDX) | Documents Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UserName
dev_langs:
- kbMDX
helpviewer_keywords:
- UserName function
ms.assetid: ecae549b-5c5e-4483-84e6-b713cd297d7e
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: e9d9dbf069eab4da9c06e1a387baba47a90c24c5
ms.contentlocale: fr-fr
ms.lasthandoff: 08/02/2017

---
# <a name="username-mdx"></a>UserName (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [Référence des fonctions MDX &#40; MDX &#41;](../mdx/mdx-function-reference-mdx.md)  
  
  

