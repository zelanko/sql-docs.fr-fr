---
title: L’instruction CREATE MEASURE (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 37a8b8ef757184e7467c3551148c8c149bb45097
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63309094"
---
# <a name="mdx-data-definition---create-measure"></a>Définition de données MDX - CREATE MEASURE


  Crée une mesure dans un modèle tabulaire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE MEASURE Table_Name[Measure_Name] = DAX_Expression  
[; CREATE MEASURE ...n]  
  
```  
  
## <a name="arguments"></a>Arguments  
 *Table_Name*  
 Littéral de chaîne valide qui fournit le nom de la table dans laquelle la mesure sera créée.  
  
 *Measure_Name*  
 Littéral de chaîne valide qui précise le nom d'une mesure.  
  
 *DAX_Expression*  
 Expression DAX valide qui retourne une seule valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Le *Measure_Name* doit être placé entre crochets.  
  
 L’instruction CREATE MEASURE peut uniquement être utilisée à l’intérieur d’une définition de script MDX ; consultez [MdxScript élément &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/mdxscript-element-assl).  
  
 Vous pouvez également définir un membre calculé qui ne doit être utilisé que par une requête unique. Pour définir un membre calculé limité à une seule requête, utilisez la clause WITH de l'instruction SELECT. Pour plus d’informations, consultez [génération de mesures dans MDX](../analysis-services/multidimensional-models/mdx/mdx-building-measures.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
