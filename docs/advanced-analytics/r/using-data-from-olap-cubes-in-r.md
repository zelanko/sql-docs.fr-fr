---
title: "À l’aide des données à partir de cubes OLAP dans R | Documents Microsoft"
ms.custom: 
ms.date: 11/03/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: "12"
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.workload: On Demand
ms.openlocfilehash: 1c55a5b834cd91478a87ded7ebb86884117c7bfb
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="using-data-from-olap-cubes-in-r"></a>À l’aide des données à partir de cubes OLAP dans R

Le **olapR** package est un package R, fourni par Microsoft pour une utilisation avec Machine Learning Server et SQL Server R Services, qui vous permet d’exécuter les requêtes MDX pour obtenir des données à partir de cubes OLAP. Avec ce package, vous n’avez pas besoin de créer des serveurs liés ou de nettoyage des ensembles de lignes aplati ; Vous pouvez utiliser des données OLAP directement dans R.

Cet article décrit l’API, ainsi que d’une vue d’ensemble fo OLAP et MDX pour les utilisateurs de R peut être de nouveau aux bases de données de cube multidimensionnel.

## <a name="what-is-an-olap-cube"></a>Qu’est un cube OLAP ?

OLAP est l’abréviation de traitement analytique en ligne. Des solutions OLAP sont couramment utilisées pour capturer et stocker des données critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [traitement analytique en ligne](https://en.wikipedia.org/wiki/Online_analytical_processing).

Microsoft fournit [Analysis Services](https://docs.microsoft.com/sql/analysis-services/analysis-services), ce qui vous permet de concevoir, déployer et interroger des données OLAP sous la forme de _cubes_ ou _les modèles tabulaires_. Un cube est une base de données multidimensionnel. _Dimensions_ ressemblent à facettes des données, ou facteurs dans r : dimensions vous permet d’identifier un sous-ensemble spécifique de données que vous souhaitez synthétiser ou analyser. Par exemple, le temps est une dimension importante, bien afin que de nombreuses solutions OLAP incluent plusieurs calendriers définis par défaut, à utiliser lors de la segmentation et de résumer les données. 

Pour des raisons de performances, une base de données OLAP calcule souvent résumés (ou _agrégations_) à l’avance, puis les stocke pour une récupération plus rapide. Récapitulatifs sont basées sur *mesures*, qui représentent des formules qui peuvent être appliquées à des données numériques. Vous utilisez les dimensions pour définir un sous-ensemble de données et vous devez calculez la mesure sur ces données. Par exemple, vous utiliseriez une mesure pour calculer le total des ventes pour une ligne de produit spécifique sur plusieurs trimestres moins taxes, pour signaler les coûts d’expédition moyenne pour un fournisseur particulier, year-to-date cumulatives salaires et ainsi de suite.

MDX, abréviation d’expressions multidimensionnelles, est la langue utilisée pour interroger des cubes. Une requête MDX contient généralement une définition de données qui inclut une ou plusieurs dimensions et au moins une mesure, thogh des requêtes MDX peuvent devenir beaucoup plus complexes et inclure la restauration de windows, les moyennes mobiles cumulatives ou les sommes, centiles. 

Voici d’autres termes qui peuvent être utiles lorsque vous commencez à créer des requêtes MDX :

+ *Le découpage* prend un sous-ensemble du cube à l’aide de valeurs à partir d’une seule dimension.

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

Cette rubrique fournit des exemples supplémentaires de la syntaxe de base pour les requêtes sur un cube : 

+ [Comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

## <a name="olapr-api"></a>olapR API

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX :

- **Utilisez le Générateur MDX.** Utilisez les fonctions R dans le package pour générer une requête MDX simple, en choisissant un cube et les axes de paramètre et les segments. Il s’agit d’un moyen simple pour créer une requête MDX valide, si vous n’avez pas accès à des outils traditionnels OLAP, ou que vous ne disposez pas des connaissances approfondies du langage MDX.

    Toutes les requêtes MDX possibles peuvent être créés à l’aide de cette méthode, MDX peut être complexe. Toutefois, cette API prend en charge la plupart des opérations plus courantes et utiles, y compris tranche, dés, exploration vers le bas, rollup et pivot dans les dimensions de N.

+ **Copier-coller MDX bien formé.** Créer manuellement, puis les coller dans une requête MDX. Cette option est la meilleure si vous avez des requêtes MDX existants que vous souhaitez réutiliser, ou si la requête que vous souhaitez générer est trop complexe pour **olapR** à gérer. 

    Générer votre MDX à l’aide d’un utilitaire client, SSMS ou Excel, par exemple, puis enregistrez la chaîne qui définit la requête MDX. Vous fournissez cette chaîne MDX en tant qu’argument à la *Gestionnaire de requête SSAS* dans les **olapR** package. La fonction envoie la requête au serveur Analysis Services spécifié et passe à nouveau les résultats vers R, si que vous êtes autorisé à interroger le cube naturellement.

Pour obtenir des exemples de génération MDX de requête ou exécuter une requête MDX existante, voir [comment créer des requêtes MDX à l’aide de R](../../advanced-analytics/r/how-to-create-mdx-queries-using-olapr.md).

## <a name="known-issues"></a>Problèmes connus

### <a name="tabular-models-not-supported"></a>Non pris en charge les modèles tabulaires

+ Si vous vous connectez à une instance tabulaire d’Analysis Services, le `explore` fonction signale une réussite avec une valeur de retour de la valeur TRUE. Toutefois, les objets de modèle tabulaire ne sont pas un type compatible et ne peut pas être explorés.

+ Les modèles tabulaires peuvent être interrogées à l’aide de DAX ou MDX. Si vous concevez une requête MDX valide par rapport à un modèle tabulaire à l’aide d’un outil externe et puis collez la requête dans cette API, la requête retourne un résultat NULL et ne signale pas d’erreur.

## <a name="resources"></a>Ressources

Si vous débutez dans l’utilisation d’OLAP ou des requêtes MDX, consultez les articles suivants sur Wikipedia : [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
[Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>Exemples

Si vous souhaitez en savoir plus sur les cubes, vous pouvez créer le cube qui est utilisé dans ces exemples en suivant le didacticiel Analysis Services jusqu’à la leçon 4 : [Création d’un cube OLAP](../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)

Vous pouvez également télécharger un cube existant en tant que sauvegarde et le restaurer sur une instance d’Analysis Services. Par exemple, vous pouvez télécharger un cube entièrement traité pour le [modèle multidimensionnel Adventure Works SQL2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334), au format compressé, puis le restaurer sur votre instance de SSAS. Pour plus d’informations, consultez [Sauvegarde et restauration](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)ou [Applet de commande Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).
