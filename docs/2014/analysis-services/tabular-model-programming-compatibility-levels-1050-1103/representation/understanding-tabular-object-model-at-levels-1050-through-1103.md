---
title: Présentation du modèle d’objet tabulaire | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6077b7e8-cb3e-4480-a5de-bb602cf9d69a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dcfd16ae7e49392c9ba0a001ea8d205c4fa88d1c
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62795340"
---
# <a name="understanding-the-tabular-object-model"></a>Présentation du modèle d'objet tabulaire
  Un modèle tabulaire est une représentation logique de tables, de relations, de hiérarchies, de perspectives, de mesures, et de performance clés. Cette section présente l'implémentation interne à l'aide d'objets AMO. Consultez [développement avec AMO (Analysis Management Objects) &#40;amo&#41;](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo) si vous n’avez pas encore utilisé AMO.  
  
 L'approche ici est hiérarchisée, tous les objets appropriés dans le modèle tabulaire sont logiquement mappés aux objets AMO, et les interactions ou le flux de travail requis sont expliqués. Un exemple de code source pour créer un modèle tabulaire à l'aide d'objets AMO, Objets AMO vers objets tabulaires est disponible dans Codeplex. Remarque importante à propos du code dans l'exemple : le code est fourni uniquement comme un support aux concepts logiques expliqués ici et ne doit pas être utilisé dans un environnement de production, ni à des fins autres que pédagogiques. L'exemple est fourni sans prise en charge ni garantie.  
  
