---
title: Clé de la boîte de dialogue colonnes (Analysis Services - données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.dataitemCollection.f1
helpviewer_keywords:
- DataItem Collection dialog box
ms.assetid: 585f27f2-d5eb-4516-b29a-2084010b7d51
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6c67966895699c34d58a0527ea27c06e7cc05ed5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48049051"
---
# <a name="key-columns-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Colonnes clés (Analysis Services - Données multidimensionnelles)
  La boîte de dialogue **Colonnes clés** permet de modifier la propriété **KeyColumns** d’un attribut. Pour plus d’informations, consultez [Modifier la propriété KeyColumn d’un attribut](multidimensional-models/attribute-properties-modify-the-keycolumn-property.md).  
  
 **Pour afficher la boîte de dialogue colonnes clés**  
  
-   Dans [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], sélectionnez un attribut puis, dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection (**…**) associé à la propriété **KeyColumns** de cet attribut.  
  
## <a name="options"></a>Options  
 **Table source**  
 Sélectionnez la table source dont vous souhaitez sélectionner les colonnes clés. Vous pouvez sélectionner la table source à partir d'une liste de toutes les tables dans la vue de source de données.  
  
 **Colonnes disponibles**  
 Sélectionnez les colonnes que vous souhaitez utiliser comme colonnes clés. Vous pouvez sélectionner les colonnes qui n’ont pas encore été sélectionnées comme colonnes clés dans une liste de colonnes de la **Table source** spécifiée.  
  
 Pour ajouter les colonnes sélectionnées à la liste **Colonnes clés** , cliquez sur le bouton **>** .  
  
 **Colonnes clés**  
 Définissez l'ordre des colonnes clés sélectionnées. L'ordre des colonnes clés est important pour définir la clé composite correcte. Pour définir ou redéfinir l’ordre de la liste de colonnes clés, sélectionnez une colonne, puis cliquez sur les boutons **Haut** ou **Bas** .  
  
 Pour supprimer une colonne de la liste **Colonnes clés** , sélectionnez la colonne, puis cliquez sur le bouton **\<** .  
  
 **Monter**  
 Cliquez pour déplacer la colonne sélectionnée dans **Colonnes clés** d’une position vers le haut.  
  
> [!NOTE]  
>  Cette option est activée uniquement si la liste contient plusieurs colonnes et si une colonne est sélectionnée.  
  
 **Descendre**  
 Cliquez pour déplacer la colonne sélectionnée dans **Colonnes clés** d’une position vers le bas.  
  
> [!NOTE]  
>  Cette option est activée uniquement si la liste contient plusieurs colonnes et si une colonne est sélectionnée.  
  
 **>**  
 Cliquez pour ajouter une nouvelle colonne à la fin des colonnes répertoriées dans **Colonnes clés**.  
  
 **<**  
 Cliquez pour supprimer la colonne sélectionnée des colonnes répertoriées dans **Colonnes clés**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
