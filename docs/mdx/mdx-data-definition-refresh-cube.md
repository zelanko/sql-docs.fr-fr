---
description: Définition de données MDX - REFRESH CUBE
title: Instruction REFRESH CUBE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 05ae95c97ae21d3b8ff7b4e457cf3ddf8cc38989
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387053"
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
 Pour les applications clientes connectées à une instance de [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , cette instruction provoque la synchronisation de la mémoire mise en cache sur l’application cliente avec le serveur. Bien que cette situation soit d'ordinaire détectée et mise à jour automatiquement, la durée qui s'écoule avant qu'elle ne se produise dépend des paramètres de chaîne de connexion du client. L'instruction REFRESH CUBE actualise immédiatement les données.  
  
 Pour les applicaions clientes connectées à un cube local, l'instruction REFRESH CUBE déclenche la reconstruction du fichier de cube local.  
  
> [!IMPORTANT]  
>  Les jeux nommés stockés sur le serveur ne sont pas actualisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;&#41;MDX ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
