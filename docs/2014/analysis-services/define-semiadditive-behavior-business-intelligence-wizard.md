---
title: Définir le comportement semi-additif (Assistant Business Intelligence) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.biwizard.semiadditivememberdetection.f1
ms.assetid: e57080ba-ce96-40f8-bca7-6701d1725b3c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 161e2cb9dd9eeae4f2ed369b77ab0799ae12a33a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66082000"
---
# <a name="define-semiadditive-behavior-business-intelligence-wizard"></a>Définir le comportement semi-additif (Assistant Business Intelligence)
  Utilisez la page **Définir le comportement semi-additif** pour activer ou désactiver le comportement semi-additif sur les mesures. Celui-ci détermine comment les mesures sont contenues dans un cube sont agrégées sur une dimension de temps.  
  
> [!NOTE]  
>  Excepté pour LastChild qui est disponible dans l'édition Standard, les comportements semi-additifs sont uniquement disponibles dans les éditions Business Intelligence ou Entreprise. En outre, étant donné que le comportement semi-additif n’est défini que sur les mesures et non les dimensions, vous ne trouverez pas cette page dans l’Assistant Business Intelligence s’il a été démarré à partir du Concepteur de dimensions ou en cliquant avec le bouton droit sur une dimension dans l’Explorateur de solutions dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].  
  
## <a name="options"></a>Options  
 **Désactiver le comportement semi-additif**  
 Désactive le comportement semi-additif dans toutes les mesures contenues dans le cube.  
  
 **L’Assistant a détecté le \<nom de la dimension > dimension de compte, qui contient des membres semi-additifs. Le serveur agrégera les membres de cette dimension selon le comportement semi-additif spécifié pour chaque type de compte.**  
 Active le comportement semi-additif pour les dimensions de compte qui contiennent des membres semi-additifs. Cette option configure la fonction d'agrégation de toutes les mesures dans des groupes qui font référence à la dimension de compte `ByAccount`.  
  
 Pour plus d’informations sur les dimensions de compte, consultez [Créer un compte Finance de la dimension de type parent-enfant](multidimensional-models/database-dimensions-finance-account-of-parent-child-type.md).  
  
 **Définir le comportement semi-additif pour les membres individuels**  
 Active le comportement semi-additif et spécifie la fonction d'agrégation semi-additive pour des mesures données. Cette fonction s'applique à toutes les dimensions référencées par le groupe de mesures qui contiennent la mesure.  
  
 **Mesures**  
 Affiche le nom d'une mesure contenue dans le cube.  
  
 **Fonction semi-additive**  
 Sélectionnez le type d'agrégation de la mesure sélectionnée. Le tableau suivant répertorie les fonctions d'agrégation disponibles.  
  
|Value|Description|  
|-----------|-----------------|  
|**AverageOfChildren**|Agrégation réalisée en retournant la moyenne des enfants de la mesure.|  
|`ByAccount`|Agrégation réalisée par la fonction d'agrégation associée au type de compte spécifié d'un attribut dans une dimension de compte.|  
|`Count`|Agrégation réalisée en utilisant la fonction `Count`.|  
|`DistinctCount`|Agrégation réalisée en utilisant la fonction `DistinctCount`.|  
|**FirstChild**|Agrégation réalisée par retour du premier membre enfant de la mesure sur une dimension de temps.|  
|**FirstNonEmpty**|Agrégation réalisée par retour du premier membre non vide de la mesure sur une dimension de temps.|  
|**LastChild**|Agrégation réalisée par retour du dernier membre enfant de la mesure sur une dimension de temps.|  
|**LastNonEmpty**|Agrégation réalisée par retour du dernier membre non vide de la mesure sur une dimension de temps.|  
|`Max`|Agrégation réalisée en utilisant la fonction `Max`.|  
|`Min`|Agrégation réalisée en utilisant la fonction `Min`.|  
|**Aucun**|L'agrégation n'est pas effectuée.|  
|`Sum`|Agrégation réalisée en utilisant la fonction `Sum`.|  
  
> [!NOTE]  
>  Les sélections effectuées pour cette option s’appliquent uniquement si l’option **Définir le comportement semi-additif pour les membres individuels** est sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide (F1) de l'Assistant Business Intelligence](business-intelligence-wizard-f1-help.md)   
 [Concepteur de cube &#40;Analysis Services - données multidimensionnelles&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Concepteur de dimensions &#40;Analysis Services - données multidimensionnelles&#41;](dimension-designer-analysis-services-multidimensional-data.md)  
  
  
