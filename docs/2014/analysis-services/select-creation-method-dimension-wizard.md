---
title: Sélectionnez la méthode de création (Assistant Dimension) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensiondefinition.f1
ms.assetid: 291b0b2d-a03a-4df6-82f7-90ad92d4d1cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1450762e09481d4b8bfa5883c5c752d01216f29e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62748111"
---
# <a name="select-creation-method-dimension-wizard"></a>Sélectionner la méthode de création (Assistant Dimension)
  La page **Sélectionner la méthode de création** permet de choisir la méthode de création de la dimension.  
  
 **Pour ouvrir l’Assistant Dimension**  
  
-   Dans [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **Dimensions** pour un projet [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , puis cliquez sur **Nouvelle dimension**.  
  
## <a name="options"></a>Options  
 **Utiliser une table existante**  
 Créez une dimension à partir d'une ou de plusieurs tables dans une source de données. Les attributs qui sont disponibles pour la dimension dépendent de la structure des données dans la table.  
  
 Pour plus d’informations, consultez [Créer une dimension à l’aide d’une table existante](multidimensional-models/create-a-dimension-by-using-an-existing-table.md).  
  
 **Générer une table de temps dans la source de données**  
 Créez une table de temps dans la source de données sous-jacente puis utilisez cette table pour créer une dimension de temps. Utilisez cette option lorsque aucune table de ce type n'existe et que vous ne souhaitez pas utiliser de script pour en créer une. La nouvelle table de temps contiendra des données pour la plage de dates, les attributs et les calendriers que vous spécifiez dans l'assistant.  
  
> [!NOTE]  
>  Pour utiliser cette option, vous devez avoir l'autorisation de créer des objets dans la source de données sous-jacente. Si vous n’avez pas l’autorisation de créer des objets dans la source de données, essayez d’utiliser l’option **Générer une table de temps sur le serveur** .  
  
 Pour plus d’informations, consultez [Créer une dimension de temps en générant une table de temps](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).  
  
 **Générer une table de temps sur le serveur**  
 Créez directement une table de temps sur le serveur, puis utilisez cette table pour créer une dimension de temps. Utilisez cette option si vous n'avez pas l'autorisation de créer des objets dans la source de données sous-jacente. La nouvelle dimension de temps contiendra des données pour la plage de dates, les attributs et les calendriers que vous spécifiez dans l'assistant.  
  
 Pour plus d’informations, consultez [Créer une dimension de temps en générant une table de temps](multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md).  
  
 **Générer une table non temporelle dans la source de données**  
 Concevez la dimension sans source de données relationnelles sous-jacente, puis générez le schéma nécessaire pour la source de données. Cette approche est appelée modélisation verticale.  
  
> [!NOTE]  
>  Pour utiliser cette option, vous devez avoir l'autorisation de créer des objets dans la source de données sous-jacente.  
  
 Vous pouvez générer la dimension avec ou sans modèle. Pour générer la dimension avec un modèle, sélectionnez le modèle dans la liste **Modèle** .  
  
 Pour plus d’informations, consultez [Créer une dimension en générant une table non temporelle dans la source de données](multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md).  
  
 **Modèle**  
 Sélectionnez le modèle que vous souhaitez utiliser pour créer la dimension. Les modèles fournissent un jeu complet de définitions d'attributs et de hiérarchies orientées vers un objectif commercial spécifique.  
  
> [!NOTE]  
>  Cette option est disponible uniquement quand l’option **Générer une table non temporelle dans la source de données** a été sélectionnée.  
  
## <a name="see-also"></a>Voir aussi  
 [Aide F1 de l’Assistant Dimension](dimension-wizard-f1-help.md)   
 [Dimensions &#40;Analysis Services - données multidimensionnelles&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [Dimensions dans les modèles multidimensionnels](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
