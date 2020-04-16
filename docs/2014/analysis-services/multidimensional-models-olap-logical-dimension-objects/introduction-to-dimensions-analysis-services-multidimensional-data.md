---
title: Introduction aux dimensions (Services d’analyse - Données multidimensionnelles) Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], about dimensions
- storage [Analysis Services], dimensions
- dimensions [Analysis Services], examples
- storing data [Analysis Services], dimensions
- storage [Analysis Services]
ms.assetid: ab170fdd-4144-42db-9497-690b9189fc25
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e1a78735cd5aee5ebc87adaac6fab48bb4e183d6
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81387899"
---
# <a name="introduction-to-dimensions-analysis-services---multidimensional-data"></a>Présentation des dimensions (Analysis Services - Données multidimensionnelles)
  Toutes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] les dimensions Microsoft sont des groupes d’attributs basés sur des colonnes de tableaux ou de vues dans une vue source de données. Les dimensions existent indépendamment d'un cube, elles peuvent être utilisées dans plusieurs cubes et plusieurs fois dans un même cube, ainsi que liées entre les instances d'[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Une dimension qui existe indépendamment d'un cube est appelée dimension de base de données et une instance de dimension de base de données dans un cube est appelée dimension de cube.  
  
## <a name="dimension-based-on-a-star-schema-design"></a>Dimension basée sur un schéma en étoile  
 La structure d'une dimension repose principalement sur la structure de la table ou des tables de dimension sous-jacentes. La structure la plus simple est appelée schéma en étoile, où chaque dimension est basée sur une seule table de dimension qui est directement liée à la table de faits par une relation clé primaire - clé étrangère.  
  
 Le diagramme suivant illustre une sous-section [!INCLUDE[ssSampleDBDWobject](../../includes/sssampledbdwobject-md.md)] de la base de données de l’échantillon, dans laquelle le tableau de faits de **FactResellerSales** est lié à deux tables de dimension, **DimReseller** et **DimPromotion**. La colonne **ResellerKey** dans le tableau **de faits de FactResellerSales** définit une relation clé étrangère avec la colonne clé primaire **de ResellerKey** dans la table de dimension **DimReseller.** De même, la colonne **PromotionKey** dans le tableau **factresellerSales** définit une relation clé étrangère avec la colonne principale **de PromotionKey** dans le tableau de dimension **DimPromotion.**  
  
 ![Schéma logique pour la relation de dimensions de fait](../../analysis-services/dev-guide/media/dimfactrelationship.gif "Schéma logique pour la relation de dimensions de fait")  
  
## <a name="dimension-based-on-a-snowflake-schema-design"></a>Dimension basée sur un schéma en flocon  
 Une structure plus complexe est fréquemment requise parce que des informations provenant de plusieurs tables sont nécessaires pour définir la dimension. Dans cette structure, appelée un schéma en flocon, chaque dimension est basée sur les attributs de plusieurs tables liées les unes aux autres ainsi qu'à la table de faits par des relations clé primaire - clé étrangère. Par exemple, le diagramme suivant illustre les tableaux nécessaires pour décrire complètement la dimension produit du projet **d’échantillon AdventureWorksDW** :  
  
 ![Tables pour la dimension Product d'AdventureWorksAS](../../analysis-services/dev-guide/media/dimproduct.gif "Tables pour la dimension Product d'AdventureWorksAS")  
  
 Pour décrire complètement un produit, la catégorie et la sous-catégorie du produit doivent être incluses dans la dimension Product. Toutefois, cette information ne réside pas directement dans le tableau principal de la dimension **DimProduct.** Une relation clé étrangère de **DimProduct** à **DimProductSubcategory**, qui à son tour a une relation clé étrangère à la table **DimProductCategory,** permet d’inclure les informations pour les catégories de produits et les sous-catégories dans la dimension produit.  
  
## <a name="snowflake-schema-versus-reference-relationship"></a>Schéma en flocon et relation de référence  
 Parfois, vous pouvez être amené à choisir entre l'utilisation d'un schéma en flocons pour définir les attributs d'une dimension à partir de plusieurs tables ou la définition de deux dimensions distinctes avec l'établissement d'une relation de dimensions de référence entre celles-ci. Le diagramme suivant montre ce scénario.  
  
 ![Schéma logique pour un exemple de dimension référencée](../../analysis-services/dev-guide/media/dimindirect.gif "Schéma logique pour un exemple de dimension référencée")  
  
 Dans le diagramme précédent, le tableau **de faits factResellerSales** n’a pas de relation clé étrangère avec la table de dimension **DimGeography.** Cependant, le tableau **de faits de FactResellerSales** a une relation clé étrangère avec la table de dimension **DimReseller,** qui à son tour a une relation clé étrangère avec la table de dimension **dimGeography.** Pour définir une dimension revendeur qui contient des informations géographiques sur chaque revendeur, vous devez récupérer ces attributs à partir des tables de dimension **DimGeography** et **DimReseller.** Cependant, dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez obtenir le même résultat en créant deux dimensions distinctes et en les liant avec un groupe de mesures en définissant une relation de dimensions de référence entre les deux dimensions. Pour plus d’informations sur les relations de dimension de référence, voir [Relations Dimension](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).  
  
 Un avantage des relations de dimensions de référence dans ce scénario est que vous pouvez créer une seule dimension Geography, puis créer plusieurs dimensions de cube basés sur cette dimension, sans qu'un espace de stockage supplémentaire soit nécessaire. Par exemple, vous pouvez lier une des dimensions de cube Geography à une dimension Reseller, et une autre dimension de cube Geography à une dimension Customer. **Sujets connexes :**[Dimensions Relations](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md), Définir une relation [référencée et des propriétés relationnelles référencées](../multidimensional-models/define-a-referenced-relationship-and-referenced-relationship-properties.md)  
  
## <a name="processing-a-dimension"></a>Traitement d'une dimension  
 Après avoir créé une dimension, vous devez traiter celle-ci avant de pouvoir afficher les membres des attributs et des hiérarchies dans la dimension. Après avoir modifié la structure d'une dimension ou après la mise à jour des informations de ses tables sous-jacentes, vous devez traiter à nouveau la dimension pour pouvoir afficher les modifications. Lorsque vous traitez une dimension après des changements structuraux, vous devez également traiter les cubes qui comprennent cette dimension, sinon le cube ne sera pas visible.  
  
## <a name="security"></a>Sécurité  
 Tous les objets subordonnés d'une dimension, y compris les hiérarchies, les niveaux et les membres, sont protégés en utilisant des rôles dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. La sécurité d'une dimension peut être appliquée à tous les cubes de la base de données qui utilisent la dimension, ou à un cube donné seulement. Pour plus d’informations sur la sécurité des dimensions, voir [les autorisations de subvention sur une dimension &#40;Services d’analyse&#41;](../multidimensional-models/grant-permissions-on-a-dimension-analysis-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Stockage de dimension](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md)   
 [Traductions dimension](../multidimensional-models-olap-logical-dimension-objects/dimension-translations.md)   
 [Dimensions activées en écriture](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
