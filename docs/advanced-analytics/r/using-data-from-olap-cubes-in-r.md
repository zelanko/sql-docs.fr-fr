---
title: "À l’aide des données à partir de cubes OLAP dans R | Documents Microsoft"
ms.custom: 
ms.prod: sql-non-specified
ms.date: 11/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: r-services
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 60e95f4c101a4afe2a8161ba40df7b27bd85f602
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>À l’aide des données à partir de cubes OLAP dans R

Le **olapR** package est un package R, fourni par Microsoft pour une utilisation avec Machine Learning Server et SQL Server, qui vous permet d’exécuter les requêtes MDX pour obtenir des données à partir de cubes OLAP. Avec ce package, vous n’avez pas besoin de créer des serveurs liés ou de nettoyage des ensembles de lignes aplati ; Vous pouvez utiliser des données OLAP directement dans R.

Cet article décrit l’API, ainsi que d’une vue d’ensemble de OLAP et MDX pour les utilisateurs de R peut être de nouveau aux bases de données de cube multidimensionnel.

> [!IMPORTANT]
> Une instance d’Analysis Services peut prendre en charge des cubes multidimensionnels classiques, ou dans les modèles tabulaires, mais une instance ne peut pas prendre en charge deux types de modèles. Par conséquent, avant de créer une requête sur une base de données Analysis Services, vérifiez qu’il contient les modèles multidimensionnels.
> 
> Bien qu’un modèle tabulaire peut être interrogé à l’aide de MDX, le **olapR** package ne prend pas en charge les connexions aux instances de modèle tabulaire. Si vous avez besoin obtenir des données à partir d’un mode tabulaire, une meilleure option doit activer [DirectQuery](https://docs.microsoft.com/sql/analysis-services/tabular-models/directquery-mode-ssas-tabular) sur le modèle et rendre l’instance disponible comme serveur lié dans SQL Server. 

## <a name="what-is-an-olap-cube"></a>Qu’est un cube OLAP ?

OLAP est l’abréviation de traitement analytique en ligne. Des solutions OLAP sont couramment utilisées pour capturer et stocker des données critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [traitement analytique en ligne](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fournit [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), ce qui vous permet de concevoir, déployer et interroger des données OLAP sous la forme de _cubes_ ou _les modèles tabulaires_. Un cube est une base de données multidimensionnel. _Dimensions_ ressemblent à facettes des données, ou facteurs dans r : dimensions vous permet d’identifier un sous-ensemble spécifique de données que vous souhaitez synthétiser ou analyser. Par exemple, le temps est une dimension importante, bien afin que de nombreuses solutions OLAP incluent plusieurs calendriers définis par défaut, à utiliser lors de la segmentation et de résumer les données. 

Pour des raisons de performances, une base de données OLAP calcule souvent résumés (ou _agrégations_) à l’avance, puis les stocke pour une récupération plus rapide. Récapitulatifs sont basées sur *mesures*, qui représentent des formules qui peuvent être appliquées à des données numériques. Vous utilisez les dimensions pour définir un sous-ensemble de données et vous devez calculez la mesure sur ces données. Par exemple, vous utiliseriez une mesure pour calculer le total des ventes pour une ligne de produit spécifique sur plusieurs trimestres moins taxes, pour signaler les coûts d’expédition moyenne pour un fournisseur particulier, year-to-date cumulatives salaires et ainsi de suite.

MDX, abréviation d’expressions multidimensionnelles, est la langue utilisée pour interroger des cubes. En règle générale, une requête MDX contient une définition de données qui inclut une ou plusieurs dimensions et au moins une mesure, bien que les requêtes MDX peuvent obtenir beaucoup plus complexes et inclure windows propagées, cumulatives moyennes, des sommes, rangs ou centiles. 

Voici d’autres termes qui peuvent être utiles lorsque vous commencez à créer des requêtes MDX :

+ *Le découpage* prend un sous-ensemble du cube à l’aide de valeurs à partir d’une seule dimension.

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>L’utilisation des olapR pour créer des requêtes MDX

L’article suivant fournit des exemples détaillés de la syntaxe de création ou de l’exécution de requêtes sur un cube :

+ [Comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX :

- **Utilisez le Générateur MDX.** Utilisez les fonctions R dans le package pour générer une requête MDX simple, en choisissant un cube, puis en définissant des segments et les axes. Il s’agit d’un moyen simple pour créer une requête MDX valide, si vous n’avez pas accès à des outils traditionnels OLAP, ou que vous ne disposez pas des connaissances approfondies du langage MDX.

    Toutes les requêtes MDX peuvent être créés à l’aide de cette méthode, MDX peut être complexe. Toutefois, cette API prend en charge la plupart des opérations plus courantes et utiles, y compris tranche, dés, exploration vers le bas, rollup et pivot dans les dimensions de N.

+ **Copier-coller MDX bien formé.** Créer manuellement, puis les coller dans une requête MDX. Cette option est la meilleure si vous avez des requêtes MDX existants que vous souhaitez réutiliser, ou si la requête que vous souhaitez générer est trop complexe pour **olapR** à gérer. 

    Générer votre MDX à l’aide d’un utilitaire client, SSMS ou Excel, par exemple, puis enregistrez la chaîne qui définit la requête MDX. Vous fournissez cette chaîne MDX en tant qu’argument à la *Gestionnaire de requête SSAS* dans les **olapR** package. La fonction envoie la requête au serveur Analysis Services spécifié et passe à nouveau les résultats vers R, si que vous êtes autorisé à interroger le cube naturellement.

Pour obtenir des exemples de génération MDX de requête ou exécuter une requête MDX existante, voir [comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie certains problèmes connus et les questions courantes sur la **olapR** package.

### <a name="tabular-models-are-not-supported"></a>Les modèles tabulaires ne sont pas pris en charge.

Si vous vous connectez à une instance d’Analysis Services qui contient un modèle tabulaire, le `explore` fonction signale une réussite avec une valeur de retour de la valeur TRUE. Toutefois, les objets de modèle tabulaire ne sont pas un type compatible et ne peut pas être explorés.

En outre, si vous concevez une requête MDX valide par rapport à un modèle tabulaire (en utilisant un outil externe) et puis collez la requête dans cette API, la requête retourne un résultat NULL et ne signale pas d’erreur.

Si vous avez besoin extraire des données à partir d’un modèle tabulaire pour une utilisation dans R, considérez ces options :

+ Activez le mode DirectQuery sur le modèle et ajouter le serveur comme serveur lié dans SQL Server. 
+ Si le modèle tabulaire a été créé sur un relationnelle mini-data warehouse, obtenez les données directement à partir de la source.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Comment déterminer si une instance contient des modèles tabulaires ou multidimensionnels

Il existe des différences fondamentales entre les modèles tabulaires et les modèles multidimensionnels qui affectent les façon dont les données est stockée et traitée. Par exemple, les modèles tabulaires sont stockées en mémoire et tirer parti des index columnstore pour effectuer des calculs très rapides. Dans les modèles multidimensionnels, les données sont stockées sur le disque et les agrégations sont définies à l’avance et récupérées à l’aide de requêtes MDX.

Pour cette raison, une seule instance d’Analysis Services peut contenir qu’un seul type de modèle. Consultez l’article suivant pour plus d’informations sur la façon de distinguer les deux types de modèles :

+ [Comparaison des modèles multidimensionnels et tabulaires](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Si vous vous connectez à Analysis Services à l’aide d’un client tel que SQL Server Management Studio, vous pouvez indiquer un coup de œil le type de modèle est pris en charge, en examinant l’icône de la base de données.

Vous pouvez également afficher les propriétés du serveur. Le **mode serveur** propriété prend en charge les deux valeurs : _multidimensionnels_ ou _tabulaire_.

Pour plus d’informations sur la façon de vérifier le type de serveur à l’aide de la propriété de serveur, consultez [OLE DB pour OLAP Schema Rowsets](https://docs.microsoft.com/sql/analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>L’écriture différée n’est pas pris en charge.

Il n’est pas possible de réécrire les résultats des calculs de R personnalisés dans le cube.

En général, même si un cube est activé pour l’écriture différée, seules les opérations limitées sont pris en charge, et une configuration supplémentaire peut être nécessaire. Nous vous recommandons d’utiliser MDX pour ces opérations.

+ [Dimensions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Définir l’accès personnalisés aux données des cellules](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

## <a name="resources"></a>Ressources

Si vous ne connaissez OLAP ou à des requêtes MDX, consultez ces articles de Wikipedia : 

+ [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
+ [Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
