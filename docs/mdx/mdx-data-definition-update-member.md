---
description: Définition de données MDX - UPDATE MEMBER
title: Instruction UPDATE MEMBER (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 3b1333a8784ea5427dec3ed7223a3c7c1a09120d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88387063"
---
# <a name="mdx-data-definition---update-member"></a>Définition de données MDX - UPDATE MEMBER


  Met à jour un membre calculé existant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UPDATE MEMBER Cube_Name.Member_Name   
   AS MDX_Expression  
      [,Property_Name = Property_Value, ...n]  
......[,SCOPE_ISOLATION = CUBE]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Chaîne valide qui spécifie le nom du cube qui contient le membre.  
  
 *Member_Name*  
 Chaîne valide qui spécifie le nom d'un membre existant.  
  
 *MDX_Expression*  
 Expression MDX (Multidimensional Expressions) valide pour laquelle le membre doit être mis à jour.  
  
 *Property_Name*  
 Chaîne valide qui spécifie le nom d'une propriété de membre calculé.  
  
 *Property_Value*  
 Expression scalaire valide qui spécifie la valeur de propriété du membre calculé.  
  
## <a name="remarks"></a>Notes  
 L'instruction UPDATE MEMBER met à jour un membre calculé existant tout en conservant la priorité relative de ce membre par rapport aux autres calculs. Par conséquent, vous ne pouvez pas utiliser l'instruction UPDATE MEMBER pour modifier SOLVEORDER.  
  
 Une instruction UPDATE MEMBER ne peut pas être spécifiée dans le script MDX pour un cube.  
  
 La spécification d'un cube autre que le cube actuellement connecté génère une erreur. C'est pourquoi vous devez utiliser CURRENTCUBE de préférence à un nom de cube, pour désigner le cube actuel.  
  
 Pour de plus amples informations sur les propriétés de membre définies par OLE DB, reportez-vous à la documentation qui l'accompagne.  
  
## <a name="standard-properties"></a>Propriétés standard  
 Chaque membre possède un jeu de propriétés par défaut. Le tableau suivant répertorie ces propriétés par défaut.  
  
|Identificateur de propriété|Signification|  
|-------------------------|-------------|  
|FORMAT_STRING|Chaîne de format de style Office que l’application cliente peut utiliser pour afficher les valeurs des cellules.|  
|VISIBLE|Valeur qui indique si le membre calculé est visible dans un ensemble de lignes de schéma. Les membres calculés visibles peuvent être ajoutés à un ensemble à l’aide de la fonction [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) . Une valeur autre que zéro indique que le membre calculé est visible. La valeur par défaut de cette propriété est *visible*.<br /><br /> Les membres calculés qui ne sont pas visibles sont généralement utilisés comme étapes intermédiaires dans des membres calculés plus complexes. Ces membres calculés peuvent également être référencés par d'autres types de membres, tels que des mesures.|  
|NON_EMPTY_BEHAVIOR|Mesure ou jeu utilisé par MDX pour déterminer le comportement des membres calculés lors de la résolution des cellules vides.|  
|CAPTION|Valeur de chaîne qui spécifie la légende que l'application cliente utilise pour afficher le membre.|  
|DISPLAY_FOLDER|Valeur de chaîne qui spécifie le chemin d'accès au dossier d'affichage dans lequel l'application cliente doit afficher le membre. Le séparateur de niveau de dossier est défini par l'application cliente. Pour les outils et clients fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , la barre oblique inverse () est le \\ séparateur de niveau. Pour fournir plusieurs dossiers d'affichage à un membre défini, utilisez un point-virgule (;) pour séparer les dossiers.|  
|ASSOCIATED_MEASURE_GROUP|Nom du groupe de mesures auquel ce membre est associé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction DROP MEMBER &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [Instruction CREATe MEMBER &#40;MDX&#41;](../mdx/mdx-data-definition-create-member.md)   
 [Instructions de définition de données MDX &#40;&#41;MDX ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
