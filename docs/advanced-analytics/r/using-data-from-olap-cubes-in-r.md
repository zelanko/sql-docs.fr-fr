---
title: Utilisation de données de cubes OLAP dans R
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ec50ee1b10a51e16b72d7ffc110448dcf016a13f
ms.sourcegitcommit: 321497065ecd7ecde9bff378464db8da426e9e14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68714974"
---
# <a name="using-data-from-olap-cubes-in-r"></a>Utilisation de données de cubes OLAP dans R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Le package olapr est un package R, fourni par Microsoft pour une utilisation avec Machine Learning Server et SQL Server, qui vous permet d’exécuter des requêtes MDX pour obtenir des données à partir de cubes OLAP. Avec ce package, vous n’avez pas besoin de créer des serveurs liés ou de nettoyer des ensembles de lignes aplatis. vous pouvez accéder aux données OLAP directement à partir de R.

Cet article décrit l’API, ainsi qu’une vue d’ensemble d’OLAP et MDX pour les utilisateurs de R qui peuvent être nouveaux dans les bases de données de cube multidimensionnels.

> [!IMPORTANT]
> Une instance de Analysis Services peut prendre en charge des cubes multidimensionnels conventionnels ou des modèles tabulaires, mais une instance ne peut pas prendre en charge les deux types de modèles. Par conséquent, avant d’essayer de générer une requête MDX sur un cube, vérifiez que l’instance Analysis Services contient des modèles multidimensionnels.

## <a name="what-is-an-olap-cube"></a>Qu’est-ce qu’un cube OLAP?

