---
description: Définition de données MDX - CREATE MEASURE
title: Instruction CREATe MEASURe (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: cdbee6f6ede5e46926f1a8189792d86cf9e99f5b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387265"
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
 Le *Measure_Name*  doit être placé entre parenthèses carrées.  
  
 L’instruction CREATe MEASURe ne peut être utilisée qu’à l’intérieur d’une définition de script MDX. consultez [MdxScript, élément &#40;&#41;ASSL ](https://docs.microsoft.com/analysis-services/assl/objects/mdxscript-element-assl?view=asallproducts-allversions).  
  
 Vous pouvez également définir un membre calculé qui ne doit être utilisé que par une requête unique. Pour définir un membre calculé limité à une seule requête, utilisez la clause WITH de l'instruction SELECT. Pour plus d’informations, consultez [génération de mesures dans MDX](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/mdx-building-measures).  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de définition de données MDX &#40;&#41;MDX ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
