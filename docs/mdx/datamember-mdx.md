---
title: DataMember (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DATAMEMBER
dev_langs:
- kbMDX
helpviewer_keywords:
- DataMember function
ms.assetid: 65bf21e8-1cb2-4ae8-bfbe-bb4d72589557
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: efd0e3ec24c64d037db0e0d83c10b4371a850bb0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="datamember-mdx"></a>DataMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Retourne le membre de données générées par le système associé à un membre non-feuille d'une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Argument*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction fonctionne sur des membres non-feuille dans n’importe quelle hiérarchie et peut être utilisée par le [UPDATE CUBE Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) commande pour l’écriture différée des données à un membre non-feuille directement, plutôt qu’à des descendants du membre feuille.  
  
> [!NOTE]  
>  Retourne le membre spécifié si ce dernier est un membre feuille ou si le membre non-feuille n'est associé à aucun membre de données.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le **DataMember** fonction dans une mesure calculée pour afficher le quota de ventes pour chaque employé individuel :  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX & #40 ; MDX & #41 ;](../mdx/mdx-function-reference-mdx.md)   
 [Concepts clés dans MDX & #40 ; Analysis Services & #41 ;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)  
  
  
