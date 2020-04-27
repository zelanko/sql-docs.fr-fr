---
title: Découper le cube source (Assistant Exploration de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.dmwizard.slicesourcecube.f1
ms.assetid: 16485608-d3b9-49ee-8baa-948038cdd7ec
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bcb156d5c0a3c1332e748878ddebda1772b80696
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66068595"
---
# <a name="slice-source-cube-data-mining-wizard"></a>Découper le cube source (Assistant Exploration de données)
  Utilisez la boîte de dialogue **Découper le cube source** afin de limiter les données utilisées pour effectuer l'apprentissage du modèle. Généralement, un cube contient les données relatives à plusieurs dimensions et attributs différents, tels que tous les magasins, toutes les régions et tous les produits. Il n'est pas pratique d'effectuer l'apprentissage d'un modèle sur des combinaisons illimitées d'attributs. C'est pourquoi, vous utilisez cette boîte de dialogue pour choisir un ensemble spécifique à utiliser dans l'apprentissage d'un modèle.  
  
 Par exemple, dans le cube AdventureWorks, vous pouvez segmenter par ligne de produits, région ou année, pour obtenir une partie des données.  
  
 Si vous n'êtes pas familiarisé avec les tranches et les cubes, nous vous recommandons de consulter les articles suivants :  
  
-   [Définissez la propriété tranche de partition &#40;Analysis Services&#41;](multidimensional-models/set-the-partition-slice-property-analysis-services.md)  
  
-   [Créer et gérer une partition locale &#40;Analysis Services&#41;](multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
> [!NOTE]  
>  Notez que les fonctions MDX dynamiques (telles que [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) ou [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) ne sont pas prises en charge dans la propriété Slice des partitions. Vous devez définir la tranche à l'aide de tuples explicites ou de références à des membres.  
>   
>  Par exemple, plutôt que d’utiliser [: &#40;plage&#41; &#40;&#41;MDX](/sql/mdx/range-mdx) pour définir une plage, vous devez énumérer chaque membre par année spécifique.  
>   
>  Si vous devez définir une tranche complexe, nous vous recommandons de définir les tuples de la tranche en utilisant un script XMLA Alter. Ensuite, vous pouvez utiliser l'outil en ligne de commande ascmd ou la [Analysis Services Execute DDL Task](../integration-services/control-flow/analysis-services-execute-ddl-task.md) SSIS pour exécuter le script et créer le jeu de membres spécifié juste avant de traiter la partition.  
  
 **Pour plus d’informations :** [Assistant Exploration de données &#40;Analysis Services - Exploration de données&#41;](data-mining/data-mining-wizard-analysis-services-data-mining.md), [Créer une structure d’exploration de données relationnelle](data-mining/create-a-relational-mining-structure.md)  
  
## <a name="options"></a>Options  
 **Dimension**  
 Sélectionnez la dimension que vous voulez découper.  
  
 **Hierarchy**  
 Sélectionnez la hiérarchie que vous voulez découper. Choisissez n'importe quel niveau d'une hiérarchie, mais les attributs utilisés dans le modèle seront uniquement au niveau choisi.  
  
 Par exemple, si vous choisissez la hiérarchie Geography, et sélectionnez le niveau Country, vous ne pouvez pas créer de modèle qui utilise City comme attribut. À l'inverse, si vous choisissez City comme niveau de la hiérarchie sur laquelle vous souhaitez découper, vous ne pouvez pas créer de modèle d'exploration de données reposant sur Country.  
  
 **Opérateur**  
 Sélectionner l'opérateur à utiliser lors de la création une expression de tranche.  
  
 Par exemple, si vous choisissez la hiérarchie Geography, vous pouvez sélectionner l’opérateur =, puis taper « Europe » comme filtre, pour obtenir les données du cube pour l’Europe uniquement.  
  
 **Expression de filtre**  
 Entrez une expression à utiliser comme critère lors du filtrage du cube sur la dimension sélectionnée.  
  
 **Parameters**  
 Cette option n'est pas utilisée pour les modèles d'exploration de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Fin de l’Assistant &#40;l’Assistant Exploration de données&#41;](completing-the-wizard-data-mining-wizard.md)   
 [Aide (F1) de l’Assistant Exploration de données &#40;Analysis Services-exploration de données&#41;](data-mining-wizard-f1-help-analysis-services-data-mining.md)   
 [Spécifier l’utilisation des colonnes du modèle d’exploration de données &#40;l’Assistant Exploration de données&#41;](specify-mining-model-column-usage-data-mining-wizard.md)  
  
  
