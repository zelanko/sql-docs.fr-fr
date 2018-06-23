---
title: Boîte de dialogue liaisons de groupe de mesures (Analysis Services - données multidimensionnelles) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.measuregroupbindings.f1
helpviewer_keywords:
- Measure Group Bindings dialog box
ms.assetid: ed642780-5350-438e-af73-b9ceab3f876d
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 1508624a9d0e5a9f36c8ec7c15093f56b37977ea
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152015"
---
# <a name="measure-group-bindings-dialog-box-analysis-services---multidimensional-data"></a>Boîte de dialogue Liaisons des groupes de mesures (Analysis Services - Données multidimensionnelles)
  Utilisez la boîte de dialogue **Liaisons des groupes de mesures** pour créer et modifier des relations directes entre des attributs non granulaires d’une dimension d’un cube et les colonnes d’un groupe de mesures. Elle permet également de spécifier des options de traitement des valeurs NULL pour tout attribut dans une dimension d’un cube, à partir de la boîte de dialogue **Définir une relation**.  
  
## <a name="options"></a>Options  
 **Table de groupe de mesures**  
 Affiche le nom de la table de faits pour le groupe de mesures sélectionné.  
  
 **Attributs**  
 Affiche une grille d'attributs et de tables de dimension. Sélectionnez un attribut pour créer ou modifier des propriétés dans **Relation** pour l'attribut sélectionné. Cette grille comporte les colonnes suivantes :  
  
|Option|Définition|  
|------------|----------------|  
|**Nom d’attribut**|Affiche le nom de l'attribut.|  
|**Table de dimension**|Affiche le nom de la table de dimension dont l'attribut est dérivé.|  
  
 **Relation**  
 Affiche une grille des relations entre les colonnes de la table de dimension pour l'attribut sélectionné et les colonnes de la table de faits pour le groupe de mesures sélectionné, ainsi que l'option de traitement des valeurs NULL pour la relation. Cette grille comporte les colonnes suivantes :  
  
|Option|Définition|  
|------------|----------------|  
|**Colonnes de dimension**|Affiche les colonnes de la table de dimension dont est dérivé l'attribut sélectionné dans **Attributs** .|  
|**Colonnes de groupe de mesures**|Sélectionnez **Hérité de la dimension** pour utiliser la relation du groupe de mesures héritée de la dimension, ou sélectionnez une colonne de la table des faits dont est dérivé le groupe de mesures pour définir explicitement une relation.|  
|**Traitement des valeurs null**|Sélectionnez une option de traitement des valeurs NULL pour l'attribut. Pour plus d’informations sur les options de traitement des valeurs NULL, consultez [Élément NullProcessing &#40;ASSL&#41;](scripting/properties/nullprocessing-element-assl.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Définir la boîte de dialogue relation &#40;Analysis Services - données multidimensionnelles&#41;](define-relationship-dialog-box-analysis-services-multidimensional-data.md)   
 [Concepteurs et boîtes de dialogue Analysis Services &#40;données multidimensionnelles&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  