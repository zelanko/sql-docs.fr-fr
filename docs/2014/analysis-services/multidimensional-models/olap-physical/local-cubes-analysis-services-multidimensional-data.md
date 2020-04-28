---
title: Cubes locaux (Analysis Services-données multidimensionnelles) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- cubes [Analysis Services], local
ms.assetid: e52e1515-35a7-4dc3-9bbf-736d176ba0c7
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 52770f78381da2eb686aa445d19e6923f0f0a275
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68889498"
---
# <a name="local-cubes-analysis-services---multidimensional-data"></a>Cubes locaux (Analysis Services - Données multidimensionnelles)
  Pour créer, mettre à jour ou supprimer des cubes locaux, vous devez écrire et exécuter un script ASSL ou un programme AMO.  
  
 Les cubes locaux et les modèles d'exploration de données locaux permettent d'analyser une station de travail cliente lorsqu'elle est déconnectée du réseau. Par exemple, une application cliente peut appeler le fournisseur OLE DB pour OLAP 9.0 (MSOLAP.3), qui à son tour charge le moteur de cube local pour créer et interroger des cubes locaux, comme l'indique l'illustration suivante.  
  
 ![Architecture cliente pour cubes locaux et modèles](../../../analysis-services/dev-guide/media/as-localcubearch9.gif "Architecture cliente pour cubes locaux et modèles")  
  
 ADMOD.NET et AMO (Analysis Management Objects) chargent également le moteur de cube local lors de l'interaction avec des cubes locaux. Un seul processus peut accéder à un fichier de cube local, car le moteur de cube local verrouille exclusivement un fichier de cube local lorsqu'il établit une connexion au cube local. Avec un processus, jusqu'à cinq connexions simultanées sont autorisées.  
  
 Un fichier .cub peut contenir plusieurs cubes ou modèles d'exploration de données. Les interrogations de cubes et modèles d'exploration de données locaux sont traitées par le moteur de cube local et ne nécessitent pas de connexion à une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  L'utilisation de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et de [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] pour gérer les cubes locaux n'est pas prise en charge.  
  
## <a name="local-cubes"></a>Cubes locaux  
 Un cube local peut être créé et rempli à partir d’un cube existant dans [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] une instance ou à partir d’une source de données relationnelle.  
  
|Source de données pour un cube local|Méthode de création|  
|------------------------------------|---------------------|  
|Cube serveur|Vous pouvez utiliser l’instruction CREATe GLOBAL CUBE ou un [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] script de langage de script (ASSL) pour créer et remplir un cube à partir d’un cube basé sur un serveur. Pour plus d’informations, consultez [Create global cube, instruction &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube) ou [Analysis Services scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).|  
|Source de données relationnelles|Vous utilisez un script ASSL pour créer et remplir un cube à partir d'une base de données relationnelle OLE DB. Pour créer un cube local via ASSL, il vous suffit de vous connecter à un fichier de cube local (*.cub) et d'exécuter le script ASSL de la même manière que vous exécutez un script ASSL sur une instance [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] pour créer un cube serveur. Pour plus d’informations, consultez [Analysis Services Scripting Language &#40;ASSL&#41; Reference](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla).|  
  
 Utilisez l'instruction REFRESH CUBE pour reconstruire un cube local et mettre à jour ses données. Pour plus d’informations, consultez [instruction Refresh CUBE &#40;&#41;MDX ](/sql/mdx/mdx-data-definition-refresh-cube).  
  
### <a name="local-cubes-created-from-server-based-cubes"></a>Cubes locaux créés à partir de cubes serveur  
 Lorsque vous concevez des cubes locaux créés à partir de cubes serveur, vous devez prendre en compte les points suivants :  
  
-   Les mesures de comptage de valeurs ne sont pas prises en charge.  
  
-   Lorsque vous ajoutez une mesure, vous devez également inclure au moins une dimension qui est liée à la mesure ajoutée. Pour plus d’informations sur les relations entre les dimensions et les groupes de mesures, consultez [relations de dimension](../../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
-   Lorsque vous ajoutez une hiérarchie parent-enfant, les niveaux et filtres d'une hiérarchie parent-enfant sont ignorés, et l'intégralité de la hiérarchie parent-enfant est incluse.  
  
-   Aucune propriété de membre n'est créée.  
  
-   Lorsque vous incluez une mesure semi-additive, aucune coupe n'est autorisée sur la dimension Account ou Time.  
  
-   Les dimensions de référence sont toujours matérialisées.  
  
-   Lorsque vous insérez une dimension plusieurs à plusieurs, les règles suivantes s'appliquent :  
  
    -   Vous ne pouvez pas découper la dimension plusieurs à plusieurs.  
  
    -   Vous devez ajouter une mesure à partir du groupe de mesures intermédiaire.  
  
    -   Vous ne pouvez pas découper les dimensions communes aux deux groupes de mesures impliqués dans la relation plusieurs à plusieurs.  
  
-   Seuls les membres calculés, jeux nommés et affectations qui reposent sur des mesures et des dimensions ajoutées au cube local apparaîtront dans le cube local. Les membres calculés, jeux nommés et affectations non valides seront automatiquement exclus.  
  
### <a name="security"></a>Sécurité  
 Pour qu’un utilisateur puisse créer un cube local à partir d’un cube de serveur, l’utilisateur doit disposer des autorisations d' **extraction et de cube local** sur le cube du serveur. Pour plus d’informations, consultez [Grant cube or Model permissions &#40;Analysis Services&#41;](../../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).  
  
 Les cubes locaux ne sont pas sécurisés à l'aide de rôles comme les cubes serveur. Toute personne bénéficiant d'un accès au niveau fichier à un fichier de cube local peut interroger les cubes contenus dans ce dernier. Vous pouvez utiliser la propriété de connexion `Encryption Password` sur un fichier de cube local pour définir un mot de passe sur le fichier de cube local. La définition d'un mot de passe sur un fichier de cube local nécessite que toutes les connexions futures au fichier de cube local utilisent ce mot de passe afin d'interroger le fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction CREATe GLOBAL CUBE &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-global-cube)   
 [Développement avec le langage de script Analysis Services &#40;ASSL&#41;](../scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)   
 [Instruction REFRESH CUBE &#40;&#41;MDX](/sql/mdx/mdx-data-definition-refresh-cube)  
  
  
