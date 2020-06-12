---
title: Boîte de dialogue modèle de nom de niveau (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542001"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Modèle de nom de niveau (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Modèle de nom de niveau** dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] pour créer un modèle de nom de niveau pour un attribut parent d'une dimension. Pour plus d’informations sur ces modèles de nom de niveau, consultez [Élément NamingTemplate &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Vous pouvez afficher la boîte de dialogue **modèle de nom de niveau** en cliquant sur le bouton de sélection (**...**) sur la `NamingTemplate` valeur d’une traduction pour un attribut dans le volet **Détails** des traductions de l’onglet **traductions** du **Concepteur de dimensions**.  
  
## <a name="options"></a>Options  
  
|Terme|Définition|  
|----------|----------------|  
|**Définissez le modèle de niveau**|Permet d'afficher une grille dans laquelle vous pouvez concevoir la hiérarchie propre aux niveaux inclus dans l'attribut parent. Cette grille comporte les colonnes suivantes :<br /><br /> **Level**: affiche la position ordinale du niveau pour lequel le nom spécifié dans **nom** est utilisé. Pour ajouter un nouveau modèle de nom pour un niveau, sélectionnez **Nom** sur la ligne qui contient un astérisque (\*) dans **Niveau**.<br /><br /> **Nom**: contient le modèle de nom utilisé pour le niveau indiqué dans **niveau**. Pour ajouter un espace réservé correspondant à la position ordinale du niveau dans le modèle de nom, ajoutez un seul astérisque (*). Pour ajouter un astérisque dans le nom créé par le modèle de nom, ajoutez deux astérisques ( \* \* ).|  
|**Effacer tout**|Permet de supprimer toutes les lignes issues de l'option **Définissez le modèle de niveau**.|  
|**Résultat**|Affiche le modèle de nom de niveau construit par la boîte de dialogue.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analysis Services les concepteurs et les boîtes de dialogue &#40;les données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Traductions &#40;concepteur de dimensions&#41; &#40;Analysis Services-données multidimensionnelles&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
