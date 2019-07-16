---
title: À l’aide des données à partir de cubes OLAP dans R - Services de SQL Server Machine Learning
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: fc7158ca426b02a9275ea2142f3e97e771dbfd1e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67962386"
---
# <a name="using-data-from-olap-cubes-in-r"></a>À l’aide des données à partir de cubes OLAP dans R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Le **olapR** package est un package R, fourni par Microsoft pour une utilisation avec Machine Learning Server et SQL Server, qui vous permet d’exécuter des requêtes MDX pour obtenir des données à partir de cubes OLAP. Avec ce package, vous n’avez pas besoin de créer des serveurs liés ou de nettoyer les ensembles de lignes aplatis ; Vous pouvez obtenir des données OLAP directement à partir de R.

Cet article décrit l’API, ainsi que d’une vue d’ensemble de OLAP et MDX pour les utilisateurs de R qui peut être nouveau pour les bases de données de cube multidimensionnel.

> [!IMPORTANT]
> Une instance d’Analysis Services peut prendre en charge des cubes multidimensionnels conventionnelles, ou dans les modèles tabulaires, mais une instance ne peut pas prendre en charge deux types de modèles. Par conséquent, avant d’essayer de créer une requête MDX sur un cube, vérifiez que l’instance Analysis Services contient les modèles multidimensionnels.

## <a name="what-is-an-olap-cube"></a>Qu’est un cube OLAP ?

