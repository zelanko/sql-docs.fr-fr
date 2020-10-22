---
title: Utilisation de données à partir de cubes OLAP dans R
description: Cet article décrit l’API olapR, ainsi qu’une vue d’ensemble des utilisateurs OLAP et MDX pour R pouvant être nouveaux dans les bases de données de cubes multidimensionnels.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 04/15/2018
ms.topic: how-to
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 5a5219b034abdd390a77e1dacd6b2b71d83a770e
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92195763"
---
# <a name="using-data-from-olap-cubes-in-r"></a>Utilisation de données à partir de cubes OLAP dans R
[!INCLUDE [SQL Server 2016 and later](../../includes/applies-to-version/sqlserver2016.md)]

Le package **olapR** est un package R, fourni par Microsoft pour une utilisation avec Machine Learning Server et SQL Server, qui vous permet d’exécuter des requêtes MDX pour obtenir des données à partir de cubes OLAP. Avec ce package, vous n’avez pas besoin de créer de serveurs liés ou de nettoyer les ensembles de lignes aplatis. Vous pouvez obtenir les données OLAP directement depuis R.

Cet article décrit l’API, ainsi qu’une vue d’ensemble des utilisateurs OLAP et MDX pour R pouvant être nouveaux dans les bases de données de cubes multidimensionnels.

> [!IMPORTANT]
> Une instance Analysis Services peut prendre en charge des cubes multidimensionnels conventionnels ou des modèles tabulaires. Toutefois, une instance ne peut pas prendre en charge les deux types de modèles. Par conséquent, avant d’essayer de générer une requête MDX sur un cube, vérifiez que l’instance Analysis Services contient des modèles multidimensionnels.

## <a name="what-is-an-olap-cube"></a>Qu’est-ce qu’un cube OLAP ?

