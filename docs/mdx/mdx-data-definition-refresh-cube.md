---
title: Instruction REFRESH CUBE (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Cube
- REFRESH CUBE
- REFRESH_CUBE
- REFRESH
dev_langs:
- kbMDX
helpviewer_keywords:
- cubes [Analysis Services], cache
- refreshing cache
- REFRESH CUBE statement
- cache [Analysis Services]
ms.assetid: b8c087fb-5d17-4b13-b7cf-9929e9aab35c
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 47bb32f3319e4e184637c3b816f10ca563d6c76d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---refresh-cube"></a>Définition de données MDX - REFRESH CUBE
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Actualise le cache client pour un cube.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
REFRESH CUBECube_Name   
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui précise le nom d'un cube.  
  
## <a name="remarks"></a>Notes  
 Pour les applications clientes connectées à une instance de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], cette instruction provoque la mémoire mise en cache sur l’application cliente pour être synchronisé avec le serveur. Bien que cette situation soit d'ordinaire détectée et mise à jour automatiquement, la durée qui s'écoule avant qu'elle ne se produise dépend des paramètres de chaîne de connexion du client. L'instruction REFRESH CUBE actualise immédiatement les données.  
  
 Pour les applicaions clientes connectées à un cube local, l'instruction REFRESH CUBE déclenche la reconstruction du fichier de cube local.  
  
> [!IMPORTANT]  
>  Les jeux nommés stockés sur le serveur ne sont pas actualisés.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions MDX de définition de données &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
