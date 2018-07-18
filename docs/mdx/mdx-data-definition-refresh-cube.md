---
title: Instruction REFRESH CUBE (MDX) | Documents Microsoft
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dafc13dda1f8ecab1400a88d1ca66eff5f317e43
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741728"
---
# <a name="mdx-data-definition---refresh-cube"></a>Définition de données MDX - REFRESH CUBE


  Actualise le cache client pour un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui précise le nom d'un cube.  
  
## <a name="remarks"></a>Notes  
 Pour les applications clientes connectées à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], cette instruction provoque la mémoire mise en cache sur l’application cliente pour être synchronisé avec le serveur. Bien que cette situation soit d'ordinaire détectée et mise à jour automatiquement, la durée qui s'écoule avant qu'elle ne se produise dépend des paramètres de chaîne de connexion du client. L'instruction REFRESH CUBE actualise immédiatement les données.  
  
 Pour les applicaions clientes connectées à un cube local, l'instruction REFRESH CUBE déclenche la reconstruction du fichier de cube local.  
  
> [!IMPORTANT]  
>  Les jeux nommés stockés sur le serveur ne sont pas actualisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions MDX de définition de données &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