OLAP signifie Traitement analytique en ligne. Les solutions OLAP sont couramment utilisées pour capturer et stocker des données métier critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [Traitement analytique en ligne](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fournit [Analysis Services](/analysis-services/analysis-services-overview), qui permet de concevoir, de déployer et d’interroger des données OLAP sous la forme de _cubes_ ou de _modèles tabulaires_. Un cube est une base de données multidimensionnelle. Les _dimensions_ sont comme des facettes de données, ou des facteurs dans R : vous utilisez des dimensions pour identifier un sous-ensemble particulier de données que vous souhaitez synthétiser ou analyser. Par exemple, le temps est une dimension importante. C’est pourquoi de nombreuses solutions OLAP incluent plusieurs calendriers définis par défaut, à utiliser lors du découpage et de la synthèse des données. 

Pour des raisons de performances, une base de données OLAP calcule souvent des résumés (ou des _agrégations_) à l’avance, puis les stocke pour une récupération plus rapide. Les résumés sont basés sur des *mesures*, qui représentent des formules qui peuvent être appliquées aux données numériques. Vous utilisez les dimensions pour définir un sous-ensemble de données, puis vous calculez la mesure sur ces données. Par exemple, vous pouvez utiliser une mesure pour calculer les ventes totales pour une ligne de produits donnée sur plusieurs trimestres moins les taxes, pour générer un rapport sur les frais d’expédition moyens d’un fournisseur particulier ou le cumul annuel des salaires jusqu’à ce jour etc.

MDX (ou expressions multidimensionnelles), est le langage utilisé pour l’interrogation des cubes. Une requête MDX contient généralement une définition de données qui inclut une ou plusieurs dimensions, et au moins une mesure. Toutefois, les requêtes MDX peuvent devenir beaucoup plus complexes et inclure des fenêtres enchaînées, des moyennes cumulées, des sommes, des rangs ou des centiles. 

Voici d’autres termes qui vous seront peut-être utiles lorsque vous commencerez à créer des requêtes MDX :

+ Le  *découpage* prend un sous-ensemble du cube à l’aide de valeurs provenant d’une dimension unique.

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Guide pratique pour créer des requêtes MDX à l’aide d’olapR

L’article suivant fournit des exemples détaillés de la syntaxe permettant de créer ou d’exécuter des requêtes sur un cube :

+ [Guide pratique pour créer des requêtes MDX à l’aide d’olapR](../../machine-learning/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>API olapr

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX :

- **Utilisez le générateur MDX.** Utilisez les fonctions R du package pour générer une requête MDX simple, en choisissant un cube, puis en définissant les axes et les segments. À l’aide de ces fonctions, vous pouvez générer facilement une requête MDX valide si vous n’avez pas accès à des outils OLAP traditionnels ou si vous n’avez pas une connaissance approfondie du langage MDX.

    Toutes les requêtes MDX ne peuvent pas être créées à l’aide de cette méthode, car MDX peut être complexe. Toutefois, cette API prend en charge la plupart des opérations les plus courantes et les plus utiles, notamment découper en tranches, découper en cubes, descendre dans la hiérarchie, regrouper et pivoter dans N dimensions.

+ **Copiez-collez des expressions multidimensionnelles bien formées.** Créez manuellement, puis collez n’importe quelle requête MDX. Cette option est idéale si vous souhaitez réutiliser des requêtes MDX existantes ou si la requête que vous souhaitez générer est trop complexe pour être gérée par **olapR** .

    Après avoir généré votre MDX à l’aide d’un utilitaire client, tel que SSMS ou Excel, enregistrez la chaîne de requête. Fournissez cette chaîne MDX comme argument au *gestionnaire de requêtes SSAS* du package **olapR**. Le fournisseur envoie la requête au serveur Analysis Services spécifié et transmet les résultats à R. 

Pour obtenir des exemples illustrant comment générer une requête MDX ou exécuter une requête MDX existante, consultez [Guide pratique pour créer des requêtes MDX à l’aide de R](../../machine-learning/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie certains problèmes connus et les questions les plus fréquentes concernant le package **olapR**.

### <a name="tabular-model-support"></a>Prise en charge des modèles tabulaires

Si vous vous connectez à une instance d’Analysis Services contenant un modèle tabulaire, la fonction `explore` signale la réussite de l’opération en renvoyant la valeur TRUE. Toutefois, les objets de modèle tabulaire sont différents des objets multidimensionnels, et la structure d’une base de données multidimensionnelle est différente de celle d’un modèle tabulaire.

Bien que DAX (Data Analysis Expressions) soit le langage généralement utilisé avec les modèles tabulaires, vous pouvez concevoir des requêtes MDX valides sur un modèle tabulaire, si vous êtes déjà familiarisé avec MDX. Vous ne pouvez pas utiliser les constructeurs olapR pour créer des requêtes MDX valides sur un modèle tabulaire.

Toutefois, les requêtes MDX sont un moyen inefficace de récupérer des données à partir d’un modèle tabulaire. Si vous avez besoin d’obtenir des données à partir d’un modèle tabulaire pour une utilisation dans R, envisagez plutôt ces méthodes :

+ Activez DirectQuery sur le modèle et ajoutez le serveur en tant que serveur lié dans SQL Server. 
+ Si le modèle tabulaire a été créé sur un mini-Data Warehouse relationnel, obtenez les données directement à partir de la source.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Comment déterminer si une instance contient des modèles tabulaires ou multidimensionnels ?

Une seule instance d’Analysis Services ne peut contenir qu’un seul type de modèle, même si elle peut contenir plusieurs modèles. Cela est dû au fait qu’il existe des différences fondamentales entre les modèles tabulaires et les modèles multidimensionnels qui régissent la façon dont les données sont stockées et traitées. Par exemple, les modèles tabulaires sont stockés en mémoire et exploitent des index columnStore pour effectuer des calculs très rapides. Dans les modèles multidimensionnels, les données sont stockées sur le disque et les agrégations sont définies à l’avance et récupérées à l’aide de requêtes MDX.

Si vous vous connectez à Analysis Services à l’aide d’un client tel que SQL Server Management Studio, vous pouvez déterminer d’un coup d’œil le type de modèle pris en charge à l’aide de l’icône de la base de données.

Vous pouvez également afficher et interroger les propriétés du serveur pour déterminer le type de modèle pris en charge par l’instance. La propriété **Mode du serveur** prend en charge deux valeurs : _multidimensionnel_ ou _tabulaire_.

Pour obtenir des informations générales sur les deux types de modèles, consultez l’article suivant :

+ [Comparaison de modèles multidimensionnels et tabulaires](/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Pour plus d’informations sur l’interrogation des propriétés du serveur, consultez l’article suivant :

+ [Ensembles de lignes de schéma OLE DB pour OLAP](/previous-versions/sql/sql-server-2012/ms126079(v=sql.110))

### <a name="writeback-is-not-supported"></a>L’écriture différée n’est pas prise en charge.

Il est impossible d’écrire en différé les résultats des calculs R personnalisés dans le cube.

En général, même lorsqu’un cube est compatible avec l’écriture différée, seules les opérations limitées sont prises en charge, et une configuration supplémentaire peut être nécessaire. Nous vous recommandons d’utiliser MDX pour ces opérations.

+ [Dimensions activées en écriture](/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitions activées en écriture](/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Définir un accès personnalisé à des données de cellule](/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>Les requêtes MDX de longue durée bloquent le traitement du cube

Bien que le package **olapR** effectue uniquement des opérations de lecture, les requêtes MDX longues peuvent créer des blocages qui empêchent le traitement du cube. Testez toujours vos requêtes MDX à l’avance pour savoir quelle quantité de données doit être renvoyée.

Si vous essayez de vous connecter à un cube verrouillé, vous risquez d’obtenir une erreur indiquant que l’entrepôt de données SQL Server ne peut pas être atteint. Les solutions suggérées incluent l’activation des connexions à distance, la vérification du nom du serveur ou de l’instance, etc. Toutefois, il se peut qu’une connexion ait été précédemment ouverte.

Un administrateur SSAS peut empêcher les problèmes de verrouillage en identifiant et en arrêtant les sessions ouvertes. Une propriété Timeout peut également être appliquée aux requêtes MDX au niveau du serveur pour forcer l’arrêt de toutes les requêtes longues.

## <a name="resources"></a>Ressources

Si vous débutez dans l’utilisation d’OLAP ou des requêtes MDX, consultez les articles suivants sur Wikipedia : 

+ [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
+ [Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)