## <a name="database-representation"></a>Représentation de la base de données  
 Une base de données fournit un objet conteneur pour le modèle tabulaire. Tous les objets dans un modèle tabulaire sont contenus dans la base de données. En termes d'objets AMO, une représentation de base de données a une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.Database> et aucun autre objet AMO principal n'est requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans l'objet de base de données AMO peuvent être utilisés lors de la modélisation.  
  
 Pour obtenir une explication détaillée sur la création et la manipulation de la représentation de base de données, consultez [représentation de base de données&#40;&#41;tabulaires](database-representation-tabular.md) .  
  
## <a name="connection-representation"></a>Représentation de la connexion  
 Une connexion établit la relation entre les données à inclure dans une solution de modèle tabulaire et le modèle lui-même. En termes d'objets AMO, une connexion a une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.DataSource> et aucun autre objet AMO principal n'est requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans l'objet datasource AMO peuvent être utilisés lors de la modélisation.  
  
 Pour une explication détaillée sur la création et la manipulation de la représentation de la source de données, consultez représentation de la [connexion &#40;&#41;tabulaire](connection-representation-tabular.md) .  
  
## <a name="table-representation"></a>Représentation d'une table  
 Les tables sont des objets de base de données qui contiennent toutes les données dans la base de données. En termes d'objets AMO, une table a une relation de mappage un-à-plusieurs. Une table est représentée par l'utilisation des objets AMO suivants : <xref:Microsoft.AnalysisServices.DataSourceView>, <xref:Microsoft.AnalysisServices.Dimension>, <xref:Microsoft.AnalysisServices.Cube>, <xref:Microsoft.AnalysisServices.CubeDimension>, <xref:Microsoft.AnalysisServices.MeasureGroup> et <xref:Microsoft.AnalysisServices.Partition> sont les principaux objets requis ; toutefois, il est important de noter que cela ne signifie pas que tous les objets contenus dans les objets AMO précédemment mentionnés peuvent être utilisés lors de la modélisation.  
  
 Pour une explication détaillée sur la création et la manipulation de la représentation de table, consultez la rubrique [représentation de Tables &#40;&#41;tabulaires](tables-representation-tabular.md) .  
  
### <a name="calculated-column-representation"></a>Représentation d'un colonne calculée  
 Les colonnes calculées sont des expressions évaluées qui génèrent une colonne dans une table, où une nouvelle valeur est calculée et stockée pour chaque ligne de la table. En termes d'objets AMO, une colonne calculée a une relation de mappage un-à-plusieurs. Une colonne calculée est représentée par l'utilisation des objets AMO suivants : <xref:Microsoft.AnalysisServices.Dimension> et <xref:Microsoft.AnalysisServices.MeasureGroup> sont les principaux objets requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans les objets AMO mentionnés précédemment peuvent être utilisés lors de la modélisation.  
  
 Pour une explication détaillée sur la création et la manipulation de la représentation de colonne calculée, consultez [représentation de colonne calculée &#40;&#41;tabulaire](tables-calculated-column-representation.md) .  
  
### <a name="calculated-measure-representation"></a>Représentation de la mesure calculée  
 Les mesures calculées sont des expressions stockées qui sont évaluées à la demande une fois le modèle déployé. En termes d'objets AMO, une mesure calculée a une relation de mappage un-à-plusieurs. Une colonne calculée est représentée par l'utilisation des objets AMO suivants : <xref:Microsoft.AnalysisServices.MdxScript.Commands%2A> et <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A> sont les principaux objets requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans les objets AMO mentionnés précédemment peuvent être utilisés lors de la modélisation.  
  
> [!NOTE]  
>  Les objets <xref:Microsoft.AnalysisServices.Measure> n'ont aucune relation avec les mesures calculées dans les modèles tabulaires et ne sont pas pris en charge dans ces modèles.  
  
 Pour obtenir une explication détaillée sur la création et la manipulation de la représentation de mesure calculée, consultez représentation de la [mesure calculée &#40;&#41;tabulaire](tables-calculated-measure-representation.md) .  
  
### <a name="hierarchy-representation"></a>Représentation d'une hiérarchie  
 Les hiérarchies permettent à l'utilisateur final d'explorer plus facilement les objets. En termes d'objets AMO, une représentation de hiérarchie a une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.Hierarchy> et aucun autre objet AMO principal n'est requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans l'objet de base de données AMO peuvent être utilisés lors de la modélisation tabulaire.  
  
 Pour obtenir une explication détaillée sur la création et la manipulation de la représentation hiérarchique, consultez [représentation hiérarchique &#40;&#41;tabulaire](tables-hierarchy-representation.md) .  
  
### <a name="key-performance-indicator--kpi--representation"></a>Indicateur de performance clé-représentation KPI  
 Un KPI évalue la performance d'une valeur, définie par une mesure de base, par rapport à une valeur cible. En termes d'objets AMO, la représentation d'un KPI a une relation de mappage un-à-plusieurs. Un KPI est représenté par l'utilisation des objets AMO suivants : <xref:Microsoft.AnalysisServices.MdxScript.Commands%2A>and <xref:Microsoft.AnalysisServices.MdxScript.CalculationProperties%2A> sont les principaux objets requis.  Il est important de noter que cela ne signifie pas que tous les objets contenus dans les objets AMO mentionnés précédemment peuvent être utilisés lors de la modélisation.  
  
> [!NOTE]  
>  En outre, il existe une différence importante, les objets <xref:Microsoft.AnalysisServices.Kpi> n'ont aucune relation avec les indicateurs de performance clés dans les modèles tabulaires. Et ils ne sont pas pris en charge dans les modèles tabulaires.  
  
 Pour obtenir une explication détaillée sur la façon de créer et de manipuler la représentation de l’indicateur de [performance clé, consultez représentation d’indicateur de performance clé &#40;&#41;tabulaire](tables-key-performance-indicator-representation.md) .  
  
### <a name="partition-representation"></a>Représentation d'une partition  
 À des fins opérationnelles, une table peut être divisée en différents sous-ensembles de lignes qui une fois combinés forment la table. Chacun de ces sous-ensembles est une partition de la table. En termes d'objets AMO, une représentation de partition a une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.Partition> et aucun autre objet AMO principal n'est requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans l'objet de base de données AMO peuvent être utilisés lors de la modélisation.  
  
 Pour une explication détaillée sur la création et la manipulation de la représentation de partition, voir [représentation sous forme de partition &#40;&#41;tabulaires](tables-partition-representation.md) .  
  
## <a name="relationship-representation"></a>Représentation d'une relation  
 Une relation est une connexion entre deux tables de données. La relation établit la façon dont les données des deux tables doivent être mises en corrélation.  
  
 Dans les modèles tabulaires, plusieurs relations peuvent être définies entre deux tables. Lorsque plusieurs relations entre deux tables sont définies, une seule peut être définie comme relation active par défaut. Toutes les autres relations sont inactives.  
  
 En termes d'objets AMO, toutes les relations inactives ont une représentation d'une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.Relationship> et aucun autre objet AMO principal n'est requis. Pour la relation active, d'autres conditions existent et un mappage à <xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension> est également requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans la relation AMO ou l'objet referenceMeasureGroupDimension peuvent être utilisés lors de la modélisation.  
  
 Pour une explication détaillée sur la création et la manipulation de la représentation de la relation, voir [représentation sous forme de relation &#40;&#41;tabulaires](relationship-representation-tabular.md) .  
  
## <a name="perspective-representation"></a>Représentation d'une perspective  
 Une perspective est un mécanisme pour simplifier ou mieux cibler le mode. En termes d'objets AMO, une représentation de relation a une relation de mappage un-à-un avec <xref:Microsoft.AnalysisServices.Perspective> et aucun autre objet AMO principal n'est requis. Il est important de noter que cela ne signifie pas que tous les objets contenus dans l'objet de perspective AMO peuvent être utilisés lors de la modélisation tabulaire.  
  
 Pour obtenir une explication détaillée sur la création et la manipulation de la représentation perspective, consultez [représentation en perspective &#40;&#41;tabulaire](perspective-representation-tabular.md) .  
  
> [!WARNING]  
>  Les perspectives ne sont pas un mécanisme de sécurité ; les objets en dehors de la perspective sont toujours accessibles à l'utilisateur via d'autres interfaces.  
  
  