OLAP est l’abréviation de traitement analytique en ligne. Des solutions OLAP sont largement utilisées pour capturer et stocker des données critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [traitement analytique en ligne](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fournit [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), ce qui vous permet de concevoir, déployer et interroger des données OLAP sous la forme de _cubes_ ou _les modèles tabulaires_. Un cube est une base de données multidimensionnelle. _Dimensions_ sont comme les facettes des données, ou facteurs dans r : dimensions vous permet d’identifier un sous-ensemble spécifique des données que vous souhaitez synthétiser ou analyser. Par exemple, le temps est une dimension importante, bien afin que de nombreuses solutions OLAP incluent plusieurs calendriers définis par défaut, à utiliser lors de la segmentation et de synthèse de données. 

Pour des raisons de performances, une base de données OLAP calcule souvent des résumés (ou _agrégations_) à l’avance, puis les stocke pour une récupération plus rapide. Résumés sont basées sur *mesures*, qui représentent des formules qui peuvent être appliqués à des données numériques. Votre utilisent les dimensions pour définir un sous-ensemble de données, vous devez calculer la mesure sur ces données. Par exemple, vous utiliseriez une mesure pour calculer le total des ventes pour une ligne de produit spécifique sur plusieurs trimestres moins de taxe, les frais de livraison moyenne pour un fournisseur particulier, year-to-date cumulatives salaires et ainsi de suite de rapports.

MDX, abréviation d’expressions multidimensionnelles, est la langue utilisée pour interroger des cubes. En règle générale, une requête MDX contient une définition de données qui inclut une ou plusieurs dimensions et au moins une mesure, bien que les requêtes MDX peuvent obtenir beaucoup plus complexes et inclure windows propagées, des moyennes cumulatives, des sommes, rangs ou centiles. 

Voici d’autres termes qui peuvent être utiles lorsque vous commencez à créer des requêtes MDX :

+ *Découpage* prend un sous-ensemble du cube à l’aide de valeurs à partir d’une seule dimension.

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>L’utilisation d’olapR pour créer des requêtes MDX

L’article suivant fournit des exemples détaillés de la syntaxe de création ou de l’exécution de requêtes par rapport à un cube :

+ [Comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>API d’olapR

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX :

- **Utilisez le Générateur MDX.** Utilisez les fonctions R dans le package pour générer une requête MDX simple, en choisissant un cube, puis en définissant axes et les segments. Il s’agit d’un moyen simple de générer une requête MDX valide si vous n’avez pas accès à des outils OLAP traditionnels, ou que vous n’avez pas une connaissance approfondie du langage MDX.

    Toutes les requêtes MDX peuvent être créés à l’aide de cette méthode, MDX peut être complexe. Toutefois, cette API prend en charge la plupart des opérations plus courantes et utiles, y compris tranche dice, exploration vers le bas, rollup et pivot dans N dimensions.

+ **Copier-coller MDX correct.** Créer manuellement, puis collez dans n’importe quelle requête MDX. Cette option est la meilleure si vous avez des requêtes MDX existantes que vous souhaitez réutiliser, ou si la requête que vous souhaitez générer est trop complexe pour **olapR** à gérer.

    Après avoir généré votre code MDX à l’aide d’un utilitaire client, tels que SSMS ou Excel, enregistrez la chaîne de requête. Fournir cette chaîne MDX en tant qu’argument à la *Gestionnaire de requêtes SSAS* dans le **olapR** package. Le fournisseur envoie la requête au serveur Analysis Services spécifié et passe à nouveau les résultats à R. 

Pour obtenir des exemples montrant comment créer un MDX interrogent ou exécuter une requête MDX existante, voir [comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie certains problèmes connus et les questions courantes sur le **olapR** package.

### <a name="tabular-model-support"></a>Prise en charge de modèle tabulaire

Si vous vous connectez à une instance d’Analysis Services qui contient un modèle tabulaire, le `explore` fonction signale une réussite avec une valeur de retour TRUE. Toutefois, les objets de modèle tabulaire sont différents des objets multidimensionnels, et la structure d’une base de données multidimensionnelle est différente de celui d’un modèle tabulaire.

Bien que DAX (analyse des données Expressions) est le langage généralement utilisé avec les modèles tabulaires, vous pouvez concevoir des requêtes MDX valides par rapport à un modèle tabulaire, si vous êtes déjà familiarisé avec MDX. Vous ne pouvez pas utiliser les constructeurs olapR pour générer des requêtes MDX valides par rapport à un modèle tabulaire.

Toutefois, les requêtes MDX sont un moyen inefficace pour récupérer des données à partir d’un modèle tabulaire. Si vous avez besoin obtenir des données à partir d’un modèle tabulaire pour une utilisation dans R, tenez compte des ces méthodes au lieu de cela :

+ Activer DirectQuery sur le modèle et ajoutez le serveur comme un serveur lié dans SQL Server. 
+ Si le modèle tabulaire a été créé sur un data mart relationnel, obtenir les données directement à partir de la source.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Comment déterminer si une instance contient les modèles tabulaires ou multidimensionnels

Une seule instance d’Analysis Services peut contenir qu’un seul type de modèle, même si elle peut contenir plusieurs modèles. La raison est qu’il existe des différences fondamentales entre les modèles tabulaires et les modèles multidimensionnels contrôlant la façon dont les données sont stockées et traitées. Par exemple, les modèles tabulaires sont stockées en mémoire et tirer parti des index columnstore pour effectuer des calculs très rapides. Dans les modèles multidimensionnels, les données sont stockées sur le disque et les agrégations sont définies à l’avance et récupérées à l’aide de requêtes MDX.

Si vous vous connectez à Analysis Services à l’aide d’un client tel que SQL Server Management Studio, vous pouvez indiquer un coup de œil le type de modèle est pris en charge, en examinant l’icône de la base de données.

Vous pouvez également afficher et interroger les propriétés du serveur pour déterminer le type de modèle prend en charge de l’instance. Le **mode serveur** propriété prend en charge deux valeurs : _multidimensionnelles_ ou _tabulaire_.

Consultez l’article suivant pour obtenir des informations générales sur les deux types de modèles :

+ [Comparaison des modèles multidimensionnels et tabulaires](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Consultez l’article suivant pour plus d’informations sur l’interrogation des propriétés du serveur :

+ [Ensembles de lignes de schéma OLE DB pour OLAP](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>L’écriture différée n’est pas pris en charge.

Il n’est pas possible d’écrire les résultats des calculs R personnalisés dans le cube.

En général, même lorsqu’un cube est activé pour l’écriture différée, seules les opérations limitées sont prises en charge et configuration supplémentaire peut être requise. Nous vous recommandons d’utiliser MDX pour ces opérations.

+ [Dimensions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Définir un accès personnalisé aux données des cellules](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>Requêtes MDX à long terme bloquent le traitement de cube

Bien que le **olapR** package effectue uniquement des opérations de lecture, longues requêtes MDX peuvent créer des verrous qui empêchent le cube à partir d’en cours de traitement. Testez toujours vos requêtes MDX à l’avance afin que vous sachiez que la quantité de données doit être retourné.

Si vous essayez de vous connecter à un cube est verrouillé, vous pouvez obtenir une erreur indiquant que l’entrepôt de données SQL Server ne peut pas être atteint. Résolutions suggérées incluent l’activation des connexions à distance, la vérification du serveur ou nom de l’instance et ainsi de suite ; Toutefois, envisagez la possibilité d’une connexion ouverte préalable.

Un administrateur SSAS peut empêcher des problèmes de verrouillage en identifiant et terminer les sessions ouvertes. Une propriété de délai d’attente peut également être appliquée aux requêtes MDX au niveau du serveur pour forcer l’arrêt de toutes les requêtes à long terme.

## <a name="resources"></a>Ressources

Si vous ne connaissez à OLAP ou à des requêtes MDX, consultez les articles de Wikipedia : 

+ [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
+ [Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
