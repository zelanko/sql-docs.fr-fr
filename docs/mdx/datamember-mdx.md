---
description: DataMember (MDX)
title: DataMember (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ea373dc4ffe7eb01b19969288afce45489ab4e8c
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92196033"
---
# <a name="datamember-mdx"></a>DataMember (MDX)


  Retourne le membre de données générées par le système associé à un membre non-feuille d'une dimension.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Member_Expression.DataMember  
```  
  
## <a name="arguments"></a>Arguments  
 *Member_Expression*  
 Expression MDX (Multidimensional Expressions) valide qui retourne un membre.  
  
## <a name="remarks"></a>Notes  
 Cette fonction opère sur des membres non-feuille dans n’importe quelle hiérarchie et peut être utilisée par la commande [Update cube Statement (MDX)](../mdx/mdx-data-manipulation-update-cube.md) pour l’écriture différée des données vers un membre non-feuille directement, plutôt que vers les descendants du membre feuille.  
  
> [!NOTE]  
>  Retourne le membre spécifié si ce dernier est un membre feuille ou si le membre non-feuille n'est associé à aucun membre de données.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la fonction **DataMember** dans une mesure calculée pour afficher le quota de ventes pour chaque employé individuel :  
  
```  
WITH MEMBER measures.InvidualQuota AS   
([Employee].[Employees].currentmember.datamember, [Measures].[Sales Amount Quota])  
,FORMAT_STRING='Currency'  
SELECT {[Measures].[Sales Amount Quota],[Measures].InvidualQuota} ON COLUMNS,  
[Employee].[Employees].MEMBERS ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des fonctions MDX &#40;&#41;MDX ](../mdx/mdx-function-reference-mdx.md)   
 [Concepts clés de MDX &#40;Analysis Services&#41;](/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)  
  
