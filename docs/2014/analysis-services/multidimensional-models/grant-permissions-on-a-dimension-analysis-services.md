---
title: Accorder des autorisations sur une dimension (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.dimensions.f1
helpviewer_keywords:
- dimensions [Analysis Services], security
- read/write permissions
- user access rights [Analysis Services], dimensions
- permissions [Analysis Services], dimensions
ms.assetid: be5b2746-0336-4b12-827e-131462bdf605
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3efce85f27db9d0695ea56e9940ab563ed40537a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074957"
---
# <a name="grant-permissions-on-a-dimension-analysis-services"></a>Octroyer des autorisations sur une dimension (Analysis Services)
  La sécurité de dimension sert à définir des autorisations sur un objet de dimension, et non sur ses données. En général, l'autorisation ou le refus de l'accès aux opérations de traitement est le principal objectif de la définition des autorisations sur une dimension.  
  
 Mais peut-être votre objectif n'est-il pas de contrôler les opérations de traitement, mais plutôt l'accès aux données d'une dimension ou aux attributs et hiérarchies qu'elle contient. Par exemple, une société ayant des divisions de ventes régionales souhaitera peut-être interdire l'accès aux chiffres des ventes au personnel étranger à la division en question. Pour autoriser ou refuser l'accès à une partie des données de dimension pour différentes composants, vous pouvez définir des autorisations sur des attributs de dimension et des membres de dimension. Notez que vous ne pouvez pas refuser l'accès à un objet de dimension proprement dit, mais uniquement à ses données. Si votre objectif immédiat consiste à autoriser ou à refuser l’accès aux membres d’une dimension, notamment les droits d’accès à des hiérarchies d’attributs spécifiques, consultez [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) pour plus d’informations.  
  
 Le reste de cette rubrique traite des autorisations que vous pouvez définir sur l'objet de dimension proprement dit, notamment :  
  
-   Les autorisations Lecture ou Lecture/Écriture (seules les options Lecture ou Lecture/Écriture sont disponibles ; vous ne pouvez pas sélectionner « Aucune »). Comme mentionné plus haut, si votre objectif consiste à restreindre l’accès à des données de dimension, consultez [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) pour plus de détails.  
  
-   Les autorisations de traitement (applicable quand le scénario requiert une stratégie de traitement nécessitant des autorisations personnalisées sur des objets spécifiques).  
  
-   Les autorisations Lire la définition (généralement pour prendre en charge le traitement interactif avec un outil ou pour fournir de la visibilité dans un modèle. Lire la définition vous permet d'afficher la structure d'une dimension, sans disposer de l'autorisation d'accès à ses données ou de modification de sa définition).  
  
 Lors de la définition des rôles pour une dimension, les autorisations disponibles varient selon que l'objet est une dimension de base de données autonome (interne à la base de données mais externe au cube) ou une dimension du cube.  
  
> [!NOTE]  
>  Par défaut, les autorisations sur une dimension de base de données sont héritées d'une dimension de cube. Par exemple, si vous activez **Lecture/Écriture** sur une dimension de base de données Client, la dimension de cube Client hérite de **Lecture/Écriture** dans le contexte du rôle actif. Vous pouvez effacer les autorisations héritées si vous souhaitez remplacer un paramètre d'autorisation.  
  
## <a name="set-permissions-on-a-database-dimension"></a>Définir des autorisations sur une dimension de base de données  
 Les dimensions de base de données sont des objets autonomes dans une base de données, ce qui permet de réutiliser une dimension au sein du même modèle. Imaginez une dimension de base de données DATE utilisée à plusieurs reprises dans un modèle, par exemple comme dimensions de cube Date de commande, Date d'expédition et Date d'échéance. Les dimensions de cube et de base de données étant des objets homologues dans une base de données, vous pouvez définir des autorisations de traitement indépendamment sur chaque objet.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], développez **Rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données (ou créez un rôle de base de données).  
  
2.  Dans le volet **Dimensions** , l’ensemble de dimensions doit avoir comme valeur **Toutes les dimensions de la base de données**.  
  
     Par défaut, les autorisations ont la valeur **Lecture**.  
  
     Bien que **Lecture/Écriture** soit disponible, nous vous recommandons de ne pas utiliser cette autorisation. **Lecture/Écriture** s’utilise pour les scénarios d’écriture différée de dimension, qui sont déconseillés. Consultez [fonctionnalités dans SQL Server 2014 Analysis Services déconseillées](../deprecated-analysis-services-features-in-sql-server-2014.md).  
  
     Vous pouvez si vous le souhaitez définir des autorisations **Lire la définition** et **Traiter** sur des objets de dimension spécifiques, à condition que ces autorisations ne soient pas déjà définies au niveau de la base de données. Pour plus d’informations, consultez [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md) et [Octroyer des autorisations Lire la définition sur des métadonnées d’objets &#40;Analysis Services&#41;](grant-read-definition-permissions-on-object-metadata-analysis-services.md).  
  
## <a name="set-permissions-on-a-cube-dimension"></a>Définir des autorisations sur une dimension de cube  
 Les dimensions de cube sont des dimensions de base de données qui ont été ajoutées à un cube. En tant que telles, elles dépendent structurellement des groupes de mesures associés. Bien que vous puissiez traiter ces objets de manière atomique, en termes d'autorisation, il est plus logique de traiter le cube et les dimensions de cube comme une seule et même entité.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connectez-vous à l’instance d’ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], développez **Rôles** pour la base de données appropriée dans l’Explorateur d’objets, puis cliquez sur un rôle de base de données (ou créez un rôle de base de données).  
  
2.  Dans le **Dimensions** volet, affectez à la dimension la valeur est \<nom-cube > **dimensions du cube**.  
  
     Par défaut, les autorisations sont héritées à partir d'une dimension de base de données correspondante. Décochez la case **Hériter** pour remplacer les autorisations de **Lecture** par **Lecture/Écriture**. Avant d’utiliser **Lecture/Écriture**, veillez à lire la remarque de la section précédente.  
  
> [!IMPORTANT]  
>  Si vous définissez des autorisations de rôle de base de données en utilisant AMO (Analysis Management Objects), les références à une dimension de cube dans l’attribut DimensionPermission d’un cube rompent l’héritage d’autorisation de l’attribut DimensionPermission de la base de données. Pour plus d’informations sur AMO, consultez [Développement avec AMO &#40;Analysis Management Objects&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).  
  
## <a name="see-also"></a>Voir aussi  
 [Rôles et autorisations &#40;Analysis Services&#41;](roles-and-permissions-analysis-services.md)   
 [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)   
 [Octroyer des autorisations sur des modèles et des structures d’exploration de données &#40;Analysis Services&#41;](grant-permissions-on-data-mining-structures-and-models-analysis-services.md)   
 [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Octroyer un accès personnalisé à des données de cellule &#40;Analysis Services&#41;](grant-custom-access-to-cell-data-analysis-services.md)  
  
  
