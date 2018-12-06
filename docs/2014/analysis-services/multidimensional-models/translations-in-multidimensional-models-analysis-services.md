---
title: Traductions dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f3238267021c0fd4054fb9757ea8d00cae6114dc
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48218939"
---
# <a name="translations-in-multidimensional-models"></a>Traductions dans les modèles multidimensionnels
  Prise en charge multilingue dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] s’effectue en utilisant des traductions. Une traduction contient un identificateur de langue et des liaisons pour les propriétés d'objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] qui peuvent être présentées dans plusieurs langues. Par exemple, vous pouvez définir une traduction pour une base de données [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] afin de présenter la légende et la description de cette base de données dans une langue donnée. Pour plus d’informations sur les traductions, consultez [traductions de Cube](../multidimensional-models-olap-logical-cube-objects/cube-translations.md).  
  
## <a name="defining-translations"></a>Définition des traductions  
 Vous pouvez définir des traductions dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] en utilisant le concepteur correspondant à l’objet [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] à traduire. Définition d’une traduction crée un `Translation` objet associé avec le bon [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet ayant des valeurs littérales explicites spécifiées, dans la langue spécifiée, pour les propriétés d’associé [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objet.  
  
 Vous pouvez associer des traductions aux objets et propriétés [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] suivants :  
  
|Object|Properties|Concepteur|  
|------------|----------------|--------------|  
|Base de données|`Caption`, `Description`|[Général &#40;Concepteur de base de données&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../general-database-designer-analysis-services-multidimensional-data.md)|  
|Cube|`Caption`, `Description`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Groupe de mesures|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Measure|`Caption`, `DisplayFolder`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Dimension de cube|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Perspective|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Indicateur de performance clé (KPI)|`Caption`, `Description`, `DisplayFolder`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Action|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Jeu nommé|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|membre calculé|`Caption`|[Traductions &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-cube-designer-analysis-services-multidimensional-data.md)|  
|Dimension de base de données|`Caption`, `AttributeAllMember`|[Traductions &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Attribute|`Caption`, `CaptionColumn` <sup>1</sup>, `AttributeHierarchyDisplayFolder`, `NamingTemplate`, `MembersWithDataCaption`|[Traductions &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Hierarchy|`Caption`, `AllMemberName`|[Traductions &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
|Level|`Caption`|[Traductions &#40;Concepteur de dimensions&#41; &#40;Analysis Services - données multidimensionnelles&#41;](../translations-dimension-designer-analysis-services-multidimensional-data.md)|  
  
 <sup>1</sup> le `CaptionColumn` propriété d’un attribut peut être lié à une colonne dans une vue de source de données et peut utiliser un classement Windows autre que celui spécifié pour l’instance, contrairement aux autres traductions.  
  
### <a name="defining-attribute-translations"></a>Définition des traductions d'attributs  
 Les traductions associées aux attributs dans les dimensions de base de données ne sont pas gérées de la même façon que les autres traductions :  
  
-   une liaison de colonne, au lieu d'une valeur littérale explicite, peut être associée à la propriété `CaptionColumn` afin que les noms des membres de cet attribut puissent être traduits ;  
  
-   un classement Windows différent du classement spécifié pour l'instance peut être utilisé afin que les membres de l'attribut puissent être triés de manière appropriée pour la langue spécifiée dans la traduction.  
  
 Vous pouvez utiliser la **traduction de données d’attribut** boîte de dialogue dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] pour définir des traductions pour les attributs dans les dimensions de la base de données. Pour plus d’informations sur la **traduction de données d’attribut** boîte de dialogue, consultez [boîte de dialogue traduction de données attribut &#40;Analysis Services - données multidimensionnelles&#41;](../attribute-data-translation-dialog-box-analysis-services-multidimensional-data.md).  
  
## <a name="resolving-translations"></a>Résolution des traductions  
 Si une application cliente demande des informations dans un identificateur de langue spécifié, l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente de convertir les données et les métadonnées des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] dans l’identificateur de langue le plus proche possible. Si l’application cliente ne spécifie pas de langue par défaut ou si elle spécifie l’identificateur local neutre (0) ou l’identificateur de langue de traitement par défaut (1024), alors [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] utilise la langue par défaut de l’instance pour renvoyer les données et les métadonnées des objets [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Si l'application cliente spécifie un identificateur de langue différent de l'identificateur de langue par défaut, l'instance parcourt toutes les traductions disponibles pour tous les objets disponibles. Si l’identificateur de langue spécifié correspond à l’identificateur de langue d’une traduction, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] renvoie cette traduction. Si aucune correspondance n'est trouvée, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente d'utiliser l'une des méthodes suivantes pour renvoyer les traductions d'un identificateur de langue qui est le plus proche possible de l'identificateur de langue spécifié :  
  
-   Pour les identificateurs de langue suivants, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tente d’utiliser un identificateur de langue de remplacement si aucune traduction n’est définie pour l’identificateur de langue spécifié :  
  
    |Identificateur de langue spécifié|Identificateur de langue de remplacement|  
    |-----------------------------------|-----------------------------------|  
    |3076 - Chinois (Hong Kong (R.A.S.), RPC)|1028 - Chinois (Taïwan)|  
    |5124 - Chinois (Macao (R.A.S.))|1028 - Chinois (Taïwan)|  
    |1028 - Chinois (Taïwan)|Langue par défaut|  
    |4100 - Chinois (Singapour)|2052 - Chinois (RPC)|  
    |2074 - Croate|Langue par défaut|  
    |3098 - Croate (Cyrillique)|Langue par défaut|  
  
-   Pour tous les autres identificateurs de langue spécifiés, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] extrait la langue primaire de l’identificateur de langue spécifié et récupère l’identificateur de langue que Windows considère comme la meilleure correspondance pour la langue primaire. Si aucune traduction n'est trouvée pour la meilleure correspondance indiquée par Windows ou si l'identificateur de langue spécifié est la meilleure correspondance pour la langue primaire, la langue par défaut est utilisée.  
  
## <a name="deleting-translation-objects"></a>Suppression des objets Translation  
 Vous pouvez cliquer avec le bouton droit sur un objet Translation dans le concepteur de cube ou de dimension afin de le supprimer définitivement. Vous ne pouvez pas restaurer ou recycler un objet supprimé. Par conséquent, veillez à vérifier la liste des objets concernés avant de continuer.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios de globalisation pour données multidimensionnelles Analysis Services](../globalization-scenarios-for-analysis-services-multiidimensional.md)   
 [Langues et classements &#40;Analysis Services&#41;](../languages-and-collations-analysis-services.md)  
  
  
