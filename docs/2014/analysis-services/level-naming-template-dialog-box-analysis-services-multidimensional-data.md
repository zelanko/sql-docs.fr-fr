---
title: Au niveau de la boîte de dialogue de modèle (Analysis Services - données multidimensionnelles) nom | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
caps.latest.revision: 20
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 89d70fcd6092b2ef06e8b28c97a5935f8fb17f88
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257425"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Modèle de nom de niveau (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Modèle de nom de niveau** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer un modèle de nom de niveau pour un attribut parent d'une dimension. Pour plus d’informations sur ces modèles de nom de niveau, consultez [Élément NamingTemplate &#40;ASSL&#41;](scripting/properties/namingtemplate-element-assl.md). Vous pouvez afficher le **modèle d’affectation de noms de niveau** boîte de dialogue en cliquant sur le bouton de sélection (**...** ) sur le `NamingTemplate` valeur d’une traduction pour un attribut dans le **détails des traductions** volet sur le **traductions** onglet de **Concepteur de dimensions**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Définir le modèle de niveau**|Permet d'afficher une grille dans laquelle vous pouvez concevoir la hiérarchie propre aux niveaux inclus dans l'attribut parent. Cette grille comporte les colonnes suivantes :<br /><br /> **Niveau**: affiche la position ordinale du niveau pour lequel le nom spécifié dans **nom** est utilisé. Pour ajouter un nouveau modèle de nom pour un niveau, sélectionnez **Nom** sur la ligne qui contient un astérisque (\*) dans **Niveau**.<br /><br /> **Nom**: contient le modèle d’affectation de noms utilisé pour le niveau indiqué dans **niveau**. Pour ajouter un espace réservé correspondant à la position ordinale du niveau dans le modèle de nom, ajoutez un seul astérisque (*). Pour ajouter un astérisque en tant que partie du nom créé par le modèle d’affectation de noms, ajoutez deux astérisques (\*\*).|  
|**Effacer tout**|Permet de supprimer toutes les lignes issues de l'option **Définissez le modèle de niveau**.|  
|**Result**|Affiche le modèle de nom de niveau construit par la boîte de dialogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Traductions &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
