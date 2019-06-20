---
title: Dimensions dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP [Analysis Services], dimensions
- dimensions [Analysis Services], about dimensions
- OLAP objects [Analysis Services], dimensions
ms.assetid: 2b62b05c-00fd-4e60-b77f-f707ba83a19b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 520d6f11e5a472d5337a3747cc73c1d3656171c2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66075181"
---
# <a name="dimensions-in-multidimensional-models"></a>Dimensions dans les modèles multidimensionnels
  Une dimension de base de données est un ensemble d'objets associés, appelés attributs, qui peuvent être utilisés pour fournir des informations sur des données dans un ou plusieurs cubes. Par exemple, les attributs les plus courants dans une dimension de produit sont le nom, la catégorie, la gamme, la taille et le prix du produit. Ces objets sont liés à une ou plusieurs colonnes dans une ou plusieurs tables d'une vue de source de données. Par défaut, ces attributs sont visibles en tant que hiérarchies d'attributs et peuvent être utilisés pour comprendre les données de faits dans un cube. Les attributs peuvent être organisés en hiérarchies définies par l'utilisateur qui fournissent des chemins d'exploration pour aider les utilisateurs lorsqu'ils recherchent des données dans un cube.  
  
 Les cubes contiennent toutes les dimensions sur lesquelles reposent les analyses de données. Une instance d'une dimension de base de données dans un cube porte le nom de dimension de cube et porte sur un ou plusieurs groupes de mesures dans le cube. Une dimension de base de données peut être utilisée plusieurs fois dans un cube. Par exemple, une table de faits peut comporter plusieurs faits dépendants de l'heure, et une dimension de cube distincte peut être définie pour permettre l'analyse de chaque fait dépendant de l'heure. Cependant, il ne doit exister qu'une seule dimension de base de données dépendant de l'heure, ce qui signifie également qu'une seule table de cette base de données doit exister pour prendre en charge plusieurs dimensions de cube basées sur l'heure.  
  
> [!NOTE]  
>  Pour obtenir des informations sur les problèmes de performances liés à la conception de dimensions, consultez le [Guide des performances SQL Server 2008 R2 Analysis Services](https://go.microsoft.com/fwlink/?LinkId=306717).  
  
## <a name="defining-dimensions-attributes-and-hierarchies"></a>Définition de dimensions, d'attributs et de hiérarchies  
 La méthode la plus simple pour définir des dimensions, des attributs et des hiérarchies de base de données et de cube consiste à utiliser l'Assistant Cube pour les créer en même temps que la définition du cube. L'Assistant Cube crée les dimensions sur la base des tables de dimension identifiées par l'Assistant dans la vue de source de données ou que vous spécifiez pour une utilisation dans le cube. L'Assistant crée ensuite les dimensions de base de données et les ajoute au nouveau cube, en créant les dimensions de cube.  
  
 Lorsque vous créez un cube, vous pouvez également ajouter au cube toute dimension existant déjà dans la base de données. Ces dimensions peuvent avoir été définies antérieurement pour un autre cube ou par l'Assistant Dimension. Une fois qu'une dimension de base de données a été définie, vous pouvez la modifier et la configurer dans le Concepteur de dimensions. Vous pouvez également personnaliser la dimension de cube, dans une certaine mesure, dans le Concepteur de cube.  
  
> [!NOTE]  
>  Vous pouvez également concevoir et configurer des dimensions, des attributs et des hiérarchies par programme à l'aide de XMLA ou d'objets AMO (Analysis Management Objects). Pour plus d’informations, consultez [Analysis Services Scripting Language &#40;ASSL&#41; référence](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) et [développement avec Analysis Management Objects &#40;AMO&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo).  
  
## <a name="in-this-section"></a>Dans cette section  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Définir des dimensions de base de données](define-database-dimensions.md)  
 Explique comment modifier et configurer une dimension de base de données à l'aide du Concepteur de dimensions.  
  
 [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md)  
 Explique comment définir, modifier et configurer un attribut de dimension de base de données à l'aide du Concepteur de dimensions.  
  
 [Définir des relations d'attributs](attribute-relationships-define.md)  
 Explique comment définir, modifier et configurer une relation d'attribut à l'aide du Concepteur de dimensions.  
  
 [Créer des hiérarchies définies par l'utilisateur](user-defined-hierarchies-create.md)  
 Explique comment définir, modifier et configurer une hiérarchie d'attributs de dimension définie par l'utilisateur à l'aide du Concepteur de dimensions.  
  
 [Utiliser l’Assistant Business Intelligence pour améliorer des dimensions](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 Explique comment améliorer une dimension de base de données à l'aide de l'Assistant Business Intelligence.  
  
## <a name="see-also"></a>Voir aussi  
 [Cubes dans les modèles multidimensionnels](cubes-in-multidimensional-models.md)  
  
  