OLAP est une abréviation réduite pour le traitement analytique en ligne. Les solutions OLAP sont largement utilisées pour la capture et le stockage des données d’entreprise critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [traitement analytique en ligne](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fournit [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), qui vous permet de concevoir, de déployer et d’interroger des données OLAP sous forme de cubes ou de _modèles tabulaires_. Un cube est une base de données multidimensionnelle. Les _dimensions_ sont semblables aux facettes des données, ou facteurs dans R: vous utilisez des dimensions pour identifier un sous-ensemble particulier de données que vous souhaitez synthétiser ou analyser. Par exemple, le temps est une dimension importante, si bien que de nombreuses solutions OLAP incluent plusieurs calendriers définis par défaut, à utiliser lors du découpage et de la synthèse des données. 

Pour des raisons de performances, une base de données OLAP calcule souventdes résumés (ou agrégations) à l’avance, puis les stocke pour une récupération plus rapide. Les résumés sont basés sur des *mesures*, qui représentent des formules qui peuvent être appliquées à des données numériques. Vous utilisez les dimensions pour définir un sous-ensemble de données, puis vous calculez la mesure sur ces données. Par exemple, vous pouvez utiliser une mesure pour calculer les ventes totales pour une ligne de produits donnée sur plusieurs trimestres moins les taxes, pour signaler les frais d’expédition moyens pour un fournisseur particulier, les salaires cumulatifs annuels à ce jour et ainsi de suite.

MDX, Short pour les expressions multidimensionnelles, est le langage utilisé pour interroger des cubes. Une requête MDX contient généralement une définition de données qui inclut une ou plusieurs dimensions, et au moins une mesure, bien que les requêtes MDX puissent devenir beaucoup plus complexes et inclure des fenêtres enchaînées, des moyennes cumulées, des sommes, des rangs ou des centile. 

Voici d’autres termes qui peuvent être utiles lorsque vous commencez à créer des requêtes MDX:

+ Le découpage utilise un sous-ensemble du cube à l’aide des valeurs d’une dimension unique.

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

## <a name="how-to-use-olapr-to-create-mdx-queries"></a>Comment utiliser OLAP pour créer des requêtes MDX

L’article suivant fournit des exemples détaillés de la syntaxe permettant de créer ou d’exécuter des requêtes sur un cube:

+ [Comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>API olapr

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX :

- **Utilisez le générateur MDX.** Utilisez les fonctions R du package pour générer une requête MDX simple, en choisissant un cube, puis en définissant les axes et les segments. Il s’agit d’un moyen simple de créer une requête MDX valide si vous n’avez pas accès à des outils OLAP traditionnels ou si vous n’avez pas une connaissance détaillée du langage MDX.

    Toutes les requêtes MDX ne peuvent pas être créées à l’aide de cette méthode, car MDX peut être complexe. Toutefois, cette API prend en charge la plupart des opérations les plus courantes et utiles, y compris les secteurs, les dés, les descente, les cumuls et les tableaux croisés dynamiques dans N.

+ **MDX correctement construit de copie/collage.** Créez et collez manuellement une requête MDX. Cette option est la meilleure si vous avez des requêtes MDX existantes que vous souhaitez réutiliser, ou si la requête que vous souhaitez générer est trop complexe pour être gérée par olapr.

    Après avoir généré votre MDX à l’aide d’un utilitaire client, tel que SSMS ou Excel, enregistrez la chaîne de requête. Fournissez cette chaîne MDX comme argument au *Gestionnaire de requêtes SSAS* dans le package **olapr** . Le fournisseur envoie la requête au serveur de Analysis Services spécifié et passe les résultats à R. 

Pour obtenir des exemples de création d’une requête MDX ou d’exécution d’une requête MDX existante, consultez [comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problèmes connus

Cette section répertorie certains problèmes connus et les questions les plus fréquentes concernant le package olapr.

### <a name="tabular-model-support"></a>Prise en charge des modèles tabulaires

Si vous vous connectez à une instance de Analysis Services qui contient un modèle tabulaire, `explore` la fonction signale la réussite avec la valeur de retour true. Toutefois, les objets de modèle tabulaire sont différents des objets multidimensionnels, et la structure d’une base de données multidimensionnelle est différente de celle d’un modèle tabulaire.

Bien que DAX (Data Analysis Expressions) soit le langage généralement utilisé avec les modèles tabulaires, vous pouvez concevoir des requêtes MDX valides sur un modèle tabulaire, si vous êtes déjà familiarisé avec MDX. Vous ne pouvez pas utiliser les constructeurs OLAP pour créer des requêtes MDX valides sur un modèle tabulaire.

Toutefois, les requêtes MDX sont un moyen inefficace de récupérer des données à partir d’un modèle tabulaire. Si vous avez besoin d’obtenir des données à partir d’un modèle tabulaire pour une utilisation dans R, envisagez plutôt ces méthodes:

+ Activez DirectQuery sur le modèle et ajoutez le serveur en tant que serveur lié dans SQL Server. 
+ Si le modèle tabulaire a été créé sur un mini-Data Warehouse relationnel, obtenez les données directement à partir de la source.

### <a name="how-to-determine-whether-an-instance-contains-tabular-or-multidimensional-models"></a>Comment déterminer si une instance contient des modèles tabulaires ou multidimensionnels

Une seule instance de Analysis Services ne peut contenir qu’un seul type de modèle, même si elle peut contenir plusieurs modèles. Cela est dû au fait qu’il existe des différences fondamentales entre les modèles tabulaires et les modèles multidimensionnels qui contrôlent la façon dont les données sont stockées et traitées. Par exemple, les modèles tabulaires sont stockés en mémoire et tirent parti des index ColumnStore pour effectuer des calculs très rapides. Dans les modèles multidimensionnels, les données sont stockées sur le disque et les agrégations sont définies à l’avance et récupérées à l’aide de requêtes MDX.

Si vous vous connectez à Analysis Services à l’aide d’un client tel que SQL Server Management Studio, vous pouvez déterminer d’un coup d’œil le type de modèle pris en charge, en examinant l’icône de la base de données.

Vous pouvez également afficher et interroger les propriétés du serveur pour déterminer le type de modèle pris en charge par l’instance. La propriété **mode serveur** prend en charge deux valeurs: multidimensionnelles ou _tabulaires_.

Pour obtenir des informations générales sur les deux types de modèles, consultez l’article suivant:

+ [Comparaison de modèles multidimensionnels et tabulaires](https://docs.microsoft.com/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas)

Pour plus d’informations sur l’interrogation des propriétés du serveur, consultez l’article suivant:

+ [Ensembles de lignes de schéma OLE DB pour OLAP](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets)

### <a name="writeback-is-not-supported"></a>L’écriture différée n’est pas prise en charge

Il n’est pas possible d’écrire les résultats des calculs R personnalisés dans le cube.

En général, même lorsqu’un cube est activé pour l’écriture différée, seules les opérations limitées sont prises en charge, et une configuration supplémentaire peut être nécessaire. Nous vous recommandons d’utiliser MDX pour ces opérations.

+ [Dimensions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions)
+ [Partitions activées en écriture](https://docs.microsoft.com/sql/analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-write-enabled-partitions)
+ [Définir un accès personnalisé à des données de cellule](https://docs.microsoft.com/sql/analysis-services/multidimensional-models/grant-custom-access-to-cell-data-analysis-services)

### <a name="long-running-mdx-queries-block-cube-processing"></a>Les requêtes MDX de longue durée bloquent le traitement du cube

Bien que le package olapr effectue uniquement des opérations de lecture, les requêtes MDX longues peuvent créer des verrous qui empêchent le traitement du cube. Testez toujours vos requêtes MDX à l’avance pour savoir quelle quantité de données doit être retournée.

Si vous essayez de vous connecter à un cube verrouillé, vous risquez d’obtenir une erreur indiquant que l’entrepôt de données SQL Server ne peut pas être atteint. Les solutions suggérées incluent l’activation des connexions à distance, la vérification du nom du serveur ou de l’instance, etc. Toutefois, tenez compte de la possibilité d’une connexion ouverte antérieure.

Un administrateur SSAS peut empêcher les problèmes de verrouillage en identifiant et en arrêtant les sessions ouvertes. Une propriété Timeout peut également être appliquée à des requêtes MDX au niveau du serveur pour forcer l’arrêt de toutes les requêtes longues.

## <a name="resources"></a>Ressources

Si vous débutez avec des requêtes OLAP ou MDX, consultez les articles suivants de Wikipedia: 

+ [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
+ [Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)
