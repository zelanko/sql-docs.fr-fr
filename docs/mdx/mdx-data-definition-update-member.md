---
title: Instruction UPDATE MEMBER (MDX) | Documents Microsoft
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
- UPDATE_MEMBER
- UPDATE MEMBER
- MEMBER
- UPDATE
helpviewer_keywords:
- calculated members [MDX]
- UPDATE MEMBER statement
ms.assetid: 07ab708d-d165-4fb1-a9f9-fb8197ff0dab
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 6f5591eeaaa2afd346e8038426f72e9b0c21520c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-data-definition---update-member"></a>Définition de données MDX - membre de la mise à jour
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
  
 *Property_name*  
 Chaîne valide qui spécifie le nom d'une propriété de membre calculé.  
  
 *Nom*  
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
|FORMAT_STRING|A [!INCLUDE[msCoName](../includes/msconame-md.md)] chaîne de format de style Office que l’application cliente peut utiliser pour afficher les valeurs de cellule.|  
|VISIBLE|Valeur qui indique si le membre calculé est visible dans un ensemble de lignes de schéma. Calculés visibles membres peuvent être ajoutés à un jeu à le [AddCalculatedMembers](../mdx/addcalculatedmembers-mdx.md) (fonction). Une valeur autre que zéro indique que le membre calculé est visible. La valeur par défaut de cette propriété est *Visible*.<br /><br /> Les membres calculés qui ne sont pas visibles sont généralement utilisés comme étapes intermédiaires dans des membres calculés plus complexes. Ces membres calculés peuvent également être référencés par d'autres types de membres, tels que des mesures.|  
|NON_EMPTY_BEHAVIOR|Mesure ou jeu utilisé par MDX pour déterminer le comportement des membres calculés lors de la résolution des cellules vides.|  
|CAPTION|Valeur de chaîne qui spécifie la légende que l'application cliente utilise pour afficher le membre.|  
|DISPLAY_FOLDER|Valeur de chaîne qui spécifie le chemin d'accès au dossier d'affichage dans lequel l'application cliente doit afficher le membre. Le séparateur de niveau de dossier est défini par l'application cliente. Pour les outils et les clients fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], la barre oblique inverse (\\) comme séparateur de niveau. Pour fournir plusieurs dossiers d'affichage à un membre défini, utilisez un point-virgule (;) pour séparer les dossiers.|  
|ASSOCIATED_MEASURE_GROUP|Nom du groupe de mesures auquel ce membre est associé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction de membre DROP &#40;MDX&#41;](../mdx/mdx-data-definition-drop-member.md)   
 [CRÉER une instruction MEMBER & #40 ; MDX & #41 ;](../mdx/mdx-data-definition-create-member.md)   
 [Instructions MDX de définition de données &#40;MDX&#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
