---
title: "Utilisation de données à partir de cubes OLAP dans R | Microsoft Docs"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- R
ms.assetid: 8093599c-8307-4237-983b-0908d0f8ab77
caps.latest.revision: 12
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 8fe9d54e1d635b5c8f1dd6e00e33bd92136343b4
ms.contentlocale: fr-fr
ms.lasthandoff: 09/21/2017

---
# <a name="using-data-from-olap-cubes-in-r"></a>Utilisation de données à partir de cubes OLAP dans R

Le package **olapR** est un nouveau package R dans Microsoft R Server et SQL Server R Services, qui vous permet d’exécuter des requêtes MDX et d’utiliser les données de cubes OLAP dans votre solution R.

Avec ce package, vous n’avez pas besoin de créer de serveurs liés ou de nettoyer les ensembles de lignes aplatis. Vous pouvez utiliser les données OLAP directement dans R.

## <a name="overview"></a>Vue d'ensemble

Un cube OLAP est une base de données multidimensionnelle qui contient des agrégations précalculées sur des *mesures*, qui capturent généralement des métriques métier importantes telles que le montant des ventes, le nombre de ventes ou d’autres valeurs numériques. Les cubes OLAP sont couramment utilisés pour capturer et stocker des données métier critiques au fil du temps. Les données OLAP sont utilisées pour l’analytique d’entreprise par différents outils, tableaux de bord et visualisations. Pour plus d’informations, consultez [Online analytical processing (Traitement analytique en ligne)](https://en.wikipedia.org/wiki/Online_analytical_processing)

Le package **olapR** prend en charge deux méthodes de création de requêtes MDX : 

- Vous pouvez générer une requête MDX simple à l’aide d’une API de type R pour choisir un cube, des axes et des segments. À l’aide de ces fonctions, vous pouvez générer des requêtes MDX valides même si vous n’avez pas accès à des outils OLAP traditionnels ou si vous n’avez pas une connaissance approfondie du langage MDX.

  Le langage MDX pouvant être très complexe, sachez qu’il n’est pas possible de créer toutes les requêtes MDX à l’aide de cette méthode dans le package **olapR** . Toutefois, toutes les opérations les plus courantes et les plus utiles sont prises en charge, notamment découper en tranches, découper en cubes, descendre dans la hiérarchie, regrouper et pivoter dans N dimensions.

+ Vous pouvez créer manuellement puis coller n’importe quelle requête MDX. Cette option est utile si vous souhaitez réutiliser des requêtes MDX existantes ou si la requête que vous souhaitez générer est trop complexe pour être gérée par **olapR** . 

  Avec cette approche, vous générez votre code MDX à l’aide d’un utilitaire client, tel que SSMS ou Excel, puis vous l’utilisez comme argument de chaîne pour le *Gestionnaire de requêtes SSAS* fourni par ce package. La fonction **olapR** envoie la requête au serveur Analysis Services spécifié et transmet les résultats à R.

Pour obtenir des exemples illustrant comment générer une requête MDX ou exécuter une requête MDX existante, consultez [Guide pratique pour créer des requêtes MDX à l’aide de R](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md).


## <a name="mdx-basics"></a>Principes de base de MDX

Les données d’un cube peuvent être récupérées à l’aide du langage de requête MDX (MultiDimensional Expression). Les données d’un cube OLAP (ou d’une base de données Analysis Services) étant multidimensionnelles plutôt que tabulaires, MDX prend en charge une syntaxe complexe et diverses opérations de filtrage et de découpage des données :

+ Le*découpage en tranches* prend un sous-ensemble du cube en choisissant une valeur pour une dimension, ce qui génère un cube ayant une dimension de moins. 

+ Le*découpage en cubes* crée un sous-cube en spécifiant une plage de valeurs sur plusieurs dimensions.

+ La*descente dans la hiérarchie* permet de naviguer d’un résumé vers les détails.

+ La*montée dans la hiérarchie* permet de passer des détails à un niveau d’agrégation plus élevé.

+ Le*regroupement* résume les données sur une dimension.

+ La*rotation* faire pivoter le cube ou la sélection de données.

Cette rubrique fournit des exemples supplémentaires qui illustrent la syntaxe de base pour l’interrogation d’un cube.
[Guide pratique pour créer des requêtes MDX à l’aide d’olapR](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)


## <a name="known-issues"></a>Problèmes connus

### <a name="tabular-models-not-supported-currently"></a>Les modèles tabulaires ne sont pas pris en charge actuellement

Vous pouvez vous connecter à une instance d’Analysis Services tabulaire et la fonction `explore` indique que l’opération a réussi avec une valeur de retour TRUE, mais les objets de modèle tabulaire ne sont pas un type compatible et ne peuvent pas être explorés. 

Les modèles tabulaires prennent en charge les requêtes MDX, mais une requête MDX valide exécutée sur un modèle tabulaire retourne un résultat NULL sans signaler d’erreur.

## <a name="resources"></a>Ressources

Si vous débutez dans l’utilisation d’OLAP ou des requêtes MDX, consultez les articles suivants sur Wikipedia : [Cubes OLAP](https://en.wikipedia.org/wiki/OLAP_cube)
[Requêtes MDX](https://en.wikipedia.org/wiki/MultiDimensional_eXpressions)

### <a name="samples"></a>Exemples

Si vous souhaitez en savoir plus sur les cubes, vous pouvez créer le cube qui est utilisé dans ces exemples en suivant le didacticiel Analysis Services jusqu’à la leçon 4 : [Création d’un cube OLAP](/sql-docs/docs/analysis-services/multidimensional-modeling-adventure-works-tutorial)

Vous pouvez également télécharger un cube existant en tant que sauvegarde et le restaurer sur une instance d’Analysis Services. Par exemple, vous pouvez télécharger un cube entièrement traité pour le [modèle multidimensionnel Adventure Works SQL2014](http://msftdbprodsamples.codeplex.com/downloads/get/882334), au format compressé, puis le restaurer sur votre instance de SSAS. Pour plus d’informations, consultez [Sauvegarde et restauration](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)ou [Applet de commande Restore-ASDatabase](../../analysis-services/powershell/restore-asdatabase-cmdlet.md).

## <a name="see-also"></a>Voir aussi
[Guide pratique pour créer des requêtes MDX à l’aide d’olapR](../../advanced-analytics/r-services/how-to-create-mdx-queries-using-olapr.md)

[Concepteur de requêtes MDX pour Analysis Services](http://msdn.microsoft.com/library/7e288eee-2d37-485e-a6a0-dbba5e041e26)



